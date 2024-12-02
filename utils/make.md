

<header>
    <h1>Guía de Uso de Make</h1>
</header>

<section>
    <h2>¿Qué es Make?</h2>
    <p><strong>Make</strong> es una herramienta de automatización de tareas utilizada para gestionar la ejecución de comandos y tareas repetitivas. Aunque se asocia principalmente con la compilación de proyectos en C y C++, puede usarse para cualquier tipo de tarea que implique ejecutar comandos de forma ordenada, como la ejecución de scripts, creación de archivos, limpieza de proyectos, entre otros.</p>
    <p>Make utiliza un archivo de texto llamado <strong>Makefile</strong>, donde se definen una serie de reglas que indican qué tareas deben ejecutarse y en qué orden, gestionando las dependencias entre las tareas. De esta forma, solo se ejecutan las tareas necesarias, lo que optimiza el proceso.</p>
</section>

<section>
    <h2>¿Por qué usar Make?</h2>
    <ul>
        <li><strong>Automatización:</strong> Permite automatizar tareas repetitivas como la ejecución de scripts, la creación de archivos, la actualización de sistemas, etc.</li>
        <li><strong>Eficiencia:</strong> Solo ejecuta las tareas que realmente necesitan ser actualizadas, evitando trabajos innecesarios.</li>
        <li><strong>Facilidad de Uso:</strong> El archivo Makefile permite definir tareas de manera sencilla con una sintaxis fácil de entender.</li>
        <li><strong>Portabilidad:</strong> Los Makefiles son fáciles de compartir y reproducir en diferentes entornos o máquinas.</li>
    </ul>
</section>

<section>
<h2>Instalación de Make</h2>

<h3>En Windows</h3>
<p>En Windows, Make no está disponible por defecto, pero se puede instalar de las siguientes formas:</p>

<h4>Opción 1: Instalar Make a través de <a href="https://chocolatey.org/install" target="_blank">Chocolatey</a></h4>
<ol>
    <li>Primero, instala <a href="https://chocolatey.org/install" target="_blank">Chocolatey</a>.</li>
    <li>Luego, abre una terminal de administrador (cmd o PowerShell) y ejecuta el siguiente comando:</li>
</ol>
<pre><code>choco install make</code></pre>

<h4>Opción 2: Instalar Make usando <a href="https://docs.microsoft.com/en-us/windows/wsl/" target="_blank">WSL (Windows Subsystem for Linux)</a></h4>
<ol>
    <li>Habilita WSL siguiendo la <a href="https://docs.microsoft.com/en-us/windows/wsl/" target="_blank">documentación oficial</a>.</li>
    <li>Abre la terminal de WSL y ejecuta los siguientes comandos:</li>
</ol>
<pre><code>sudo apt update</code></pre>
<pre><code>sudo apt install make</code></pre>

<h3>En macOS</h3>
<p>En macOS, puedes instalar Make fácilmente usando el gestor de paquetes <a href="https://brew.sh/" target="_blank">Homebrew</a>.</p>
<ol>
    <li>Si aún no tienes Homebrew, instala con el siguiente comando:</li>
</ol>
<pre><code>/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"</code></pre>
<ol>
    <li>Una vez que tengas Homebrew instalado, ejecuta el siguiente comando para instalar Make:</li>
</ol>
<pre><code>brew install make</code></pre>

<h3>En Linux</h3>
<p>En la mayoría de las distribuciones de Linux, Make está disponible en los repositorios de paquetes. Para instalarlo, ejecuta el siguiente comando según tu distribución:</p>

<h4>Para distribuciones basadas en Debian (Ubuntu, Linux Mint, etc.)</h4>
<pre><code>sudo apt update</code></pre>
<pre><code>sudo apt install make</code></pre>

<h4>Para distribuciones basadas en Red Hat (CentOS, Fedora, etc.)</h4>
<pre><code>sudo dnf install make</code></pre>

<h4>Para distribuciones basadas en Arch Linux</h4>
<pre><code>sudo pacman -S make</code></pre>
</section>

<section>
<h2>Uso Básico de Make</h2>
<p>Make utiliza archivos llamados <strong>Makefiles</strong>, donde se definen una serie de reglas. Cada regla tiene tres componentes:</p>
<ol>
    <li><strong>Regla:</strong> Define la tarea a ejecutar.</li>
    <li><strong>Dependencias:</strong> Archivos o tareas que deben existir antes de ejecutar la regla.</li>
    <li><strong>Acción:</strong> El comando que se ejecuta para realizar la tarea.</li>
</ol>

<h3>Ejemplo de Makefile Simple</h3>
<p>El siguiente Makefile crea un archivo <code>hello.txt</code> con el contenido "¡Hola, Mundo!".</p>
        <pre><code>
# Makefile simple

all: hello.txt

hello.txt:
    echo "¡Hola, Mundo!" > hello.txt
        </code></pre>
<p>Para ejecutar este Makefile, solo debes ejecutar el siguiente comando en la terminal:</p>
<pre><code>make</code></pre>
<p>Cuando ejecutas <code>make</code>, el archivo <code>hello.txt</code> será creado si no existe.</p>

<h3>Uso Genérico de Make</h3>
<p>Make no se limita solo a la compilación de código, también puede usarse para cualquier tarea repetitiva. Algunos ejemplos incluyen:</p>

<h4>1. Ejecutar un script</h4>
<p>Para ejecutar un script de Python o Bash, puedes crear una regla como la siguiente:</p>
<pre><code>
run-script:
    python3 my_script.py
        </code></pre>
<p>Ejecuta esta tarea con:</p>
<pre><code>make run-script</code></pre>

<h4>2. Crear un archivo comprimido</h4>
<p>Para crear un archivo comprimido con los archivos <code>.txt</code> en el directorio, usa la siguiente regla:</p>
<pre><code>
archive:
    tar -cvf archive.tar *.txt
        </code></pre>
        <p>Ejecuta esta tarea con:</p>
        <pre><code>make archive</code></pre>

<h4>3. Limpiar archivos temporales</h4>
<p>Para eliminar archivos temporales generados por otros procesos, usa la siguiente regla:</p>
<pre><code>
clean:
    rm -f *.tmp
        </code></pre>
        <p>Ejecuta esta tarea con:</p>
        <pre><code>make clean</code></pre>

<h3>Variables en Makefiles</h3>
<p>También puedes definir variables para hacer tus Makefiles más reutilizables:</p>
        <pre><code>
FILES = file1.txt file2.txt

archive:
    tar -cvf archive.tar $(FILES)
        </code></pre>
<p>En este ejemplo, la variable <code>FILES</code> contiene los archivos que serán comprimidos. Para usarlos, simplemente referénciate a la variable con <code>$(FILES)</code>.</p>
</section>


