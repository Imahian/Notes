# 🛠 Herramienta `whois` en Redes y Ciberseguridad

La herramienta `whois` es ampliamente utilizada en redes y ciberseguridad para obtener información detallada sobre la propiedad y los registros de dominios, direcciones IP y redes. A continuación, se describe su funcionamiento, características principales y algunas herramientas complementarias para enriquecer su uso.

---

## ¿Qué es `whois`?

`whois` es un protocolo y una herramienta de consulta que permite acceder a bases de datos públicas donde se almacenan los registros de dominios y direcciones IP. Este servicio es proporcionado por diversas organizaciones que gestionan dominios y recursos de Internet, como ICANN (Internet Corporation for Assigned Names and Numbers). Los datos obtenidos suelen incluir información sobre:

- Propietario del dominio o IP
- Fecha de creación y expiración del dominio
- Información de contacto del administrador
- Servidores DNS asociados

---

## Funcionamiento Básico de `whois`

El comando `whois` realiza consultas sobre los registros de bases de datos de Internet y devuelve información detallada de un dominio o dirección IP. Su funcionamiento es simple: se envía una solicitud a través del protocolo `whois` a servidores públicos, que devuelven los datos registrados para la entidad solicitada.

### Ejemplo Básico de Uso

Para obtener información sobre un dominio específico, se usa el siguiente comando:

```bash
whois example.com
```

Este comando devolverá la información registrada sobre example.com, como datos de contacto, fechas de registro y estado del dominio.

---

## Consultas de Direcciones IP
whois también permite consultas sobre rangos de direcciones IP para obtener detalles sobre el proveedor de servicio (ISP) y la ubicación. Por ejemplo:

```bash
whois 8.8.8.8
```

Este comando devolverá los datos asociados a la IP 8.8.8.8, que es uno de los servidores DNS de Google.


## Campos Principales en los Resultados de whois


Al realizar una consulta con whois, los resultados incluirán varios campos importantes:

- Domain Name: El nombre del dominio consultado.
- Registry Domain ID: Un identificador único para el dominio en el registro.
- Registrar: La organización que administra el registro del dominio.
- Creation Date y Expiration Date: Fechas de creación y expiración del dominio.
- Registrar Contact Information: Información de contacto del registrador, incluyendo correo y teléfono.
- Name Servers: Servidores DNS asociados al dominio.
- Status: Estado del dominio (activo, bloqueado, en proceso de renovación, etc.)

# Herramientas Complementarias a whois

Además de whois, existen varias herramientas que se utilizan en conjunto o como alternativa para profundizar en la recolección de información sobre dominios y direcciones IP:


### 1. nslookup

nslookup permite obtener información sobre la dirección IP asociada a un nombre de dominio o viceversa. Es útil para verificar registros DNS y se ejecuta de la siguiente manera:

## Herramientas Complementarias a `whois`

Además de `whois`, existen varias herramientas que se utilizan en conjunto o como alternativa para profundizar en la recolección de información sobre dominios y direcciones IP:

### 1. `nslookup`
`nslookup` permite obtener información sobre la dirección IP asociada a un nombre de dominio o viceversa. Es útil para verificar registros DNS y se ejecuta de la siguiente manera:

```bash
nslookup example.com
```

### 2. `dig`


dig (Domain Information Groper) proporciona información más detallada sobre los registros DNS de un dominio. Es ideal para consultar tipos de registros específicos, como A, MX, TXT o CNAME.

```bash
dig example.com

```

## Ejemplo Práctico de `whois` en Ciberseguridad

Al realizar un análisis de ciberseguridad, el uso de `whois` puede ser el primer paso para identificar al propietario y los detalles administrativos de un dominio sospechoso. Este proceso se conoce como **recolección de información pasiva**, ya que no implica interacción directa con los sistemas del objetivo, sino que se basa en información pública.

### Ejemplo de Uso:

Para investigar un dominio sospechoso, puedes utilizar el siguiente comando:

```bash
whois maliciousdomain.com
```

#### ** ¿Qué Información Puede Revelar?
La información obtenida a través de whois podría incluir:

Ubicación geográfica: Información sobre la región o el país donde se encuentra registrado el dominio.
Organización responsable: Nombre de la entidad o empresa propietaria del dominio.
Detalles de contacto: Información de contacto de los administradores del dominio, como correos electrónicos y números de teléfono.
Esta información es útil para analizar la legitimidad de un dominio y puede ayudar a identificar actividades sospechosas relacionadas con el mismo.

Con el conocimiento y las herramientas descritas, podrás realizar una investigación inicial efectiva en el análisis de dominios y redes, utilizando whois y sus herramientas complementarias para obtener información detallada y segura.
