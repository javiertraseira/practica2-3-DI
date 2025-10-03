# Práctica 2.3 – Elemento combobox

El objetivo es aprender a manipular modelos de datos en un combobox, controlar duplicados y personalizar la interfaz gráfica aplicando un Look and Feel moderno mediante una librería externa.
Utiliza *branches* para delimitar los cambios que vayas haciendo.

## Parte 1

- Crea un nuevo proyecto de tipo **Maven**
- Crea una ventana que permita agregar elementos al listado de un *combobox* al darle al botón añadir.
- La interfaz debe **evitar duplicados**: no se podrán introducir elementos repetidos en el combobox.

![](media/9d5dec85d5a68aeb8e5ba53d5fd897f7.png)


## Parte 2

Mejora el ejercicio anterior:

- Agrega un botón Agregar todo que incluya de golpe todos los módulos del curso en el combobox.
- Agrega un botón Borrar todo que vacíe el combobox.
- Cambiar el **Look and Feel** de la ventana por defecto para que utilice **flatLaf**, una librería moderna actual que permite dar un aspecto profesional y moderno a las interfaces Swing:
    - Para ello deberás añadir a tu fichero `pom.xml` las líneas necesarias para agregar dependencias buscando en el [respositorio oficial de Maven](https://mvnrepository.com/) la última versión de flaLaf (Flat Look and Feel)
    - Después deberás de agregar el import a tu código y utilizarlo en el *main* de tu programa, editando el código ya propuesto de la línea *Look and feel setting code (optional)* para usar flatLaf.
 


## Parte 3

En esta parte vamos a **mejorar la interactividad y la personalización** de la aplicación agregando nuevas funcionalidades:

1. **Selección de Look and Feel**
    - Crea un nuevo combobox que permita elegir entre tres estilos visuales para la aplicación:
        - Clásico (Look and Feel por defecto de Swing, Nimbus o el del sistema operativo).
        - FlatLaf Light (tema claro moderno).
        - FlatLaf Dark (tema oscuro moderno).
2. **Gestión de cursos y módulos**
    - Añade otro combobox para seleccionar el curso: Primero o Segundo.
    - Comportamiento esperado:
        - Cuando se agregue un módulo de forma manual, el nombre debe incluir al principio 1º o 2º según el curso seleccionado.
        - El botón Agregar todos debe cargar únicamente los módulos correspondientes al curso elegido.
3. **Eliminación de elementos individuales**
    - Agrega un botón que permita borrar únicamente el módulo seleccionado del combobox de módulos.
    - Este botón debe mostrar un icono de papelera en lugar de texto para representar de manera visual la acción de eliminar.

![](media/9d5dec85d5a68aeb8e5ba53d5234234.png)


## Pruebas (testing) 

### Tabla pruebas parte 1 y 2

| ID Caso Prueba | Descripción Caso de Prueba         | Entrada                   | Salida Esperada                                                     | Resultado   |
|----------------|-----------------------------------|---------------------------|---------------------------------------------------------------------|-------------|
| 01             | Comprobación del botón "agregar"   | Texto del campo módulo    | Se agrega el texto del módulo al combobox.                           | OK/No cumple|
| 02             | Validación de duplicados           | Texto del campo módulo    | No permite agregar un campo duplicado y avisa con un mensaje modal.  | OK/No cumple|
| 03             | Botón "agregar todo"               | N/D                       | Agrega todos los módulos del curso al combobox.                       | OK/No cumple|
| 04             | Botón "borrar todo"                | N/D                       | Borra todo el contenido del combobox.                                 | OK/No cumple|
| 05             | Look and feel de la aplicación     | N/D                       | Se ha modificado el look and feel por defecto.                        | OK/No cumple|


### Tabla pruebas parte 3

| ID Caso Prueba | Descripción Caso de Prueba      | Entrada                  | Salida Esperada                                          | Resultado   |
|----------------|--------------------------------|--------------------------|----------------------------------------------------------|-------------|
| 01             | Selección combobox curso        | Seleccionar curso combobox| Agrega el curso 1º/2º al inicio del texto en el combobox principal | OK/No cumple|
| 02             | Botón "agregar todo"            | Seleccionar curso combobox| Agrega todos los módulos del curso seleccionado en el combobox | OK/No cumple|
| 03             | Botón "borrar"                  | Seleccionar curso combobox| Borra el curso del combobox que esté seleccionado         | OK/No cumple|
 
