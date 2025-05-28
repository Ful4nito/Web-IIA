# Practica 7

## Lista doblemente enlazada

Instrucciones:

``` cpp
// Jonathan Leon Baez Pacheco 

# include <stdio.h>
# include <iostream>

struct NODO {
  int valor;
  NODO *sig, *ant;
};

NODO *inicial, *aux, *actual;

int menu = 1;
int opcion = 0;

int main () {
  inicial = NULL;
  aux = NULL;
  actual = NULL;


  printf("\n  Lista de nodos doblemente enlazada");
  printf("\n  | 1 Agregar nodo al inicio       |");
  printf("\n  | 2 Agregar nodo al final        |");
  printf("\n  | 3 Mostrar nodos                |");
  printf("\n  | 4 SALIR                        |");
  printf("\n  ==================================");

  while (menu == 1) {
    printf("\n   Elige una opcion >>> ");
    scanf("%i", &opcion);

    switch (opcion) {
    case 1 : // INSERTAR AL INICIO
      aux = new(NODO);
      if (aux == NULL) {
        printf("   No hay mas espacio en memoria.\n");
      }
      else {
        printf("   Inserte valor: ");
        scanf("%i", &aux->valor);
      
        if (inicial == NULL) {
          inicial = aux;
          aux->sig = NULL;
          aux->ant = NULL;
        }
        else {
          aux->sig = inicial;
          aux->ant = NULL;
          inicial = aux;
        }
      }
      break;

    case 2 : // INSERTAR AL FINAL
    aux = new(NODO);
    if (aux == NULL) {
      printf("   No hay mas espacio en memoria.\n");
    }
    else {
      printf("   Inserte valor: ");
      scanf("%i", &aux->valor);
      
      if (inicial == NULL) {
        inicial = aux;
        aux->sig = NULL;
        aux->ant = NULL;
      }
      else {
        actual = inicial;
        while (actual->sig != NULL) {
          actual = actual->sig;
        }
        actual->sig = aux;
        aux->ant = actual;
        aux->sig = NULL;
      }
    }
    break;

    case 3 : // MOSTRAR NODOS
      if (inicial == NULL) {
        printf("   La lista esta vacia.\n");
        break;
      }

      printf("  ");
      actual = inicial;
      while (actual->sig != NULL) {
        printf("%3i  ", actual->valor);
        actual = actual->sig;
      }
      printf("%3i  \n", actual->valor);
      break;

    case 4 :
      menu = 0;
      break;
    
    default:
      break;
    }
  }
  
}
```