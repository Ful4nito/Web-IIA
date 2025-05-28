# Practica 11

## Arboles binarios

Instrucciones: Crear un Arbol Binario dentro del codigo, despues realizar los reccorridos e imprimir los valores de preorden, inorden, postorden, y por niveles

``` cpp
// Baez Pacheco Jonathan Leon 

# include <stdio.h>
# include <stdlib.h>

struct nodo {
  int valor;
  nodo *izq, *der;
};

typedef nodo *apu_nodo;
apu_nodo raiz, aux, actual;

void preorden(nodo *actual);
void postorden(nodo *actual);
void inorden(nodo *actual);

//          21      
//       /      \
//      14       9   
//     / \      / \
//    N   7    3   6
//       / \  / \ / \
//       N N  N N N N 

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

  actual = raiz;

  printf("\n Preorden  > ");
  preorden(raiz);

  printf("\n Postorden > ");
  postorden(raiz);

  printf("\n Inorden   > ");
  inorden(raiz);
}

void preorden (nodo *actual) {
  if(actual != NULL) {
    printf(" %d", actual->valor);
    preorden(actual->izq);
    preorden(actual->der);
  }
}

void inorden (nodo *actual) {
  if(actual != NULL) {
    inorden(actual->izq);
    printf(" %d", actual->valor);
    inorden(actual->der);
  }
}

void postorden (nodo *actual) {
  if(actual != NULL) {
    postorden(actual->izq);
    postorden(actual->der);
    printf(" %d", actual->valor);
  }
}
```
