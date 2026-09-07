[[01_EVENTGUARD]]
[[02_EVT_Fast_Object_Detection]]
# Referencias  

- [Página oficial IDS UE-39B0XCP-E](https://www.ids-imaging.us/store_us/ue-39b0xcp-e.html)  
- [Descargas y documentación IDS EVS](https://en.ids-imaging.com/download-details/1011378.html)  
- [Ficha técnica resumida](https://www.1stvision.com/cameras/models/IDS-Imaging/UE-39B0XCP-E)  
- [Descripción técnica adicional](https://aegis-elec.com/ids-ue-39b0xcp-e.html)  
# ¿Qué es esta cámara?  

La **UE-39B0XCP-E** es una cámara basada en eventos (*Event-Based Vision Sensor*). A diferencia de una cámara convencional, no envía imágenes completas a una frecuencia fija, sino que cada píxel genera eventos cuando detecta cambios de luminosidad.  

Ventajas:  

- Muy baja latencia.  

- Menor volumen de datos.  

- Excelente comportamiento ante movimientos rápidos.  

- Ausencia de *motion blur*.  

- Alto rango dinámico (HDR).  

  

### Especificaciones principales  

- Sensor: **Sony Prophesee IMX636**  

- Resolución: **1280 × 720**  

- Formato sensor: **1/2.5"**  

- Interfaz: **USB 3.0 (5 Gbps)**  

- Montura: **C-Mount**  

- Sensor monocromo  

- Consumo aproximado: **0.4 W - 2 W**  

  

## Hardware necesario  

  

### Obligatorio  

- Cámara UE-39B0XCP-E  

- Cable USB 3.0 Micro-B  

- PC Linux o Windows  

- Lente C-Mount  

  

### Recomendado  

- Lente de 6 mm o 8 mm  

- Puerto USB 3.0 dedicado  

- Trípode o soporte fijo  

  

## Conexión física  

  

### Montar la lente  

Roscar la lente C-Mount en la cámara.  

  

### Conectar por USB  

```text  

UE-39B0XCP-E  

│  

USB 3.0  

│  

PC  

```  

La cámara se alimenta directamente por USB y no necesita fuente externa.  

  

## Instalación del software  

La cámara utiliza el ecosistema de desarrollo de **Prophesee Metavision SDK** junto con un plugin específico de IDS.  

  

### Componentes necesarios  

- Metavision SDK  

- IDS HAL Plugin para cámaras uEye EVS  

  

### Recursos útiles  

- https://www.prophesee.ai/development-center/  

- https://www.prophesee.ai/metavision-sdk5-pro-request/  

- https://en.ids-imaging.com/download-details/1011378.html  

  

## Verificación de la instalación  

Comprobar que el sistema detecta la cámara:  

  

```bash  

lsusb  

```  

  

Comprobar que Metavision ve el dispositivo:  

  

```bash  

metavision_platform_info  

```  

  

o  

  

```bash  

metavision_viewer  

```  

  

Si todo es correcto, la cámara debería aparecer entre los dispositivos disponibles.  

  

## Primera visualización  

Lanzar:  

  

```bash  

metavision_viewer  

```  

  

Mover una mano delante de la cámara.  

  

Observaciones:  

- Cuando la escena está quieta apenas se generan eventos.  

- Cuando algo se mueve aparecen miles de eventos.  

- Cuanto más rápido es el movimiento, más eventos aparecen.  

  

## Cómo funcionan los datos  

Cada evento generado por el sensor contiene:  

  

```python  

{  

"x": 453,  

"y": 221,  

"t": 123456789,  

"p": 1  

}  

```  

  

Donde:  

- **x** → coordenada horizontal.  

- **y** → coordenada vertical.  

- **t** → timestamp.  

- **p** → polaridad (+1 o -1).  

  

## Primer programa en Python  

Lectura básica de eventos:  

  

```python  

from metavision_core.event_io import EventsIterator  

  

mv_iterator = EventsIterator("")  

  

for events in mv_iterator:  

print(f"Received {len(events)} events")  

```  

  

Esto verifica que la comunicación con la cámara funciona correctamente.  

  

## Generar pseudo-frames  

Aunque la cámara no produce imágenes convencionales, es habitual acumular eventos durante unos pocos milisegundos para formar una imagen temporal.  

  

```python  

import numpy as np  

  

frame = np.zeros((720, 1280), dtype=np.uint8)  

  

for ev in events:  

frame[ev["y"], ev["x"]] = 255  

```  

  

Visualización:  

  

```python  

import cv2  

  

cv2.imshow("events", frame)  

```  

  

Reinicio de la ventana temporal:  

  

```python  

frame[:] = 0  

```  

  

## Primera detección: movimiento  

La forma más sencilla de detectar actividad.  

  

```python  

if len(events) > 5000:  

motion_detected = True  

```  

  

Aplicaciones:  

- Presencia de personas.  

- Vigilancia.  

- Activación de sistemas.  

- Detección industrial.  

  

## Detección mediante clustering  

Una técnica habitual consiste en agrupar eventos espacialmente cercanos.  

  

### Pipeline  

```text  

Eventos  

↓  

Filtro temporal  

↓  

DBSCAN  

↓  

Bounding Box  

↓  

Tracking  

```  

  

### Ejemplo  

```python  

from sklearn.cluster import DBSCAN  

import numpy as np  

  

points = np.column_stack(  

(events["x"], events["y"])  

)  

  

clustering = DBSCAN(  

eps=8,  

min_samples=20  

).fit(points)  

```  

  

Cada cluster suele corresponder a un objeto en movimiento.  

  

## Bounding Boxes  

Una vez agrupados los eventos:  

  

```python  

x_min = points[:,0].min()  

x_max = points[:,0].max()  

  

y_min = points[:,1].min()  

y_max = points[:,1].max()  

```  

  

Obtendremos:  

  

```text  

+----------------------+  

| |  

| Objeto |  

| |  

+----------------------+  

```  

  

## Tracking básico  

Pipeline recomendado:  

  

```text  

Eventos  

↓  

Acumulación temporal  

↓  

DBSCAN  

↓  

Centroide  

↓  

Kalman Filter  

↓  

Track ID  

```  

  

Muy útil para:  

- Robots móviles.  

- Seguimiento de personas.  

- Drone tracking.  

- Sistemas de inspección rápida.  

  

## Detección rápida con OpenCV  

  

```python  

import cv2  

import numpy as np  

  

frame = np.zeros((720, 1280), np.uint8)  

  

for ev in events:  

frame[ev["y"], ev["x"]] = 255  

  

_, th = cv2.threshold(  

frame,  

20,  

255,  

cv2.THRESH_BINARY  

)  

  

contours, _ = cv2.findContours(  

th,  

cv2.RETR_EXTERNAL,  

cv2.CHAIN_APPROX_SIMPLE  

)  

  

for cnt in contours:  

x, y, w, h = cv2.boundingRect(cnt)  

  

if w * h > 500:  

cv2.rectangle(  

frame,  

(x, y),  

(x + w, y + h),  

255,  

2  

)  

```  

  

Resultado:  

  

```text  

Eventos  

↓  

Contornos  

↓  

Bounding Boxes  

↓  

Detecciones  

```  

  

## Integración con ROS2  

Pipeline típico:  

  

```text  

UE-39B0XCP-E  

↓  

Metavision SDK  

↓  

Acumulación 5-10 ms  

↓  

DBSCAN  

↓  

Bounding Box  

↓  

Tracker  

↓  

ROS2 Publisher  

```  

  

### Tópicos habituales  

  

```text  

/events  

/detections  

/tracks  

/camera_info  

```  

  

## Recomendaciones de configuración inicial  

  

### Acumulación temporal  

  

Comenzar con:  

  

```text  

5 ms  

```  

  

Si hay pocos eventos:  

  

```text  

10 ms  

```  

  

Si hay demasiados:  

  

```text  

2 ms  

```  

  

### Lente recomendada  

- Laboratorio: 6 mm  

- Uso general: 8 mm  

- Distancias largas: 12 mm  

  

### Escenarios ideales  

- Objetos rápidos.  

- Vibraciones mecánicas.  

- Robótica móvil.  

- Drones.  

- Seguimiento de proyectiles.  

- Motion capture.  

- Clasificación por movimiento.  

  

## Proyecto mínimo recomendado  

  

### Fase 1  

- Instalar Metavision SDK.  

- Verificar cámara en Metavision Viewer.  

  

### Fase 2  

- Leer eventos desde Python.  

- Mostrar contador de eventos.  

  

### Fase 3  

- Generar pseudo-frame cada 5 ms.  

  

### Fase 4  

- Aplicar DBSCAN.  

  

### Fase 5  

- Obtener bounding boxes.  

  

### Fase 6  

- Añadir tracking mediante Kalman Filter o SORT.  

  

### Fase 7  

- Publicar detecciones mediante ROS2.  

  

## Arquitectura recomendada para Jetson Orin Nano  

  

```text  

UE-39B0XCP-E  

│  

▼  

Metavision SDK  

│  

▼  

Acumulación temporal (5 ms)  

│  

▼  

DBSCAN  

│  

▼  

Bounding Boxes  

│  

▼  

Tracker (SORT/Kalman)  

│  

▼  

ROS2  

│  

├── /events  

├── /detections  

└── /tracks  

```  

  

## Siguiente nivel: detección mediante IA  

Una vez tengas el pipeline básico funcionando, suele ser más efectivo utilizar la cámara para generar pseudo-frames cada 5-10 ms y alimentar un detector tradicional:  

  

```text  

Eventos  

↓  

Acumulación temporal  

↓  

Pseudo-frame  

↓  

YOLO  

↓  

Detecciones  

↓  

Tracking  

```  

  

Alternativamente, pueden utilizarse modelos específicos para visión basada en eventos:  

- YOLO adaptado a eventos.  

- Event Camera Object Detection.  

- Spiking Neural Networks (SNN).  

- Event Transformers.  

- Networks incluidas en Metavision SDK.  

  

Para una primera prueba en Jetson Orin Nano, la opción más sencilla suele ser:  

  

```text  

Eventos → Pseudo-frame → YOLOv8n → SORT  

```  

  

porque permite reutilizar herramientas de visión artificial convencionales manteniendo gran parte de las ventajas de una cámara de eventos.