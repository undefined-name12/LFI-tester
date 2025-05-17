[![Python 3](https://img.shields.io/badge/Python-3-blue.svg)](https://www.python.org/downloads/)

# AVISO LEGAL
• Esta herramienta es solo para fines educativos.

• Los desarrolladores y colaboradores no se hacen responsables del uso ilegal de esta herramienta.

# LFITester

LFITester es una herramienta para Python 3 que comprueba si un servidor es vulnerable a ataques de Inclusión Local de Archivos (LFI).

Funciona en sistemas Linux/Unix, pero también es compatible con Windows. Para usar este programa:

• Debe tener Python 3 instalado en su sistema o puede descargarlo desde https://www.python.org/downloads/

• También necesitará pip. Si no lo tiene, simplemente ejecute ```sudo apt install python3-pip``` para Linux.

• Descarga el programa o clona el repositorio en tu sistema: `git clone https://github.com/kostas-pa/LFITester.git`

• Accede a la carpeta LFITester

• Primero ejecuta el comando ```sudo chmod +x setup.sh```

• Luego ejecuta ```sudo ./setup.sh```, que instalará automáticamente los paquetes necesarios.

• Después, puedes ejecutar ```lfitester`` como comando.

Se recomienda ejecutar el indicador **--update** antes de iniciar un ataque.

# Ataques admitidos

- Recorrido de rutas y omisiones (byte nulo, codificación, omisiones de filtros)
- Filtro PHP
- Ejecución remota de código (RCE) mediante:
- Envenenamiento de registros (Apache, Nginx)
- Archivos de sesión PHP
- Wrappers PHP

```
$python3 LFITester.py
└──╼ $./LFITester.py
_ ______ _____ _______ _
| | | ____|_ _|__ __| | |
| | | |__ | | | | ___ ___| |_ ___ _ __
| | | __| | | | |/ _ \/ __| __/ _ \ '__|
| |____| | _| |_ | | __/\__ \ || __/ |
|______|_| |_____| |_|\___||___/\__\___|_|

**************************************************************************************************************************************************************************************************
LFITester
Pruebas LFI automatizadas
************************************************************************************************************************************************************************************************
Uso: LFITester.py [-h] [-u URL] [-L Archivo_URL] [-c] [-v] [-o [ARCHIVO_SALIDA]] [--creds [usuario:contraseña]] [-p] [--autopwn IP]
[-m Carga] [-f] [--update] [--batch-ans LOTE] [-s] [--poc-file POC] [-H ENCABEZADOS] [-C COOKIES]

Modos de carga útil:
0: TCP bash simple
1: TCP bash alternativo
2: UDP sh simple
3: TCP sh alternativo
4: TCP Perl
5: TCP Perl alternativo
6: TCP Python
7: TCP Python alternativo
8: TCP Python alternativo 2
9: TCP Python alternativo 3
10: TCP Python alternativo (sin espacios)
11: TCP Python alternativo (sin espacios)
12: TCP Python alternativo (sin espacios)
13: TCP Python alternativo (sin espacios) abreviado
14: TCP Python alternativo (sin espacios) abreviado
15: TCP Python alternativo (sin espacios) abreviado
16: TCP Python alternativo (sin espacios) abreviado Python TCP
17: Alternativa (sin espacios) Acortado aún más 2 Python TCP
18: Alternativa (sin espacios) Acortado aún más 3 Python TCP
19: Python3 TCP
20: Alternativa Python3 TCP
21: Alternativa 2 Python3 TCP
22: Alternativa 3 Python3 TCP
23: Alternativa (sin espacios) Python3 TCP
24: Alternativa (sin espacios) Python3 TCP
25: Alternativa (sin espacios) Python3 TCP
26: Alternativa (sin espacios) Acortado Python3 TCP
27: Alternativa (sin espacios) Acortado aún más 2 Python3 TCP
28: Alternativa (sin espacios) Acortado aún más 3 Python3 TCP
29: Alternativa (sin espacios) Acortado aún más 30: Alternativa (sin espacios) Acortado aún más 2 python3 TCP
31: Alternativa (sin espacios) Acortada aún más 3 python3 TCP
32: Php exec
33: Php shell_exec
34: Php over sh
35: Php system
36: Php passthru
37: Php popen
38: Php proc_open
39: Ruby
40: Alternativa a Ruby
41: Go
42: Netcat sh
43: Netcat bash
44: Netcat alternative bash
45: Netcat openBSD
46: Ncat
47: Ncat UDP

Opciones:
-h, --help Mostrar este mensaje de ayuda y salir
-u URL, --url URL La URL para probar. La URL suele ser http://[URL]?[algo]=
-L Archivo_URL, --list-url Archivo_URL
Introduce una lista de URL desde un archivo externo. El formato de las URL suele ser http://[URL]?[algo]=
-c, --crawl Usa el rastreador para probar todos los endpoints
-v, --verbose Aumenta el nivel de detalle de la salida
-o [ARCHIVO_DE_SALIDA], --output [ARCHIVO_DE_SALIDA]
El archivo donde se guarda el resultado
lts
--creds [usuario:contraseña] Las credenciales para iniciar sesión
-p, --enable-proxies Habilita la redirección de proxy. Los proxies predeterminados son gratuitos y puedes cambiarlos. Si no quieres los proxies predeterminados, puedes proporcionar los tuyos propios y esta opción se anulará. Ten en cuenta que los proxies se seleccionarán aleatoriamente para cada solicitud.
--autopwn IP Si la aplicación web es vulnerable a LFI, intentará explotarla y devolverá un shell. Esta opción requiere tu IP para conectarse con el revshell.
-m Carga útil, --mode Carga útil
Selecciona la carga útil que mejor se adapte. Prueba diferentes si el exploit no funciona.
-f, --force Trata el endpoint como activo incluso si devuelve 404.
--update Actualiza LFITester.
--batch-ans LOTE Responde a todos los mensajes sí/no.
-s, --stealth Habilita el modo oculto.
--poc-file POC Tu archivo POC personalizado. -H ENCABEZADOS, --headers ENCABEZADOS
Añadir encabezados adicionales
-C COOKIES, --cookies COOKIES
Añadir cookies adicionales
-r ARCHIVO_DE_PAQUETE, --packet-file ARCHIVO_DE_PAQUETE
Importar encabezados/cookies/cuerpo desde un archivo de paquete (formato HTTP o Burp)

Los proxies de la lista deben tener el siguiente formato: protocolo://{proxyip}
usuario:contraseña (nueva línea). Si no tiene un proxy autenticado, omita la entrada "nombre de usuario:contraseña" y escriba una nueva línea.

Ejemplos:

LFITester.py -u "http://URL?smt=" = probar un endpoint específico

LFITester.py -L test.txt = probar una lista de endpoints del archivo

LFITester.py -c -u "http://URL" = rastrear y probar todos los endpoints de esa URL

LFITester.py -c -L test.txt = rastrear y probar todos los endpoints de cada URL del archivo

LFITester.py --creds abc:abc -u "http://URL?smt=" = probar un endpoint específico que requiere inicio de sesión

Desarrolladores: Konstantinos Papanagnou (https://github.com/Konstantinos-Papanagnou)

Konstantinos Pantazis (https://github.com/kostas-pa)

Timothy Stowe (https://github.com/timothy90990)
```

• Uso básico: `python3 LFITester.py -u "http://myvulnerabledomain/vulnerable/application?test_param="`

# Nueva función: AUTOPWN y compatibilidad con subprocesos
- Abre automáticamente una shell inversa si encuentra RCE (ver todas las shells inversas en la descripción).
- Se añadieron subprocesos a los ataques y a los proxies, lo que agiliza considerablemente el proceso.

# ⚠️ Problemas comunes
• Si tienes problemas con una URL con dos parámetros de consulta, como http://url?param1=1&param2=2, intenta ejecutarla con "" como "http://url?param1=1&param2=2"

• Si eres usuario y recibes un error sobre Git, intenta ejecutar lfitester con el comando sudo como **sudo lfitester [flags]**

• Si tienes problemas con una biblioteca, intenta ejecutar el comando **--update** y luego ```sudo pip3 install -r requirements.txt``, ya que los requisitos podrían haber cambiado.

• Si no ves el color en el archivo de salida, pero en su lugar ves códigos de color, busca en Google ```[tu editor de texto] mostrar códigos de color ANSI``.

• Si setup.sh no puede instalar un paquete de Python, intenta instalarlo manualmente con el comando ```sudo pip3 install [paquete]```

• Si se bloquea, simplemente presiona Enter, por ahora :)

• Si obtienes resultados de codificación extraños, intenta eliminar cualquier valor de los parámetros, incluidos los archivos Burp.

# Nota al margen
• Si te gusta este proyecto, considera darle una estrella.
