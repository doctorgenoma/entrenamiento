# App de Entrenamiento Personal — Guía de publicación

## Archivos incluidos

| Archivo | Descripción |
|---|---|
| `index.html` | La app completa (autocontenida) |
| `manifest.json` | Permite instalarla como app en el móvil |
| `README.md` | Esta guía |

---

## 1. Publicar en GitHub Pages (gratuito, enlace permanente)

### Paso a paso

1. **Crea una cuenta en GitHub** (si no tienes): https://github.com/signup

2. **Crea un repositorio nuevo**
   - Ve a https://github.com/new
   - Nombre: `entrenamiento` (o el que quieras)
   - Visibilidad: **Public**
   - Haz clic en "Create repository"

3. **Sube los archivos**
   - En la página del repositorio, haz clic en "uploading an existing file"
   - Arrastra los archivos `index.html` y `manifest.json`
   - Haz clic en "Commit changes"

4. **Activa GitHub Pages**
   - Ve a Settings → Pages (menú lateral izquierdo)
   - En "Source", selecciona: **Deploy from a branch**
   - Branch: **main** / carpeta: **/ (root)**
   - Haz clic en "Save"

5. **Espera 1-2 minutos** y tu app estará en:
   ```
   https://TU-USUARIO.github.io/entrenamiento/
   ```

6. **Comparte ese enlace con tus clientes** — pueden abrirlo desde el móvil y añadirlo a la pantalla de inicio como si fuera una app nativa.

---

## 2. Integrar en Google Sites

> Google Sites no permite incrustar HTML arbitrario directamente por seguridad.
> La solución es publicar primero en GitHub Pages y luego incrustar el enlace.

### Opción A — Incrustar como iframe en Google Sites (recomendada)

1. Publica la app en GitHub Pages siguiendo los pasos de arriba.

2. Abre tu Google Site: https://sites.google.com

3. En la página donde quieras la app, haz clic en **Insertar → Insertar URL**

4. Pega tu URL de GitHub Pages:
   ```
   https://TU-USUARIO.github.io/entrenamiento/
   ```

5. Google Sites mostrará una vista previa. Ajusta el tamaño del bloque a **grande** o **pantalla completa**.

6. Publica el site.

> **Resultado**: Los clientes abren tu Google Site y ven la app directamente incrustada, sin salir de la página.

### Opción B — Botón de enlace en Google Sites

Si el iframe no muestra la app correctamente:

1. En Google Site, inserta un **Botón** o un bloque de texto.
2. Añade el enlace de GitHub Pages.
3. Los clientes hacen clic y se abre la app en una pestaña nueva.

---

## 3. Cómo recibir los datos de los clientes

Los datos se guardan en el navegador de cada cliente (localStorage). Para centralizar los datos hay dos opciones:

### Opción sencilla — CSV manual
Cada cliente pulsa "Descargar mis datos (CSV)" y te envía el archivo por WhatsApp o email. Tú lo abres en Google Sheets.

### Opción automática — Google Apps Script
Si quieres que los datos lleguen directamente a una hoja de Google Sheets:

1. Crea una hoja de cálculo en Google Sheets.
2. Ve a Extensiones → Apps Script.
3. Crea una función `doPost` que reciba los datos y los añada como fila.
4. Despliega el script como "Aplicación web" (acceso: cualquiera).
5. Copia la URL del script y pégala en el archivo `index.html` donde pone `GOOGLE_SCRIPT_URL`.

---

## Personalización

Para cambiar el nombre de la app o los colores, edita estas líneas en `index.html`:

```html
<title>Mi entrenamiento</title>          <!-- nombre en la pestaña -->
--green: #1D9E75;                         /* color principal */
```

Para añadir o quitar ejercicios, edita el array `EXERCISES` en el `<script>` de `index.html`.
