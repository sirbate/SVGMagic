<!-- README.html -->

<h1>🔔 PowerApps Toast Notification Component</h1>

<blockquote>
  Una alternativa visual y personalizable a las notificaciones por defecto de Power Apps.<br>
  Este componente permite mostrar mensajes tipo <strong>toast</strong> con estilo, color y comportamiento definidos por el usuario.
</blockquote>

<hr>

<h2>⚙️ Funcionalidades</h2>
<ul>
  <li>✅ <strong>Notificaciones tipo toast</strong> modernas y elegantes</li>
  <li>✅ Personalización de:
    <ul>
      <li>Título del mensaje</li>
      <li>Cuerpo del mensaje</li>
      <li>Duración en pantalla (en segundos)</li>
      <li>Tipo de notificación:
        <ul>
          <li><code>Success</code> ✅</li>
          <li><code>Error</code> ❌</li>
          <li><code>Info</code> ℹ️</li>
          <li><code>Warning</code> ⚠️</li>
        </ul>
      </li>
    </ul>
  </li>
  <li>✅ Cada tipo tiene un color visual distintivo</li>
  <li>✅ Animación de entrada y salida</li>
  <li>✅ Fácil de reutilizar en cualquier app Power Apps</li>
</ul>

<hr>

<h2>📸 Capturas de Pantalla</h2>

<table>
  <tr>
    <td><strong>Ejemplo - Toast tipo <code>Success</code></strong></td>
  </tr>
  <tr>
    <td><img src="./screenshots/toast-success.png" alt="Toast Success" width="500px"></td>
  </tr>
</table>

<p>✅ <strong>Correcto</strong><br>
<em>Guardado con éxito.</em></p>

<p>Este mismo estilo se adapta automáticamente al tipo:</p>
<ul>
  <li><strong>Error</strong> (rojo ❌)</li>
  <li><strong>Warning</strong> (naranja ⚠️)</li>
  <li><strong>Info</strong> (azul ℹ️)</li>
</ul>

<hr>

<h2>🚀 Instalación</h2>

<h3>📁 Opción 1: Importar desde archivo</h3>
<ol>
  <li>Descarga el archivo <code>.msapp</code> o <code>.mscx</code> desde la carpeta <code>/component/</code>.</li>
  <li>En Power Apps Studio, entra al editor de tu app.</li>
  <li>Ve a <strong>Componentes &gt; + Nuevo componente &gt; Importar componente</strong>.</li>
  <li>Selecciona el archivo descargado y úsalo en tus pantallas.</li>
</ol>

<h3>📄 Opción 2: Definir vía YAML (para documentación/configuración externa)</h3>

<p>Si estás documentando o automatizando este componente vía YAML (por ejemplo, en Docusaurus o GitHub Pages), puedes usar un bloque así para mostrar ejemplos:</p>

<pre><code>toast_component:
ComponentDefinitions:
  Bate_Toast:
    DefinitionType: CanvasComponent
    CustomProperties:
      ToastDuration:
        PropertyKind: Input
        DisplayName: ToastDuration
        Description: Duración del toast en milisegundos
        DataType: Number
        Default: =2000
      ToastMessage:
        PropertyKind: Input
        DisplayName: ToastMessage
        Description: Mensaje del toast
        DataType: Text
        Default: ="Your notification message"
      ToastTitle:
        PropertyKind: Input
        DisplayName: ToastTitle
        Description: Título del toast
        DataType: Text
        Default: ="Text"
      ToastType:
        PropertyKind: Input
        DisplayName: ToastType
        Description: Tipo de toast ("Success", "Error", "Warning", "Info")
        DataType: Text
        Default: =Bate_Toast.ToastTypes.Error
      ToastTypes:
        PropertyKind: Output
        DisplayName: ToastTypes
        Description: Tipos de Toast
        DataType: Record
      ToastVisible:
        PropertyKind: Output
        DisplayName: ToastVisible
        Description: Visible Toast
        DataType: Boolean
    Properties:
      Height: =80
      OnReset: |-
        =Set(
            IsVisible,
            Not(IsVisible)
        );
        If(
            Not(IsVisible),
            Reset(tim_AutoCloseToast)
        )
      ToastTypes: |-
        ={
            Success: "Success",
            Warning: "Warning",
            Error: "Error",
            Info: "Info"
        }
      ToastVisible: =IsVisible
      Width: =350
    Children:
      - tim_AutoCloseToast:
          Control: Timer@2.1.0
          Properties:
            BorderColor: =ColorFade(Self.Fill, -15%)
            Color: =RGBA(255, 255, 255, 1)
            DisabledBorderColor: =ColorFade(Self.BorderColor, 70%)
            DisabledColor: =ColorFade(Self.Fill, 90%)
            DisabledFill: =ColorFade(Self.Fill, 70%)
            Duration: =Bate_Toast.ToastDuration
            Fill: =RGBA(56, 96, 178, 1)
            Font: =Font.'Open Sans'
            Height: =32
            HoverBorderColor: =ColorFade(Self.BorderColor, 20%)
            HoverColor: =RGBA(255, 255, 255, 1)
            HoverFill: =ColorFade(RGBA(56, 96, 178, 1), -20%)
            OnTimerEnd: |+
              =Set(
                  IsVisible,
                  false
              );
            PressedBorderColor: =Self.Fill
            PressedColor: =Self.Fill
            PressedFill: =Self.Color
            Reset: =true
            Start: =IsVisible
            Visible: =false
            X: =60
            Y: =60
      - cnt_ToastRoot:
          Control: GroupContainer@1.3.0
          Variant: AutoLayout
          Properties:
            BorderColor: =btn_Color.Fill
            BorderThickness: =0.5
            DropShadow: =DropShadow.Semilight
            Fill: =RGBA(255, 255, 255, 1)
            Height: =Parent.Height-4
            LayoutAlignItems: =LayoutAlignItems.Center
            LayoutDirection: =LayoutDirection.Horizontal
            LayoutJustifyContent: =LayoutJustifyContent.SpaceBetween
            RadiusBottomLeft: =10
            RadiusBottomRight: =10
            RadiusTopLeft: =10
            RadiusTopRight: =10
            Width: |+
              =Parent.Width-4
            X: =2
            Y: =2
          Children:
            - btn_Color:
                Control: Classic/Button@2.2.0
                Properties:
                  AlignInContainer: =AlignInContainer.Center
                  BorderColor: =ColorFade(Self.Fill, -15%)
                  BorderThickness: =0
                  Color: =RGBA(0, 0, 0, 0)
                  DisabledBorderColor: =RGBA(0, 0, 0, 0)
                  DisabledColor: =RGBA(0, 0, 0, 0)
                  DisabledFill: =RGBA(0, 0, 0, 0)
                  DisplayMode: =DisplayMode.View
                  Fill: |+
                    =Switch(
                        Bate_Toast.ToastType,
                        "Success", ColorValue("#28a745"),
                        "Error", ColorValue("#dc3545"),
                        "Warning", ColorValue("#ffc107"),
                        "Info", ColorValue("#007bff")
                    )
                  Font: =Font.'Open Sans'
                  Height: =Parent.Height
                  HoverBorderColor: =
                  HoverColor: =RGBA(0, 0, 0, 0)
                  HoverFill: =
                  OnSelect: =
                  PaddingBottom: =0
                  PaddingLeft: =0
                  PaddingRight: =0
                  PaddingTop: =0
                  PressedBorderColor: =
                  PressedColor: =
                  PressedFill: =
                  RadiusBottomLeft: =0
                  RadiusBottomRight: =0
                  RadiusTopLeft: =0
                  RadiusTopRight: =0
                  Text: =
                  Width: =20
            - cnt_ToastIcon:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  AlignInContainer: =AlignInContainer.SetByContainer
                  DropShadow: =DropShadow.None
                  FillPortions: =0
                  Height: =Parent.Height
                  LayoutAlignItems: =LayoutAlignItems.Center
                  LayoutDirection: =LayoutDirection.Vertical
                  LayoutJustifyContent: =LayoutJustifyContent.Center
                  Width: =40
                  X: =40
                  Y: =40
                Children:
                  - img_ToastTypeIcon:
                      Control: Image@2.2.3
                      Properties:
                        BorderColor: =RGBA(0, 18, 107, 1)
                        Height: =40
                        Image: |+
                          =Switch(
                              Bate_Toast.ToastType,
                              "Success", "data:image/svg+xml;utf8," & EncodeUrl("<svg xmlns='http://www.w3.org/2000/svg' width='16' height='16' fill='#28a745' class='bi bi-check-circle-fill' viewBox='0 0 16 16'><path d='M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0m-3.97-3.03a.75.75 0 0 0-1.08.022L7.477 9.417 5.384 7.323a.75.75 0 0 0-1.06 1.06L6.97 11.03a.75.75 0 0 0 1.079-.02l3.992-4.99a.75.75 0 0 0-.01-1.05z'/></svg>"),
                              "Error", "data:image/svg+xml;utf8," & EncodeUrl("<svg xmlns='http://www.w3.org/2000/svg' width='16' height='16' fill='#dc3545' class='bi bi-x-circle-fill' viewBox='0 0 16 16'><path d='M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0M5.354 4.646a.5.5 0 1 0-.708.708L7.293 8l-2.647 2.646a.5.5 0 0 0 .708.708L8 8.707l2.646 2.647a.5.5 0 0 0 .708-.708L8.707 8l2.647-2.646a.5.5 0 0 0-.708-.708L8 7.293z'/></svg>"),
                              "Warning", "data:image/svg+xml;utf8," & EncodeUrl("<svg xmlns='http://www.w3.org/2000/svg' width='16' height='16' fill='#ffc107' class='bi bi-exclamation-circle-fill' viewBox='0 0 16 16'><path d='M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0M8 4a.905.905 0 0 0-.9.995l.35 3.507a.552.552 0 0 0 1.1 0l.35-3.507A.905.905 0 0 0 8 4m.002 6a1 1 0 1 0 0 2 1 1 0 0 0 0-2'/></svg>"),
                              "Info", "data:image/svg+xml;utf8," & EncodeUrl("<svg xmlns='http://www.w3.org/2000/svg' width='16' height='16' fill='#007bff' class='bi bi-info-circle-fill' viewBox='0 0 16 16'><path d='M8 16A8 8 0 1 0 8 0a8 8 0 0 0 0 16m.93-9.412-1 4.705c-.07.34.029.533.304.533.194 0 .487-.07.686-.246l-.088.416c-.287.346-.92.598-1.465.598-.703 0-1.002-.422-.808-1.319l.738-3.468c.064-.293.006-.399-.287-.47l-.451-.081.082-.381 2.29-.287zM8 5.5a1 1 0 1 1 0-2 1 1 0 0 1 0 2'/></svg>")
                          )
                        Width: =40
                        X: =10
                        Y: =13
            - cnt_ToastText:
                Control: GroupContainer@1.3.0
                Variant: AutoLayout
                Properties:
                  AlignInContainer: =AlignInContainer.SetByContainer
                  DropShadow: =DropShadow.None
                  FillPortions: =0
                  Height: =Parent.Height
                  LayoutAlignItems: =LayoutAlignItems.Stretch
                  LayoutDirection: =LayoutDirection.Vertical
                  LayoutJustifyContent: =LayoutJustifyContent.Center
                  LayoutMinHeight: =Parent.Height
                  Width: =200
                Children:
                  - lbl_ToastTitle:
                      Control: Text@0.0.50
                      Properties:
                        Align: ='TextCanvas.Align'.Start
                        AlignInContainer: =AlignInContainer.Start
                        Font: =Font.'Segoe UI'
                        FontColor: =RGBA(0, 0, 0, 1)
                        Height: |+
                          =Parent.Height/2
                        LayoutMinWidth: =Parent.Width
                        PaddingLeft: =0
                        Size: =20
                        Text: =Bate_Toast.ToastTitle
                        VerticalAlign: =VerticalAlign.Bottom
                        Weight: ='TextCanvas.Weight'.Bold
                        Width: =Parent.Width
                        X: =1
                        Y: =9
                  - lbl_ToastMessage:
                      Control: Text@0.0.50
                      Properties:
                        Align: ='TextCanvas.Align'.Start
                        AlignInContainer: =AlignInContainer.Center
                        Font: =Font.'Segoe UI'
                        FontColor: =RGBA(0, 0, 0, 1)
                        Height: =Parent.Height/2
                        PaddingLeft: =0
                        Text: =Bate_Toast.ToastMessage
                        VerticalAlign: =VerticalAlign.Top
                        Weight: ='TextCanvas.Weight'.Medium
                        Width: =Parent.Width
                        X: =1055
                        Y: =25
            - cnt_ToastAction:
                Control: GroupContainer@1.3.0
                Variant: ManualLayout
                Properties:
                  DropShadow: =DropShadow.None
                  FillPortions: =0
                  LayoutMinHeight: =Parent.Height
                  Width: =40
                Children:
                  - ico_CloseToast:
                      Control: Classic/Icon@2.5.0
                      Properties:
                        BorderColor: =RGBA(0, 18, 107, 1)
                        Color: =RGBA(101, 101, 101, 1)
                        Height: =20
                        Icon: =Icon.Cancel
                        OnSelect: '=Set(IsVisible, false); '
                        Width: =20
                        X: =7
                        Y: =8

</code></pre>


<hr>

<h2>📦 Ejemplo de uso del componente</h2>

<pre><code>Toast.ShowToast("Guardado correctamente", "Success", "Éxito", 3)</code></pre>

<p><strong>Parámetros:</strong></p>
<pre><code>Mensaje, Tipo, Título, Duración (segundos)</code></pre>

<hr>

<h2>🧠 Notas Técnicas</h2>
<ul>
  <li>El componente usa una colección interna para controlar el estado de visibilidad.</li>
  <li>Animaciones creadas con <code>Transition</code> y <code>Visible</code>.</li>
  <li>Colores definidos en variables globales:
    <ul>
      <li><code>varToastSuccessColor</code></li>
      <li><code>varToastErrorColor</code></li>
      <li><code>varToastInfoColor</code></li>
      <li><code>varToastWarningColor</code></li>
    </ul>
  </li>
  <li>Reutilizable en múltiples pantallas sin duplicar lógica.</li>
</ul>

<hr>

<h2>👨‍💻 Autor</h2>
<p><strong>Tu Nombre</strong><br>
<a href="https://linkedin.com/in/tuusuario" target="_blank">LinkedIn</a> • 
<a href="https://tusitio.com" target="_blank">Portafolio</a> • 
<a href="mailto:tucorreo@dominio.com">tucorreo@dominio.com</a></p>

<hr>

<h2>🪪 Licencia</h2>
<p><strong>MIT</strong> — puedes usar, modificar y compartir libremente este componente.<br>
¡Dame crédito si te sirvió! 😊</p>
