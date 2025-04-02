# Práctica 4

Lista simplemente enlazada: agregar al final y mostrar objetos 

Los datos de la estructura seran ingresados por el usuario

``` cpp
// Baez Pacheco Jonathan Leon 

# include <stdio.h>
# include <iostream>

struct nodo {
  int valor;
  nodo *sig;
};

typedef nodo *apunodo;

apunodo inicial, aux, actual;

int menu = 1;
int opcion = 0;
int i = 0;

int main() {
  inicial = NULL;
  aux = NULL;
  actual = NULL;
  
  while (menu == 1) {
    printf("\n Lista simplemente ligada\n");
    printf("   1 Agregar nodo\n");
    printf("   2 Mostrar lista\n");
    printf("   3 Salir\n");
    printf("   Que opcion queres: ");
    scanf("%i", &opcion);
    
    switch (opcion) {
      case 1:
        aux = new nodo;
        if (aux == NULL) {
          printf("  No hay mas espacio en la memoria.\n");
          break;
        }
        printf("   Inserte valor: ");
        scanf("%i", &aux->valor);
        aux->sig = NULL; 

        if (inicial == NULL) {
          inicial = aux;
          actual = aux;
          break;
        }
        actual->sig = aux;
        actual = aux;

        break;
      case 2:
        aux = inicial;
        if (aux == NULL) {
          printf("\n La lista esta vacia.\n");
          break;
        }
        
        i = 0;
        while (aux->sig != NULL) {
          printf("\n Nodo %-4i Valor %i", i+1, aux->valor);
          aux = aux->sig;
          i += 1;
        }
        printf("\n Nodo %-4i Valor %i\n", i+1, aux->valor);

        break;
      case 3:
        menu = 0;
        break;
      default:
        break;
    }
  }
}
```