# Trabajo Parcial Complejidad Algoritmica

Integrantes: 

• Ramos Terrones, Breydi U201916864

• Fuentes Ortiz, Omar U20181A993

• Ramirez Zarate, Denilson Nider - U201824021

## Introducción
El Problema del Traveling Salesman 
Para este trabajo hemos hecho uso de algoritmos para la graficación y recorridos de grafos con la finalidad de poder mostrar cual sería la ruta óptima.El Problema del vendedor viajero o problema del agente viajero (TSP por sus siglas en inglés) es uno de los problemas más estudiados en matemáticas computacionales,este responde a la siguiente pregunta: dada una lista de ciudades y las distancias entre cada par de ellas, ¿cuál es la ruta más corta posible que visita cada ciudad exactamente una vez y al finalizar regresa a la ciudad origen? Este es un problema difícil dentro en la optimización combinatoria, muy importante en la investigación de operaciones y en la ciencia de la computación. 

### TSP - Travelling Salesman Problem
Entre estos problemas de complejidad NP, se encuentra el problema del vendedor viajero (TSP, por sus siglas en ingles). Dada una colección de ciudades y las distancias entre sus conexiones (costo), el  problema consiste en encontrar un camino que recorra todas las ciudades una única vez y regrese al punto inicial con la menor distancia posible.
![enter image description here](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/Aco_TSP.svg/600px-Aco_TSP.svg.png)
Fuente: [Wikipedia - Travelling salesman problem](https://en.wikipedia.org/wiki/Travelling_salesman_problem)

## Objetivos

• Desarrollar la competencia general de razonamiento cuantitativo y la competencia específica de uso de técnicas y herramientas acorde a los objetivos del curso.

• Desarrollar un algoritmo que permita resolver completa o parcialmente el problema del vendedor viajero.

• Determinar la importancia de la aplicación de algoritmos eficientes a la hora de resolver un problema.

• Analizar la eficiencia y complejidad de los algoritmos planteados.

## Marco Teorico

### Algoritmo de Prim


El resultado de ejecutar el algoritmo de Prim es un arbol de expansion minima, dado un grafo no dirigido y conexo, es decir encuentra un subconjunto de las aristas que formen un arbol que incluya los vertices del grafo inicial, donde el peso total de las aristas es la minima posible.

##### Funcionamiento

1. Se marca un vértice cualquiera. Será el vértice de partida.
2. Se selecciona la arista de menor peso incidente en el vértice seleccionado anteriormente y se selecciona el otro vértice en el que     incide dicha arista.
3. Repetir el paso 2 siempre que la arista elegida enlace un vértice seleccionado y otro que no lo esté. Es decir, siempre que la arista elegida no cree ningún ciclo.
4. El árbol de expansión mínima será encontrado cuando hayan sido seleccionados todos los vértices del grafo.


#### Complejidad

El bucle principal se. ejecuta n- 1 veces, en cada iteración cada bucle interior toma O(n), por lo tanto el tiempo de ejecución del algoritmo de PRIM toma O(n^2 ) . 

## Experimentación

### Solución Aplicando algoritmo de Prim

Para esta solución utilizaremos el algoritmo de Prim para hallar árboles de expansión mínima. En primer lugar, se obtendrán los datos de todos los centros poblados desde un archivo con extensión csv. Para ello definimos el siguiente modelo:
```python 
	url="https://raw.githubusercontent.com/lmcanavals/algorithmic_complexity/main/data/poblaciones.csv"
	poblacionesDF = pd.read_csv(url)
```
Luego se creó un árbol que contenga tanto los pesos entre todos los nodos contra todos los nodos, como los centros poblados tanto de distritos como de provincias:
```python 
	G = nx.Graph()
col = 'CENTRO POBLADO'

for i, cp1 in pro.iterrows():
  for j, cp2 in pro.iterrows():
    if cp1[col] != cp2[col]:
      G.add_edge(cp1[col], cp2[col], weight=dist(cp1, cp2))
```

