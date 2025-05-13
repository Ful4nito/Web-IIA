
# Posible practica 8

``` cpp
// Baez Pacheco Jonathan Leon  

# include <stdio.h>

struct NODO {
  int valor;
  NODO *sig;
};

NODO *tope, *aux;

int opcion = 0;
int menu = 1;
int dato = 0;

int main () {
  tope = NULL;
  aux = NULL;

  printf("\n  Pila simplemente enlazada");
  printf("\n  |  1 Agregar Nodo       |");
  printf("\n  |  2 Extraer Nodo       |");
  printf("\n  |  3 Mostrar Tope       |");
  printf("\n  |  4 SALIR              |");
  printf("\n  =========================");

  while (menu == 1) {
    printf("\n   Opcion >>> ");
    scanf("%i", &opcion);

    switch (opcion) {
      case 1:
        aux = new NODO;
        if (aux != NULL) {
          printf("   Inserte valor: ");
          scanf("%i", &aux->valor);
          if (tope == NULL) {
            aux->sig = NULL;
          }
          else {
            aux->sig = tope;
          }
          tope = aux;
        }
        else {
          printf("   ! No hay seficiente espacio en memoria");
        }
        break;
          
      case 2:
        if (tope != NULL) {
          aux = tope;
          printf("   Nodo %i eliminado\n", aux->valor);
          tope = tope->sig;
          delete(aux);
        }
        else {
          printf("   ! La lista esta vacia\n");
        }
        break;
        
      case 3:
        if (tope != NULL) {
          printf("   El tope es: %i\n", tope->valor);
        }
        else {
          printf("   ! La lista esta vacia\n");
        }
        break;
        
      case 4:
        printf("   Finalizado.\n\n");
        menu = 0;
        break;

      default:
        printf("   ! Opcion no valida\n");
        break;
    }
  }

}

```
