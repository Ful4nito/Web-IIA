
# Practicas

## Practica 1

Ordenamiento Burbuja de números generados aleatoriamente 180225

Un programa que pide al usuario cuantos números aleatorios desea generar, estos estarán en el rango de 0 a 100, posteriormente serán ordenados con el método _burbuja_ aplicando solamente una iteración.

``` c
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

## Practica 2

Objeto con datos ingresados por el usuario  250225

Genere un programa que pida al usuario que inserte los datos de un alumno tales como Nombre completo, Boleta y grupo, estos deberán ser almacenados en un objeto, puede ser utilizando _class_ ó _struct_ , después mostrar los datos del alumno en pantalla.

``` c
// Baez Pacheco Jonatha Leon

# include <stdio.h>
# include <stdlib.h>

class ALUMNO {
 char nombre[30];
int boleta;
 char grupo[5];
} Alumno;

int main(void) {
 printf("Inserte nombre del alumno: ");
 scanf("%[^\n]s", Alumno.nombre);
 printf("Boleta: ");
 scanf("%i", &Alumno.boleta);
 printf("Greupo: ");
 scanf("%s", Alumno.grupo);
 
 printf(" 1  %-30s", Alumno.nombre);
 printf("%-11i ", Alumno.boleta, );
 printf("%-5s\n", Alumno.grupo);
}
```

## Practica 3

``` c
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

## Practica 4

``` c
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

## Practica 5

``` c
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
