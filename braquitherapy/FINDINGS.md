# MOSAIQ - CONTEXT (Generador JS PDF?)

Descripción general de los descubrimientos para importar información de pacientes en un pdf a través del engine javascript de Adobe. 

Si suponemos que vamos a contar con un visor de pdfs en cada computadora, equivalente a Adobe Reader o Foxit Reader, podemos suponer que existirá la opción de importar información mediante Javascript directamente de la base de Datos de MOSAIQ.

En este sentido, los descubrimientos son:

- Context permite generar tablas perfectas definiendo cada medida correctamente y adjuntar código js. 

- Javascript brinda ADBC que permite conectarse a un ODBC de Windows
- Desde python puedo conectarme a SRVMOSAIQAPP y hacer query remotamente
- En SRVMOSAIQAPP el PAT_ID es siempre par y se sigue la siguiente regla:
  - LAst2(PAT_ID) mod 100 brinda la carpeta que organiza el paciente en IMAGES folder
  - PAT_ID HEX brinda la subcarpeta específica del paciente
  - Todos los archivos se encuentran en formato .acr, .o00 y .org

Entonces debería ser posible crear un pdf con código javascript que utilice el ID del paciente para obtener su foto, nombre, historial de tratamiento, etc. y documentar tratamientos, o cualquier otra información relevante.

### Javascript

[JavaScript APi](https://www.adobe.com/content/dam/acom/en/devnet/acrobat/pdfs/js_api_reference.pdf) indica 

> The ADBC plug-in allows JavaScript in PDF documents to access databases through a consistent object model. ADBC is a Windows-only feature and requires ODBC to be installed on the client machine.

# CONTEXT Javascript Library

## Fuentes Externas
El uso de fuentes externas se garantiza con los siguientes comandos: 
```tex 
\definefontfamiliy[mainface] [rm, ss, tt, mm] [Calibry] 
\setmainbody[mainface, ss, 10pt]
```
Sin embargo, es importante observar que esta fuente no será utilizada en los fields utilizados por el usuario.