# Práctica 6

Lista enlazada

``` cpp
// Baez Pacheco Jonathan Leon

# include <stdio.h>
# include <time.h>
# include <iostream>

struct nodo {
  int valor;
  nodo *sig;
};

typedef nodo *apunodo;
apunodo inicial, anterior, actual, aux;

int menu = 1;
int opcion = 0;
int dato = 0;
int renglon = 0;
int cambios = 0;
int n = 0;
int i = 0;

int main(void) {
  inicial = NULL;
  anterior = NULL;
  actual = NULL;
  aux = NULL;

  srand(time(NULL));

  printf("\n  Lista de alumnos simplemente ligada\n");
  printf("  |  1 Agragar nodo al inicio       |\n");
  printf("  |  2 Agregar nodo al final        |\n");
  printf("  |  3 Agregar nodo ordenadamente   |\n");
  printf("  |  4 Generar lista de n nodos     |\n");
  printf("  |  5 Mostrar todos los nodos      |\n");
  printf("  |  6 Ordenar por burbuja          |\n");
  printf("  |  7 Buscar nodo por valor        |\n");
  printf("  |  8 Eliminar nodo por valor      |\n");
  printf("  |  9 Elininar lista               |\n");
  printf("  | 10 SALIR                        |\n");
  printf("  ===================================\n");
  
  while(menu == 1) {
    printf("\n  Elige una operacion >>> ");
    scanf("%i", &opcion);

    switch(opcion) {
/* ------------------------------------------------------------------------------------- */        
      case 1: //                           <===  Agregar nodo al inicio               1
        aux = new nodo;

        if (aux == NULL) {
          printf("  No hay más espacio en memoria.\n");
          break;
        }

        printf("  Inserte el nuevo valor: ");
        scanf("%i", &aux->valor);
        aux->sig = NULL;

        if (inicial == NULL) {
          inicial = aux;
          actual = aux;
        }
        else {
          aux->sig = inicial;
          inicial = aux;
        }
        break;

/* ------------------------------------------------------------------------------------- */        
      case 2: //                           <===  Agregar nodo al final                2
        aux = new nodo;

        if (aux == NULL) {
          printf("  No hay mas espacio en memoria.\n");
          break;
        }

        printf("  Inserte el nuevo valor: ");
        scanf("%i", &aux->valor);
        aux->sig = NULL;

        if (inicial == NULL) {
          inicial = aux;
          actual = aux;
        }
        else {
          actual = inicial;
          
          while (actual->sig != NULL) {
            actual = actual->sig;
          }
          actual->sig = aux;
          actual = aux;
        }
        break;

/* ------------------------------------------------------------------------------------- */        
      case 3: //                           <===  Agregar nodo ordenadamente           3       
        aux = new nodo;

        if (aux == NULL) {
          printf("  No hay mas espacio en memoria.\n");
          break;
        }

        printf("  Inserte el nuevo valor: ");
        scanf("%i", &aux->valor);
        aux->sig = NULL;

        if (inicial == NULL) {
          inicial = aux;
          actual = aux;
        }
        else {
          actual = inicial;

          if (aux->valor < actual->valor) {
            aux->sig = actual;
            inicial = aux;
          }
          else {
            while (actual->valor <= aux->valor && actual->sig != NULL) {
              anterior = actual;
              actual = actual->sig;
            }

            if (actual->valor > aux->valor) {
              aux->sig = actual;
              anterior->sig = aux;
            }
            else {
              actual->sig = aux;
            }
          }  
        }  
        break;

/* ------------------------------------------------------------------------------------- */        
      case 4: //                           <===  Generar lista de numeros aleatorios  4
          printf("  Cuantos nodos: ");
          scanf("%i", &n);

          for (i=0; i < n; i++) {
            aux = new nodo;
            aux->valor = rand() % 101;
            aux->sig = NULL;

            if (inicial == NULL) {
              inicial = aux;
            }
            else {
              actual = inicial;
              while (actual->sig != NULL) {
                actual = actual->sig;  
              }
              actual->sig = aux;
            }
          }
        break;

/* ------------------------------------------------------------------------------------- */        
      case 5: //                           <===  Mostrar lista de nodos               5     
        if (inicial == NULL) {
          printf("  La lista esta vacia.\n");
          break;
        }

        printf("\n");
        for (renglon = 0; renglon < 5; renglon ++) {
          aux = inicial;
          while (aux->sig != NULL) {
            if (renglon == 0 || renglon == 4) {
              printf(" ========    ");
            }
            else if (renglon == 1 || renglon == 3) {
              printf(" |      |    ");
            }
            else {
              printf(" |  %-3i | ==>", aux->valor);
            }
            aux = aux->sig;
          }
          if (renglon == 0 || renglon == 4) {
            printf(" ========\n");
          }
          else if (renglon == 1 || renglon == 3) {
            printf(" |      |\n");
          }
          else {
            printf(" |  %-3i |\n", aux->valor);
          }
        }  
        printf("\n");
        break;
      
/* ------------------------------------------------------------------------------------- */        
      case 6: //                          <===  Ordenamiento burbuja                  6 
        if (inicial == NULL) {
          printf("  La lista esta vacia. \n");
          printf("  No hay numeros que ordenar.\n");
          break;
        }
        else if (inicial->sig == NULL){
          break;
        }

        cambios = 1;
        printf("  Ordenando ...\n  ");

        while (cambios == 1) {
          cambios = 0;
          aux = inicial;
          actual = inicial->sig;

          while (actual != NULL ) {
            if (aux->valor > actual->valor) {
              cambios = 1;
              aux->sig = actual->sig; // Reenlazar nodos
              actual->sig = aux;      // inicio en intermedio

              if (aux == inicial) {
                inicial = actual;
              }
              else {
                anterior->sig = actual;
              }
              
              anterior = actual;
              actual = aux->sig;
            }
            else { // Avanzar nodos 
              anterior = aux;
              aux = actual;
              actual = actual->sig;
            }
          }
        }
        printf("  Nodos ordenados exitosamente\n");
        break;

/* ------------------------------------------------------------------------------------- */        
      case 7: //                           <===  Buscar nodo y mostrar ubicacion      7
        if (inicial == NULL) {
          printf("  La lista esta vacia.\n");
          break;
        }

        printf("  Inserte valor a buscar: ");
        scanf("%i", &dato);
        aux = inicial;
        while ((dato != aux->valor) && (aux->sig != NULL)) {
          aux = aux->sig;
        }

        if (dato != aux->valor) {
          printf("  No se encontro el nodo con valor %i\n", dato);
          break;
        }
        else {
          printf("  La ubicacion del nodo es %p\n", aux);
        }
        break;

/* ------------------------------------------------------------------------------------- */        
      case 8: //                           <===  Eliminar nodo dada una condicion     8
        if (inicial == NULL) {
          printf("  La lista esta vacia.\n");
          break;
        }

        printf("  Inserte valor a eliminar: ");
        scanf("%i", &dato);
        
        actual = inicial;
        anterior = inicial;

        while (actual->sig != NULL) {
          if (inicial == actual) { 
            if (actual->valor == dato) { // Condicion 
              inicial = inicial->sig;
              actual = inicial;
              delete(anterior);
            }
            else {
              actual = actual->sig;
            }
          }
          else if (actual->valor == dato) { // Condicion
            anterior->sig = actual->sig;
            delete(actual);
            actual = anterior->sig;
          }
          else {
            actual = actual->sig;
            anterior = anterior->sig;
          }
        }
        if (actual->valor == dato) { // Condicion
          anterior->sig = NULL;
          delete(actual);
        }
        break;

/* ------------------------------------------------------------------------------------- */        
      case 9: //                           <===  Eliminar todos los nodos             9 
        if (inicial == NULL) {
          printf("  La lista esta vacia.\n");
          break;
        }

        aux = inicial;
        while (inicial->sig != NULL) {
          inicial = inicial->sig;
          delete(aux);
          aux = inicial;
        }
        delete(aux);
        inicial = NULL;
        printf("  Nodos eliminados.\n");

        break;

/* ------------------------------------------------------------------------------------- */        
      case 10: //                          <===  SALIR                               10 
        menu = 0;
        break;

/* ------------------------------------------------------------------------------------- */        
      default:
        printf("  Opcion no valida. \n");
        break;
    }
  }
}
```