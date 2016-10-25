# Servidor de base de datos MongoDB

<p style="font-size: 16px;">Instalación y configuración de MongoDB en Archlinux / Ubuntu</p>

### 1. Instalar

#### Archlinux

```bash
$ sudo pacman -S mongodb
```

### 3. Arrancar y habilitar servicio

```bash
# Iniciar servicio
$ sudo systemctl start mongodb.service
# Iniciar habilitar inicio automático con el sistema
$ sudo systemctl enable mongodb.service
```

### 3. Arreglando Problemas

- Arreglango mensaje de advertencia `WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.`

    ```bash
    $ mongo
    MongoDB shell version: 3.2.9
    connecting to: test
    Welcome to the MongoDB shell.
    For interactive help, type "help".
    For more comprehensive documentation, see
    	http://docs.mongodb.org/
    Questions? Try the support group
    	http://groups.google.com/group/mongodb-user
    Server has startup warnings:
    2016-10-24T19:27:50.766-0500 I CONTROL  [initandlisten]
    2016-10-24T19:27:50.766-0500 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
    2016-10-24T19:27:50.766-0500 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
    2016-10-24T19:27:50.766-0500 I CONTROL  [initandlisten]
    ```

    ```bash
    $ sudo echo never > /sys/kernel/mm/transparent_hugepage/enabled
    ```

    ```bash
    $ sudo systemctl restart mongodb.service
    ```
