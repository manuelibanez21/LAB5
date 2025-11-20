# Punto 2 — Comunicación RS-485 entre Raspberry Pi y Arduino (Modbus RTU)

## 🎯 Objetivo
Implementar una comunicación industrial RS-485 entre una Raspberry Pi y un Arduino, aplicando la estructura maestro-esclavo del protocolo Modbus RTU. Demostrar el intercambio confiable de datos a través de un medio diferencial, característico de entornos industriales que requieren robustez frente a interferencias electromagnéticas y largas distancias de transmisión.

## 🔧 Descripción del Sistema

### Arquitectura del Montaje
Sistema maestro-esclavo compuesto por:
- **Raspberry Pi** como dispositivo maestro
- **Arduino Uno** como dispositivo esclavo  
- **Módulos MAX485** para conversión de niveles TTL a RS-485

### Características de los Módulos MAX485
Cada módulo incluye pines de control críticos:
- **DE** (Driver Enable) - Habilita transmisión
- **RE** (Receiver Enable) - Habilita recepción

## 🔌 Esquema de Conexiones

### Configuración del Bus RS-485

| Dispositivo      | Pin/Función       | Conexión               | Descripción               |
|------------------|-------------------|------------------------|---------------------------|
| Raspberry Pi     | GPIO17            | Módulo MAX485 (DE)     | Control de transmisión    |
| Raspberry Pi     | GPIO18            | Módulo MAX485 (RE)     | Control de recepción      |
| Raspberry Pi     | TX/RX UART        | Módulo MAX485          | Canal de datos serie      |
| Arduino Uno      | Pin 10 (RX) / 11 (TX) | Módulo MAX485     | Comunicación serial       |
| Ambos            | A+ ↔ A+           | Bus RS-485             | Línea diferencial positiva|
| Ambos            | B− ↔ B−           | Bus RS-485             | Línea diferencial negativa|
| Ambos            | GND ↔ GND         | Tierra común           | Referencia eléctrica      |

## 💻 Implementación del Software

### 🖥️ Raspberry Pi (Maestro)
**Lenguaje:** Python  
**Puerto serial:** `/dev/serial0`

#### Flujo de Operación Maestro:
1. **Modo Transmisión** - Activar GPIO17 y GPIO18 (nivel alto)
2. **Envío de Datos** - Transmitir "Hola desde Raspberry Pi"
3. **Cambio a Recepción** - Desactivar GPIO17 y GPIO18 (nivel bajo)  
4. **Espera de Respuesta** - Monitoreo continuo del bus

### 🔄 Arduino (Esclavo)
**Librería:** SoftwareSerial  
**Pines comunicación:** 10 (RX) y 11 (TX)  
**Pines control:** 2 (DE) y 3 (RE)

#### Funcionamiento Esclavo:
- Monitoreo constante del bus RS-485
- Detección y procesamiento de mensajes entrantes
- Respuesta automática con "Hola desde Arduino"

## 📊 Resultados y Verificación

### ✅ Comportamiento Observado
- ✅ Intercambio bidireccional continuo de mensajes
- ✅ Comunicación estable sin pérdida de datos
- ✅ Correcta alternancia entre modos TX/RX
- ✅ Demostración práctica del principio maestro-esclavo

### 🛡️ Validación del Enlace
El experimento confirmó la efectividad de RS-485 para:
- Comunicación robusta en entornos con interferencias
- Implementación de arquitecturas multi-dispositivo
- Transmisión confiable mediante medios diferenciales
- Aplicaciones industriales con requerimientos de distancia extendida

---

**Nota:** Esta implementación sirve como base para sistemas industriales más complejos que requieran comunicación confiable entre múltiples dispositivos en entornos electromagnéticamente hostiles.
