---


---

<h1 id="🚀-despliegue-de-aplicación-pokedex-en-azure">🚀 Despliegue de Aplicación PokeDex en Azure</h1>
<h2 id="📌-información-general">📌 Información General</h2>
<ul>
<li><strong>Proyecto:</strong> PokeDex Web</li>
<li><strong>Tipo:</strong> Aplicación web estática (Angular)</li>
<li><strong>Plataforma de despliegue:</strong> Microsoft Azure Static Web Apps</li>
<li><strong>Repositorio:</strong>  <a href="https://github.com/PAPILILOFER/pokedex">https://github.com/PAPILILOFER/pokedex</a></li>
</ul>
<hr>
<h2 id="🎯-objetivo">🎯 Objetivo</h2>
<p>Realizar el despliegue de una aplicación web en la nube utilizando buenas prácticas de DevOps y seguridad, asegurando su disponibilidad pública y correcta configuración.</p>
<hr>
<h2 id="⚙️-tecnologías-utilizadas">⚙️ Tecnologías Utilizadas</h2>
<ul>
<li>Angular</li>
<li>Node.js</li>
<li>Git &amp; GitHub</li>
<li>Azure Static Web Apps</li>
</ul>
<hr>
<h2 id="🧩-proceso-de-despliegue">🧩 Proceso de Despliegue</h2>
<h3 id="creación-del-repositorio">1. Creación del Repositorio</h3>
<p>Se creó un repositorio en GitHub llamado <code>pokedex</code>, donde se subió el código fuente completo del proyecto Angular.</p>
<pre><code>git init
git add .
git commit -m "subiendo proyecto angular"
git branch -M main
git remote add origin https://github.com/Mi_User_git/pokedex.git
git push -u origin main
</code></pre>
<h3 id="configuración-del-workflow">2. Configuración del Workflow</h3>
<p>Azure generó automáticamente un workflow de GitHub Actions para automatizar el despliegue.</p>
<p>Se ajustó la configuración para soportar Angular:</p>
<pre><code>app_location: "/"
api_location: ""
output_location: "dist/pokedex-angular"
</code></pre>
<p>Esta configuración permite que Azure compile el proyecto y despliegue correctamente los archivos generados.</p>
<hr>
<h3 id="proceso-de-build">4. Proceso de Build</h3>
<p>El sistema ejecuta automáticamente:</p>
<pre><code>npm install
npm run build
</code></pre>
<p>Generando la carpeta:</p>
<pre><code>dist/pokedex-angular
</code></pre>
<p>Donde se encuentra el archivo <code>index.html</code> necesario para el despliegue.</p>
<hr>
<h3 id="resolución-de-errores">5. Resolución de Errores</h3>
<h4 id="error-inicial">Error inicial:</h4>
<pre><code>Failed to find a default file in the app artifacts folder
</code></pre>
<h4 id="solución">Solución:</h4>
<p>Se corrigió la propiedad <code>output_location</code> en el workflow para apuntar a la carpeta correcta del build.</p>
<hr>
<h3 id="problemas-con-rutas-y-recursos">6. Problemas con rutas y recursos</h3>
<p>Durante el despliegue se presentaron errores relacionados con las rutas de la aplicación, especialmente porque Angular estaba generando URLs incorrectas con <code>/pokedex-angular/</code>.</p>
<p>Esto provocaba errores 404 en archivos como scripts, estilos e imágenes.</p>
<p>Para solucionarlo se ajustaron las rutas a una estructura más simple usando <code>assets/</code> sin prefijos adicionales, asegurando que los recursos se cargaran correctamente tanto en local como en producción.</p>
<hr>
<h3 id="configuración-de-seguridad-headers-http">7. Configuración de seguridad (headers HTTP)</h3>
<p>Se añadieron encabezados de seguridad para mejorar la protección de la aplicación desde Azure mediante el archivo:</p>
<p>📄 <code>staticwebapp.config.json</code></p>
<p>{<br>
“globalHeaders”: {<br>
“X-Content-Type-Options”: “nosniff”,<br>
“X-Frame-Options”: “DENY”,<br>
“Referrer-Policy”: “strict-origin-when-cross-origin”,<br>
“Strict-Transport-Security”: “max-age=31536000; includeSubDomains; preload”,<br>
“Permissions-Policy”: “geolocation=(), camera=(), microphone=()”,<br>
“Content-Security-Policy”: “default-src ‘self’; img-src ‘self’ <a href="https://pokeapi.co">https://pokeapi.co</a> <a href="https://assets.pokemon.com">https://assets.pokemon.com</a> data:; script-src ‘self’ ‘unsafe-inline’; style-src ‘self’ ‘unsafe-inline’;”<br>
}<br>
}</p>
<p>Durante esta parte se presentaron bloqueos de imágenes externas debido a la CSP, lo que llevó a ajustar los dominios permitidos para que la aplicación pudiera consumir correctamente recursos como sprites de Pokémon.</p>
<hr>
<h3 id="prueba-de-seguridad">8. Prueba de seguridad</h3>
<p>Se utilizó la herramienta:</p>
<p><a href="https://securityheaders.com/">https://securityheaders.com/</a></p>
<p>El análisis permitió verificar que los encabezados de seguridad estaban correctamente aplicados, mejorando la calificación general del sitio.</p>
<h2 id="⚠️-problemas-encontrados">⚠️ Problemas encontrados</h2>
<ul>
<li>Rutas incorrectas generadas por Angular en producción</li>
<li>Errores 404 por uso de <code>/pokedex-angular/</code> en recursos</li>
<li>Bloqueo de imágenes externas por la política CSP</li>
<li>Diferencias entre entorno local y producción</li>
</ul>
<hr>
<h2 id="✅-soluciones-aplicadas">✅ Soluciones aplicadas</h2>
<ul>
<li>Corrección de rutas a <code>assets/</code> sin prefijos</li>
<li>Ajuste del <code>navigationFallback</code> para SPA</li>
<li>Configuración de CSP para permitir recursos externos necesarios</li>
<li>Limpieza de builds y despliegues en Azure</li>
</ul>
<hr>
<h2 id="🧠-conclusión">🧠 Conclusión</h2>
<p>El despliegue permitió entender cómo una aplicación Angular cambia su comportamiento entre entorno local y producción. También se evidenció la importancia de configurar correctamente rutas, builds y políticas de seguridad.</p>
<p>Además, se aprendió que la seguridad web no es solo un complemento, sino una parte fundamental del despliegue, ya que los encabezados HTTP ayudan a proteger la aplicación frente a ataques comunes y mejoran su calidad general en entornos reales.</p>

