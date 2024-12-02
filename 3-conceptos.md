<h1>3. Conceptos Básicos de Docker</h1>

<h2>Imágenes y Contenedores</h2>

<h3>¿Qué es una Imagen Docker?</h3>
<p>Una <strong>imagen Docker</strong> es un archivo que contiene todo lo necesario para ejecutar una aplicación: el código, las dependencias, las bibliotecas del sistema operativo, las configuraciones, etc. Las imágenes son inmutables, lo que significa que una vez creadas, no pueden modificarse.</p>
<p>Las imágenes se construyen a partir de un <strong>Dockerfile</strong>, que es un archivo de texto que contiene instrucciones sobre cómo debe ser configurada la imagen. Las imágenes pueden ser reutilizadas para crear múltiples contenedores.</p>

<h3>¿Qué es un Contenedor Docker?</h3>
<p>Un <strong>contenedor Docker</strong> es una instancia en ejecución de una imagen. Es un proceso aislado que se ejecuta en el sistema operativo host y tiene su propio sistema de archivos, procesos y red, pero comparte el núcleo del sistema operativo del host.</p>
<p>A diferencia de las máquinas virtuales, los contenedores son más ligeros y eficientes porque no necesitan un sistema operativo completo. Los contenedores se pueden iniciar, detener, mover y eliminar de manera rápida.</p>

<h2>Docker Hub y Repositorios</h2>
<p><strong>Docker Hub</strong> es un repositorio centralizado donde puedes encontrar imágenes Docker listas para usar, tanto oficiales como de la comunidad. Puedes buscar imágenes de diferentes aplicaciones y servicios, como bases de datos, servidores web, lenguajes de programación, etc.</p>

<h3>Subir tus propias imágenes a Docker Hub</h3>
<p>Para subir una imagen propia a Docker Hub, sigue estos pasos:</p>
<ol>
    <li><strong>Inicia sesión en Docker Hub</strong><br>
        Si aún no tienes una cuenta, crea una en <a href="https://hub.docker.com/" target="_blank">Docker Hub</a>.
        Luego, inicia sesión desde la terminal:
        <pre><code>docker login</code></pre>
    </li>
    <li><strong>Etiqueta tu imagen</strong><br>
        Las imágenes deben estar etiquetadas con tu nombre de usuario en Docker Hub. Usa el siguiente comando para etiquetar una imagen:
        <pre><code>docker tag &lt;ID_de_imagen&gt; &lt;usuario&gt;/&lt;repositorio&gt;:&lt;etiqueta&gt;</code></pre>
    </li>
    <li><strong>Sube la imagen</strong><br>
        Después de etiquetar la imagen, puedes subirla con:
        <pre><code>docker push &lt;usuario&gt;/&lt;repositorio&gt;:&lt;etiqueta&gt;</code></pre>
    </li>
</ol>

<h2>Comandos Básicos de Docker</h2>

<p>A continuación, algunos de los comandos más comunes de Docker que deberías conocer:</p>

<h3>docker build</h3>
<p>Este comando se utiliza para construir una imagen a partir de un Dockerfile. Debes ejecutar este comando en el directorio donde se encuentra tu Dockerfile:</p>
<pre><code>docker build -t &lt;nombre_de_imagen&gt; .</code></pre>
<p>Esto creará una imagen con el nombre &lt;nombre_de_imagen&gt;.</p>

<h3>docker run</h3>
<p>Este comando ejecuta un contenedor a partir de una imagen. Si no existe la imagen, Docker la descargará del Docker Hub.</p>
<pre><code>docker run -d --name &lt;nombre_contenedor&gt; &lt;nombre_imagen&gt;</code></pre>
<ul>
    <li><strong>-d</strong>: Ejecuta el contenedor en segundo plano (detached mode).</li>
    <li><strong>--name</strong>: Asigna un nombre al contenedor.</li>
</ul>

<h3>docker ps</h3>
<p>Muestra todos los contenedores en ejecución en el sistema. Para listar todos los contenedores, incluidos los detenidos, usa el siguiente comando:</p>
<pre><code>docker ps -a</code></pre>

<h3>docker images</h3>
<p>Este comando lista todas las imágenes disponibles en tu máquina local:</p>
<pre><code>docker images</code></pre>

<h3>docker stop</h3>
<p>Este comando detiene un contenedor en ejecución:</p>
<pre><code>docker stop &lt;nombre_contenedor&gt;</code></pre>

<h3>docker rm</h3>
<p>Este comando elimina un contenedor detenido. Si el contenedor está en ejecución, primero debes detenerlo:</p>
<pre><code>docker rm &lt;nombre_contenedor&gt;</code></pre>

<h3>docker rmi</h3>
<p>Este comando elimina una imagen localmente:</p>
<pre><code>docker rmi &lt;nombre_imagen&gt;</code></pre>

<h3>docker logs</h3>
<p>Muestra los logs de un contenedor en ejecución. Esto es útil para depurar aplicaciones dentro del contenedor:</p>
<pre><code>docker logs &lt;nombre_contenedor&gt;</code></pre>

<h3>docker exec</h3>
<p>Este comando permite ejecutar un comando dentro de un contenedor en ejecución:</p>
<pre><code>docker exec -it &lt;nombre_contenedor&gt; &lt;comando&gt;</code></pre>
<p>Por ejemplo, para abrir una terminal dentro del contenedor:</p>
<pre><code>docker exec -it &lt;nombre_contenedor&gt; bash</code></pre>


