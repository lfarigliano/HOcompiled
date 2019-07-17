0000000000000000 t add_abs
                 U _GLOBAL_OFFSET_TABLE_
000000000000002a T main
                 U printf
0000000000000000 r val1
0000000000000004 R val2
0000000000000000 d val3
0000000000000004 D val4

t=es una función definida en el texto y es local.
U= No esta definido en ningun lado al momento
T= Definido en el archivo, y es global
r= es una constante local (solo lectura) y esta definida en el 
archivo
R=es una constante global y esta definida en el archivo
d= es una variable iniciada local y declarada en el archivo
D= es una variable global, declarada en el archivo



