# Bugs

## General

Si no pongo flag de debug, el debugger lldb no me deja poner un breakpoint en una línea: me dice 

`Breakpoint 1: no locations (pending).
WARNING:  Unable to resolve breakpoint to any actual locations.`

Con el flag -g, sí me deja poner breakpoints en líneas. El mejor flag de optimización es -O0 (pedirle que no optimice).


## Add_array_static

Error: la suma da cualquier cosa.

Pongo un breakpoint en la línea 22, después del for que define los arrays a y b, y me doy cuenta de que estos arrays están bien definidos. Por lo tanto, el error viene de la función add_array. Veo que en el for que hay dentro de esta función el límite superior está mal. Lo corrijo y anda todo bien.


## Add_array_dynamic

Error: la suma da cualquier cosa.

Empiezo corrigiendo el mismo error del código anterior y entonces ya anda bien, así que no hago nada más.


## Add_array_segfault

Error: segmentation fault.

Después de corregir el mismo bug de antes, tras lo cual persiste el error, pongo de vuelta un breakpoint en la línea 22 y veo que a y b tienen problemas: me dice

`error: Couldn't apply expression side effects : Couldn't dematerialize a result variable: couldn't read its memory`

Me doy cuenta de que en este caso a y b son punteros y no están alocados. Los aloco y todo bien.

