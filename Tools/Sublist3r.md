# Sublist3r en Kali Linux

## ¿Qué es Sublist3r?
Sublist3r es una herramienta de **reconocimiento** en **ciberseguridad** que permite enumerar **subdominios** de un dominio objetivo. Esta herramienta facilita la recolección de subdominios, un paso importante en el proceso de **reconocimiento** en pruebas de penetración y auditorías de seguridad.

Sublist3r realiza la enumeración de subdominios consultando múltiples motores de búsqueda y servicios API, como **Google**, **Bing**, **Yahoo**, **Baidu**, y **VirusTotal**.

## Instalación
Sublist3r viene preinstalado en **Kali Linux**. Para verificar que está instalado, abre una terminal y ejecuta:

# Comandos de Sublist3r

A continuación, se presentan los comandos más utilizados de la herramienta **Sublist3r**:

## Comandos Básicos

### Escaneo de un dominio y a ciertos puertos
```bash
sublist3r -d dominio.com -p80,443
```
### Escaneo de un dominio con un motor de búsqueda
```bash
sublist3r -d dominio.com --engine google
```
# Ejemplos
```bash
  sublister -d google.com
  sublister -d example.com -p80,443
  sublist3r -v -d example.com
  sublist3r -b -d example.com
  sublist3r -e google,yahoo,virustotal -d example.com
```
  
