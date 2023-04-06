---
sidebar_position: 1
---

# Doc Intro
<p><b>Nota:</b> Documentación en construcción.</p>

Genera Form utiliza algunos data-* attribute propios para permitir que un HTML Form tenga funcionalidad básica de crud y persistencia:
```jsx title="Form con persitencia en Git Hub Gist y agregado/eliminación de filas"
<form data-gx-gist>
  <fieldset id="fieldset">
    <input type="text" id="inputbox" name="inputbox" placeholder="Hola mundo..." ">
    <button
      class="gxTrigger"
      data-gx-type="remove" 
      data-gx-target="fieldset" 
    >Quitar</button>
  </fieldset>
  <button 
    class="gxTrigger" 
    data-gx-type="clone-clean" 
    data-gx-target="fieldset" 
    data-gx-insert="after"
  >Agregar</button>
</form>
```


## Comencemos

Ingrese a **[generaForm](https://generaform.netlify.app/)**.

## Genere un nuevo formulario

Ingrese al menu **Form**, haremos un ejemplo completo de agregado de filas en un table.

Reemplace el ejemplo que viene por defecto con el siguiente codigo:

```
<form>
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
<p><b>Nota:</b> recuerde que si no se especifica ningún Gist la persistencia por defecto es local (en el localstorge del dispositivo).</p>

