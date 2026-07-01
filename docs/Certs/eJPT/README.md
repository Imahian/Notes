# 📚 Notas del Curso eLearnSecurity: eJPT (Junior Penetration Tester)

---

## Módulo 1: Fundamentos de Redes

En este módulo, abordaremos los conceptos esenciales de redes que sirven como base para comprender cómo se estructuran y operan las redes de computadoras. Este conocimiento es fundamental para realizar pruebas de penetración, ya que la mayoría de los ataques y defensas en ciberseguridad están directamente relacionados con las redes. 

### 1. Conceptos Básicos de Redes y Terminología

Las redes permiten la comunicación y transferencia de datos entre dispositivos. Entender los términos básicos es crucial para comprender el resto de los temas en ciberseguridad y redes.

- **Red**: Conjunto de dispositivos conectados entre sí para compartir información y recursos. Puede ser una red local (LAN) o una red extendida (WAN).
  
- **Nodo**: Cada dispositivo o punto que se conecta a la red, como computadoras, routers y switches.

- **Protocolo**: Conjunto de reglas que determina cómo se deben enviar y recibir los datos a través de una red. Ejemplos de protocolos incluyen TCP/IP, HTTP y FTP.

- **Ancho de Banda**: La cantidad máxima de datos que se puede transmitir en una red en un tiempo determinado, generalmente medido en bits por segundo (bps).

- **Latencia**: El tiempo que tarda un paquete de datos en viajar desde el origen hasta el destino. Una latencia baja es ideal para una comunicación rápida.

- **Paquete**: Unidad básica de datos que se transmite por la red. Contiene una carga útil de datos y encabezados que especifican la dirección de origen y destino.

- **Firewall**: Dispositivo o software que protege una red al controlar el tráfico entrante y saliente según reglas de seguridad.

Comprender estos términos es esencial para trabajar con redes, ya que constituyen los elementos básicos con los que se estructura la conectividad y seguridad en sistemas interconectados.

---

### 2. Modelos OSI y TCP/IP

Los modelos OSI y TCP/IP son arquitecturas de referencia que describen cómo los datos se comunican a través de una red. Conocer estos modelos es fundamental para entender el flujo de datos y la estructura de las comunicaciones en una red.

#### Modelo OSI (Open Systems Interconnection)

El **Modelo OSI** es una referencia en siete capas que estandariza las funciones de un sistema de comunicación. Cada capa tiene funciones específicas y se encarga de una parte del proceso de transmisión de datos:

1. **Capa Física**: Define las conexiones físicas de los dispositivos (cables, señales, voltajes). Ejemplos: Ethernet, USB.
2. **Capa de Enlace de Datos**: Gestiona la comunicación directa entre dos nodos en una misma red. Ejemplo: MAC (Control de Acceso al Medio).
3. **Capa de Red**: Se encarga de dirigir los datos entre redes distintas. Ejemplo: IP (Protocolo de Internet).
4. **Capa de Transporte**: Proporciona entrega confiable de datos entre dispositivos finales. Ejemplo: TCP (Protocolo de Control de Transmisión).
5. **Capa de Sesión**: Controla las conexiones y sesiones entre aplicaciones. Ejemplo: RPC (Remote Procedure Call).
6. **Capa de Presentación**: Se encarga de la traducción de datos entre la red y el formato que la aplicación necesita. Ejemplo: SSL/TLS para cifrado.
7. **Capa de Aplicación**: Es la capa más cercana al usuario y maneja las aplicaciones y servicios de red. Ejemplo: HTTP, FTP, SMTP.

#### Modelo TCP/IP

El **Modelo TCP/IP** es más simplificado y se utiliza ampliamente en Internet. Este modelo tiene cuatro capas:

1. **Capa de Acceso a la Red**: Equivalente a las capas física y de enlace de datos del modelo OSI. Define cómo los datos se transmiten físicamente en la red.
2. **Capa de Internet**: Equivalente a la capa de red del OSI. Se encarga de la direccionamiento y enrutamiento de paquetes. Ejemplo: IP.
3. **Capa de Transporte**: Similar a la capa de transporte del OSI, permite la comunicación confiable entre los dispositivos. Ejemplo: TCP, UDP.
4. **Capa de Aplicación**: Equivale a las capas de aplicación, presentación y sesión del modelo OSI. Maneja los protocolos de comunicación directa entre aplicaciones. Ejemplo: HTTP, FTP, DNS.

---

### 3. Subneteo y Máscaras de Red

El **subneteo** es una técnica para dividir una red más grande en subredes más pequeñas, permitiendo un uso más eficiente del espacio de direcciones IP y mejorando la seguridad y el rendimiento.

#### Conceptos Clave

- **Dirección IP**: Identificador único de un dispositivo en una red. Puede ser IPv4 (ej. 192.168.1.1) o IPv6 (ej. 2001:0db8:85a3:0000:0000:8a2e:0370:7334).

- **Máscara de Subred**: Una combinación de bits que separa la parte de red y la parte de host en una dirección IP. Ejemplo común: 255.255.255.0.

- **CIDR (Classless Inter-Domain Routing)**: Un método para asignar y especificar direcciones IP que incluye la máscara de subred, como en `192.168.1.0/24`.

#### ¿Cómo Funciona el Subneteo?

Al aplicar una máscara de subred a una dirección IP, se pueden separar la **parte de la red** y la **parte del host**. Esto ayuda a definir subredes, permitiendo que varios segmentos de red funcionen de manera independiente dentro de una misma red más amplia.

#### Ejemplo de Subneteo

Consideremos la dirección IP `192.168.1.0/24`:
- **/24** indica que los primeros 24 bits se usan para la identificación de la red y los 8 bits restantes para los hosts.
- Esto permite **256 direcciones IP** (192.168.1.0 - 192.168.1.255), donde la primera y la última dirección son reservadas, dejando **254 direcciones utilizables** para dispositivos.

#### Ventajas del Subneteo

- **Seguridad**: Permite aislar segmentos de red para limitar el acceso y mejorar la protección.
- **Eficiencia**: Mejora la administración de IPs y evita desperdicios en redes grandes.
- **Reducción de Tráfico**: Cada subred puede manejar tráfico localmente, disminuyendo el tráfico total en la red principal.

---

Con estos conocimientos fundamentales, estarás mejor preparado para comprender cómo se estructuran y se protegen las redes de computadoras, lo que te permitirá avanzar en el estudio de técnicas de ciberseguridad en redes.
