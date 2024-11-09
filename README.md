# Taller Paradigma Logico
## Ejercicio 1: Base de Hechos y Reglas
```prolog


% Hechos
padre(john, mary).
padre(mary, susan).
padre(peter, susan).
padre(susan, ann).
padre(john, michael). % Nuevo hecho
padre(michael, tom). % Nuevo hecho
padre(mary, james). % Nuevo hecho

% Reglas
abuelo(X, Y) :- padre(X, Z), padre(Z, Y).
hermano(X, Y) :- padre(Z, X), padre(Z, Y), X \= Y.
tio(X, Y) :- hermano(X, Z), padre(Z, Y).
```

## Ejercicio 2: Consultas en Prolog



 1. ¿Quién es abuelo de Ann?
- abuelo(X, ann).
 Resultado:
 X = john.

 2. ¿Quiénes son los hermanos de Susan?
- hermano(X, susan).
 Resultado:
 X = mary.

 3. ¿Mary es madre de quién?
- padre(mary, Y).
 Resultado:
 Y = susan;
 Y = james.
## Ejercicio 3:
```prolog

% Hechos
animal(tigre).       
animal(aguila).      
animal(tiburon).     
animal(cocodrilo).  
animal(loro).      
animal(delfin).    

mamifero(tigre).     
mamifero(delfin).    

ave(aguila).        
ave(loro).         

pez(tiburon).       

reptil(cocodrilo). 

% Reglas
puede_volar(X) :- ave(X).                              % Los animales que son aves pueden volar
puede_nadar(X) :- pez(X); mamifero(X), X \= tigre; reptil(X), X = cocodrilo.  % Pueden nadar los peces, algunos mamíferos (excepto el tigre), y los cocodrilos

% Consultas de ejemplo:
% ¿Qué animales pueden volar?
% ?- puede_volar(X).

% ¿Qué animales pueden nadar?
% ?- puede_nadar(X).
```


## Consultas y resultados

Animales que pueden volar
- puede_volar(X).
 Resultados:
 X = aguila ;
 X = loro.

 Animales que pueden nadar
- puede_nadar(X).
 Resultados:
 X = tiburon ;
 X = delfin ;
 X = cocodrilo.

## Ejercicio 4

### Definición del Problema
### Área de interés: 
Zoología <br>
### Problema: 
Crear una base de hechos y reglas para identificar qué animales son herbívoros, carnívoros o omnívoros. Además, queremos saber qué tipo de alimento consume cada animal.

```prolog
% Hechos
animal(elefante).
animal(leon).
animal(oso).
animal(conejo).

dieta(elefante, herbivoro).
dieta(leon, carnivoro).
dieta(oso, omnivoro).
dieta(conejo, herbivoro).

come(elefante, plantas).
come(leon, carne).
come(oso, plantas).
come(oso, carne).
come(conejo, plantas).

% Reglas
% Regla para determinar si un animal es herbívoro
es_herbivoro(X) :- dieta(X, herbivoro).

% Regla para determinar si un animal es carnívoro
es_carnivoro(X) :- dieta(X, carnivoro).

% Regla para determinar si un animal es omnívoro
es_omnivoro(X) :- dieta(X, omnivoro).
```
### Consultas y resultados

Consulta para saber si un animal es herbívoro
- es_herbivoro(elefante).
 Resultado:
 true.

Consulta para saber qué animal es carnívoro
- es_carnivoro(X).
 Resultado:
 X = leon.

 Consulta para saber qué come un oso
- come(oso, Y).
 Resultado:
 Y = plantas ;
 Y = carne.
