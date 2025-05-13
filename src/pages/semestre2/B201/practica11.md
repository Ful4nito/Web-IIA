# Practica 11
Arboles binarios

``` cpp
// Baez Pacheco Jonathan Leon 

# include <stdio.h>
# include <stdlib.h>
# include <iostream>

struct nodo {
  int valor;
  nodo *izq, *der;
};

typedef nodo *apu_nodo;
apu_nodo raiz, aux, actual;

int main () {
  raiz = NULL;
  aux = NULL;
  actual = NULL;

  raiz = new nodo;
  raiz->valor = 21;

  aux = new nodo;
  aux->valor = 14;
  aux->izq = NULL;
  raiz->izq = aux;
  
  aux = new nodo;
  aux->valor = 9;
  raiz->der = aux;
  
  aux = new nodo;
  aux->valor = 7;
  aux->der = NULL;
  raiz->izq->der = aux;
  
  aux = new nodo;
  aux->valor = 3;
  aux->izq = NULL;
  aux->der = NULL;
  raiz->der->izq = aux;
  
  aux = new nodo;
  aux->valor = 6;
  aux->izq = NULL;
  aux->der = NULL;
  raiz->der->der = aux;
  
  aux = new nodo;
  aux->valor = 5;
  aux->izq = NULL;
  aux->der = NULL;
  raiz->izq->der->izq = aux;
}
```
