# Proyecto Integrador

Este proyecto consiste en el desarrollo de una aplicación en Python utilizando Flet para crear un formulario de registro de estudiantes. El propósito de la práctica es aplicar conceptos de interfaces gráficas, validación de datos y programación orientada a eventos.

La aplicación permite capturar información del estudiante, validar que los datos estén completos y mostrar los registros guardados en un panel dinámico, además de llevar un conteo total de estudiantes registrados.

El objetivo principal es reforzar el uso de controles gráficos, validaciones y actualización dinámica de la interfaz dentro de un entorno interactivo.

## Para poder realizar el proyecto
- Instalar Python desde:
  <img width="638" height="117" alt="image" src="https://github.com/user-attachments/assets/bc7afc8b-5d1f-4cce-a7e2-fd80b3fcdc0e" />

  - Abir el link e ir a download
    <img width="556" height="276" alt="image" src="https://github.com/user-attachments/assets/c1697607-001e-4c6e-bd8a-a1052a4f255a" />

    - Descargarlo, y ejecutar en el sistema

    ## Instalar flet
    
    - Se instala desde el **cmd** del sistema

      `pip install flet`

    - Ahora generar el entorno virtual

   ` python -m venv venv`
      
    - Esto crea una carpeta llamada venv/

  Desde Powershell:
      
   `venv\Scripts\Activate`
      
  - Desde CMD:

  `venv\Scripts\activate.bat`

  - Se mostrara en la terminal lo siguiente:

  `(venv) C:\ruta-del-proyecto>`

 - Activar el entorno virtual desde Linux/MacOs
  
 ### Paso 1: Crear entorno virtual
 `python3 -m venv venv`

### Paso 2: Activarlo
`source venv/bin/activate`

La terminal mostrará:

`(venv) user@pc:~/proyecto$`

---
    
## Configuracion de la ventana

`page.title = "Registro de Estudiantes"
page.window_width = 900
page.window_height = 650
page.bgcolor = "#B2EBF2"
`

Aquí se configura:

- El título de la aplicación

- Tamaño de la ventana

- Color de fondo azul claro

- Se usa Flet para crear una aplicación gráfica moderna

---

## Campos del formulario

Se crean los controles donde el usuario ingresará los datos.

## Campo Nombre
`txt_nombre = ft.TextField(label="Nombre completo")`

Permite ingresar texto libre.

## Número de Control (Solo números)

`txt_control = ft.TextField(
    keyboard_type=ft.KeyboardType.NUMBER,
    input_filter=ft.NumbersOnlyInputFilter()
)`

Aquí se aplican dos validaciones importantes:

`keyboard_type=NUMBER` → muestra teclado numérico

NumbersOnlyInputFilter() → bloquea letras

Esto garantiza que solo se ingresen números.

## Correo electrónico

`txt_email = ft.TextField(label="Correo electrónico")`

Luego se valida usando expresión regular:

`email_valido = re.match(r"^[^@\s]+@[^@\s]+\.[^@\s]+$", txt_email.value or "")`

Esto verifica que tenga:

- Texto

- @

- Dominio

- Punto

## Dropdowns (Listas desplegables)

Semestre:

`dd_semestre = ft.Dropdown(
    options=[ft.dropdown.Option(str(i)) for i in range(1, 7)]
)`

Carrera:

`dd_carrera = ft.Dropdown(...)`

Permiten seleccionar opciones predefinidas, evitando errores de escritura.

## Género (Radio Buttons)

`genero_group = ft.RadioGroup(...)`

Permite elegir solo una opción a la vez.

---

## Sistema de almacenamiento
`lista_registros = ft.Column(scroll="auto")
total = 0
contador = ft.Text("Total registrados: 0")`

Aquí:

`lista_registros` guarda visualmente cada registro

`total` cuenta estudiantes registrados

`contador` muestra el total en pantalla

## Panel lateral dinámico
`panel_lateral = ft.Container(
    width=400,
    visible=False
)`

Este panel:

- Aparece solo cuando se guarda un registro

- Muestra el último registro

- Muestra todos los registros acumulados

- Tiene botón para cerrarlo

---

## Panel lateral dinámico
`panel_lateral = ft.Container(
    width=400,
    visible=False
)`

Este panel:

- Aparece solo cuando se guarda un registro

- Muestra el último registro

- Muestra todos los registros acumulados

- Tiene botón para cerrarlo

---

## Función principal: guardar()

`def guardar(e):`

Esta función:

## Paso 1: Validar datos

Verifica que:

- No haya campos vacíos

- Email sea válido

- Dropdowns tengan valor

- Género esté seleccionado

## Paso 2: Crear el registro visual
`registro = ft.Container(...)`

Se construye un contenedor que muestra:

- Nombre

- Número de Control

- Email

- Carrera

- Semestre

- Género

## Paso 3: Guardarlo en la lista

`lista_registros.controls.append(registro)`

Esto hace que se acumulen registros dinámicamente.

## Paso 4: Actualizar contador
`total += 1
contador.value = f"Total registrados: {total}"
`

Incrementa el número total de estudiantes registrados.

## Paso 5: Mostrar panel lateral
`panel_lateral.visible = True`

Hace visible el panel derecho con:

- Último registro

- Lista completa

- Total

- Botón cerrar

## Paso 6: Limpiar campos
`txt_nombre.value = ""
...
`

Deja el formulario listo para un nuevo registro.

## Función cerrar_panel()
`def cerrar_panel(e):
    panel_lateral.visible = False`

Oculta el panel lateral sin borrar los registros.

## Estructura de la interfaz

Se usa:

`ft.Row([formulario, panel_lateral])`

Esto divide la pantalla en dos partes:

<img width="516" height="86" alt="image" src="https://github.com/user-attachments/assets/a8650e1c-ba5a-4a02-a5f5-c471f26f4a9b" />

## ¿Cómo funciona el proyecto?

- El usuario llena el formulario.

- Presiona "Enviar".

- El sistema valida la información.

- Si todo es correcto:

- Se guarda el registro

- Se actualiza el contador

- Se muestra el panel lateral

- Si hay error:

- Muestra mensaje en rojo (SnackBar)

  ## Como ejecutar el proyecto
  
   - Ubicar la carpeta en donde se guardo el proyecto

     <img width="230" height="23" alt="image" src="https://github.com/user-attachments/assets/a463d72c-a4a3-4490-ae77-36188269edb1" />

  - Selecionar el archivo con el nombre que se le puso al proyecto

    <img width="195" height="24" alt="image" src="https://github.com/user-attachments/assets/9a5c5002-0477-4eab-a078-d32c7512a39b" />

  - Dar click derecho en el archivo y selecionar la opcion que dice **Open Git Bash Here**

    <img width="415" height="259" alt="image" src="https://github.com/user-attachments/assets/36e13cdf-8e7d-488a-8948-c90149cdae79" />

  - Se abrira la terminal de **Git bash**

      <img width="376" height="162" alt="image" src="https://github.com/user-attachments/assets/3e9f05f8-5509-45cd-b6e2-984d7b4d870f" />

  - Ahora poner el comando **python elnombredelarchivo.py**

      <img width="340" height="197" alt="image" src="https://github.com/user-attachments/assets/3a464801-474b-4c20-a543-867a2268aaf5" />

   - Una vez puesto el comando se abrira la ventana del proyecto ejecutado

     <img width="481" height="518" alt="image" src="https://github.com/user-attachments/assets/7912395d-666c-41f2-9cfc-7687e8c70957" />

     <img width="359" height="516" alt="image" src="https://github.com/user-attachments/assets/3a083050-642f-4456-b667-3c65271fc6d8" />

     <img width="835" height="616" alt="image" src="https://github.com/user-attachments/assets/93de2b50-35e6-427e-a596-a7c52909bebb" />




      






