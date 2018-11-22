# Fortran

## 1-loop-interch

Primero compilo con el flag -O0 (sin optimizar) y mido el tiempo: 1.723 segundos.
Con -O1 (optimizar), tarda 1.388 segundos.
Con -O3 (optimizar aún más), 0.540 segundos.

## test_gprof1

Compilo primero con el flag -O0 para que no optimice. Mido el tiempo: 3.05 segundos. Hago un profiling con la aplicación "Instruments" de mac (por lo que encontré en google, es la mejor opción: perf funciona sólo con linux, y stackexchange desaconseja tratar de instalar gprof), y veo que la subrutina good_assign se usa 0.637 segundos, mientras que bad_assign consume 1.97 segundos (más que la otra, como esperábamos).

Compilo luego con -O1. Tiempo total: 1.04 segundos, de los cuales la función bad_assign se usa 0.014 segundos. La función good_assign no aparece en el profiler, quizá porque se usa demasiado poco tiempo (si hago nm del ejecutable, la función good_assign aparece).

Compilo finalmente con -O3. Tiempo total: 28 ms. No aparecen ni good_assign ni bad_assign en el profiler, quizá porque ambas funciones gastan demasiado poco tiempo.

