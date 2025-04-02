# Práctica 5

Lista simplemente enlazada: agregar al inicio, al final, mostrar y buscar nodos

``` cpp
// Baez Pacheco Jonathan Leon

# include <stdio.h>
# include <iostream>

struct ALUMNO {
  int boleta;
  char nombre[15];
  float promedio;
  ALUMNO *sig;
};

typedef ALUMNO *apunodo;
apunodo inicial, actual, aux;

int menu = 1;
int opcion = 0;
int dato = 0;

int main(void) {
  inicial = NULL;
  actual = NULL;
  aux = NULL;

  while(menu == 1) {
    printf("\n Lista de alumnos simplemente ligada\n");
    printf("    1 Insertar nodo al inicio\n");
    printf("    2 Insertar nodo al final\n");
    printf("    3 Mostrar todos los nodos\n");
    printf("    4 Buscar valor por boleta\n");
    printf("    5 Salir\n");
    printf("    Elija una opcion: ");
    scanf("%i", &opcion);

    switch(opcion) {
      case 1:
        aux = new ALUMNO;

        if (aux == NULL) {
          printf(" No hay mas espacio en memoria.\n");
          break;
        }
        printf("\n    Inserte boleta del alumno: ");
        scanf("%i", &aux->boleta);
        printf("    Inserte nombre del alumno: ");
        scanf("%s", aux->nombre);
        printf("    Inserte promedio del alumno: ");
        scanf("%f", &aux->promedio);
        aux->sig = NULL;

        if (inicial == NULL) {
          inicial = aux;
          actual = aux;
          break;
        }
        aux->sig = inicial;
        inicial = aux;
        break;

      case 2:
        aux = new ALUMNO;

        if (aux == NULL) {
          printf(" No hay mas espacio en memoria.\n");
          break;
        }
        printf("\n    Inserte boleta del alumno: ");
        scanf("%i", &aux->boleta);
        printf("    Inserte nombre del alumno: ");
        scanf("%s", aux->nombre);
        printf("    Inserte promedio del alumno: ");
        scanf("%f", &aux->promedio);
        aux->sig = NULL;

        if (inicial == NULL) {
          inicial = aux;
          actual = aux;
          break;
        }
        actual->sig = aux;
        actual = aux;
        break;

      case 3:
        if (inicial == NULL) {
          printf(" La lista esta vacia\n");
          break;
        }

        aux = inicial;
        printf("\n %-12s %-12s %s \n", "BOLETA", "NOMBRE", "PROMEDIO");
        while (aux->sig != NULL) {
          printf(" %-12i %-12s %.1f\n", aux->boleta, aux->nombre, aux->promedio);
          aux = aux->sig;
        }
        printf(" %-12i %-12s %.1f\n", aux->boleta, aux->nombre, aux->promedio);
        break;
      
      case 4:
        if (inicial == NULL) {
          printf(" La lista esta vacia\n");
          break;
        }
        printf("\n Boleta que quiere buscar: ");
        scanf("%i", &dato);
        aux = inicial;
        while ((dato != aux->boleta) && (aux->sig != NULL)) {
          aux = aux->sig;
        }
        if (dato != aux->boleta) {
          printf("\n No se encontro el alumno.\n");
          break;
        }
        else {
          printf("\n %-12s %-12s %s \n", "BOLETA", "NOMBRE", "PROMEDIO");
          printf(" %-12i %-12s %.1f\n", aux->boleta, aux->nombre, aux->promedio);
        }
        break;

      case 5:
        menu = 0;
        break;

      default:
        break;
    }
  }
}
```