# planificador_didactico
programa para guardar y clasificar sesiones de clase

## Pruebas manuales

1. Abrir `index.html` en un navegador.
2. Ingresar en "Sesión de Aprendizaje" el texto `<script>alert('xss')</script>` y guardar la sesión.
3. Verificar que al mostrar o imprimir la sesión no se ejecuta ninguna alerta y la etiqueta `<script>` no aparece.
4. Repetir la prueba con contenido como `<img src=x onerror=alert('xss')>` y comprobar que el atributo peligroso se elimina.
