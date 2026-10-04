# Práctica 2.3 – Elementos interfaz mixta

El objetivo de esta práctica es profundizar en el uso de componentes gráficos y en la gestión de eventos, creando una interfaz formada por dos zonas que deberán mantenerse sincronizadas.

Durante la práctica se trabajará con distintos tipos de controles, diferentes eventos y listeners, menús, validación en tiempo real y algunas propiedades específicas de FlatLaf.

## Preparación del proyecto

Crea dentro de la carpeta `SOL` de tu repositorio local un nuevo proyecto Maven de Apache NetBeans llamado:

`practica2-3`

Utiliza ramas para separar las distintas partes de la práctica.

Como mínimo deberán existir:

- `parte-1`
- `parte-2`
- `parte-3`
- `parte-4`

Cada parte deberá desarrollarse inicialmente en su rama correspondiente y posteriormente integrarse en `main`.

Realiza commits descriptivos durante el desarrollo.

La aplicación deberá utilizar **FlatLaf**, añadiendo la dependencia correspondiente al fichero `pom.xml`, tal y como se realizó en la práctica anterior.

> Recuerda que todos los componentes utilizados en la interfaz desde código deberán tener nombres descriptivos.


## Parte 1 Creación de componentes y sincronización mediante eventos

Crea mediante el editor visual de Netbeans una interfaz mixta utilizando *FlatLaf* con los elementos indicados y con ellos duplicados en espejo.

Los cambios en la primera parte de la interfaz, sea una imagen para la otra mitad de forma inmediata, excepto al primer campo de texto, que deberá mostrar el duplicado con el texto en *orden inverso*.

Se hará uso de los siguientes **controles clásicos** de una interfaz:

-   *2 Campos de texto (JTextField)*
-   *1 Campo de Password (JPasswordField)*
-   *3 Botones (JButtons)*
-   *3 Radio buttons (JRadiobutton)*
-   *3 Casillas verificación (JCheckbox)*
-   *1 Listado (JCombobox)*
-   *1 Barra deslizadora (JSlider)*
-   *1 JSpinner*

![](media/b659313c2f89bf08a4f35281a33b65c3.png)

Puedes utilizar `JPanel` para organizar los componentes.

### Sincronización de componentes

Los cambios realizados en la zona superior deberán reflejarse automáticamente en el componente equivalente de la zona inferior. 
Para ello habrá que hacer uso de los **eventos** relacionados con cada componente, para duplicarlos en su correspondiente elemento. 

Así, por ejemplo:

- al escribir en un campo de texto, el otro deberá actualizarse;
- al marcar un `JCheckBox`, el correspondiente deberá cambiar al mismo estado;
- al seleccionar una opción del `JComboBox`, el otro deberá seleccionar el mismo elemento;
- al mover el `JSlider`, deberá actualizarse el segundo;
- al modificar el `JSpinner`, deberá mostrarse el mismo valor en el otro.

### Campos de texto en tiempo real

La actualización de los JTextField deberá producirse mientras el usuario escribe, sin necesidad de pulsar Enter.


### Sincronización de componentes

El primero de los campos `JTextField` tendrá un comportamiento diferente.

El texto escrito en el campo izquierdo deberá mostrarse en el campo derecho en orden inverso.

### Uso de eventos

Durante esta parte deberás utilizar al menos **cuatro tipos diferentes de eventos o listeners**.

Por ejemplo:

| Componente | Evento o listener |
|---|---|
| `JButton` | `ActionListener` |
| `JCheckBox` | `ItemListener` |
| `JComboBox` | `ActionListener` |
| `JSlider` | `ChangeListener` |
| `JSpinner` | `ChangeListener` |
| `JTextField` | `DocumentListener` |

## Parte 2 Menú, barra de estado y validación en tiempo real

### Menú

Amplía la ventana añadiendo una barra de menús mediante `JMenuBar`.

Deberá contener como mínimo:

```text
Archivo
Edición
```

**Menú Archivo**

Añade al menos la opción:

```text
Salir
```

que deberá cerrar correctamente la aplicación.

**Menú Edición**

Añade la opción:

```text
Borrar todo
```

Al seleccionarla, todos los componentes deberán volver a su estado inicial.

Evita realizar todas estas operaciones directamente dentro del evento del menú.

### Barra de estado

Añade un `JPanel` en la parte inferior de la ventana que funcione como **barra de estado**.

Dentro puede incluirse un `JLabel`.

Por ejemplo:

```java
lblEstado
```

La barra deberá mostrar mensajes relacionados con algunas acciones de la aplicación.

Por ejemplo:

```text
Formulario reiniciado
Correo válido
Selección modificada
Tema actualizado
```

### Validación de correo en tiempo real

Uno de los `JTextField` deberá utilizarse para introducir una dirección de correo electrónico.

Mientras el usuario escribe deberá comprobarse si el formato es correcto.

Puedes utilizar:

```java
matches(...)
```

con una expresión regular sencilla.

Por ejemplo, deberá reconocer correctamente valores similares a:

```text
usuario@dominio.com
```

Cuando el correo no sea válido:

- el campo deberá mostrar un borde de color rojo;
- la barra de estado deberá indicar que el correo no es válido.

Cuando el correo sea válido:

- deberá recuperarse el borde normal;
- deberá marcarse automáticamente un `JCheckBox` destinado a indicar que el correo es válido;
- la barra de estado deberá mostrar un mensaje correspondiente.

Crea un método auxiliar como:

```java
private boolean validarCorreo(String correo)
```

### Parte 3. Personalización con FlatLaf

Utiliza algunas propiedades específicas de FlatLaf para modificar ciertos componentes.

### Campo de contraseña

Configura el `JPasswordField` para que permita mostrar u ocultar temporalmente la contraseña mediante un botón integrado.

Investiga las propiedades disponibles en:

```java
FlatClientProperties
```

para conseguir este comportamiento.

---

### Botón redondeado

Uno de los botones deberá utilizar un estilo redondeado mediante:

```java
FlatClientProperties.BUTTON_TYPE
```

con:

```java
FlatClientProperties.BUTTON_TYPE_ROUND_RECT
```

Por ejemplo:

```java
btnRedondo.putClientProperty(
    FlatClientProperties.BUTTON_TYPE,
    FlatClientProperties.BUTTON_TYPE_ROUND_RECT
);
```


---

### Botón de ayuda

Otro botón deberá utilizar el estilo específico de ayuda proporcionado por FlatLaf.

Puedes utilizar:

```java
btnAyuda.putClientProperty(
    FlatClientProperties.BUTTON_TYPE,
    FlatClientProperties.BUTTON_TYPE_HELP
);
```

Al pulsarlo deberá mostrarse un `JOptionPane` con una breve explicación sobre la aplicación.


![](media/b659313c2f89bf08a4f35281a33b65c4.png)

## Documentación



## Pruebas (testing) 

| ID Caso Prueba | Descripción Caso de Prueba                       | Entrada / Acción                                       | Salida Esperada                                                                                 | Resultado    |
| -------------- | ------------------------------------------------ | ------------------------------------------------------ | ----------------------------------------------------------------------------------------------- | ------------ |
| 01             | Verificar campos de texto (`JTextField`)         | Escribir texto en el primer campo                      | Se duplica en la otra mitad en orden inverso                                                    | OK/No cumple |
| 02             | Verificar campos de texto (`JTextField`)         | Escribir texto en el segundo campo                     | Se duplica igual en la otra mitad                                                               | OK/No cumple |
| 03             | Verificar campo contraseña (`JPasswordField`)    | Escribir una contraseña                                | Se duplica en la otra mitad (oculta). Permite mostrar u ocultar el texto con el botón integrado | OK/No cumple |
| 04             | Verificar botones (`JButton`)                    | Pulsar los botones                                     | Su acción se refleja en el botón duplicado                                                      | OK/No cumple |
| 05             | Verificar botón redondo (`FlatLaf`)              | Observar el botón redondo                              | Tiene forma redonda según la propiedad FlatLaf                                                  | OK/No cumple |
| 06             | Verificar botón de ayuda (`FlatLaf`)             | Pulsar el botón ayuda                                  | Muestra un icono de ayuda y/o mensaje emergente                                                 | OK/No cumple |
| 07             | Verificar Radio Buttons (`JRadioButton`)         | Cambiar la selección de un grupo de radio buttons      | Se duplica en la otra mitad y se respeta la exclusividad de grupo                               | OK/No cumple |
| 08             | Verificar Casillas de verificación (`JCheckBox`) | Marcar y desmarcar una casilla                         | Se duplica el estado en la otra mitad                                                           | OK/No cumple |
| 09             | Verificar Listado (`JComboBox`)                  | Cambiar el valor seleccionado                          | Se actualiza en la otra mitad                                                                   | OK/No cumple |
| 10             | Verificar Spinner (`JSpinner`)                   | Cambiar el valor                                       | Se duplica el valor en la otra mitad                                                            | OK/No cumple |
| 11             | Verificar Barra deslizadora (`JSlider`)          | Deslizar la barra                                      | Se duplica en la otra mitad y se muestra el porcentaje                                          | OK/No cumple |
| 12             | Verificar `JSplitPane`                           | Cambiar el tamaño de las divisiones                    | Se refleja el color o posición en ambas mitades                                                 | OK/No cumple |
| 13             | Verificar Menú “Archivo”                         | Desplegar el menú                                      | Se muestran las opciones correspondientes                                                       | OK/No cumple |
| 14             | Verificar Menú “Edición → Borrar todo”           | Seleccionar “Borrar todo”                              | Todos los campos y selecciones se restablecen                                                   | OK/No cumple |
| 15             | Verificar Barra de estado (`JPanel` inferior)    | Realizar distintas acciones                            | Muestra mensajes contextuales (validación, acciones, etc.)                                      | OK/No cumple |
| 16             | Validación campo correo (incorrecto)             | Escribir correo sin formato válido                     | Se muestra borde rojo                                                                           | OK/No cumple |
| 17             | Validación campo correo (correcto)               | Escribir correo con formato correcto (con @ y dominio) | Borde normal, se marca checkbox verde y muestra mensaje en barra de estado                      | OK/No cumple |

