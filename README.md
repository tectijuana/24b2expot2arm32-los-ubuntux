
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

## Anatomia de un Programa en Assembly (Ensamblador)
### Secciones
---
![image](https://github.com/tectijuana/24b2expot2arm32-los-ubuntux/assets/105456306/100de38c-3f6f-4556-b4e6-d649878afc36)

**1. Sección de Datos (.data)**
  
Esta sección contiene las definiciones de variables inicializadas con valores específicos. 
Dentro de esta se definen las etiquetas (símbolos) que representan las direcciones de memoria de estas variables. 

**2. Sección de Código (.text)**
  
Esta sección contiene las instrucciones ejecutables del programa. 
Cada instrucción está precedida por una etiqueta opcional que puede ser utilizada para hacer referencia a esa ubicación de memoria.

**3. Sección de Datos No Inicializados (.bss)**
  
Esta sección contiene las instrucciones ejecutables del programa. 
Cada instrucción está precedida por una etiqueta opcional que puede ser utilizada para hacer referencia a esa ubicación de memoria.

### Etiquetas
---

Son identificadores simbólicos que representan direcciones de memoria específicas. Pueden ser utilizadas para hacer referencia a variables, subrutinas o ubicaciones de código.

![image](https://github.com/tectijuana/24b2expot2arm32-los-ubuntux/assets/105456306/63f2dbd5-08e4-46e1-a2bf-886319eee065)

### Instrucciones
--- 

Son las operaciones básicas que realiza el procesador, como mover datos entre registros y memoria, realizar operaciones aritméticas y lógicas, y controlar el flujo del programa mediante saltos condicionales e incondicionales.

## Proceso de Compilación
--- 

El proceso de compilación convierte el código fuente escrito en lenguaje ensamblador a código objeto (archivos .o). Este proceso se lleva a cabo mediante una herramienta llamada ensamblador (por ejemplo, as en sistemas Unix/Linux).

Los pasos principales del proceso de compilación son:

**1. Preprocesamiento** 

En esta etapa, el preprocesador del ensamblador maneja las directivas del ensamblador, como la inclusión de archivos y la definición de macros.

**2. Ensamblado**

El ensamblador traduce las instrucciones en lenguaje ensamblador a código máquina, que es la representación binaria que entiende el procesador. Además, resuelve las referencias simbólicas (etiquetas) a direcciones de memoria dentro del mismo archivo fuente.

**3. Generación de código objeto** 

El resultado del ensamblado es un archivo objeto que contiene el código máquina generado, así como información adicional necesaria para el siguiente paso del proceso, que es el enlazado.

![image](https://github.com/tectijuana/24b2expot2arm32-los-ubuntux/assets/105456306/8b771de7-e0de-4876-b761-a78ff7f5e9f7)

## Proceso de Compilación y Enlazado
--- 

El proceso de compilación y enlazado convierte el código fuente en lenguaje ensamblador en un ejecutable que puede ser ejecutado por el sistema operativo. Este proceso consta de dos pasos principales:

**1. Compilación**

* El ensamblador (as) traduce el código fuente en ensamblador a código objeto (archivos .o).
* Resuelve las referencias simbólicas (etiquetas) a direcciones de memoria dentro del mismo archivo fuente.
* Genera un archivo objeto que contiene el código máquina e información adicional.


**2. Enlazado**
* El enlazador (ld) combina uno o más archivos objeto en un solo archivo ejecutable.
* Resuelve las referencias externas a funciones y variables definidas en otros archivos objeto o bibliotecas.
* Vincula las bibliotecas necesarias (por ejemplo, libc) con el ejecutable final.
* Asigna ubicaciones de memoria para las diferentes secciones del programa (código, datos, etc.).
* Genera el archivo ejecutable final que contiene todo el código y los datos necesarios.

![image](https://github.com/tectijuana/24b2expot2arm32-los-ubuntux/assets/105456306/efaaf861-9f26-4c75-a919-e518f34dbe06)

## Creación de un Makefile simple
--- 
![image](https://github.com/tectijuana/24b2expot2arm32-los-ubuntux/assets/105456306/cac1a06f-2b39-479b-acd0-50a02b6280bd)


Un Makefile es un archivo que contiene instrucciones para automatizar el proceso de compilación y enlazado de un programa. Aquí hay un ejemplo de un Makefile simple para un programa en ensamblador:

* makefile

* Copy code
---
### Nombre del objetivo final

* TARGET = programa
---
### Archivos fuente

* SOURCES = main.s
---
### Reglas de compilación

all: $(TARGET)

$(TARGET): $(SOURCES)

    as -o $(TARGET).o $(SOURCES)
    
    ld -o $(TARGET) $(TARGET).o

clean:
    rm -f $(TARGET) $(TARGET).o
En este Makefile:

TARGET es el nombre del ejecutable final.
SOURCES es una lista de archivos fuente en lenguaje ensamblador.
La regla all define el objetivo principal, que en este caso es el ejecutable $(TARGET).
La regla $(TARGET) compila el archivo fuente $(SOURCES) utilizando el ensamblador (as) y genera un archivo objeto $(TARGET).o.
Luego, el archivo objeto se enlaza con el enlazador (ld) para generar el ejecutable $(TARGET).
La regla clean elimina los archivos generados durante la compilación y el enlazado.
Para compilar y enlazar el programa, simplemente ejecuta make en la línea de comandos. Para eliminar los archivos generados, ejecuta make clean.



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

