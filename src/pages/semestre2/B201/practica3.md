# Practica 3

Lista de objetos simplemente enlazada

El usuario no ingresa datos

``` cpp
// Baez Pacheco Jonathan Leon   

# include <stdio.h>
# include <iostream>

struct NODO {
  int valor;
  NODO* sig;
};

int main(void) {
  NODO *inicial, *actual;

  inicial = new(NODO);
  inicial->valor = 5;
  inicial->sig = new(NODO);

  actual = inicial->sig;
  actual->valor = 10;
  actual->sig = new(NODO);
  
  actual = actual->sig;
  actual->valor = 15;
  actual->sig = NULL;

  actual = inicial;

  while(actual->sig != NULL) {
    printf(" %i\n", actual->valor);
    actual = actual->sig;
  }
  printf(" %i\n", actual->valor);

}
```