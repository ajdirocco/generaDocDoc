# Genera Form - Utilidades
## Snippets, data-* attributes y classes.
<p>Encuentre aquí todos los elementos con los que puede marcar el HTML.</p>

## Snippets
<p>Escriba con Markdown y algunos snippets.</p>
Los snippets son fragmentos de texto que representan de forma simplicada un bloque HTML o Markdown a generar.
La regla es sencialla, escriba "s." y seguido el nombre del snippet.

#### InputBox
"s.inputbox" más texto opcional entre corchetes. El texto se mostrará a la izquierda del input.
<pre>s.inputbox[]</pre>
<pre>s.inputbox[Ingrese un texto:]</pre>

#### TextArea
"s.textarea" más texto opcional entre corchetes. El texto se mostrará a la izquierda del input.
<pre>s.textarea[]</pre>
<pre>s.textarea[Ingrese un texto:]</pre>

#### Select
"s.select" más una lista de texto separada por comas y entre corchetes. La primer coma representa el titulo.
<pre>.select[title,option-1,option-n]</pre>
Ejemplo:
<pre>s.select[Saludos,,Hola,Como va, Que tal]</pre>

#### CheckBox
"s.checkbox" más texto opcional entre corchetes. El texto se mostrará a la izquierda del input. Puede generar más de un checkbox si los separa entre comas.
<pre>.checkbox[option-1,option-n]</pre>
Ejemplos
<pre>s.checkbox[]</pre>
<pre>s.checkbox[Ok entendido]</pre>
<pre>s.checkbox[Manzana, Naranja, Frutilla]</pre>

#### RadioBox
"s.radiobox" más una lista de texto separada por comas y entre corchetes. La primer coma representa el name (evita la multiselección de los radio buttons).
<pre>s.radiobox[name_radio,option-1,option-n]</pre>

#### Link
"s.a" más la URL y el nombre a mostrar, todo entre corchetes. El link se abrirá en la misma ventana.
<pre>s.a[https://google.com Google]</pre>

#### LinkBlank
"s.a.b" más la URL y el nombre a mostrar, todo entre corchetes. El link se abrirá en un nuevo tab del navegador.
<pre>.a.b[https://google.com Google (new Tab)]</pre>

#### Section
"s.section" para navegar dentro del documento.
<pre>.section[section_name,sectionLabel]</pre>

#### Table - Markdown
"s.table.m" genera un snippet de table Markdown de dos columnas y dos filas.
<pre>s.table.m</pre>

#### Table - HTML
"s.table.h" genera un snippet de table HTML de tres columnas y dos filas.
<pre>s.table.h</pre>

#### Center
"s.center" más el elemento HTML a centrar con su texto, seprado entre comas y todo entre corchetes. Se puede usar un Heading (h1 a h6) o Paragraphs (p).
<pre>.center[tag, text]</pre>
Ejemplos
<pre>s.center[h1, Hola mundo]</pre>
<pre>s.center[h2, Hola mundo]</pre>
<pre>s.center[h3, Hola mundo]</pre>
<pre>s.center[h4, Hola mundo]</pre>
<pre>s.center[h5, Hola mundo]</pre>
<pre>s.center[h6, Hola mundo]</pre>
<pre>s.center[p, Hola mundo]</pre>
**Nota:** este snippet agrega formato al texto para reducir el espacio entre lineas con el siguiente style:
 <pre>style="margin-top:10px;margin-bottom:0px;"</pre>

#### Comment
"s.comment" agrega un comentario dentro del documento fuente.
<pre>s.comment</pre>

#### Form
"s.form" genera un HTML form mas un boton que imprime todos los elementos mas sus valores que incluya dentro del form.
<pre>s.form</pre>

#### Button
"s.button" genera un HTML button.
<pre>s.button</pre>

#### Date
"s.button" genera un HTML date picker.
<pre>s.date</pre>

#### Time
"s.button" genera un HTML time picker.
<pre>s.time</pre>

#### Color
"s.color" genera un HTML color picker.
<pre>s.color</pre>

## HTML data-*
<p>Con los siguientes tags y class puede marcar el HTML y generar la funcionalidad de agregar o eliminar elementos y tambien puede persistir sus valores</p>

### Clases
Con el class <b>gxTrigger</b> puede marcar un elemento HTML para que ejecute el agregado o eliminación de un elemento referenciado con el atributo con data-gx-target.

### Atributos de manipulación
<p>Permiten clonar o eliminar elementos HTML directamente del DOM.</p>

#### data-gx-target
Indica el id del elemento al que se le aplicará el data-gx-type, pudiendo ser asi clonado o eliminado.

#### data-gx-type
Indica el tipo de manipulación sobre los elementos HML:
 1. <b>clone</b>:
    Duplica el elemento, junto con su valor (propiedad value), referenciado con data-gx-target.
 2. <b>clone-clean</b>:
    La misma funcionalidad de clone pero limpia todos los imputs (deja vacia su propiedad value).
 3. <b>remove</b>:
    Permite eliminar el elemento referenciado en data-gx-target.

#### data-gx-insert
Indica donde se quiere insertar un elemento clonado
 1. <b>before</b>:
    se inserta antes del elemento referenciado en data-gx-target.
 2. <b>after</b>:
    se inserta despues del elemento referenciado en data-gx-target.
 3. <b>child</b>:
    se inserta luego del último elemento hijo del elemento padre referenciado en data-gx-target. Es el valor por defecto si no se especifica el atributo data-gx-insert.

### Atributos de persistencia
Permiten guardar los valores de los elementos HTML. Dicha persistencia se realiza utlizando como repositorio [GitHub Gist](https://gist.github.com/).

#### data-gx-gist
Atributo necesario para persistir los datos del form en [GitHub Gist](https://gist.github.com/) (Ver detalle: [Persistencia - GitHub Gist](#GitHub Gist). Representa el nombre del gist. Se debe referenciar dentro del HTML tag form.

#### data-gx-gist-file
Atributo para persistir los datos del form en [GitHub Gist](https://gist.github.com/). Representa el nombre de un file dentro de un gist. Se debe referenciar dentro del HTML tag fieldset del form. Se puede especificar un file distinto para cada fieldset, si no se especifica ninguno se crea un file por defecto que contiene todos los campos del form exista o no un HTML tag fieldset.

## Persistencia
### Local
<p>Por defecto se persiste todo el HTML y el valor de los HTML inputs que se encuentren dentro de un HTML form y que posean el atributo name en el localStorage de cada dispositivo.</p>

### GitHub Gist
Se persiste en [GitHub Gist](https://gist.github.com/) el valor de los HTML inputs que posean el atributo name y que se encuentren dentro de un elemento HTML marcado con el data attribute [data-gx-gist](#data-gx-gist). Los elementos hijos pueden o no estar agrupados (por ejemplo un div), pero si lo estan se puede utilizar el atributo [data-gx-gist-file](#data-gx-gist-file) para especificar, si se desea, un gist file por cada grupo, si no se especifica ninguno se grabaran todos los inputs en un solo file.

<p><b>NOTA:</b> La persistencia se produce en el boton "Guardar" tanto de generaForm como de generaCRUD. se guarda tanto el valor de cada input como asi tambien todo el HTML generado.</p>

#### Ejemplos de manipulación + persistencia en [GitHub Gist](https://gist.github.com/)

<p><b>Un gist y un file</b></p>

<p>El siguiente es un ejemplo de persistencia de los valores de los inputs de un form en GitHub Gist. Lo persiste todo en un solo gist file por defecto. Combinando los siguientes snippets, class y attribute se obtiene un form que junto a sus datos se periste en Gist:</p>

<p>s.form + s.button + gxTrigger + data-gx-type + data-gx-target + data-gx-gist</p>

```
<center><h1 style="margin-top:10px;margin-bottom:20px;">Form CRUD</h1></center>  
<form data-gx-gist="GIST-NAME">
<fieldset id="fieldset">
<label for="inputbox">Hola:&nbsp;</label><input type="text" id="inputbox" name="inputbox" placeholder=" mundo..." style="border-radius:0.25rem;border-width:1px;border-color:black;margin-bottom:10px;width: 62%;">&nbsp;<button class="gxTrigger" data-gx-type="remove" data-gx-target="fieldset" type="button" style="border-radius:0.25rem;border-width:1px;border-color:black;padding-left:5px;padding-right:5px;" >Quitar</button><br></fieldset>
<button class="gxTrigger" data-gx-type="clone-clean" data-gx-target="fieldset"  data-gx-insert="after" type="button" style="border-radius:0.25rem;border-width:1px;border-color:black;padding-left:5px;padding-right:5px;float: right;" >Agregar</button>
</form>
```

<p>En el caso anterior el data-gx-gist esta a nivel del tag form y persisitirá cada input en el gist especificado, pero puede colocarlo donde desee. Por ejemplo podría tener dos divs o fieldsets y solo marcar uno solo, de esta manera solo se persistirá el grupo marcado. Vea el siguiente ejemplo:</p>

<p>s.form + s.button + gxTrigger + data-gx-type + data-gx-target + data-gx-gist + data-gx-file</p>

```
<center><h1 style="margin-top:10px;margin-bottom:20px;">Form CRUD</h1></center>  
<form data-gx-gist="GIST-NAME">
<fieldset><label for="inputbox">Hola:&nbsp;</label><input type="text" id="inputbox" name="inputbox" placeholder=" mundo..." style="border-radius:0.25rem;border-width:1px;border-color:black;margin-bottom:10px;width: 62%;">&nbsp;</fieldset>
<fieldset id="fieldset" data-gx-gist-file="GIST-FILE-NAME">
<label for="inputbox">Hola:&nbsp;</label><input type="text" id="inputbox" name="inputbox" placeholder=" mundo..." style="border-radius:0.25rem;border-width:1px;border-color:black;margin-bottom:10px;width: 62%;">&nbsp;<button class="gxTrigger" data-gx-type="remove" data-gx-target="fieldset" type="button" style="border-radius:0.25rem;border-width:1px;border-color:black;padding-left:5px;padding-right:5px;" >Quitar</button><br></fieldset>
<button class="gxTrigger" data-gx-type="clone-clean" data-gx-target="fieldset"  data-gx-insert="after" type="button" style="border-radius:0.25rem;border-width:1px;border-color:black;padding-left:5px;padding-right:5px;float: right;" >Agregar</button>
</form>
```
<p>En el ejemplo anterior se puede ver que se duplica y persiste solo los datos del segundo fieldset.</p>

<p>En el siguiente ejemplo se puede ver como insertar una nueva fila en un table y se persiste todo el contenido en un gist:</p>

<p>s.form + s.table.h + gxTrigger + data-gx-type + data-gx-target + data-gx-gist</p>

```
<form data-gx-gist="GIST-NAME">
<table>
<tbody>
  <tr>
    <th>Columna 1</th>
    <th>Columna 2</th>
    <th>Columna 3</th>
  </tr>
  <tr id="fieldset">
    <td>hola</td>
    <td>mundo</td>
    <td>como va</td>
  </tr>
</tbody>
</table>
<button class="gxTrigger" data-gx-target="fieldset" data-gx-type="clone-clean" data-gx-insert="after" type="button" style="border-radius:0.25rem;border-width:1px;border-color:black;padding-left:5px;padding-right:5px;float: right;">Agregar</button>
</form>
```

<p><b>Nota:</b> recuerde que si no se especifica ningún gist la persistencia por defecto es local (en el localstorge del dispositivo).</p>

<p><b>Un gist y dos files</b></p>
<p>El siguiente es un ejemplo de persistencia de los valores de los inputs de un form en GitHub Gist. Lo persiste todo en un solo gist pero un file por cada grupo de inputs marcados.</p>

<p>s.form + s.button + gxTrigger + data-gx-type + data-gx-target + data-gx-gist + data-gx-file</p>

```
<center><h1 style="margin-top:10px;margin-bottom:20px;">Form CRUD</h1></center>  
<form data-gx-gist="GIST-NAME">
<fieldset data-gx-gist-file="GIST-FILE-NAME-1"><label for="inputbox">Hola:&nbsp;</label><input type="text" id="inputbox" name="inputbox" placeholder=" mundo..." style="border-radius:0.25rem;border-width:1px;border-color:black;margin-bottom:10px;width: 62%;">&nbsp;</fieldset>
<fieldset id="fieldset" data-gx-gist-file="GIST-FILE-NAME-2">
<label for="inputbox">Hola:&nbsp;</label><input type="text" id="inputbox" name="inputbox" placeholder=" mundo..." style="border-radius:0.25rem;border-width:1px;border-color:black;margin-bottom:10px;width: 62%;">&nbsp;<button class="gxTrigger" data-gx-type="remove" data-gx-target="fieldset" type="button" style="border-radius:0.25rem;border-width:1px;border-color:black;padding-left:5px;padding-right:5px;" >Quitar</button><br></fieldset>
<button class="gxTrigger" data-gx-type="clone-clean" data-gx-target="fieldset"  data-gx-insert="after" type="button" style="border-radius:0.25rem;border-width:1px;border-color:black;padding-left:5px;padding-right:5px;float: right;" >Agregar</button>
</form>
```
<p>En el ejemplo anterior se puede ver que se duplica solo el segundo fieldset y se persisten ambos, cada fieldset en un file específico.</p>

## Librerias externas
<p>generaForms y generaCRUD por defecto soportan Alpinejs y Tailwindcss.</p>

```
<h1 x-data="{ message: 'I ❤️ Alpine' }" x-text="message" style="text-align: center;"></h1>
<a href="" class="block overflow-hidden rounded-2xl" >
  <img style="margin-bottom: 0px;margin-top: 0px;"class="object-cover w-full h-56" src="https://images.unsplash.com/photo-1524758631624-e2822e304c36?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80" alt="" />
 <div class="p-4 bg-gray-900">
 <p class="text-xs text-gray-500">website.com</p>
<h5 class="text-sm text-white">How to position your furniture for positivity</h5>
<p class="mt-1 text-xs text-gray-500">Lorem ipsum dolor sit amet consectetur, adipisicing elit. Rerum nobis aliquid accusamus? Sint, sequi voluptas.</p>
 </div>
</a>
```
## Form css
<p>generaForms y generaCRUD poseen su propio css (static/form.css) con las siguientes clases:</p>

#### ga-disabled
esta clase desabilita todo el conjunto de elementos contenidos dentro de otro elemento HTML.
```
<form class="ga-disabled" action="/action_page.php">
  <label for="fname">First name:</label>
  <input type="text" id="fname" name="fname"><br><br>
  <label for="lname">Last name:</label>
  <input type="text" id="lname" name="lname"><br><br>
  <input type="submit" value="Submit">
</form>
```
