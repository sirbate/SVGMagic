<!-- README.html / GitHub landing -->

<h1>🧙‍♂️ SVG Magic for Power Apps</h1>

<blockquote>
  Transforma gráficos SVG en fragmentos funcionales de Power FX y YAML para Power Apps — de forma simple, visual y profesional.
</blockquote>

<hr>

<nav>
  <ul>
    <li><a href="#funcionalidades">⚙️ Funcionalidades</a></li>
    <li><a href="#como-usar">🧪 Cómo usar esta herramienta</a></li>
    <li><a href="#preview">🖼️ Captura</a></li>
    <li><a href="#autor">👨‍💻 Autor</a></li>
    <li><a href="#licencia">🪪 Licencia</a></li>
  </ul>
</nav>

<hr>

<h2 id="funcionalidades">⚙️ Funcionalidades</h2>
<ul>
  <li>✅ Conversión directa de SVG a Power FX (EncodeUrl con base64)</li>
  <li>✅ Generador automático de bloques YAML listos para importar</li>
  <li>✅ Carga de SVG por texto o archivo</li>
  <li>✅ Vista previa interactiva del SVG</li>
  <li>✅ Selector de color integrado (Pickr)</li>
  <li>✅ Soporte multilenguaje: Español 🇪🇸, Inglés 🇺🇸, Portugués 🇧🇷</li>
  <li>✅ Interfaz oscura moderna, responsiva y ligera</li>
</ul>

<hr>

<h2 id="como-usar">🧪 Cómo usar esta herramienta</h2>

<h3>1️⃣ Copiar Código Power FX</h3>
<p>
  Pega tu SVG o súbelo → se genera automáticamente la línea Power FX con <code>EncodeUrl</code>:
</p>
<pre><code>= "data:image/svg+xml;utf8," & EncodeUrl("&lt;svg...&gt;")</code></pre>
<p>Luego podés usarlo directamente en un control de imagen en Power Apps.</p>

<h3>2️⃣ Copiar bloque YAML</h3>
<p>
  La herramienta también genera automáticamente un bloque YAML estructurado:
</p>

<pre><code>- SVGMagic:
    Control: Image
    Properties:
        Image: '= "data:image/svg+xml; utf-8, " & EncodeUrl($"&lt;svg ... /&gt;")'
        Height: =150
        Width: =150
        X: =50
        Y: =50
</code></pre>

<p>Este bloque puede ser utilizado en configuraciones avanzadas, documentación técnica o flujos ALM.</p>

<hr>

<h2 id="preview">🖼️ Captura de pantalla</h2>
<p>Vista de la herramienta en ejecución:</p>
<img src="./screenshots/preview.png" alt="Vista previa de SVG Magic" width="700px" />

<hr>

<h2 id="autor">👨‍💻 Autor</h2>
<p><strong>Andrés Velásquez</strong><br>
<a href="https://linkedin.com/in/andresvelasquezb" target="_blank">LinkedIn</a> • 
<a href="https://andresvelasquez.dev" target="_blank">Portafolio</a> • 
<a href="mailto:andres.velasquez@powerapps.com">Correo</a></p>

<hr>

<h2 id="licencia">🪪 Licencia</h2>
<p><strong>MIT</strong> — libre para usar, modificar y compartir.<br>
Por favor menciona el proyecto si te fue útil. 😊</p>
