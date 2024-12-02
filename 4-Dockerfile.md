<h1>4. Dockerfile</h1>

<h2>¿Qué es un Dockerfile?</h2>
<p>Un <strong>Dockerfile</strong> es un archivo de texto que contiene una serie de instrucciones que Docker usa para construir una imagen. Las instrucciones indican cómo instalar las dependencias, copiar archivos, configurar el entorno y ejecutar los comandos necesarios para la aplicación dentro del contenedor. Un Dockerfile es esencial para crear imágenes personalizadas que se adapten a tus necesidades específicas.</p>

<h3>¿Por qué usar un Dockerfile?</h3>
<p>Usar un Dockerfile tiene varias ventajas:</p>
<ul>
    <li><strong>Automatización</strong>: Puedes automatizar el proceso de construcción de imágenes.</li>
    <li><strong>Reproducibilidad</strong>: Asegura que la misma imagen se pueda construir en cualquier entorno, garantizando consistencia.</li>
    <li><strong>Facilidad de mantenimiento</strong>: Si necesitas actualizar la imagen, solo tienes que modificar el Dockerfile y volver a construir la imagen.</li>
</ul>

<h2>Sintaxis Básica de un Dockerfile</h2>
<p>La sintaxis de un Dockerfile es muy simple, pero hay ciertas convenciones que debes seguir. A continuación, se describen las instrucciones más comunes:</p>

<h3>1. FROM</h3>
<p>Define la imagen base a partir de la cual se construirá la nueva imagen. Esta es la primera instrucción que debes incluir en un Dockerfile.</p>

```dockerfile
FROM <imagen_base>
```
<p>Ejemplo:</p>

```dockerfile
FROM ubuntu:20.04
```

<h3>2. RUN</h3>
<p>Ejecuta un comando dentro de la imagen durante el proceso de construcción. Esto se utiliza para instalar dependencias o realizar configuraciones.</p>

```dockerfile
RUN <comando>
```
<p>Ejemplo:</p>

```dockerfile
RUN apt-get update && apt-get install -y python3
```

<h3>3. COPY</h3>
<p>Copia archivos o directorios desde el sistema de archivos del host al contenedor.</p>

```dockerfile
COPY <fuente> <destino>
```
<p>Ejemplo:</p>

```dockerfile
COPY ./app /app
```

<h3>4. WORKDIR</h3>
<p>Define el directorio de trabajo en el contenedor. Todos los comandos siguientes (como RUN, CMD, etc.) se ejecutarán desde este directorio.</p>

```dockerfile
WORKDIR /app
```

<h3>5. CMD</h3>
<p>Especifica el comando que se ejecutará cuando se inicie el contenedor. Solo debe haber una instrucción CMD en el Dockerfile. Si se incluye más de una, solo se ejecutará la última.</p>

```dockerfile
CMD ["python3", "app.py"]
```

<h3>6. EXPOSE</h3>
<p>Indica qué puertos deben ser abiertos en el contenedor. Esto no publica los puertos, solo los hace visibles para otros contenedores.</p>

```dockerfile
EXPOSE 8080
```

<h3>7. ENV</h3>
<p>Establece variables de entorno en el contenedor.</p>

```dockerfile
ENV <clave> <valor>
```
<p>Ejemplo:</p>

```dockerfile
ENV APP_ENV=production
```

<h3>8. VOLUME</h3>
<p>Crea un punto de montaje para un volumen, lo que permite que datos persistentes se mantengan fuera del contenedor.</p>

```dockerfile
VOLUME ["/data"]
```

<h2>Ejemplo Completo de un Dockerfile</h2>
<p>A continuación, se muestra un ejemplo completo de un Dockerfile que crea una imagen para una aplicación Python:</p>

```dockerfile
# Usa una imagen base de Python
FROM python:3.8-slim

# Establece el directorio de trabajo
WORKDIR /app

# Copia el archivo de requisitos
COPY requirements.txt /app/

# Instala las dependencias
RUN pip install -r requirements.txt

# Copia el código fuente de la aplicación
COPY . /app

# Expone el puerto donde la app escuchará
EXPOSE 5000

# Comando para ejecutar la aplicación
CMD ["python", "app.py"]
```

<p>En este ejemplo:</p>
<ul>
    <li>Se utiliza una imagen base de Python 3.8.</li>
    <li>Se establece un directorio de trabajo /app dentro del contenedor.</li>
    <li>Se copian los archivos <code>requirements.txt</code> y el código de la aplicación.</li>
    <li>Se instalan las dependencias desde el archivo <code>requirements.txt</code>.</li>
    <li>Se expone el puerto 5000, que es donde la aplicación escuchará las conexiones.</li>
    <li>El contenedor ejecutará el comando <code>python app.py</code> cuando se inicie.</li>
</ul>

<h2>Construcción de una Imagen con un Dockerfile</h2>
<p>Una vez que tengas tu Dockerfile listo, puedes construir una imagen usando el siguiente comando en la misma carpeta donde se encuentra el Dockerfile:</p>
<pre><code>docker build -t &lt;nombre_de_imagen&gt; .</code></pre>
<p>Esto construirá la imagen y la etiquetará con el nombre &lt;nombre_de_imagen&gt;. Puedes verificar que la imagen se haya creado correctamente usando el comando <code>docker images</code>.</p>

<h2>Buenas Prácticas al Escribir Dockerfiles</h2>
<ul>
    <li><strong>Optimiza las capas</strong>: Cada instrucción en un Dockerfile crea una nueva capa en la imagen. Intenta combinar las instrucciones <code>RUN</code> para minimizar el número de capas.</li>
    <li><strong>Usa imágenes base pequeñas</strong>: Si no necesitas una imagen base grande, usa imágenes más ligeras como <code>alpine</code> o versiones específicas como <code>python:3.8-slim</code> para reducir el tamaño de la imagen.</li>
    <li><strong>Minimiza el uso de COPY</strong>: Si solo necesitas copiar archivos específicos, hazlo de manera selectiva en lugar de copiar todo el directorio.</li>
    <li><strong>Evita información sensible</strong>: Nunca pongas contraseñas o información sensible directamente en el Dockerfile.</li>
</ul>