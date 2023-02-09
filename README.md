# Algoritmo de Decker
## 01.py
Cada proceso espera a que sea su turno para entrar en la parte critica. El problema es que si un proceso tarda mucho, el resto de procesos deben esperar a que ese proceso entre en la parte critica antes de poder seguir ejecutandose, ya que debe mantener el orden

## 02.py
Aqui, el proceso evalua is_anybody_inside antes de entrar a la parte critica y _en teoria_, solo entra a la parte critica si no hay ningun otro proceso distinto ejecutando la parte critica, arreglando asi el problema del orden, ya que los procesos entraran siempre que este libre la parte critica
En la práctica, el problema es que si se modifica critical mientras otro proceso esta corriendo el bucle de anybody, puede ocurrir que ya haya pasado por ese valor antes de ser cambiado y por tanto entren dos procesos a la vez en la parte critica

## 03.py
En este programa, se mantiene el problema de 02.py, y surge un nuevo problema: es más dificil que un programa entre a la solucion critica, llevando a stack overflow y explotando el interprete. Esto ocurre por que para que un proceso llegue a la parte critica, el resto de procesos que quieren entrar a esta deben de rendirse al mismo tiempo, y el tiempo de estar rendido son solo dos intrucciones, por lo que es muy dificil que un proceso entre a la parte critica y la mayor parte del tiempo, todos los procesos se encuentran encerrados en un bucle

## 04_decker.py
Este programa hace lo mismo que el 03.py pero añade una nueva condicion. Por el bucle while turn.value == tid, nos aseguramos que un proceso no puede entrar en la seccion critica dos veces seguidas en el caso de que haya algun otro proceso que quiera entrar. De esta forma se soluciona que exista un proceso que acapare todos los recursos, agilizando el programa
