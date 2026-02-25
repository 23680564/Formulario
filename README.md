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

     ## Codigo completo
     
```
import flet as ft
import re

def main(page: ft.Page):
    page.title = "Registro de Estudiantes"
    page.window_width = 900
    page.window_height = 650
    page.bgcolor = "#B2EBF2"

    # -----------------------------
    # CAMPOS DEL FORMULARIO
    # -----------------------------
    txt_nombre = ft.TextField(label="Nombre completo")
    txt_control = ft.TextField(
        label="Número de Control",
        keyboard_type=ft.KeyboardType.NUMBER,
        input_filter=ft.NumbersOnlyInputFilter()
    )
    txt_email = ft.TextField(label="Correo electrónico")

    dd_semestre = ft.Dropdown(
        label="Semestre",
        options=[ft.dropdown.Option(str(i)) for i in range(1, 7)]
    )

    dd_carrera = ft.Dropdown(
        label="Carrera",
        options=[
            ft.dropdown.Option("Ingeniería en Sistemas"),
            ft.dropdown.Option("Ingeniería Civil"),
            ft.dropdown.Option("Ingeniería Industrial"),
            ft.dropdown.Option("Contador Público"),
            ft.dropdown.Option("Electrónica")
        ]
    )

    genero_group = ft.RadioGroup(
        content=ft.Row([
            ft.Radio(value="Masculino", label="Masculino"),
            ft.Radio(value="Femenino", label="Femenino")
        ])
    )

    # -----------------------------
    # LISTA DE REGISTROS
    # -----------------------------
    lista_registros = ft.Column(scroll="auto")
    total = 0
    contador = ft.Text("Total registrados: 0")

    # PANEL LATERAL (inicialmente vacío)
    panel_lateral = ft.Container(
        width=400,
        padding=15,
        bgcolor="white",
        visible=False
    )

    # -----------------------------
    # FUNCIÓN GUARDAR
    # -----------------------------
    def guardar(e):
        nonlocal total

        email_valido = re.match(r"^[^@\s]+@[^@\s]+\.[^@\s]+$", txt_email.value or "")

        if (txt_nombre.value and txt_control.value and email_valido
            and dd_carrera.value and dd_semestre.value and genero_group.value):

            # Crear registro visual
            registro = ft.Container(
                content=ft.Column([
                    ft.Text(f"Nombre: {txt_nombre.value}"),
                    ft.Text(f"Número de Control: {txt_control.value}"),
                    ft.Text(f"Correo: {txt_email.value}"),
                    ft.Text(f"Carrera: {dd_carrera.value}"),
                    ft.Text(f"Semestre: {dd_semestre.value}"),
                    ft.Text(f"Género: {genero_group.value}")
                ]),
                padding=10,
                border=ft.border.all(1, "black"),
                border_radius=8
            )

            lista_registros.controls.append(registro)

            total += 1
            contador.value = f"Total registrados: {total}"

            # Mostrar en panel lateral
            panel_lateral.content = ft.Column([
                ft.Text("Último Registro Enviado",
                        size=18,
                        weight="bold"),
                registro,
                ft.Divider(),
                ft.Text("Todos los Registros",
                        size=18,
                        weight="bold"),
                lista_registros,
                contador,
                ft.ElevatedButton("Cerrar Panel", on_click=cerrar_panel)
            ], scroll="auto")

            panel_lateral.visible = True

            # Limpiar campos
            txt_nombre.value = ""
            txt_control.value = ""
            txt_email.value = ""
            dd_carrera.value = None
            dd_semestre.value = None
            genero_group.value = None

        else:
            page.snack_bar = ft.SnackBar(
                ft.Text("Error, falta de datos"),
                bgcolor="red"
            )
            page.snack_bar.open = True

        page.update()

    def cerrar_panel(e):
        panel_lateral.visible = False
        page.update()

    # -----------------------------
    # INTERFAZ PRINCIPAL
    # -----------------------------
    formulario = ft.Container(
        content=ft.Column([
            ft.Text("Formulario de Registro",
                    size=24,
                    weight="bold"),

            txt_nombre,
            txt_control,
            txt_email,
            dd_carrera,
            dd_semestre,

            ft.Row([
                ft.Text("Género:"),
                genero_group
            ]),

            ft.ElevatedButton("Enviar", on_click=guardar)
        ],
        spacing=15),
        padding=20,
        width=400
    )

    # Mostrar formulario a la izquierda y panel a la derecha
    page.add(
        ft.Row([
            formulario,
            panel_lateral
        ])
    )

ft.app(target=main)
```




      






