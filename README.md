# Planificador Didáctico

Aplicación web para guardar y clasificar sesiones de clase.

## Objetivos del Proyecto
- Facilitar la planificación de sesiones mediante formularios guiados.
- Centralizar la información en una hoja de cálculo de Google mediante un script de Google Apps Script.
- Permitir editar, duplicar, eliminar y buscar sesiones almacenadas.

## Arquitectura
La aplicación se compone de:

- **Front-end:** un solo archivo [`index.html`](index.html) con HTML, JavaScript y estilos. Se ejecuta en el navegador y gestiona la interfaz, almacenamiento temporal en `localStorage` y la comunicación con el backend.
- **Backend:** un script de Google Apps Script que expone un endpoint web para crear, listar, actualizar y eliminar sesiones. Este script suele conectarse a una hoja de cálculo de Google para almacenar la información.

## Configuración de `SCRIPT_URL`
1. Crear o copiar el script de Google Apps Script que provee las operaciones de almacenamiento.
2. En el editor de Apps Script, desplegar el proyecto como **Web App** (`Deploy > New deployment`) y copiar la URL generada.
3. Abrir [`index.html`](index.html) y buscar la constante `SCRIPT_URL` dentro del objeto `config`.
4. Reemplazar el valor existente con la URL copiada. Ejemplo:
   ```javascript
   SCRIPT_URL: "https://script.google.com/macros/s/XXXX/exec",
   ```

## Ejecutar la aplicación localmente
1. Clonar este repositorio.
2. Configurar `SCRIPT_URL` como se describe arriba.
3. Abrir `index.html` en un navegador moderno (doble clic o sirviendo el directorio con un servidor estático).
4. Crear, editar o imprimir sesiones según sea necesario.

## Dependencias externas
- [Tailwind CSS](https://tailwindcss.com) para los estilos, cargado desde CDN.
- [SunEditor](https://github.com/JiHong88/SunEditor) como editor WYSIWYG, también desde CDN.

## Limitaciones y posibles mejoras
- Requiere conexión a Internet para cargar los recursos de CDN y comunicarse con Google Apps Script.
- El backend expuesto como Web App no implementa autenticación; para uso compartido podrían considerarse controles de acceso.
- Futuras mejoras podrían incluir empaquetar la aplicación como PWA, soporte offline y validaciones adicionales.

## Pruebas manuales
1. Abrir `index.html` en un navegador.
2. Ingresar en "Sesión de Aprendizaje" el texto `<script>alert('xss')</script>` y guardar la sesión.
3. Verificar que al mostrar o imprimir la sesión no se ejecuta ninguna alerta y la etiqueta `<script>` no aparece.
4. Repetir la prueba con contenido como `<img src=x onerror=alert('xss')>` y comprobar que el atributo peligroso se elimina.

