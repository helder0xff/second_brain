# Especificaciones del sistema EventGuard

> \*\*Documento de síntesis técnica\*\*   
> Proyecto: \*\*EventGuard\*\*  

## 1\. Objeto y alcance

EventGuard es un sistema optrónico multisensor avanzado destinado a la vigilancia de líneas limítrofes terrestres. El sistema debe mejorar las capacidades de observación, detección, reconocimiento, seguimiento y generación de alertas tempranas frente a tránsitos irregulares y actividades ilícitas.

La solución debe:

* Operar de forma continuada, **`24 h / 365 días`**.
* **Detectar personas**, grupos de personas **y vehículos**.
* Funcionar en **condiciones** ambientales y atmosféricas **adversas**.
* Integrar sensórica **MWIR**, visible extendida **VIS-NIR** y un sensor de **eventos**.
* Incorporar **procesamiento avanzado** de imagen e **inteligencia artificial** embebida.
* Permitir **operación** manual, **semiautomática** y automática.
* **Integrarse** con sistemas de vigilancia de orden superior, especialmente **SIVE** o sistemas equivalentes.
* Evolucionar hasta niveles de madurez tecnológica **TRL 7-8** en las fases posteriores del proyecto.

Quedan fuera de este documento los detalles de diseño e implementación, producción de componentes críticos y procedimientos detallados de prueba y verificación.

## 2\. Escenario operativo

### 2.1 Área de vigilancia

* Vigilancia de **zonas terrestres** en las que puedan producirse **tránsitos irregulares o ilícitos**.
* Cobertura de hasta **`1 km` a ambos lados de la línea limítrofe**.
* **Longitud de línea vigilada de hasta `8 km`**.
* Exploración y observación continuada bajo cualquier condición ambiental prevista.

### 2.2 Objetos de interés

#### Personas y grupos

* Altura: entre `1,5 m` y `1,8 m`.
* Peso: entre `40 kg` y `120 kg`.
* Movimiento: paso lento, rápido o carrera.
* Desplazamiento en campo abierto o con presencia de vegetación. **Oclusiones.**
* Presencia junto a elementos interpuestos, como vallas, verjas o muros.
* Diferencia de temperatura aparente respecto al fondo: `10 °C`.
* Tamaño del grupo: entre `1` y `50` personas.

#### Vehículos

* Tipo: turismo o todoterreno de gama baja o media.
* Velocidad: entre `10 km/h` y `100 km/h`.
* Desplazamiento por vía terrestre o campo con presencia de vegetación.
* Diferencia de temperatura aparente respecto al fondo: `10 °C`.
* Ocupación típica: entre `3` y `5` personas.

### 2.3 Modos de operación

* **Manual:** el operador controla la observación, clasificación y generación de alertas.
* **Semiautomático:** el sistema asiste al operador en detección, seguimiento y evaluación.
* **Automático:** la IA ejecuta funciones de exploración, detección, clasificación, seguimiento y alerta con supervisión del operador.





## 3\. Arquitectura funcional

El sistema se organiza en cuatro bloques principales.

### 3.1 Adquisición y procesamiento de imagen

* Canal infrarrojo MWIR o LWIR para detección y reconocimiento a larga distancia.
* Canal visible extendido VIS-NIR, con posible cobertura SWIR, para operación diurna, crepuscular y nocturna con iluminación residual.
* Sensor de eventos para detección ultrarrápida de cambios, reducción del desenfoque por movimiento y apoyo en baja iluminación.
* Procesamiento en tiempo real para:

  * Mejora de contraste.
  * Reducción de ruido.
  * Realce de detalles.
  * Mejora de resolución y discriminación luminosa.
  * Fusión IR, VIS y eventos.
  * Generación de productos de imagen adaptados al escenario.

### 3.2 Inteligencia artificial

* Detección automática de objetos de interés.
* Clasificación e identificación de personas, grupos y vehículos.
* Seguimiento automático y multiobjetivo.
* Análisis de comportamiento y evaluación de amenaza.
* Generación automática de alertas tempranas.
* Parametrización, entrenamiento, validación y adaptación de modelos.

### 3.3 Estabilización y autotracking

* Plataforma multieje con estabilización de la línea de mira.
* Arquitectura jerárquica de control:

  * Apuntamiento grueso.
  * Ajuste fino.
* Compensación de vibraciones, viento y movimientos de plataforma.
* Mantenimiento del objetivo centrado durante el seguimiento.
* Adecuación a campos de visión muy estrechos y distancias superiores a `25 km`.

### 3.4 Interfaces e integración

* Exportación de vídeo, datos, telemetría, detecciones, tracks y alertas.
* Control local y remoto sin pérdida de prestaciones.
* Integración lógica y funcional con SIVE.
* Sincronización temporal común entre subsistemas.
* Registro trazable de vídeo, eventos, detecciones y parámetros de operación.

## 4\. Requisitos funcionales

|ID|Función|Especificación|
|-|-|-|
|F1|Captación optrónica multibanda|Adquisición sincronizada en MWIR, VIS-NIR y canal de eventos.|
|F2|Procesamiento avanzado|Mejora automática de contraste, resolución y fusión multisensor.|
|F3|Estabilización y orientación|Mantenimiento de la línea de mira, estabilización multieje y control angular preciso.|
|F4|Detección e identificación automática|Detección, identificación y clasificación mediante IA.|
|F5|Seguimiento automático|Seguimiento integrado de objetivos detectados.|
|F6|Alertas tempranas|Generación manual, semiautomática y automática con alta fiabilidad.|
|F7|Transmisión e integración|Envío de vídeo, datos y metadatos al puesto remoto y al sistema superior.|
|F8|Grabación y trazabilidad|Registro sincronizado de vídeo, detecciones, eventos y metadatos.|
|F9|Calibración de línea de mira|Ajuste horizontal y vertical para asegurar precisión angular.|
|F10|Autodiagnóstico|Monitorización de subsistemas y comunicación de fallos.|
|F11|Gestión de modos|Cambio entre modos manual, semiautomático y automático.|
|F12|Control remoto|Operación completa desde un puesto remoto.|
|F13|Sincronización temporal|Códigos comunes de tiempo y posición para correlación de datos.|
|F14|Mantenimiento|Soporte a mantenimiento preventivo, correctivo y diagnóstico.|
|F15|Grabación de vídeo|Grabación digital con resolución y compresión configurables.|

## 5\. Requisitos de usabilidad

|ID|Requisito|Valor o condición|
|-|-|-|
|R1|Interfaz amigable|Acceso a todas las funciones con baja latencia y bajo riesgo de error.|
|R2|Formación básica|Duración máxima de `8 h`.|
|R3|Operación continua|Funcionamiento `24 h / 365 días`.|
|R4|Cambio de canal|Conmutación inmediata entre IR, visible y eventos.|
|R5|Configuración persistente|Conservación de parámetros entre ciclos de encendido.|
|R6|Control ergonómico|Joystick o trackball rugerizado, teclado QWERTY y dos monitores de al menos `21 pulgadas`.|

## 6\. Prestaciones operativas mínimas

### 6.1 Alcances DRI en banda infrarroja

|Objeto|Función|Probabilidad|Alcance|Extinción atmosférica indicada|
|-|-|-:|-:|-:|
|Persona|Detección|95 %|10 km|2 km|
|Persona|Detección|50 %|12 km|3 km|
|Persona|Reconocimiento|95 %|7 km|2 km|
|Persona|Reconocimiento|50 %|9 km|2 km|
|Vehículo|Detección|95 %|28 km|6 km|
|Vehículo|Detección|50 %|35 km|8 km|
|Vehículo|Reconocimiento|95 %|21 km|6 km|
|Vehículo|Reconocimiento|50 %|26 km|7 km|

### 6.2 Alcances DRI en banda visible

|Objeto|Función|Probabilidad|Alcance|Extinción atmosférica indicada|
|-|-|-:|-:|-:|
|Persona|Detección|95 %|10 km|2 km|
|Persona|Detección|50 %|13 km|3 km|
|Persona|Reconocimiento|95 %|8 km|2 km|
|Persona|Reconocimiento|50 %|10 km|3 km|
|Vehículo|Detección|95 %|31 km|7 km|
|Vehículo|Detección|50 %|38 km|8 km|
|Vehículo|Reconocimiento|95 %|24 km|7 km|
|Vehículo|Reconocimiento|50 %|29 km|8 km|

> \*\*Nota:\*\* La columna de extinción atmosférica se conserva según la representación del documento fuente. Su denominación y unidades deberán confirmarse en el ICD o en el plan de verificación antes de emplearla como criterio de ensayo.

### 6.3 Parámetros principales de rendimiento

|ID|Parámetro|Subsistema|Requisito|
|-|-|-|-:|
|R7|Alcance de detección de persona|IR|10 a 12 km|
|R8|Alcance de reconocimiento de persona|IR|7 a 9 km|
|R9|Alcance de detección de vehículo|IR|28 a 35 km|
|R10|Alcance de reconocimiento de vehículo|IR|21 a 26 km|
|R11|Alcance de detección de persona|Visible|10 a 13 km|
|R12|Resolución del detector IR|MWIR/LWIR|`>= 1280 x 1024 px`|
|R13|Pixel pitch|VIS/NIR/SWIR|`< 10 µm`|
|R14|NETD|MWIR/LWIR|`<= 25 mK`|
|R15|Resolución espacial IR|MWIR/LWIR|`<= 0,010 mrad`|
|R16|Frecuencia de adquisición IR|MWIR/LWIR|`>= 25 fps`|
|R17|Resolución visible|VIS/NIR/SWIR|`>= 3840 x 2160 px`|
|R18|Iluminación mínima|VIS/NIR/SWIR|`<= 0,8 lux`|
|R19|Rango dinámico|VIS/NIR/SWIR|`>= 70 dB`|
|R20|Precisión de estabilización|Plataforma|`<= 10 µrad RMS`|
|R21|Deriva de línea de mira|Plataforma|`< 0,20 grados/min`|
|R22|Mejora de contraste y nitidez|Procesamiento|`>= 30 %`, objetivo `50 %`|
|R23|Tasa de aciertos IA|IA|`>= 70 %`|
|R24|Tasa de falsos positivos|IA|`<= 30 %`|

## 7\. Especificaciones mínimas de los sensores

### 7.1 Sensor infrarrojo MWIR/LWIR

|Parámetro|Requisito mínimo|
|-|-:|
|Banda espectral MWIR|`3 a 5 µm`|
|Banda espectral LWIR|`8 a 12 µm`|
|NETD|`<= 25 mK`|
|Resolución|`1280 x 1024 px`|
|Frecuencia de adquisición|`>= 25 fps`|
|Vida útil|`>= 20.000 h`|
|Pixel pitch|Aproximadamente `12 µm`|
|Resolución espacial|`0,010 mrad`|

### 7.2 Sensor VIS-NIR-SWIR

|Parámetro|Requisito mínimo|
|-|-:|
|Banda espectral|Dentro del rango `0,4 a 2,5 µm`|
|Resolución|`3840 x 2160 px`|
|Relación señal-ruido|`>= 44 dB`|
|Rango dinámico|`> 70 dB`|
|Iluminación mínima|`0,8 lux`|
|Campo de visión horizontal y vertical|`< 0,5 grados`|
|Pixel pitch|`< 10 µm`|

### 7.3 Sensor de eventos

|Parámetro|Requisito mínimo|
|-|-:|
|Banda espectral|`0,5 a 0,9 µm`|
|Resolución|`1280 x 720 px`|
|Tasa equivalente asíncrona|`> 10.000 fps`|
|Rango dinámico operativo|`> 86 dB`, entre `5` y `100.000 lux`|
|Rango dinámico teórico|`> 120 dB`, entre `0,08` y `100.000 lux`|
|Latencia por píxel a 1.000 lux|`< 100 µs`|
|Latencia por píxel a 5 lux|`< 1.000 µs`|

## 8\. Procesamiento e inteligencia artificial

### 8.1 Procesamiento de imagen

El sistema debe proporcionar, como mínimo:

* Procesamiento paralelo y en tiempo real.
* Fusión espacial y temporal de IR, VIS y eventos.
* Corrección de no uniformidad.
* Control automático de ganancia.
* Reducción de ruido.
* Mejora de contraste y nitidez.
* Realce de detalles.
* Compensación de degradaciones atmosféricas.
* Generación de metadatos de posición, tiempo y orientación.
* Parametrización de los procesos y adaptación al escenario.

### 8.2 Inteligencia artificial

El subsistema de IA debe soportar:

* Ejecución automática embarcada.
* Detección y extracción de objetos.
* Clasificación e identificación.
* Análisis de comportamiento.
* Evaluación de amenaza.
* Seguimiento automático.
* Generación de alertas.
* Calibración de tasas de acierto, descarte y falsos positivos.
* Entrenamiento con conjuntos de datos representativos.
* Etiquetado y control de calidad del dataset.
* Validación en entorno operativo.
* Medición de precisión, recall y F1-score.

Criterios mínimos de aceptación:

* Tasa de aciertos: `>= 70 %`.
* Tasa de falsos positivos: `<= 30 %`.

## 9\. Estabilización y orientación

|Parámetro|Requisito|
|-|-:|
|Arquitectura|Multieje, con control grueso y fino|
|Precisión de estabilización|`<= 10 µrad RMS`|
|Deriva de línea de mira|`< 0,20 grados/min`|
|Cobertura de acimut|Objetivo de cobertura continua `360 grados`|
|Adaptación dinámica|Compensación de vibración, viento y movimiento|
|Seguimiento|Centrado automático del objetivo|
|Sincronización|Comunicación en tiempo real con sensores y procesamiento|

## 10\. Interfaces

### 10.1 Interfaces externas

|ID|Interfaz|Requisito|
|-|-|-|
|I1|Vídeo|Transmisión simultánea en tiempo real de IR, visible y vídeo procesado. H.264/H.265, al menos 30 fps, HD-SDI y ancho de banda mínimo de 6 Mbps por canal.|
|I2|Datos y control remoto|Control completo, configuración y telemetría sin pérdida de prestaciones frente a la operación local.|
|I3|ICD|Definición de requisitos, diseño, procedimientos de control y metadatos de vídeo.|
|I4|Integración SIVE|Compatibilidad lógica y funcional, control y monitorización remota.|
|I5|Alimentación|Conexión segura y con continuidad de servicio al sistema energético del emplazamiento.|

### 10.2 Interfaces internas

|ID|Interfaz|Requisito|
|-|-|-|
|I6|Sensores a procesamiento|Transporte digital de IR, VIS-NIR y eventos para fusión y mejora.|
|I7|Procesamiento a IA|Flujo optimizado para detección, clasificación, seguimiento y alertas.|
|I8|Estabilización a sensores|Comunicación en tiempo real para mantener la línea de mira.|
|I9|Sincronización temporal|Distribución de reloj y códigos de tiempo a todos los subsistemas.|

### 10.3 Interfaz de usuario

|ID|Interfaz|Requisito|
|-|-|-|
|I10|Operación local|Joystick o trackball rugerizado, teclado QWERTY y dos monitores de al menos 21 pulgadas. Visualización simultánea de dos canales.|
|I11|GUI|Acceso a configuración, operación y monitorización, con diseño orientado a reducir errores.|
|I12|Operación remota|Visualización y control de vídeo, datos y alertas con calidad suficiente y baja latencia.|
|I13|Estado y alarmas|Indicaciones visuales y sonoras para alarmas críticas, advertencias y confirmaciones.|

## 11\. Grabación, sincronización y trazabilidad

El sistema debe:

* Grabar vídeo en soporte digital.
* Permitir configurar resolución y formato de compresión.
* Registrar detecciones, tracks, alertas, errores y cambios de configuración.
* Asociar códigos de tiempo, posición y orientación a los datos.
* Mantener sincronizados los distintos canales y subsistemas.
* Permitir trazabilidad bidireccional entre requisitos, figuras de mérito, indicadores de éxito, ensayos y evidencias.
* Conservar la configuración de operación entre ciclos de encendido.

## 12\. Requisitos ambientales

|ID|Condición|Requisito|Norma o método|
|-|-|-:|-|
|R25|Temperatura de operación|`-15 °C a +45 °C`|MIL-STD-810G, métodos 501.5 y 502.5|
|R26|Almacenamiento y tránsito|`-20 °C a +50 °C`|MIL-STD-810G, métodos 501.5 y 502.5|
|R27|Humedad relativa|`90 % a 40 °C`, sin condensación|MIL-STD-810G, método 507.5|
|R28|Hongos|Sin desarrollo de hongos|MIL-STD-810G, método 508.6|
|R29|Arena y polvo|Hasta `10 g/m³`|MIL-STD-810G, método 510.5|
|R30|Niebla salina|Sin corrosión|MIL-STD-810G, método 509.5|
|R31|Hielo|Cargas de hasta `1 kg/m²`|MIL-STD-810G, método 521.3|
|R32|Lluvia|Sin filtraciones ni corrosión a `30 mm/h`|MIL-STD-810G, método 506.5|
|R33|Radiación solar|Hasta `1.130 W/m²` sin degradación|MIL-STD-810G, método 505.5|
|R34|Vibración|Sin degradación funcional|MIL-STD-810G, método 514.6|
|R35|Choque mecánico|Sin fallo estructural|MIL-STD-810G, método 516.6|
|R36|Viento|`150 km/h` en torres y `180 km/h` en estructuras|Ensayo estructural|
|R37|Compatibilidad electromagnética|Cumplimiento|MIL-STD-461E|

## 13\. Fiabilidad, mantenibilidad y ciclo de vida

|ID|Parámetro|Requisito|
|-|-|-:|
|R38|Ciclo operativo|Continuo, `24 h / 365 días`|
|R39|Modos de operación|Manual, semiautomático y automático|
|R40|MTBF del sistema criogénico IR|`>= 20.000 h`|
|R41|MTBF de subsistemas no criogénicos|`>= 50.000 h`|
|R42|Diagnóstico de fallos|`<= 4 h`|
|R43|Recuperación en campo|Entre `2 h` y `48 h`, según criticidad|
|R44|Recuperación en laboratorio|`<= 30 días`|
|R45|Vida útil operativa|`>= 15 años`|

## 14\. Seguridad

El diseño debe incluir:

* Protección frente a lluvia, salinidad, polvo, radiación solar, hielo, vibraciones, choques y viento.
* Protección del operador frente a riesgos eléctricos, mecánicos y térmicos.
* Control térmico automático.
* Apagado seguro ante sobrecalentamiento o fallo crítico.
* Alarmas visuales y sonoras.
* Registro automático de fallos y condiciones de riesgo.
* Cumplimiento de buenas prácticas de seguridad industrial.

> \*\*Observación de consistencia:\*\* el documento fuente utiliza dos veces el identificador `R46`, una para protección ambiental y otra para protección del operador. En la línea base definitiva conviene asignar identificadores únicos.

## 15\. Transición de madurez tecnológica

|Subsistema|TRL inicial|TRL objetivo|Actividades principales|Evidencia esperada|
|-|-:|-:|-|-|
|Canal MWIR|5|7|Integración con óptica y canal de eventos, validación controlada|Ensayos térmicos y NETD|
|Canal VIS-NIR|5|7|Optimización óptica, calibración espectral y validación multibanda|Ensayos de contraste y alcance|
|Canal de eventos|4|6-7|Integración electrónica y sincronización con VIS e IR|Demostración de fusión en laboratorio|
|Plataforma de estabilización|5|7|Control multieje y validación bajo vibraciones reales|Pruebas en banco dinámico|
|Procesamiento avanzado|5|8|Implementación embebida y validación de latencia|Ensayos en tiempo real|
|Inteligencia artificial|5|8|Entrenamiento con datos reales y validación operativa|Precisión, recall y F1-score|
|Interfaces e integración SIVE|5|8|ICD definitivo y pruebas de interoperabilidad|Ensayo preoperacional con sistema superior|

## 16\. Criterios de verificación y aceptación

Cada requisito deberá asociarse, como mínimo, con:

1. Un identificador único.
2. El subsistema responsable.
3. Una figura de mérito.
4. Un indicador de éxito.
5. Un método de verificación:

   * Inspección.
   * Análisis.
   * Demostración.
   * Ensayo.
6. Un umbral cuantitativo de aceptación.
7. La evidencia objetiva generada.
8. El entorno de verificación, ya sea laboratorio, banco dinámico, entorno controlado o escenario preoperacional.

La validación final deberá realizarse en un escenario preoperacional localizado en territorio español, en una zona limítrofe de Andalucía, y deberá incluir la integración con un sistema de vigilancia de orden superior.

## 17\. Puntos abiertos y aspectos a normalizar

Antes de congelar la línea base de requisitos se recomienda resolver los siguientes puntos:

* Confirmar las unidades y definición exacta de la columna denominada "extinción atmosférica" en las tablas DRI.
* Unificar el alcance espectral del canal visible extendido, ya que se emplean las denominaciones VIS-NIR y VIS-NIR-SWIR.
* Determinar si el canal IR definitivo será MWIR, LWIR o una configuración combinada.
* Especificar la métrica exacta para la tasa de aciertos de IA y la tasa de falsos positivos.
* Definir latencias máximas de extremo a extremo para vídeo, detección, seguimiento y alerta.
* Establecer la precisión de sincronización temporal entre los tres canales.
* Definir formatos concretos de metadatos, tracks y alertas.
* Detallar protocolos de integración SIVE en el ICD.
* Especificar perfiles H.264/H.265, resolución, frecuencia, bitrate y latencia por canal.
* Asignar identificadores únicos a todos los requisitos, corrigiendo la duplicidad de `R46`.
* Convertir expresiones aproximadas, como `\~12 µm`, en rangos de aceptación verificables.
* Definir disponibilidad operacional, mantenibilidad y criterios de degradación aceptable.
* Confirmar qué prestaciones deben cumplirse por sensor aislado y cuáles se evaluarán únicamente a nivel de sistema fusionado.

## 18\. Resumen de requisitos críticos

* Operación continua: `24 h / 365 días`.
* Integración multisensor: MWIR o LWIR, VIS-NIR-SWIR y eventos.
* Resolución IR: `>= 1280 x 1024 px`.
* NETD IR: `<= 25 mK`.
* Resolución visible: `>= 3840 x 2160 px`.
* Tasa de eventos equivalente: `> 10.000 fps`.
* Precisión de estabilización: `<= 10 µrad RMS`.
* Mejora de contraste y nitidez: `>= 30 %`, objetivo `50 %`.
* Tasa de aciertos IA: `>= 70 %`.
* Falsos positivos IA: `<= 30 %`.
* Vídeo: H.264/H.265, `>= 30 fps`, mínimo `6 Mbps` por canal.
* MTBF criogénico: `>= 20.000 h`.
* MTBF no criogénico: `>= 50.000 h`.
* Vida útil: `>= 15 años`.
* Compatibilidad ambiental: MIL-STD-810G.
* Compatibilidad electromagnética: MIL-STD-461E.
* Integración con SIVE mediante ICD y control remoto completo.
* Objetivo de madurez: TRL 7-8, según subsistema.

