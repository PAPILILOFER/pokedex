---


---

<h1 id="🚀-paso-a-paso-del-despliegue-en-azure-static-web-apps">🚀 Paso a paso del despliegue en Azure Static Web Apps</h1>
<p>Primero crear una cuenta en Azure (en mi caso fue personal y la vinculé con una tarjeta).<br>
Luego buscar en la parte superior el servicio <strong>“Static Web Apps”</strong> y entrar a esa opción.</p>
<p>Después dar clic en <strong>Crear</strong> para iniciar la configuración.</p>
<h2 id="⚙-configuración">⚙ Configuración</h2>
<p>Seleccionar la suscripción que quieras en (mi caso por defecto) y crear un nuevo grupo de recursos llamado <strong>pokedex-rg</strong>.</p>
<p>Elegir una región cercana (en mi caso una global).</p>
<p>Luego conectar la cuenta de GitHub e iniciar sesión.</p>
<p>Después seleccionar:</p>
<ul>
<li>El repositorio: <strong>pokedex</strong></li>
<li>La rama: <strong>main</strong></li>
</ul>
<h2 id="🛠-configuración-del-build">🛠 Configuración del build</h2>
<p>En esta parte elegir la opción de proyecto estático (HTML, React, etc.).</p>
<p>Dejar las rutas por defecto:</p>
<ul>
<li>Ubicación de la app: <strong>/</strong></li>
<li>Ubicación de la API: <strong>/</strong></li>
<li>Carpeta de salida: <strong>/</strong></li>
</ul>
<h2 id="🎯-finalización">🎯 Finalización</h2>
<p>Después de que Azure revisé la configuración y dar clic en <strong>Crear</strong>.</p>
<p>Azure empieza a configurar todo automáticamente y al finalizar redireccionara a una página donde ya estará creado el entorno y la URL del proyecto desplegado.</p>
<h2 id="🗒-nota">🗒 Nota</h2>
<p>Al inicio la página puede mostrar una vista por defecto de Azure mientras termina el despliegue completo, pero después ya carga la aplicación correctamente.</p>
<h1 id="reflexión-técnica">Reflexión Técnica</h1>
<p><strong>1. ¿Qué vulnerabilidades previenen los encabezados implementados?</strong><br>
Previenen varios ataques comunes en la web. Por ejemplo, el CSP evita que se ejecuten scripts maliciosos (XSS), el X-Frame-Options protege contra clickjacking, y el HSTS obliga a usar HTTPS para evitar que intercepten la información. En general, ayudan a que la app solo cargue recursos seguros y no pueda ser manipulada fácilmente.</p>
<p><strong>2. ¿Qué aprendiste sobre la relación entre despliegue y seguridad web?</strong><br>
Aprendí que la seguridad no depende solo del código, sino mucho del entorno donde se despliega. En local todo funcionaba bien, pero en producción aparecieron problemas con rutas, recursos y políticas de seguridad. Me di cuenta de que en Azure se configuran cosas clave como headers y que un mal ajuste ahí puede romper la app o dejarla vulnerable.</p>
<p><strong>3. ¿Qué desafíos encontraste en el proceso?</strong><br>
Tuve problemas con rutas, errores 404, diferencias entre local y 		     producción, y la configuración del CSP que me bloqueaba cosas como  imágenes. También fue difícil entender qué se arreglaba en Angular y qué en   Azure.</p>

