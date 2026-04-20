---


---

<h1 id="🚀-paso-a-paso-del-despliegue-en-azure-static-web-apps">🚀 Paso a paso del despliegue en Azure Static Web Apps</h1>
<p>Primero creé una cuenta en Azure (en mi caso fue personal y la vinculé con una tarjeta).<br>
Luego busqué en la parte superior el servicio <strong>“Static Web Apps”</strong> y entré a esa opción.</p>
<p>Después di clic en <strong>Crear</strong> para iniciar la configuración.</p>
<h2 id="⚙-configuración">⚙ Configuración</h2>
<p>Seleccioné la suscripción por defecto y creé un nuevo grupo de recursos llamado <strong>pokedex-rg</strong>.</p>
<p>Elegí una región cercana (en mi caso una global o East US).</p>
<p>Luego conecté mi cuenta de GitHub e inicié sesión.</p>
<p>Después seleccioné:</p>
<ul>
<li>El repositorio: <strong>pokedex</strong></li>
<li>La rama: <strong>main</strong></li>
</ul>
<h2 id="🛠-configuración-del-build">🛠 Configuración del build</h2>
<p>En esta parte elegí la opción de proyecto estático (HTML, React, etc.).</p>
<p>Dejé las rutas por defecto:</p>
<ul>
<li>Ubicación de la app: <strong>/</strong></li>
<li>Ubicación de la API: <strong>/</strong>(no aplica en este caso)</li>
<li>Carpeta de salida: <strong>/</strong></li>
</ul>
<h2 id="🎯-finalización">🎯 Finalización</h2>
<p>Después revisé la configuración y di clic en <strong>Crear</strong>.</p>
<p>Azure empezó a configurar todo automáticamente y al finalizar me llevó a una página donde ya estaba creado el entorno y la URL de mi proyecto desplegado.</p>
<h2 id="🗒-nota">🗒 Nota</h2>
<p>Al inicio la página puede mostrar una vista por defecto de Azure mientras termina el despliegue completo, pero después ya carga la aplicación correctamente.</p>
<h1 id="reflexión-técnica">Reflexión Técnica</h1>
<p><strong>1. ¿Qué vulnerabilidades previenen los encabezados implementados?</strong><br>
Previenen varios ataques comunes en la web. Por ejemplo, el CSP evita que se ejecuten scripts maliciosos (XSS), el X-Frame-Options protege contra clickjacking, y el HSTS obliga a usar HTTPS para evitar que intercepten la información. En general, ayudan a que la app solo cargue recursos seguros y no pueda ser manipulada fácilmente.</p>
<p><strong>2. ¿Qué aprendiste sobre la relación entre despliegue y seguridad web?</strong><br>
Aprendí que la seguridad no depende solo del código, sino mucho del entorno donde se despliega. En local todo funcionaba bien, pero en producción aparecieron problemas con rutas, recursos y políticas de seguridad. Me di cuenta de que en Azure se configuran cosas clave como headers y que un mal ajuste ahí puede romper la app o dejarla vulnerable.</p>
<p><strong>3. ¿Qué desafíos encontraste en el proceso?</strong><br>
Tuve problemas con rutas, errores 404, diferencias entre local y 		     producción, y la configuración del CSP que me bloqueaba cosas como  imágenes. También fue difícil entender qué se arreglaba en Angular y qué en   Azure.</p>

