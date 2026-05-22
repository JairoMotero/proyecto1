# ☁️ PrivaNube

## Nube privada con Nextcloud desplegada sobre Proxmox

**PrivaNube** es un proyecto de implantación de una nube privada basada en **Nextcloud**, desarrollado para simular una solución realista de almacenamiento y gestión de archivos para la empresa **Infosur**.

El objetivo principal del proyecto es crear una plataforma propia donde los usuarios puedan acceder a sus documentos, organizarlos y gestionarlos desde una interfaz web, evitando depender completamente de servicios externos como Google Drive, OneDrive o Dropbox.

La solución ha sido desplegada sobre una infraestructura virtualizada mediante **Proxmox VE**, utilizando un servidor asignado para el proyecto. Además, se ha configurado acceso mediante **HTTPS** y se ha validado el acceso externo a la plataforma mediante un túnel público generado con **ngrok**.

---

## 📌 ¿Qué problema resuelve?

En muchas pequeñas empresas, los archivos pueden estar repartidos entre varios equipos, memorias externas o servicios en la nube de terceros. Esto puede provocar desorganización, pérdida de control sobre los datos y dificultad para acceder a la información desde diferentes lugares.

**PrivaNube** propone una solución centralizada, donde los archivos se almacenan en una plataforma propia y accesible desde navegador web.

Con este proyecto se busca demostrar que una pequeña empresa puede disponer de una nube privada funcional utilizando software libre y recursos virtualizados.

---

## 🎯 Objetivo del proyecto

El objetivo del proyecto es implantar una nube privada funcional que permita:

- Centralizar el almacenamiento de archivos.
- Acceder a la información desde una interfaz web.
- Gestionar usuarios y documentos dentro de Nextcloud.
- Usar una infraestructura virtualizada mediante Proxmox.
- Proteger el acceso mediante HTTPS.
- Validar el acceso externo mediante ngrok.
- Simular una solución aplicable a una pequeña empresa.

---

## 🧠 Descripción general

La plataforma principal del proyecto es **Nextcloud**, una solución de nube privada que permite almacenar, compartir y gestionar archivos desde navegador web.

El servicio se ejecuta sobre un entorno virtualizado en **Proxmox VE**, lo que permite administrar el sistema de forma centralizada y aprovechar mejor los recursos disponibles.

Durante el proyecto se han validado dos formas de acceso:

- **Acceso local**, desde la red del centro.
- **Acceso externo**, mediante una URL pública generada con ngrok.

Esto permite demostrar que la nube privada no funciona únicamente dentro de la red local, sino que también puede ser accesible desde fuera mediante navegador web.

---

## 🏗️ Arquitectura del sistema

La arquitectura de PrivaNube se basa en una estructura sencilla y funcional:

```text
Usuario
  |
  | Navegador web / HTTPS
  v
Nextcloud
  |
  v
Servidor virtualizado en Proxmox
```

Para el acceso externo, se utiliza ngrok como túnel temporal:

```text
Usuario externo
  |
  | URL pública de ngrok
  v
Túnel ngrok
  |
  v
Nextcloud
  |
  v
Proxmox VE
```

Esta arquitectura permite simular un entorno real de nube privada, manteniendo una complejidad adecuada para un proyecto académico.

---

## 🖥️ Infraestructura utilizada

El proyecto se ha desplegado sobre un entorno virtualizado mediante **Proxmox VE**.

| Elemento | Descripción |
|---|---|
| Plataforma de virtualización | Proxmox VE |
| Servicio principal | Nextcloud |
| Máquina virtual | NextCloud |
| Nodo Proxmox | marisma003 |
| Acceso local | `https://10.4.0.206` |
| Acceso externo | `https://backache-aneurism-marsupial.ngrok-free.dev` |
| Seguridad | HTTPS mediante certificado SSL/TLS |

---

## 🌐 Accesos configurados

### Acceso local

El acceso local se realiza desde la red del centro mediante la dirección:

```text
https://10.4.0.206
```

Este acceso permite entrar directamente a Nextcloud desde la red interna y también se utiliza para validar el funcionamiento del cliente **Nextcloud Desktop**.

### Acceso externo

Para comprobar el acceso desde fuera de la red local, se ha utilizado **ngrok**, generando una URL pública temporal:

```text
https://backache-aneurism-marsupial.ngrok-free.dev
```

Esta dirección permite acceder a la interfaz web de Nextcloud desde diferentes equipos y ubicaciones externas.

---

## ⚙️ Funcionalidades implementadas

Durante el desarrollo del proyecto se han implementado y validado las siguientes funcionalidades:

- Acceso web a Nextcloud.
- Inicio de sesión con usuario y contraseña.
- Gestión de archivos y carpetas.
- Subida y descarga de documentos.
- Acceso local mediante IP interna.
- Acceso externo mediante ngrok.
- Configuración de HTTPS.
- Uso básico del panel principal de Nextcloud.
- Prueba del cliente Nextcloud Desktop mediante acceso local.

---

## 🔐 Seguridad aplicada

La seguridad del proyecto se ha trabajado principalmente mediante el uso de **HTTPS**, permitiendo cifrar la comunicación entre el usuario y el servidor.

Esto es importante porque Nextcloud trabaja con credenciales de usuario y archivos que pueden contener información sensible.

Medidas aplicadas:

- Acceso mediante HTTPS.
- Uso de credenciales de usuario.
- Validación del acceso local y externo.
- Separación entre acceso web y cliente de escritorio.
- Documentación de limitaciones técnicas.

En una implantación real, sería recomendable ampliar la seguridad con autenticación en dos factores, copias de seguridad automáticas, dominio propio y certificado público definitivo.

---

## ⚠️ Limitación detectada

Durante las pruebas se detectó una limitación con el cliente **Nextcloud Desktop**.

La interfaz web de Nextcloud funciona correctamente desde el exterior mediante la URL pública generada con ngrok. Sin embargo, el cliente de escritorio no funciona correctamente usando esa URL externa, ya que ngrok actúa como un túnel temporal orientado principalmente al acceso web desde navegador.

Por este motivo, el cliente Nextcloud Desktop se valida utilizando la dirección local:

```text
https://10.4.0.206
```

Esta limitación no impide cumplir el objetivo principal del proyecto, ya que el acceso web externo sí queda validado correctamente.

---

## 📷 Evidencias del proyecto

La documentación del proyecto incluye capturas que demuestran:

- Arquitectura general de PrivaNube.
- Máquina virtual NextCloud en Proxmox.
- Acceso local a Nextcloud.
- Configuración de HTTPS.
- Servicio ngrok activo.
- Acceso externo mediante URL pública.
- Inicio de sesión correcto.
- Gestión de archivos dentro de Nextcloud.
- Cliente Nextcloud Desktop configurado con acceso local.

---

## 🚀 Mejoras futuras

Aunque el proyecto cumple con los objetivos principales, se podrían aplicar varias mejoras para acercarlo más a un entorno empresarial real:

- Sustituir ngrok por un dominio propio.
- Configurar un certificado SSL/TLS público.
- Implementar copias de seguridad automáticas.
- Añadir autenticación en dos factores.
- Crear grupos de usuarios por departamentos.
- Mejorar el acceso externo del cliente Nextcloud Desktop.
- Ampliar el almacenamiento disponible.
- Integrar edición colaborativa de documentos.
- Añadir monitorización del servicio.

---

## 🏁 Conclusión

**PrivaNube** demuestra que es posible implantar una nube privada funcional utilizando software libre y una infraestructura virtualizada.

El proyecto permite centralizar archivos, acceder a la información desde navegador web y validar el acceso externo mediante ngrok. Además, la configuración de HTTPS mejora la seguridad de las conexiones y hace que la solución sea más cercana a un entorno real.

A pesar de las limitaciones propias de un entorno académico, el sistema cumple con su objetivo principal: ofrecer una plataforma de nube privada funcional, documentada y aplicable a una pequeña empresa.

---

## 👨‍💻 Autor

**Jairo Motero García**  
Proyecto Intermodular  
C.F.G.M. Sistemas Microinformáticos y Redes  
I.E.S. La Marisma  
Curso 2025/2026

---

## 📄 Nota

Este proyecto ha sido desarrollado en un entorno académico con recursos asignados por el centro educativo.

La solución no está planteada como una infraestructura empresarial en producción, sino como una demostración funcional y documentada de una nube privada basada en Nextcloud.