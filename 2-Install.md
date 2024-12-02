# 2. Instalación de Docker

## Windows

### Requisitos previos
Antes de instalar Docker en Windows, asegúrate de que tu sistema cumple con los siguientes requisitos:
- **Windows 10** o **Windows 11** (versiones Home, Professional o Enterprise).
- **Virtualización habilitada** en la BIOS.
- **WSL 2** (Windows Subsystem for Linux 2) debe estar habilitado para la correcta ejecución de contenedores Docker.

### Instalación paso a paso

1. **Descargar Docker Desktop**:
   - Dirígete a la página de [descarga de Docker Desktop para Windows](https://www.docker.com/products/docker-desktop) y descarga el instalador.

2. **Ejecutar el instalador**:
   - Una vez descargado el archivo `.exe`, ejecútalo para iniciar la instalación. Durante el proceso, asegúrate de seleccionar la opción de instalar **WSL 2** si no lo has hecho previamente.

3. **Configurar Docker Desktop**:
   - Después de la instalación, abre Docker Desktop desde el menú de inicio. Docker se iniciará y configurará automáticamente.
   - Si es la primera vez que lo usas, es posible que se te pida reiniciar el sistema para aplicar la configuración de WSL 2.

4. **Verificación de la instalación**:
   - Abre una terminal (por ejemplo, PowerShell) y ejecuta el siguiente comando para verificar que Docker esté correctamente instalado:
     ```bash
     docker --version
     ```
   - Deberías ver la versión de Docker que has instalado. Si ves esto, significa que la instalación ha sido exitosa.

---

## Linux

### Requisitos previos
Asegúrate de tener los siguientes requisitos antes de proceder con la instalación de Docker:
- Una distribución de Linux compatible (Ubuntu, Debian, Fedora, CentOS, etc.).
- Privilegios de superusuario (root).

### Instalación paso a paso (para Ubuntu/Debian)

1. **Actualizar los paquetes**:
   - Abre una terminal y ejecuta los siguientes comandos para asegurarte de que los paquetes de tu sistema están actualizados:
     ```bash
     sudo apt update
     sudo apt upgrade
     ```

2. **Instalar dependencias necesarias**:
   - Ejecuta el siguiente comando para instalar las dependencias necesarias para Docker:
     ```bash
     sudo apt install apt-transport-https ca-certificates curl software-properties-common
     ```

3. **Añadir la clave GPG de Docker**:
   - Asegúrate de que tu sistema pueda verificar la autenticidad de los paquetes de Docker ejecutando:
     ```bash
     curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
     ```

4. **Añadir el repositorio de Docker**:
   - Ejecuta el siguiente comando para añadir el repositorio de Docker a tu lista de fuentes:
     ```bash
     echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
     ```

5. **Instalar Docker**:
   - Instala Docker ejecutando:
     ```bash
     sudo apt update
     sudo apt install docker-ce
     ```

6. **Verificación de la instalación**:
   - Una vez instalado Docker, verifica la instalación ejecutando:
     ```bash
     docker --version
     ```
   - También puedes probar si Docker está funcionando correctamente ejecutando un contenedor de prueba:
     ```bash
     sudo docker run hello-world
     ```

---

## Mac OS

### Requisitos previos
Para instalar Docker en macOS, asegúrate de tener:
- **macOS 10.14** o superior.
- **Virtualización habilitada**.

### Instalación paso a paso

1. **Descargar Docker Desktop**:
   - Dirígete a la página de [descarga de Docker Desktop para Mac](https://www.docker.com/products/docker-desktop) y descarga el instalador.

2. **Ejecutar el instalador**:
   - Abre el archivo `.dmg` descargado y arrastra el ícono de Docker a la carpeta de Aplicaciones.

3. **Configurar Docker Desktop**:
   - Abre Docker Desktop desde la carpeta de Aplicaciones. Al iniciar por primera vez, Docker puede solicitar permisos para instalar componentes adicionales como HyperKit, que es necesario para la virtualización.

4. **Verificación de la instalación**:
   - Abre la terminal y ejecuta:
     ```bash
     docker --version
     ```
   - Si la instalación fue exitosa, verás la versión de Docker instalada. También puedes ejecutar el siguiente comando para verificar que Docker esté funcionando:
     ```bash
     docker run hello-world
     ```

---

Con estos pasos, Docker debería estar correctamente instalado en Windows, Linux o macOS, y listo para comenzar a utilizarse.

