#include <iostream>
using namespace std;

struct Nodo {
    int valor;
    Nodo* izq;
    Nodo* der;
    Nodo(int v) : valor(v), izq(nullptr), der(nullptr) {}
};

void imprimirInOrden(Nodo* nodo) {
    if (nodo == nullptr) return;
    imprimirInOrden(nodo->izq);
    cout << nodo->valor << " ";
    imprimirInOrden(nodo->der);
}

int main() {
    Nodo* raiz = new Nodo(10);          // Nodo Raíz
    raiz->izq = new Nodo(5);            // Hijo izquierdo
    raiz->der = new Nodo(15);           // Hijo derecho
    raiz->izq->izq = new Nodo(3);       // Hoja izquierda
    raiz->izq->der = new Nodo(7);       // Hoja derecha
    raiz->der->der = new Nodo(20);      // Hoja derecha

    cout << "Recorrido In-orden: ";
    imprimirInOrden(raiz);              // Salida esperada: 3 5 7 10 15 20
    cout << endl;

    return 0;
}
