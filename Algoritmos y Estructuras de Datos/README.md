16/09/2021
# Algoritmos y Estructuras de Datos
Los algoritmos y las estructuras de datos forman parte de la preparación elemental de un ingeniero en sistemas computacionales, estas dos materias, cuando las curse durante la carrera, me parecieron sumamente interesantes, aun así, por lo que he logrado notar en algunas de las juntas o videos que he visto sobre las grandes empresas, te suelen preguntar el concepto en general de muchos de los algoritmos y estructuras de datos, sus casos de uso y en cuales no se utilizan, además de su notación, es por ello que he decidido basarme en la página **Geeks for Geeks** para hacer un resumen de los más importantes. 

Un **algoritmo** es una serie de pasos secuencial, ordenada y finita, que está diseñado para solucionar un problema. 

Una **estructura de datos** es una forma de organizar la información para manipularla, organizarla, buscar e insertar datos de manera eficiente.
## Algoritmos
### Searching and Sorting (Búsqueda y Ordenamiento):
#### Linear Search (Búsqueda Lineal)
Tomando en cuenta que tenemos un arreglo o lista enlazada de n elementos, se nos pide buscar un valor ‘a’ dentro de esta, la opción más natural es pararnos en el primer elemento de la lista (el que está más a la izquierda) e ir avanzando de uno en uno hasta llegar al elemento que estamos buscando, en el caso de que encuentre el numero, regresa el index en el que se encuentra, en el caso contrario, regresa un -1.
**Mejor Caso:** O(1)    **Peor Caso:**O(n)
La búsqueda lineal es un algoritmo muy lento, es por ello que casi no se utiliza, existen dos maneras de “mejorarlo”, la primera es preguntando si el elemento se encuentra en alguna de las orillas del arreglo (Su peor caso sería O(n-1)) y la segunda es paralelizando el algoritmo.
**El código en C es el siguiente:**
``` 
int search(int arr[], int n, int x) //arr[] es el arreglo, n es el numero de elementos en el y x es el numero que se esta buscando
{
    int i;
    for (i = 0; i < n; i++)
        if (arr[i] == x)
            return i;
    return -1;
}
```
<p align="center">
  <img src="Linear-Search.png" width="380" height="225"/>
</p>

#### Binary Search (Búsqueda Binaria)
Tomando en cuenta un **arreglo ordenado**, debemos de buscar un elemento en esté, lo primero que tenemos que hacer es dividir el arreglo en dos partes, tomando un elemento de en medio, si el que estamos buscando es menor a esté elemento seleccionado, significa que el elemento a buscar se encuentra en el grupo de la izquierda, de lo contrario, es pertenece al segundo grupo, este algoritmo se pude realizar *recursivamente* o *cíclicamente*.

Considero que es un algoritmo muy rápido de utilizar, su única desventaja es que el arreglo debe estar ya ordenado (los algoritmos de ordenamiento están más adelante), también, se puede cambiar un poco el algoritmo, para que en el caso de que el elemento se encuentre en medio, regrese inmediatamente su índice, de esta manera su complejidad podría llegar a ser *constante*
**Mejor Caso:** O(log n)    **Peor Caso:**O(n)
**El código *Recursivo* en C es el siguiente:**
``` 
int binarySearch(int arr[], int l, int r, int x)
{
    if (r >= l) {
        int mid = l + (r - l) / 2;
  
        if (arr[mid] == x)
            return mid;
  
        if (arr[mid] > x)
            return binarySearch(arr, l, mid - 1, x);
  
        return binarySearch(arr, mid + 1, r, x);
    }
    return -1;
}

//Primera llamada en el main
 int result = binarySearch(arr, 0, n - 1, x);
``` 
**El código *Recursivo* en C es el siguiente:**
``` 
int binarySearch(int arr[], int l, int r, int x)
{
    while (l <= r) {
        int m = l + (r - l) / 2;

        if (arr[m] == x)
            return m;
  
        if (arr[m] < x)
            l = m + 1;
  
        else
            r = m - 1;
    }
  
    return -1;
}
//Primera llamada en el main
int result = binarySearch(arr, 0, n - 1, x);
``` 
**Paradigma del Algoritmo:** Decrease and Conquer.
<p align="center">
  <img src="Binary-Search.png" width="380" height="225"/>
</p>