# 🛠️ README – Laboratorio de Configuración de VLANs

## 📌 1. Objetivo del laboratorio

El objetivo de este laboratorio fue configurar una red segmentada mediante VLANs (Virtual Local Area Networks) y verificar su funcionamiento mediante pruebas de:

- Direccionamiento IP
- Tablas ARP  
- Conectividad (ping)
- Análisis de topología

El propósito principal fue aislar el tráfico entre grupos de dispositivos, logrando que cada VLAN funcionara como una red independiente dentro de la misma infraestructura física.

## 🖥️ 2. Equipos y topología utilizada

En la práctica se empleó la siguiente infraestructura:

- 1 router de capa 3
- 2 switches de capa 2
- PCs finales conectados de forma distribuida en los switches

Debido a la disponibilidad de equipos, una de las VLAN operó únicamente con un PC, aunque el diseño inicial contemplaba dos PCs por switch.

## ⚙️ 3. Configuración del router y los switches

### 🔧 Router

- Configuración básica para gestión y direccionamiento
- Preparación para permitir el enrutamiento entre VLANs, si fuera necesario
- Configuración de interfaces virtuales (SVI) para cada VLAN

### 🔧 Switches

- Creación de dos VLANs independientes para la segmentación del tráfico
- Cada VLAN utilizó una red del tipo `192.168.x.0/24`
- Configuración y asignación de puertos a su VLAN correspondiente
- Activación de puertos necesarios y verificación de su estado
- Configuración de puertos troncales para interconexión entre switches

**Objetivo:** Garantizar la comunicación interna dentro de cada VLAN y el aislamiento lógico entre VLANs distintas.

## 🔍 4. Verificación de la VLAN 1

Se llevaron a cabo las siguientes pruebas:

- Revisión de direcciones IP asignadas
- Pruebas de conectividad mediante `ping`
- Consulta de la tabla ARP usando `arp -a`

**Resultados:** La comunicación fue exitosa dentro de la VLAN 1, confirmando que los dispositivos resolvían correctamente direcciones IP y MAC.

## 🔍 5. Verificación de la VLAN 2

Las pruebas realizadas fueron:

- Verificación de configuración IP
- Conectividad con `ping` entre dispositivos
- Comprobación de ARP

**Resultados:**
- Los dispositivos de la VLAN 2 se comunicaron correctamente entre sí
- Los intentos de `ping` hacia otras VLAN fallaron, lo cual confirma el aislamiento entre VLANs
- Las direcciones MAC fueron registradas correctamente por el switch

## 🏗️ 6. Comprobación de la arquitectura y topología

La red implementó un diseño jerárquico:

- El router (capa 3) gestionó el enrutamiento y el control de la comunicación entre redes
- Los switches (capa 2) administraron la segmentación mediante VLANs

El análisis de puertos, IPs, ARP y conectividad confirmó una implementación correcta y operativa de la red.

## 🟦 7. VLAN 1

**Contenido a incluir:**
- Captura de pantalla de la tabla de direccionamiento IP de los dispositivos
- Resultados de los comandos `ping` entre hosts de la VLAN 1
- Captura del comando `show vlan` en los switches mostrando los puertos asignados
- Resultados del comando `arp -a` en los PCs de esta VLAN
- Diagrama de conexión física y lógica de la VLAN 1

## 🟪 8. VLAN 2

**Contenido a incluir:**
- Captura de configuración IP de los dispositivos de la VLAN 2
- Resultados de pruebas de conectividad interna con `ping`
- Captura de los comandos de verificación de VLAN en los switches
- Resultados de pruebas de aislamiento (ping fallidos a otras VLANs)
- Evidencia de la tabla ARP de los equipos en esta VLAN

## ⚙️ 9. Otras configuraciones

**Contenido a incluir:**
- Configuración de puertos troncales (trunk) entre switches
- Configuración de VLAN nativa si se aplicó
- Configuración de port security si se implementó
- Configuración de STP (Spanning Tree Protocol) si fue necesario
- Comandos de verificación de conectividad entre switches
