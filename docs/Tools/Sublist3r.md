# 🛠 Herramienta Sublist3r en Redes y Ciberseguridad

**Sublist3r** es una herramienta ampliamente utilizada en redes y ciberseguridad para realizar **enumeración de subdominios** de manera efectiva. A continuación, se describe su funcionamiento, características principales y algunas herramientas complementarias para enriquecer su uso en la investigación de dominios.

---

## ¿Qué es Sublist3r?
Sublist3r es una herramienta de **reconocimiento de subdominios** que ayuda a obtener una lista completa de subdominios asociados a un dominio objetivo. Es muy útil en **pruebas de penetración** y **auditorías de seguridad** para identificar subdominios expuestos, los cuales podrían representar puntos vulnerables en la infraestructura de una organización.

La herramienta consulta varios motores de búsqueda y servicios API, como **Google**, **Bing**, **Yahoo**, **Baidu**, y **VirusTotal**, para recolectar información de subdominios de manera rápida y automatizada.

### ¿Por qué es importante?
La enumeración de subdominios es un paso esencial en el proceso de reconocimiento. Al identificar subdominios, se puede construir un mapa más detallado de la infraestructura de una organización, revelando posibles puntos de entrada y servicios no documentados o expuestos accidentalmente.

---

## Funcionamiento Básico de Sublist3r
Sublist3r realiza solicitudes a través de diferentes motores de búsqueda y servicios, recolectando datos sobre subdominios registrados para el dominio especificado. Es una herramienta de **recolección pasiva**, lo que significa que se basa en información pública y no interactúa directamente con los servidores del objetivo.

### Ejemplo Básico de Uso
Para obtener una lista de subdominios de un dominio específico, se usa el siguiente comando:

```bash
sublist3r -d example.com
```
Este comando devolverá una lista de subdominios asociados a `example.com`, tales como `sub.example.com`, `mail.example.com`, entre otros.

--------

## Opciones Principales en Sublist3r

Sublist3r ofrece diversas opciones para personalizar y optimizar el proceso de búsqueda:

- **-d**: Especifica el dominio objetivo.
- **-o**: Guarda los resultados en un archivo de salida.
- **-v**: Habilita el modo verboso, mostrando información adicional sobre el progreso de la búsqueda.
- **-b**: Utiliza **Baidu** como motor de búsqueda para obtener subdominios adicionales.


