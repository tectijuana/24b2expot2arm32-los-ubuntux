
<!---
   Para comentarios usar este bloque para documentar pendientes, secuencias, etc.
--->


![](https://s3.amazonaws.com/videos.pentesteracademy.com/videos/badges/low/arm-assembly.png)

Borrar y modificar README

# Utilizar los dos directorios

- code  - ahi depositar sus programas los ***archivos extensión *.s****  (Source File) algunos autores en x86 de ponen .asm y en otras plataformas ARM compatibles la extension *.s
- Todo programa lleva su comentario en la parte de arriba, objetivo y nombre del programador minimo, como templete
- images  - de haber algo de pantallas ahi se presentaran, su busca documentarlas en MARKDOWN el código es:

``` ![](images/---archivo.jpg---) recordar que no lleva espacios```

<!---
  Los nombres de las imagenes no deben cambiar de preferenci el nombre del programa como:  KIOSKO.cpp (su pantallas serian KISOCO.jpg, KIOSCO-1.jpg, KIOSCO-2.jpg ... )
  Y asi procurar estar agrupados.
--->



- Programa en MarkDown es inicia con tres tildes * (`) sin espacio, seguido de el lenguaje de programacion, al final del codigo se poner otra vez los mismos tilder..

No se usan espacios en nombres de archivos, usar los nombres estilo camelCase (primera palabra minusculas, mayuscula solo la 1ra letra de cada palabra subsecuente):  ejemplo: sensorHumo, etc.

Suerte.



------

<pre>

	<p align=center>

Tecnológico Nacional de México
Instituto Tecnológico de Tijuana

Departamento de Sistemas y Computación
Ingeniería en Sistemas Computacionales

Semestre:
Febrero - Junio 2022

Materia:
Lenguajes de interfaz

Docente:
M.C. Rene Solis Reyes 

Unidad:
2

Título del trabajo:
Exposicion Tema 2

Estudiante:
Hernandez Leon Julio Alejandro

Campos Ibarra Sebastian

Muñoz Medina Ramiro Guadalupe

Rivas Huerta Olaf

Leal Lua Luis Roberto

	</p>

</pre>

## Anatomia de un Programa en Assembly
### Secciones
---
<pre>

	<p align=left>
	jejejej


	</p>

</pre>

### Etiquetas
---
<pre>

	<p align=left>


	</p>

</pre>

### Instrucciones
--- 
<pre>

	<p align=left>


	</p>

</pre>

## Proceso de Compilación
--- 
<pre>

	<p align=left>


	</p>

</pre>

## Proceso de Compilación y Enlazado
--- 
<pre>

	<p align=left>


	</p>

</pre>

## Creación de un Makelife simple
--- 
<pre>

	<p align=left>


	</p>

</pre>

# Programa que realiza operaciones aritméticas básicas.
--- 
 ```S
section .data
    ; Declaración de variables
    num1    db  10      ; Primer número
    num2    db  5       ; Segundo número
    result  db  0       ; Variable para almacenar el resultado

section .text
    global _start

_start:
    ; Suma
    mov al, [num1]     ; Mueve el primer número a AL
    add al, [num2]     ; Suma el segundo número a AL
    mov [result], al   ; Almacena el resultado en la variable 'result'

    ; Resta
    mov al, [num1]     ; Mueve el primer número a AL
    sub al, [num2]     ; Resta el segundo número de AL
    mov [result + 1], al ; Almacena el resultado en la siguiente posición de 'result'

    ; Multiplicación
    mov al, [num1]     ; Mueve el primer número a AL
    imul byte [num2]  ; Multiplica AL por el segundo número
    mov [result + 2], al ; Almacena el resultado en la siguiente posición de 'result'

    ; División
    mov al, [num1]     ; Mueve el primer número a AL
    mov bl, [num2]     ; Mueve el segundo número a BL
    xor ah, ah         ; Limpiar AH para dividir
    div bl             ; Divide AL por BL
    mov [result + 3], al ; Almacena el cociente en la siguiente posición de 'result'

    ; Mostrar el resultado
    mov edx, 3         ; Longitud del resultado (suma, resta, multiplicación)
    mov ecx, result    ; Dirección del resultado
    mov ebx, 1         ; Descriptor de archivo estándar (stdout)
    mov eax, 4         ; Llamada al sistema para escribir
    int 0x80           ; Interrupción del sistema

    ; Salir del programa
    mov eax, 1         ; Llamada al sistema para salir
    xor ebx, ebx       ; Código de salida cero
    int 0x80           ; Interrupción del sistema

