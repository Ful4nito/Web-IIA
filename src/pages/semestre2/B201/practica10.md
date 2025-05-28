# Practica 10

## Ordenamiento por Seleccion

Instrucciones:
Desarrollar un programa que ordene por seleccion una lista estatica de numeros enteros, Solicitar al usuario cuantos numeros aleatorios desea generar, estos debene tomar valores entre 0 y 100, la cantidad de numeros aleatorios debe der de 1 a 100.

``` cpp
// Baez Pacheco Jonathan Leon  

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int arr[100];
int n = 0;
int i = 0;
int j = 0;

int k = 0;
int cambios = 0;

int minimo = 0;
int temp = 0;

int main () {
  srand(time(NULL));

  printf("\n ===== Ordenamiento por Seleccion =====");
  printf("\n  Cuantos numeros desea generar > ");
  scanf("%i", &n);

  printf("  ");
  for (i=0; i<n; i++) {
    arr[i] = rand() % 101;
    printf(" %-3i", arr[i]);
  }
  printf("\n");

  for (i=0; i<n; i++) {
    cambios = 0;
    temp = arr[i];
    for (j=i+1; j<n; j++) {
      if (arr[j] < temp) {
        temp = arr[j];
        minimo = j;
        cambios = 1;
      }
    }

    arr[minimo] = arr[i];
    arr[i] = temp;
    
    if (cambios == 1) {
      printf("\n  ");
      for (k=0; k<n; k++) {
        printf(" %-3i", arr[k]);
      }
    }
  }
}
```
