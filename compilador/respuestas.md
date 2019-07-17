1- El proceso de compilación se divide en 4 etapas. Pre-procesador, 
  compilación I (traducción de C  a assembler), compilación II 
  (traducción de assembler a binario) y el linkeo.
  En la primera etapa, se traduce todo lo incluido en los include, 
  donde se encuentran las funciones predefinidas en cada uno de los
  archivos incluidos. Ademas te permite mejorar los errores del 
  progrma.
  En la etapa 2 se traduce el codigo escrito en lenguaje C a assember, 
  pasa a un lenjuage intermededio, optimizando a un lenguaje de menor 
  nivel. Optimiza cosas irrelevantes del codigo
  En la etapa 3 hace optimizaciones de hardware, y produce el .o 
  en un lenguaje de acuerdo a la maquina.
  En la etapa 4 busca todas los link a todo lo que llamaste, en estado 
  estatio o dinámico, estatico podia en el main, y dinámico apunta a 
  donde está. Estático es más rápido, en el caso de la dinámica puedo 
  modificarla y se va actualizando. 
  
2.En la practica la primera etapa pusimos.
  gcc -E calculator.c -o calculator.pp.c
  Lo que hace es declarar las funciones, y les dice a futuros pasos
  que no haga nada hasta que llegue el link.
  Informa que las funciones son externas y que en la etapa de link va a
  saber donde buscarlas.
  En la segunda etapa
  gcc -S calculator.c -o calculator.asm
  Lo que vemos en el .asm, se detalla el programa escrito en C, escrito 
  en un lenguaje de menor nivel llamado assembler.
  En la estapa 3
  gcc -c calculator.c -o calculator.o
  Se termina de complicar si se quiere ver con un editor normal.
  si lo vemos con nm
000000000000003e T add_numbers
                 U _GLOBAL_OFFSET_TABLE_
0000000000000000 T main
                 U printf
  T significa que esta definido en el texto, en esa seccion. En cambio
  U no esta definida.
  En la etapa 4
  gcc -v calculator.o -o calculator.e
  Linkea todas las partes y con -v te muestra todas las dependencias o 
  linkeos

3.call	add_numbers  call_printf@PLT en esas lineas se llaman a las 
funciones que aparecen en el lenguaje C.

4.a partir del nm, permite ver el descriptor y las entradas del codigo.
El en punto dos son descriptas para este caso. Descriptores T, U, 
   entradas printf y add_number.

5. En el ejecutable a partir de nm se ven muchos mas detalle. En 
particular se ve que el printf sigue como U pero se linkea a la direción 
de la libreria. En este caso es una libreria dinámica.
