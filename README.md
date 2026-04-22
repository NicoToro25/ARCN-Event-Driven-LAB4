# ARCN-Event-Driven-LAB4

---

## Bitacora de conflictos

1. Se tuvo problemas con el devcontainer.json, especificamente con la imagen ya que chocaba con la Feature en el JSON, chocaban las versiones ya bloqueadas en la imagen de Java. Al no poder crear el entorno que se pidió, se "asigna una máquina de emergencia" que es el **Recovery Mode**, esta máquina de emergencia no tiene herramienras ni permisos de escritura, por lo que fallaba, en pocas palabras, todo.

Se solucionó usando una nueva imagen que viene con docker ya instalado y no la sugerida por el laboratorio, con el propósito de evitar más errores.


