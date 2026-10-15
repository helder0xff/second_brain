
El dynamic range (rango dinámico) de una cámara es la **capacidad que tiene el sensor para captar simultáneamente zonas muy oscuras y zonas muy luminosas** de una escena sin perder detalle.

# Ejemplo

En una escena de playa podemos tener:

- ☀️ Cielo muy brillante
    
- 🧍 Una persona
    
- 🌊 Zonas de sombra
    

Una cámara con poco rango dinámico puede tener problemas:

- Si exponemos para el cielo → la persona y las sombras pueden quedar prácticamente negras.
    
- Si exponemos para las sombras → el cielo puede quedar completamente blanco (_clipped_ o saturado).
    

Una cámara con **mucho rango dinámico** puede conservar información en ambas zonas.

# Definición técnica

De forma simplificada:

$$  
DR = \frac{L_{\max}}{L_{\min}}  
$$

donde:

- $L_{\max}$ = máxima señal que puede registrar el sensor antes de saturarse.
    
- $L_{\min}$ = mínima señal distinguible del ruido.
    

El dynamic range puede expresarse en **stops** o en **decibelios (dB)**.

## Stops

Un **stop** representa aproximadamente una duplicación de la cantidad de luz.

Por ejemplo:

|Dynamic Range|Rango de intensidades|
|---|---|
|10 stops|$2^{10} = 1.024:1$|
|12 stops|$2^{12} = 4.096:1$|
|14 stops|$2^{14} = 16.384:1$|

Por tanto, una cámara de 14 stops puede representar un rango de intensidades mucho mayor que una de 10 stops.

# Dynamic Range en cámaras event-based

El concepto es especialmente interesante en event cameras.

Una cámara convencional mide la intensidad absoluta:

$$  
L(x,y,t)  
$$

Mientras que una event camera genera un evento cuando detecta un cambio suficiente en la intensidad, aproximadamente:

$$  
\frac{L(t)-L(t-\Delta t)}{L(t-\Delta t)}  
$$

Por tanto, **la información de una event camera está relacionada principalmente con cambios relativos de intensidad, no con la intensidad absoluta**.

Esto contribuye a que las event cameras puedan trabajar con un dynamic range muy elevado.

## Intuición

```
Cámara convencional

Sol ☀️ ───────────────────────→ saturación
Sombra 🌑 ────────────────────→ ruido


Event camera

Sol ☀️ ────────────────────────┐
                               │
                               ├──→ eventos producidos
Sombra 🌑 ─────────────────────┘
                                  por cambios de intensidad
```

# Importante

Un dynamic range elevado no significa que una event camera pueda ver perfectamente en cualquier condición de iluminación.

Siguen existiendo limitaciones relacionadas con:

- Sensibilidad del sensor
- Ruido
- Saturación
- Iluminación mínima
- Respuesta temporal
- Rango dinámico efectivo del circuito de lectura