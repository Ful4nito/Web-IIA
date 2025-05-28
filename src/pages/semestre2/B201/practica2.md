# Practica 2

## Objeto con datos ingresados por el usuario  25/02/25

Instrucciones:
Genere un programa que pida al usuario que inserte los datos de un alumno tales como Nombre completo, Boleta y grupo, estos deberán ser almacenados en un objeto, puede ser utilizando class ó struct, después mostrar los datos del alumno en pantalla.

``` cpp
// Baez Pacheco Jonathhan Leon      

#include <stdio.h>
#include <stdlib.h>

class ALUMNO{
  public:
    char nombre[30];
    int boleta;
    char grupo[5];
} Alumno;

int main (void) {
  
    printf("Inserte nombre del alumno: ");
    scanf("%[^\n]s", Alumno.nombre);
    printf("Boleta: ");
    scanf("%i", &Alumno.boleta);
    printf("Grupo: ");
    scanf("%s", Alumno.grupo);
  
    printf("\n 1  %-30s %-11i %-5s\n", Alumno.nombre, Alumno.boleta, Alumno.grupo);

}
```