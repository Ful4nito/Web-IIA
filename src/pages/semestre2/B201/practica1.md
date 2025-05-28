# Practica 1

## Ordenamiento Burbuja de números generados aleatoriamente 18/02/25

Instrucciones:
Un programa que pide al usuario cuantos números aleatorios desea generar, estos deben estar en el rango de 0 a 100, posteriormente se le aplicara solamente una iteracion de ordenamiento burnuja y se mostrara el resultado por pantalla.

``` cpp
// Baez Pacheco Jonathan Leon

# include <stdio.h>
# include <stdlib.h>
# include <time.h>

int arr[100];
int n = 0;
int temp = 0;
int pasadas = 1;

int main() {
  srand(time(NULL));
  printf("\nCantidad de numeros aleatorios: ");
  scanf("%i", &n);

  for (int i=0; i<n; i++) {
    arr[i] = rand() % 101;
    printf("%i\t", arr[i]);
  }
  printf("\n");

  for(int i=0; i<pasadas; i++) {
    for (int j=0; j<(n-1); j++) {
      if(arr[j]>arr[j+1]) {
        temp = arr[j+1];
        arr[j+1] = arr[j];
        arr[j] = temp;
      }
    }

    for(int i=0; i<n; i++)
      printf("%i\t", arr[i]);
    printf("\n\n");
  }
}
```