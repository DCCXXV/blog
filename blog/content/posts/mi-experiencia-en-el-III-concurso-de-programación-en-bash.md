+++
title = 'Mi Experiencia en el «III Concurso De Programación En Bash»'
date = 2025-03-28T18:03:48+01:00
tags = ["programación", "UCM", "linux", "bash"]
draft = false
+++

El III Concurso de programación en bash es la tercera edición de un concurso de Bash scripting que se realiza en la **Facultad de Informática** de la **UCM**, en el que se proponen una serie de problemas muy variados a resolver usando diversos comandos de **GNU/Linux** y las diferentes herramientas de **Bash**.

Aunque llevo usando Linux desde que empecé la universidad, la verdad es que mis conocimientos específicos de *scripting* en **Bash** antes de empezar a prepararme para esto eran escasos. Decidí apuntarme precisamente porque buscaba ponerme a prueba y esperaba encontrarme con algo que realmente supusiera un desafío. Además, no voy a negar que la mejora en la calificación en la asignatura de Sistemas Operativos era un buen incentivo.

Durante la semana pasada he estado preparándome el concurso repasando y aprendiendo comandos como `sed`, `awk`, `cut`, `grep`, `tail`... y muchos más. Algo de lo que me di cuenta al ponerme a resolver problemas de ediciones anteriores es que al programar con **Bash** lo más importante es saber qué comando es el más adecuado para conseguir lo que quieres, por lo que mi preparación al inicio fue sobre todo aprender qué hacían los comandos más básicos y cómo usarlos eficientemente. Daré un ejemplo de un problema que realicé para practicar:

```bash
#!/bin/bash

# (Similar al enunciado original)
# Escribe un script que busca archivos regulares dentro de un
# directorio especificado (o el directorio actual por defecto)
# que hayan sido modificados en los últimos 60 segundos. Para cada 
# archivo encontrado que cumpla esta condición, imprime su nombre 
# (sin la ruta del directorio) seguido de un punto y coma y su 
# antigüedad exacta en segundos.

directorio="${1:-.}"
for nombre_archivo in "$directorio"/*;do
    if [ -f "$nombre_archivo" ]; then
        antiguedad_segundos=$(date -r "$nombre_archivo" +%s)
        tiempo_actual_segundos=$(date +%s)
        diferencia=$((tiempo_actual_segundos - antiguedad_segundos))
        if [ "$diferencia" -le 60 ]; then
            nombre_archivo=${nombre_archivo#*/}
            echo "$nombre_archivo;$diferencia"
        fi
    fi
done
```

Como ya he comentado la dificultad real de estos problemas es principalmente identificar qué comandos son los más adecuados para cada paso y cómo combinarlos. Cada problema se puede resolver con una infinidad de comandos distintos y es por esto que es muy dificil que dos respuestas sean iguales. Por ejemplo, para ver la fecha de modificación en vez de `date -r` podría haber usado `stat`, para cada procesamiento de texto podría haber usado `sed` o `awk`, etc.

El concurso en sí fue muy entretenido. Se realizó en el Laboratorio 8 y el ambiente bastante bueno, los organizadores estaban muy atentos para resolver dudas. Tuvimos 13 problemas a resolver en 2 horas, aunque realmente no estaba pensado para hacer los 13 enteros, ya que la persona que más consiguió resolvió 9 (en todo momento se podía ver por el proyector el tablón con el usuario dado y los problemas resueltos). 

Los problemas tenian un enunciado muy claro con un ejemplo de ejecución y una o dos pistas con comandos que podrían ayudar a resolverlo. Los primeros fueron bastante sencillos, pero a partir del ejercicio 5 la dificultad empezó a subir y me quedé atascado en un problema por olvidarme de como usar el delimitador en el comando `cut` para delimitar por espacios. Sin embargo el problema realmente díficil y el que solo completamos dos personas fue el ejercicio 7, donde se pedía un control bastante avanzado del comando `date` y en el que empleaba la variable de entorno **TZ**.

```bash
$ ./program.sh "2025-03-28 15:30" "Europa/Madrid" "Asia/Tokio"

En Asia/Tokyo son las 23:30 del 2025-03-28.
Eso supone una diferencia de 8:00 horas
```

Era un problema realmente díficil si no se conocía el comando `date` lo suficiente y es una muestra de lo variados que son los problemas. Entre intentar resolver este y los anteriores, las dos horas se esfumaron (e incluso me pasé un poco). Al final, conseguí resolver 7 problemas dejándome en segundo lugar en el tablón, resultado que considero satisfactorio.

En conclusión, estoy muy contento de haber participado y, viendo la dificultad y lo que he aprendido, definitivamente espero participar en la próxima edición.