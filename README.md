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

