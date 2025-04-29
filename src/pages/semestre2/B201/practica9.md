# Practica 9

``` cpp
// Baez Pacheco Jonathan Leon 

# include <stdio.h>
# include <iostream>

struct nodo {
  int valor;
  nodo *sig;
};

typedef nodo *apu_nodo;

apu_nodo salida, entrada, aux;

int opcion = 0;
int menu = 1;

int main (void) {
  salida = NULL;
  entrada = NULL;
  aux = NULL;

  printf("\n  ===== Cola dinamica =====");
  printf("\n  |  1 Agregar            |");
  printf("\n  |  2 Mostrar            |");
  printf("\n  |  3 Extraer o Borrar   |");
  printf("\n  |  4 SALIR              |");
  printf("\n  =========================");

  while (menu == 1) {   
    printf("\n  Elija una opcion >> ");
    scanf("%i", &opcion);
    switch (opcion) {
      case 1:
        aux = new nodo;
        if(aux != NULL) {
          printf("  Inserte valor: ");
          scanf("%i", &aux->valor);
          if (entrada == NULL) {
            aux->sig = NULL;
            entrada = aux;
            salida = aux;
          }
          else {
            entrada->sig = aux;
            aux->sig = NULL;
            entrada = aux;
          }
        }
        break;
      
      case 2:
        if (salida == NULL) {
          printf("  ! La cola esta vacia.\n");
        }
        else {
          printf("  Valor de Salida: %i\n", salida->valor);
        }
        break;
      
      case 3:
        if (salida == NULL) {
          printf("  ! La cola esta vacia.\n");
        }
        else if (entrada == salida) {
          printf("  Valor %i eliminado\n", salida->valor);
          delete (salida);
          entrada = NULL;
          salida = NULL;
        }
        else {
          aux = salida;
          printf("  Valor %i eliminado\n", aux->valor);
          salida = salida->sig;
          delete (aux);
          aux = NULL;
        }
        break;
      
      case 4:
        menu = 0;
        break;
      
      default:
        break;
    }
  }
}
```