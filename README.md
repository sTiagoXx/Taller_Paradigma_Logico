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
## Ejercicio 2:
```prolog

% Hechos
animal(tigre).       % Tigre
animal(aguila).      % Águila
animal(tiburon).     % Tiburón
animal(cocodrilo).   % Cocodrilo
animal(loro).        % Loro
animal(delfin).      % Delfín

mamifero(tigre).     % Tigre es un mamífero
mamifero(delfin).    % Delfín es un mamífero

ave(aguila).         % Águila es un ave
ave(loro).           % Loro es un ave

pez(tiburon).        % Tiburón es un pez

reptil(cocodrilo).   % Cocodrilo es un reptil

% Reglas
puede_volar(X) :- ave(X).                              % Los animales que son aves pueden volar
puede_nadar(X) :- pez(X); mamifero(X), X \= tigre; reptil(X), X = cocodrilo.  % Pueden nadar los peces, algunos mamíferos (excepto el tigre), y los cocodrilos

% Consultas de ejemplo:
% ¿Qué animales pueden volar?
% ?- puede_volar(X).

% ¿Qué animales pueden nadar?
% ?- puede_nadar(X).
```
