# Servidor de Correo con Postfix y Dovecot – Mail y Listas de Distribución

![Portada del proyecto](cover.png)

## Descripción del Proyecto
Proyecto personal de **Administración de Sistemas** enfocado en la configuración de un servidor de correo completo con **Postfix** (SMTP) y **Dovecot** (IMAP/POP3), dominios virtuales, usuarios virtuales, listas de distribución, aliases y pruebas de envío/recepción interna y externa.

Características principales:
- Instalación y configuración de Postfix y Dovecot.
- Configuración de dominios virtuales y aliases para usuarios y listas.
- Listas de distribución para envíos grupales.
- Usuarios virtuales con directorios Maildir.
- Pruebas con Thunderbird para envío/recepción.
- Verificación de conexiones con telnet a puertos SMTP/IMAP/POP3.
- Configuración de NAT y rutas para acceso externo.

Entorno reproducible en Linux con pruebas de funcionalidad completa.

## Tecnologías y Herramientas Utilizadas
- **Postfix** para SMTP, aliases y listas de distribución
- **Dovecot** para IMAP/POP3 y recepción segura
- Archivos: /etc/postfix/main.cf, virtual, aliases; /etc/dovecot/dovecot.conf, 10-mail.conf, 10-auth.conf
- **Thunderbird** como cliente para pruebas reales
- Comandos: telnet, systemctl status, postmap, adduser, mkdir Maildir
- NAT y rutas para simular entorno externo

## Objetivos Alcanzados
- Servidor de correo funcional con envío y recepción segura.
- Implementación de listas de distribución y aliases virtuales.
- Autenticación y directorios Maildir para usuarios virtuales.
- Pruebas internas y externas con clientes reales.
- Verificación de puertos y conexiones con telnet.

## Proceso Completo – Explicación Detallada

### 1. Creación de Máquinas Virtuales y Adaptadores de Red
Se crean las máquinas virtuales y se asignan adaptadores de red para cada una.

![Paso 1: Creación máquinas y adaptadores](screenshots/screenshots (1).png)

### 2. Asignación de IPs en Máquina 1
Asignación de direcciones IP estáticas en la Máquina 1 (servidor de correo).

![Paso 2: Asignación IPs Máquina 1](screenshots/screenshots (2).png)

### 3. Asignación de IPs en Máquina 2
Asignación de direcciones IP en la Máquina 2 (cliente o relay).

![Paso 3: Asignación IPs Máquina 2](screenshots/screenshots (3).png)

### 4. Añadir Usuarios en Máquina 1
Creación de usuarios locales con adduser y establecimiento de contraseñas.

![Paso 4: Añadir usuarios Máquina 1](screenshots/screenshots (4).png)

### 5. Añadir Usuarios en Máquina 2
Creación de usuarios en la Máquina 2 para pruebas.

![Paso 5: Añadir usuarios Máquina 2](screenshots/screenshots (5).png)

### 6. Edición del Archivo /etc/hosts en Máquina 1
Configuración del archivo hosts para resolución de nombres.

![Paso 6: Edición hosts Máquina 1](screenshots/screenshots (6).png)

### 7. Edición del Archivo /etc/hosts en Máquina 2
Configuración del archivo hosts en la Máquina 2.

![Paso 7: Edición hosts Máquina 2](screenshots/screenshots (7).png)

### 8. Instalación de Postfix en Cada Máquina
Instalación del paquete Postfix, seleccionando "Internet Site" y configurando nombre.

![Paso 8: Instalación Postfix](screenshots/screenshots (8).png)

### 9. Edición de main.cf en Postfix
Revisión y edición del archivo /etc/postfix/main.cf para dominios virtuales y alias.

![Paso 9: Edición main.cf](screenshots/screenshots (9).png)

### 10. Configuración de Dominios Virtuales y Usuarios en /etc/postfix/virtual
Creación del archivo virtual con usuarios y dominios.

![Paso 10: Archivo virtual usuarios](screenshots/screenshots (10).png)

### 11. Configuración de Listas de Distribución en /etc/postfix/virtual
Añadimos aliases para listas de distribución.

![Paso 11: Aliases listas de distribución](screenshots/screenshots (11).png)

### 12. Postmap para Actualizar Virtual
Ejecutamos postmap para aplicar cambios en el archivo virtual.

![Paso 12: postmap virtual](screenshots/screenshots (12).png)

### 13. Reinicio y Status de Postfix
Reinicio del servicio Postfix y verificación de estado.

![Paso 13: Reinicio Postfix](screenshots/screenshots (13).png)

### 14. Instalación de Mailutils
Instalación de mailutils para pruebas de envío desde consola.

![Paso 14: Instalación mailutils](screenshots/screenshots (14).png)

### 15. Configuración de Dovecot (dovecot.conf)
Edición de /etc/dovecot/dovecot.conf para habilitar protocolos IMAP y POP3.

![Paso 15: dovecot.conf protocolos](screenshots/screenshots (15).png)

### 16. Configuración 10-mail.conf en Dovecot
Edición de /etc/dovecot/conf.d/10-mail.conf para definir mail_location = maildir:~/Maildir.

![Paso 16: 10-mail.conf mail_location](screenshots/screenshots (16).png)

### 17. Configuración 10-auth.conf en Dovecot
Edición de /etc/dovecot/conf.d/10-auth.conf para permitir autenticación plaintext (para pruebas).

![Paso 17: 10-auth.conf disable_plaintext_auth](screenshots/screenshots (17).png)

### 18. Reinicio y Status de Dovecot
Reinicio del servicio Dovecot y verificación de estado.

![Paso 18: Reinicio Dovecot](screenshots/screenshots (18).png)

### 19. Creación de Directorios Maildir para Usuarios
Creación de directorios Maildir para usuarios virtuales.

![Paso 19: mkdir Maildir usuarios](screenshots/screenshots (19).png)

### 20. Pruebas con Telnet a SMTP (puerto 25)
Verificación de conexión SMTP con telnet localhost 25.

![Paso 20: Telnet SMTP](screenshots/screenshots (20).png)

### 21. Pruebas con Telnet a IMAP (puerto 143)
Verificación de conexión IMAP con telnet localhost 143.

![Paso 21: Telnet IMAP](screenshots/screenshots (21).png)

### 22. Pruebas con Telnet a POP3 (puerto 110)
Verificación de conexión POP3 con telnet localhost 110.

![Paso 22: Telnet POP3](screenshots/screenshots (22).png)

### 23. Configuración de Thunderbird para Usuarios
Configuración de cuentas en Thunderbird para envío/recepción.

![Paso 23: Thunderbird config usuarios](screenshots/screenshots (23).png)

### 24. Envío de Correo Interno y Externo
Prueba de envío de correo interno y externo con Thunderbird.

![Paso 24: Envío interno/externo](screenshots/screenshots (24).png)

### 25. Recepción y Verificación Final de Listas de Distribución
Verificación de recepción en clientes, entrega a listas y pruebas con NAT.

![Paso 25: Verificación final listas](screenshots/screenshots (25).png)

## Capturas del Proceso Completo (Galería completa)

<div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); gap: 15px; margin: 30px 0;">

  <img src="screenshots/screenshots (1).png" alt="Paso 1: Creación máquinas y adaptadores">
  <img src="screenshots/screenshots (2).png" alt="Paso 2: Asignación IPs Máquina 1">
  <img src="screenshots/screenshots (3).png" alt="Paso 3: Asignación IPs Máquina 2">
  <img src="screenshots/screenshots (4).png" alt="Paso 4: Añadir usuarios Máquina 1">
  <img src="screenshots/screenshots (5).png" alt="Paso 5: Añadir usuarios Máquina 2">
  <img src="screenshots/screenshots (6).png" alt="Paso 6: Edición hosts Máquina 1">
  <img src="screenshots/screenshots (7).png" alt="Paso 7: Edición hosts Máquina 2">
  <img src="screenshots/screenshots (8).png" alt="Paso 8: Instalación Postfix">
  <img src="screenshots/screenshots (9).png" alt="Paso 9: Edición main.cf">
  <img src="screenshots/screenshots (10).png" alt="Paso 10: Archivo virtual usuarios">
  <img src="screenshots/screenshots (11).png" alt="Paso 11: Aliases listas de distribución">
  <img src="screenshots/screenshots (12).png" alt="Paso 12: postmap virtual">
  <img src="screenshots/screenshots (13).png" alt="Paso 13: Reinicio Postfix">
  <img src="screenshots/screenshots (14).png" alt="Paso 14: Instalación mailutils">
  <img src="screenshots/screenshots (15).png" alt="Paso 15: dovecot.conf protocolos">
  <img src="screenshots/screenshots (16).png" alt="Paso 16: 10-mail.conf mail_location">
  <img src="screenshots/screenshots (17).png" alt="Paso 17: 10-auth.conf disable_plaintext_auth">
  <img src="screenshots/screenshots (18).png" alt="Paso 18: Reinicio Dovecot">
  <img src="screenshots/screenshots (19).png" alt="Paso 19: mkdir Maildir usuarios">
  <img src="screenshots/screenshots (20).png" alt="Paso 20: Telnet SMTP">
  <img src="screenshots/screenshots (21).png" alt="Paso 21: Telnet IMAP">
  <img src="screenshots/screenshots (22).png" alt="Paso 22: Telnet POP3">
  <img src="screenshots/screenshots (23).png" alt="Paso 23: Thunderbird config usuarios">
  <img src="screenshots/screenshots (24).png" alt="Paso 24: Envío interno/externo">
  <img src="screenshots/screenshots (25).png" alt="Paso 25: Verificación final listas">

</div>

## Aprendizajes Clave
- Configuración de Postfix para dominios virtuales y listas de distribución.
- Dovecot para recepción segura con IMAP/POP3.
- Pruebas con Thunderbird y telnet para verificación.
- Gestión de NAT y rutas para acceso externo.

## Relevancia Profesional
Habilidades para:
- Administración de servidores de correo (internos/externos).
- DevOps/Cloud (base para servicios como AWS SES o Google Workspace).
- Ciberseguridad (autenticación y conexiones seguras).

## Conclusión
Proyecto funcional con servidor de correo, listas de distribución y pruebas completas.

¡Gracias por visitar! Dale ⭐ si te gusta.

---
**Autor**: Pau Olivé Moreno  
**Fecha**: Principios de 2025