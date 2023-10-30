# Documentación para el código de Buscaminas

## Clase `Minesweeper`

La clase `Minesweeper` representa el juego de Buscaminas. Permite inicializar un nuevo juego y realizar operaciones sobre él.

### Métodos y atributos

#### `__init__(self, height=8, width=8, mines=8)`

- Inicializa un nuevo juego de Buscaminas con las dimensiones dadas.
- Parámetros:
  - `height` (int): Altura del tablero.
  - `width` (int): Ancho del tablero.
  - `mines` (int): Número de minas en el tablero.

#### `print(self)`

- Imprime una representación del juego en texto mostrando las minas en el tablero.

#### `is_mine(self, cell)`

- Comprueba si una celda dada contiene una mina.
- Parámetros:
  - `cell` (tuple): Coordenadas (fila, columna) de la celda.
- Devuelve `True` si la celda contiene una mina, `False` en caso contrario.

#### `nearby_mines(self, cell)`

- Devuelve el número de minas adyacentes a una celda dada, sin incluir la celda en sí.
- Parámetros:
  - `cell` (tuple): Coordenadas (fila, columna) de la celda.
- Devuelve un entero que representa el número de minas adyacentes a la celda.

#### `won(self)`

- Comprueba si se han encontrado todas las minas en el tablero.
- Devuelve `True` si se han encontrado todas las minas, `False` en caso contrario.

## Clase `Sentence`

La clase `Sentence` representa una sentencia lógica sobre el juego del Buscaminas. Una sentencia consta de un conjunto de celdas del tablero y el número de minas en esas celdas.

### Métodos y atributos

#### `__init__(self, cells, count)`

- Inicializa una nueva sentencia con el conjunto de celdas y el número de minas.
- Parámetros:
  - `cells` (set): Conjunto de coordenadas de celdas del tablero.
  - `count` (int): Número de minas en las celdas dadas.

#### `known_mines(self)`

- Devuelve el conjunto de todas las celdas en la sentencia que se sabe que son minas.
- Devuelve un conjunto de celdas conocidas como minas.

#### `known_safes(self)`

- Devuelve el conjunto de todas las celdas en la sentencia que se sabe que son seguras.
- Devuelve un conjunto de celdas conocidas como seguras.

#### `mark_mine(self, cell)`

- Actualiza la representación interna del conocimiento dado que se puede afirmar que una celda es una mina.
- Parámetros:
  - `cell` (tuple): Coordenadas (fila, columna) de la celda conocida como mina.

#### `mark_safe(self, cell)`

- Actualiza la representación interna del conocimiento dado que se puede afirmar que una celda es segura.
- Parámetros:
  - `cell` (tuple): Coordenadas (fila, columna) de la celda conocida como segura.

## Clase `MinesweeperAI`

La clase `MinesweeperAI` representa una IA que puede jugar al Buscaminas.

### Métodos y atributos

#### `__init__(self, height=8, width=8)`

- Inicializa la IA jugadora de Buscaminas.
- Parámetros:
  - `height` (int): Altura del tablero.
  - `width` (int): Ancho del tablero.

#### `mark_mine(self, cell)`

- Marca una celda como mina y actualiza todo el conocimiento.
- Parámetros:
  - `cell` (tuple): Coordenadas (fila, columna) de la celda conocida como mina.

#### `mark_safe(self, cell)`

- Marca una celda como segura y actualiza todo el conocimiento.
- Parámetros:
  - `cell` (tuple): Coordenadas (fila, columna) de la celda conocida como segura.

#### `add_knowledge(self, cell, count)`

- Se llama cuando el tablero del Buscaminas indica cuántas celdas vecinas tienen minas para una celda segura determinada.
- Realiza las siguientes tareas:
  1. Marca la celda como un movimiento que se ha realizado.
  2. Marca la celda como segura.
  3. Agrega una nueva sentencia a la base de conocimientos de la IA basada en el valor de "cell" y "count."
  4. Marca celdas adicionales como seguras o como minas si se puede concluir basándose en la base de conocimientos de la IA.
  5. Agrega nuevas oraciones a la base de conocimientos de la IA si pueden inferirse del conocimiento existente.

#### `make_safe_move(self)`

- Devuelve una celda segura para elegir en el tablero del Buscaminas.
- Devuelve las coordenadas de la celda segura o `None` si no hay celdas seguras disponibles.

#### `make_random_move(self)`

- Devuelve un movimiento aleatorio para hacer en el tablero del Buscaminas.
- Devuelve las coordenadas del movimiento aleatorio o `None` si no hay movimientos posibles.