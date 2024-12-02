<h1>5. Docker Compose</h1>

<h2>¿Qué es Docker Compose?</h2>
<p><strong>Docker Compose</strong> es una herramienta que permite definir y ejecutar aplicaciones Docker multi-contenedor. Con Compose, puedes configurar los contenedores necesarios para una aplicación, sus redes, volúmenes y dependencias en un solo archivo YAML. Esto simplifica la administración de aplicaciones complejas y facilita la configuración y la puesta en marcha de múltiples contenedores simultáneamente.</p>

<h3>Ventajas de Docker Compose</h3>
<ul>
    <li><strong>Definir todo en un solo archivo</strong>: Puedes definir todos los servicios y configuraciones en un solo archivo <code>docker-compose.yml</code>.</li>
    <li><strong>Fácil de usar</strong>: Docker Compose permite iniciar, detener y gestionar múltiples contenedores con un solo comando.</li>
    <li><strong>Automatización</strong>: Permite automatizar la creación y configuración de los contenedores necesarios para tu aplicación.</li>
    <li><strong>Escalabilidad</strong>: Puedes escalar servicios para manejar mayores cargas de trabajo sin necesidad de configurar cada contenedor individualmente.</li>
</ul>

<h2>Archivo docker-compose.yml</h2>
<p>El archivo <code>docker-compose.yml</code> es donde defines la configuración de todos los servicios, redes y volúmenes que tu aplicación necesita. Este archivo se escribe en formato YAML y sigue una estructura específica. A continuación se explican las secciones principales:</p>

<h3>1. version</h3>
<p>Especifica la versión de la configuración de Docker Compose que se utilizará. Por lo general, puedes usar la versión más reciente, que es la que garantiza todas las funciones más avanzadas.</p>
<pre><code>version: '3.8'</code></pre>

<h3>2. services</h3>
<p>En esta sección se definen los contenedores que forman parte de la aplicación. Cada servicio es un contenedor con su propia configuración (puerto, volumen, red, etc.).</p>

```yaml
services:
  web:
    image: nginx
    ports:
      - "80:80"
  db:
    image: postgres
    environment:
      POSTGRES_PASSWORD: example
```
<p>En este ejemplo, hay dos servicios: <code>web</code> y <code>db</code>. El servicio <code>web</code> utiliza la imagen <code>nginx</code> y expone el puerto 80, mientras que el servicio <code>db</code> usa la imagen <code>postgres</code> y establece una variable de entorno para la contraseña de la base de datos.</p>

<h3>3. networks</h3>
<p>Define las redes que utilizarán los servicios. Esto es útil si deseas controlar cómo los servicios se comunican entre sí.</p>

```yaml
networks:
  default:
    external:
      name: my-network
```

<h3>4. volumes</h3>
<p>Define volúmenes que serán compartidos entre los contenedores y/o persistirán datos fuera de los contenedores.</p>

```yaml
volumes:
  my-data:
```

<h2>Ejemplo Completo de docker-compose.yml</h2>
<p>A continuación, te mostramos un ejemplo de un archivo <code>docker-compose.yml</code> para una aplicación web sencilla que incluye un contenedor para la base de datos y otro para el servidor web:</p>

```yaml
services:
  web:
    image: nginx
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
    networks:
      - frontend
  db:
    image: postgres:latest
    environment:
      POSTGRES_PASSWORD: example
    networks:
      - backend

networks:
  frontend:
  backend:

volumes:
  db_data:
```

<p>En este ejemplo:</p>
<ul>
    <li>El servicio <code>web</code> utiliza la imagen de <code>nginx</code> y expone el puerto 8080 en el host, redirigiéndolo al puerto 80 dentro del contenedor. También monta un volumen local <code>./html</code> para servir contenido web.</li>
    <li>El servicio <code>db</code> utiliza la imagen de <code>postgres</code> y establece la contraseña de la base de datos mediante la variable de entorno <code>POSTGRES_PASSWORD</code>.</li>
    <li>Ambos servicios se conectan a diferentes redes, <code>frontend</code> para el servicio web y <code>backend</code> para la base de datos.</li>
    <li>Se define un volumen persistente para la base de datos con <code>db_data</code>.</li>
</ul>

<h2>Comandos Básicos de Docker Compose</h2>

<h3>1. `docker-compose up`</h3>
<p>Este comando construye y ejecuta los contenedores definidos en el archivo <code>docker-compose.yml</code>. Si los contenedores no están construidos, los construye primero. Si quieres ejecutarlos en segundo plano, puedes usar el modificador <code>-d</code>:</p>
<pre><code>docker-compose up -d</code></pre>

<h3>2. `docker-compose down`</h3>
<p>Este comando detiene y elimina los contenedores, redes y volúmenes definidos en el archivo Compose. Esto no elimina las imágenes:</p>
<pre><code>docker-compose down</code></pre>

<h3>3. `docker-compose build`</h3>
<p>Este comando construye o reconstruye las imágenes de los servicios definidos en el archivo <code>docker-compose.yml</code>:</p>
<pre><code>docker-compose build</code></pre>

<h3>4. `docker-compose logs`</h3>
<p>Este comando muestra los registros de los contenedores:</p>
<pre><code>docker-compose logs</code></pre>

<h3>5. `docker-compose exec`</h3>
<p>Este comando ejecuta un comando dentro de un contenedor en ejecución. Por ejemplo, para ejecutar una shell interactiva dentro del servicio web:</p>
<pre><code>docker-compose exec web bash</code></pre>

<h2>Conclusión</h2>
<p>Docker Compose simplifica la gestión de aplicaciones que requieren varios contenedores, como bases de datos, servidores web, y otros servicios. Usando un archivo YAML, puedes definir, administrar y poner en marcha estos contenedores con facilidad, lo que mejora la productividad y facilita la creación de entornos de desarrollo consistentes.</p>
