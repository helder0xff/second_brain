[[01_EVENTGUARD]]
# Índice  
- [[#1. Objeto y alcance ]] 
- [[#2. Escenario operativo]]
- [[#3. Arquitectura funcional]]
- [[#4. Requisitos funcionales]]  
- [[#5. Prestaciones mínimas]]  
- [[#6. Sensores]]  
- [[#7. Interfaces]]  
- [[#8. Entorno y operación]]  
- [[#9. Seguridad]]  
- [[#10. Transición TRL]]  
- [[#11. Puntos abiertos]]  
# 1. Objeto y alcance  

  EventGuard es un **sistema optrónico multisensor** destinado a mejorar la **observación, detección, reconocimiento, seguimiento y generación de alertas tempranas** ante tránsitos irregulares y actividades ilícitas en líneas limítrofes terrestres.  

El sistema debe:  
- Operar de forma continuada, `24 h / 365 días`.  
- Detectar personas, grupos de personas y vehículos.  
- Funcionar en condiciones ambientales y atmosféricas adversas.  
- Integrar canales MWIR o LWIR, VIS-NIR-SWIR y un sensor de eventos.  
- Incorporar procesamiento avanzado de imagen e inteligencia artificial embebida.  

- Permitir operación manual, semiautomática y automática.  

- Integrarse con SIVE o sistemas equivalentes.  

- Alcanzar un nivel TRL 7-8 en las fases posteriores del proyecto.  

  

## 2. Escenario operativo  

  

### 2.1. Área de vigilancia  

  

- Cobertura de hasta `1 km` a ambos lados de la línea limítrofe.  

- Longitud de línea vigilada de hasta `8 km`.  

- Exploración y observación continua.  

- Funcionamiento bajo todas las condiciones ambientales previstas.  

- Vigilancia de zonas terrestres con posibles tránsitos irregulares o ilícitos.  

  

### 2.2. Objetos de interés  

  

#### Personas y grupos  

  

- **Altura:** entre `1,5 m` y `1,8 m`.  

- **Peso:** entre `40 kg` y `120 kg`.  

- **Movimiento:** paso lento, paso rápido o carrera.  

- **Entorno:** campo abierto o zonas con presencia de vegetación.  

- **Obstáculos:** vallas, verjas, muros u otros elementos interpuestos.  

- **Diferencia térmica aparente respecto al fondo:** `10 °C`.  

- **Tamaño del grupo:** entre `1` y `50` personas.  

  

#### Vehículos  

  

- **Tipo:** turismo o todoterreno de gama baja o media.  

- **Velocidad:** entre `10 km/h` y `100 km/h`.  

- **Entorno:** vías terrestres o campo con presencia de vegetación.  

- **Diferencia térmica aparente respecto al fondo:** `10 °C`.  

- **Ocupación típica:** entre `3` y `5` personas.  

  

### 2.3. Modos de operación  

  

- **Manual:** el operador controla la observación, clasificación y generación de alertas.  

- **Semiautomático:** el sistema asiste al operador en la detección, seguimiento y evaluación.  

- **Automático:** la inteligencia artificial ejecuta las funciones de exploración, detección, clasificación, seguimiento y generación de alertas bajo la supervisión del operador.  

  

## 3. Arquitectura funcional  

  

### 3.1. Adquisición y procesamiento de imagen  

  

- Canal infrarrojo MWIR o LWIR.  

- Canal visible extendido VIS-NIR, con posible cobertura SWIR.  

- Sensor de eventos.  

- Procesamiento en tiempo real.  

- Mejora automática de contraste.  

- Reducción de ruido.  

- Realce de detalles.  

- Mejora de resolución y discriminación luminosa.  

- Fusión espacial y temporal de IR, visible y eventos.  

- Generación de productos de imagen adaptados al escenario.  

  

### 3.2. Inteligencia artificial  

  

- Detección automática de objetos de interés.  

- Clasificación e identificación de personas, grupos y vehículos.  

- Seguimiento automático.  

- Seguimiento multiobjetivo.  

- Análisis de comportamiento.  

- Evaluación de amenazas.  

- Generación automática de alertas tempranas.  

- Entrenamiento, validación y adaptación de modelos.  

- Parametrización de los modelos de inteligencia artificial.  

  

### 3.3. Estabilización y autotracking  

  

- Plataforma multieje.  

- Estabilización de la línea de mira.  

- Arquitectura jerárquica de control.  

- Apuntamiento grueso.  

- Ajuste fino.  

- Compensación de vibraciones.  

- Compensación de viento.  

- Compensación del movimiento de la plataforma.  

- Mantenimiento automático del objetivo en el centro de la imagen.  

- Funcionamiento con campos de visión muy estrechos.  

- Funcionamiento a distancias superiores a `25 km`.  

  

### 3.4. Interfaces e integración  

  

- Exportación de vídeo.  

- Exportación de datos y telemetría.  

- Exportación de detecciones, tracks y alertas.  

- Control local.  

- Control remoto sin pérdida de prestaciones.  

- Integración lógica y funcional con SIVE.  

- Sincronización temporal común entre subsistemas.  

- Registro trazable de vídeo, eventos, detecciones y parámetros de operación.  

  

## 4. Requisitos funcionales  

  

| ID | Función | Especificación |  

|---|---|---|  

| F1 | Captación optrónica multibanda | Adquisición sincronizada en MWIR, VIS-NIR y canal de eventos. |  

| F2 | Procesamiento avanzado | Mejora automática de contraste, resolución y fusión multisensor. |  

| F3 | Estabilización y orientación | Mantenimiento de la línea de mira, estabilización multieje y control angular preciso. |  

| F4 | Detección e identificación automática | Detección, identificación y clasificación mediante inteligencia artificial. |  

| F5 | Seguimiento automático | Seguimiento integrado de los objetivos detectados. |  

| F6 | Alertas tempranas | Generación manual, semiautomática y automática de alertas. |  

| F7 | Transmisión e integración | Envío de vídeo, datos y metadatos al puesto remoto y al sistema superior. |  

| F8 | Grabación y trazabilidad | Registro sincronizado de vídeo, detecciones, eventos y metadatos. |  

| F9 | Calibración de línea de mira | Ajuste horizontal y vertical para asegurar la precisión angular. |  

| F10 | Autodiagnóstico | Monitorización de subsistemas y comunicación de fallos. |  

| F11 | Gestión de modos | Cambio entre los modos manual, semiautomático y automático. |  

| F12 | Control remoto | Operación completa desde un puesto remoto. |  

| F13 | Sincronización temporal | Utilización de códigos comunes de tiempo y posición. |  

| F14 | Mantenimiento | Soporte al mantenimiento preventivo, correctivo y al diagnóstico. |  

| F15 | Grabación de vídeo | Grabación digital con resolución y compresión configurables. |  

  

## 5. Prestaciones mínimas  

  

### 5.1. Alcances en banda infrarroja  

  

| Objeto | Función | Probabilidad | Alcance |  

|---|---|---:|---:|  

| Persona | Detección | `95 %` | `10 km` |  

| Persona | Detección | `50 %` | `12 km` |  

| Persona | Reconocimiento | `95 %` | `7 km` |  

| Persona | Reconocimiento | `50 %` | `9 km` |  

| Vehículo | Detección | `95 %` | `28 km` |  

| Vehículo | Detección | `50 %` | `35 km` |  

| Vehículo | Reconocimiento | `95 %` | `21 km` |  

| Vehículo | Reconocimiento | `50 %` | `26 km` |  

  

### 5.2. Alcances en banda visible  

  

| Objeto | Función | Probabilidad | Alcance |  

|---|---|---:|---:|  

| Persona | Detección | `95 %` | `10 km` |  

| Persona | Detección | `50 %` | `13 km` |  

| Persona | Reconocimiento | `95 %` | `8 km` |  

| Persona | Reconocimiento | `50 %` | `10 km` |  

| Vehículo | Detección | `95 %` | `31 km` |  

| Vehículo | Detección | `50 %` | `38 km` |  

| Vehículo | Reconocimiento | `95 %` | `24 km` |  

| Vehículo | Reconocimiento | `50 %` | `29 km` |  

  

### 5.3. Parámetros principales  

  

| Parámetro | Requisito |  

|---|---:|  

| Detección de persona en IR | `10 a 12 km` |  

| Reconocimiento de persona en IR | `7 a 9 km` |  

| Detección de vehículo en IR | `28 a 35 km` |  

| Reconocimiento de vehículo en IR | `21 a 26 km` |  

| Detección de persona en visible | `10 a 13 km` |  

| Resolución del detector IR | `>= 1280 x 1024 px` |  

| NETD del detector IR | `<= 25 mK` |  

| Resolución espacial IR | `<= 0,010 mrad` |  

| Frecuencia de adquisición IR | `>= 25 fps` |  

| Resolución visible | `>= 3840 x 2160 px` |  

| Iluminación mínima visible | `<= 0,8 lux` |  

| Rango dinámico visible | `>= 70 dB` |  

| Precisión de estabilización | `<= 10 µrad RMS` |  

| Deriva de línea de mira | `< 0,20 grados/min` |  

| Mejora de contraste y nitidez | `>= 30 %`, objetivo `50 %` |  

| Tasa de aciertos de la IA | `>= 70 %` |  

| Tasa de falsos positivos de la IA | `<= 30 %` |  

  

## 6. Sensores  

  

### 6.1. Sensor infrarrojo MWIR/LWIR  

  

- **Banda espectral MWIR:** `3 a 5 µm`.  

- **Banda espectral LWIR:** `8 a 12 µm`.  

- **NETD:** `<= 25 mK`.  

- **Resolución:** `1280 x 1024 px`.  

- **Frecuencia de adquisición:** `>= 25 fps`.  

- **Vida útil:** `>= 20.000 h`.  

- **Pixel pitch:** aproximadamente `12 µm`.  

- **Resolución espacial:** `0,010 mrad`.  

  

### 6.2. Sensor VIS-NIR-SWIR  

  

- **Banda espectral:** dentro del rango `0,4 a 2,5 µm`.  

- **Resolución:** `3840 x 2160 px`.  

- **Relación señal-ruido:** `>= 44 dB`.  

- **Rango dinámico:** `> 70 dB`.  

- **Iluminación mínima:** `0,8 lux`.  

- **Campo de visión horizontal:** `< 0,5 grados`.  

- **Campo de visión vertical:** `< 0,5 grados`.  

- **Pixel pitch:** `< 10 µm`.  

  

### 6.3. Sensor de eventos  

  

- **Banda espectral:** `0,5 a 0,9 µm`.  

- **Resolución:** `1280 x 720 px`.  

- **Tasa equivalente asíncrona:** `> 10.000 fps`.  

- **Rango dinámico operativo:** `> 86 dB`, entre `5` y `100.000 lux`.  

- **Rango dinámico teórico:** `> 120 dB`, entre `0,08` y `100.000 lux`.  

- **Latencia por píxel a 1.000 lux:** `< 100 µs`.  

- **Latencia por píxel a 5 lux:** `< 1.000 µs`.  

  

## 7. Procesamiento e inteligencia artificial  

  

### 7.1. Procesamiento de imagen  

  

El sistema debe proporcionar:  

  

- Procesamiento paralelo.  

- Procesamiento en tiempo real.  

- Fusión espacial y temporal de IR, visible y eventos.  

- Corrección de no uniformidad.  

- Control automático de ganancia.  

- Reducción de ruido.  

- Mejora de contraste.  

- Mejora de nitidez.  

- Realce de detalles.  

- Compensación de degradaciones atmosféricas.  

- Generación de metadatos de posición, tiempo y orientación.  

- Parametrización y adaptación al escenario.  

  

### 7.2. Inteligencia artificial  

  

El subsistema de inteligencia artificial debe soportar:  

  

- Ejecución automática embarcada.  

- Detección y extracción de objetos.  

- Clasificación e identificación.  

- Análisis de comportamiento.  

- Evaluación de amenazas.  

- Seguimiento automático.  

- Generación de alertas.  

- Calibración de las tasas de acierto y falsos positivos.  

- Entrenamiento con conjuntos de datos representativos.  

- Etiquetado y control de calidad del dataset.  

- Validación en un entorno operativo.  

- Medición de precisión, recall y F1-score.  

  

#### Criterios mínimos de aceptación  

  

- **Tasa de aciertos:** `>= 70 %`.  

- **Tasa de falsos positivos:** `<= 30 %`.  

  

## 8. Estabilización y orientación  

  

- **Arquitectura:** multieje con control grueso y fino.  

- **Precisión de estabilización:** `<= 10 µrad RMS`.  

- **Deriva de línea de mira:** `< 0,20 grados/min`.  

- **Cobertura de acimut:** objetivo de cobertura continua de `360 grados`.  

- **Adaptación dinámica:** compensación de vibración, viento y movimiento.  

- **Seguimiento:** centrado automático del objetivo.  

- **Sincronización:** comunicación en tiempo real con los sensores y el sistema de procesamiento.  

  

## 9. Interfaces  

  

### 9.1. Interfaces externas  

  

- Transmisión simultánea en tiempo real de vídeo IR, visible y procesado.  

- Compresión H.264/H.265.  

- Frecuencia mínima de `30 fps`.  

- Interfaz HD-SDI.  

- Ancho de banda mínimo de `6 Mbps` por canal.  

- Control remoto completo.  

- Configuración remota.  

- Transmisión de telemetría.  

- Definición de un ICD.  

- Integración lógica y funcional con SIVE.  

- Conexión segura al sistema energético del emplazamiento.  

  

### 9.2. Interfaces internas  

  

- Transporte digital de los canales IR, VIS-NIR y eventos.  

- Comunicación entre el procesamiento de imagen y la inteligencia artificial.  

- Comunicación en tiempo real entre la estabilización y los sensores.  

- Distribución común de reloj y códigos de tiempo.  

- Sincronización de todos los subsistemas.  

  

### 9.3. Interfaz de usuario  

  

- Joystick o trackball rugerizado.  

- Teclado QWERTY.  

- Dos monitores de al menos `21 pulgadas`.  

- Visualización simultánea de dos canales.  

- Interfaz gráfica para configuración, operación y monitorización.  

- Operación remota con baja latencia.  

- Indicaciones visuales y sonoras para alarmas críticas.  

- Presentación de advertencias y confirmaciones.  

  

## 10. Grabación, sincronización y trazabilidad  

  

El sistema debe:  

  

- Grabar vídeo en soporte digital.  

- Permitir configurar la resolución.  

- Permitir configurar el formato de compresión.  

- Registrar detecciones.  

- Registrar tracks.  

- Registrar alertas.  

- Registrar errores y cambios de configuración.  

- Asociar códigos de tiempo, posición y orientación.  

- Mantener sincronizados todos los canales.  

- Mantener sincronizados los subsistemas.  

- Permitir trazabilidad entre requisitos, ensayos y evidencias.  

- Conservar la configuración entre ciclos de encendido.  

  

## 11. Entorno y operación  

  

### 11.1. Requisitos ambientales  

  

| Condición | Requisito | Norma |  

|---|---:|---|  

| Temperatura de operación | `-15 °C a +45 °C` | MIL-STD-810G |  

| Almacenamiento y tránsito | `-20 °C a +50 °C` | MIL-STD-810G |  

| Humedad relativa | `90 % a 40 °C`, sin condensación | MIL-STD-810G |  

| Hongos | Sin desarrollo de hongos | MIL-STD-810G |  

| Arena y polvo | Hasta `10 g/m³` | MIL-STD-810G |  

| Niebla salina | Sin corrosión | MIL-STD-810G |  

| Hielo | Cargas de hasta `1 kg/m²` | MIL-STD-810G |  

| Lluvia | `30 mm/h`, sin filtraciones | MIL-STD-810G |  

| Radiación solar | Hasta `1.130 W/m²` | MIL-STD-810G |  

| Vibración | Sin degradación funcional | MIL-STD-810G |  

| Choque mecánico | Sin fallo estructural | MIL-STD-810G |  

| Viento en torres | Hasta `150 km/h` | Ensayo estructural |  

| Viento en estructuras | Hasta `180 km/h` | Ensayo estructural |  

| Compatibilidad electromagnética | Cumplimiento | MIL-STD-461E |  

  

### 11.2. Fiabilidad y ciclo de vida  

  

- **Ciclo operativo:** `24 h / 365 días`.  

- **MTBF del sistema criogénico IR:** `>= 20.000 h`.  

- **MTBF de subsistemas no criogénicos:** `>= 50.000 h`.  

- **Tiempo de diagnóstico de fallos:** `<= 4 h`.  

- **Recuperación en campo:** entre `2 h` y `48 h`.  

- **Recuperación en laboratorio:** `<= 30 días`.  

- **Vida útil operativa:** `>= 15 años`.  

  

## 12. Seguridad  

  

El diseño debe incluir:  

  

- Protección frente a lluvia.  

- Protección frente a salinidad.  

- Protección frente a polvo.  

- Protección frente a radiación solar.  

- Protección frente a hielo.  

- Protección frente a vibraciones y choques.  

- Protección frente al viento.  

- Protección del operador frente a riesgos eléctricos.  

- Protección del operador frente a riesgos mecánicos.  

- Protección del operador frente a riesgos térmicos.  

- Control térmico automático.  

- Apagado seguro ante sobrecalentamiento.  

- Apagado seguro ante fallos críticos.  

- Alarmas visuales y sonoras.  

- Registro automático de fallos.  

- Registro de condiciones de riesgo.  

  

> [!warning] Inconsistencia de identificadores  

> El documento fuente utiliza dos veces el identificador `R46`, una vez para la protección ambiental y otra para la protección del operador. La línea base definitiva deberá asignar identificadores únicos.  

  

## 13. Transición TRL  

  

| Subsistema | TRL inicial | TRL objetivo |  

|---|---:|---:|  

| Canal MWIR | `5` | `7` |  

| Canal VIS-NIR | `5` | `7` |  

| Canal de eventos | `4` | `6-7` |  

| Plataforma de estabilización | `5` | `7` |  

| Procesamiento avanzado | `5` | `8` |  

| Inteligencia artificial | `5` | `8` |  

| Interfaces e integración SIVE | `5` | `8` |  

  

## 14. Verificación y aceptación  

  

Cada requisito deberá asociarse con:  

  

1. Un identificador único.  

2. El subsistema responsable.  

3. Una figura de mérito.  

4. Un indicador de éxito.  

5. Un método de verificación:  

- Inspección.  

- Análisis.  

- Demostración.  

- Ensayo.  

6. Un umbral cuantitativo de aceptación.  

7. La evidencia objetiva generada.  

8. El entorno de verificación.  

  

La validación final deberá:  

  

- Realizarse en un escenario preoperacional.  

- Ejecutarse en territorio español.  

- Utilizar una zona limítrofe de Andalucía.  

- Incluir la integración con un sistema de vigilancia de orden superior.  

  

## 15. Puntos abiertos  

  

- [ ] Confirmar la definición y las unidades de la extinción atmosférica.  

- [ ] Unificar las denominaciones VIS-NIR y VIS-NIR-SWIR.  

- [ ] Determinar la configuración IR definitiva: MWIR, LWIR o combinada.  

- [ ] Definir las métricas exactas de acierto y falsos positivos de IA.  

- [ ] Definir las latencias máximas de vídeo, detección, seguimiento y alerta.  

- [ ] Establecer la precisión de sincronización entre canales.  

- [ ] Definir los formatos de metadatos, tracks y alertas.  

- [ ] Detallar los protocolos de integración en el ICD.  

- [ ] Especificar los perfiles H.264/H.265.  

- [ ] Definir resolución, frecuencia, bitrate y latencia por canal.  

- [ ] Asignar identificadores únicos a todos los requisitos.  

- [ ] Corregir la duplicidad del requisito `R46`.  

- [ ] Convertir los valores aproximados en intervalos verificables.  

- [ ] Definir la disponibilidad operacional.  

- [ ] Definir los criterios de degradación aceptable.  

- [ ] Confirmar qué prestaciones se verifican por sensor.  

- [ ] Confirmar qué prestaciones se verifican a nivel de sistema fusionado.  

  

## 16. Resumen de requisitos críticos  

  

- **Operación continua:** `24 h / 365 días`.  

- **Integración multisensor:** MWIR o LWIR, VIS-NIR-SWIR y eventos.  

- **Resolución IR:** `>= 1280 x 1024 px`.  

- **NETD IR:** `<= 25 mK`.  

- **Resolución visible:** `>= 3840 x 2160 px`.  

- **Tasa equivalente del sensor de eventos:** `> 10.000 fps`.  

- **Precisión de estabilización:** `<= 10 µrad RMS`.  

- **Mejora de contraste y nitidez:** `>= 30 %`, objetivo `50 %`.  

- **Tasa de aciertos de la IA:** `>= 70 %`.  

- **Tasa de falsos positivos:** `<= 30 %`.  

- **Vídeo:** H.264/H.265 a `>= 30 fps`.  

- **Ancho de banda:** mínimo `6 Mbps` por canal.  

- **MTBF criogénico:** `>= 20.000 h`.  

- **MTBF no criogénico:** `>= 50.000 h`.  

- **Vida útil:** `>= 15 años`.  

- **Compatibilidad ambiental:** MIL-STD-810G.  

- **Compatibilidad electromagnética:** MIL-STD-461E.  

- **Integración:** SIVE mediante ICD.  

- **Madurez tecnológica objetivo:** TRL 7-8.  