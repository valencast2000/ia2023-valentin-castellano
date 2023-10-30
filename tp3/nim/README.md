# Juego de Nim con Aprendizaje por Refuerzo

Este proyecto implementa un juego de Nim y una inteligencia artificial (IA) que aprende a jugar al Nim utilizando el algoritmo de aprendizaje por refuerzo conocido como Q-learning.

## Introducción

El juego de Nim es un juego de estrategia en el que dos jugadores se turnan para eliminar objetos de pilas. El jugador que elimina el último objeto es el perdedor. El objetivo de este proyecto es entrenar a la IA para que aprenda a jugar al Nim de manera óptima y tome decisiones inteligentes.

## Estructura del Código

El código se divide en dos clases principales: `Nim` y `NimAI`.

### Clase `Nim`

#### `__init__(self, initial=[1, 3, 5, 7])`
- Esta función inicializa el juego de Nim. Se toma una lista `initial` como argumento que representa la cantidad de objetos en cada pila al comienzo del juego. Por defecto, se inicia con [1, 3, 5, 7]. Es decir, 4 pilas, donde cada valor representa los elementos de esa pila.
- La función inicializa las pilas, el jugador actual (0 o 1) y al ganador (inicialmente `None`).

#### `available_actions(cls, piles)`
- Método de clase que toma una lista `piles` como entrada y devuelve todas las acciones disponibles `(i, j)` en ese estado. Las acciones representan quitar `j` elementos de la pila `i`.
- Itera sobre todas las pilas y las combinaciones posibles de objetos que se pueden quitar de esas pilas.

#### `other_player(cls, player)`
- Método de clase que toma un jugador (0 o 1) como entrada y devuelve el otro jugador. Es una forma de alternar entre los dos jugadores.

#### `switch_player(self)`
- Cambia el jugador actual al otro jugador. Se utiliza después de que un jugador realiza un movimiento.

#### `move(self, action)`
- Realiza un movimiento en el juego. El argumento `action` es una tupla `(i, j)` que representa quitar `j` objetos de la pila `i`.
- La función verifica si el movimiento es válido y actualiza el estado del juego.
- Comprueba si hay un ganador después de realizar el movimiento.

### Clase `NimAI`

#### `__init__(self, alpha=0.5, epsilon=0.1)`
- Inicializa la IA para el juego de Nim. Puede tomar dos argumentos opcionales: `alpha` es la tasa de aprendizaje, y `epsilon` controla la exploración frente a la explotación.

#### `update(self, old_state, action, new_state, reward)`
- Actualiza el modelo de aprendizaje por refuerzo de la IA después de un movimiento. Utiliza la fórmula de Q-learning para actualizar los valores Q.
- Toma el estado anterior `old_state`, la acción realizada, el nuevo estado `new_state`, y la recompensa recibida por el movimiento.

#### `get_q_value(self, state, action)`
- Devuelve el valor Q para un estado y una acción dados. Si no existe un valor Q para el par estado/acción en el diccionario `self.q`, devuelve 0.

#### `update_q_value(self, state, action, old_q, reward, future_rewards)`
- Actualiza el valor Q para un estado y una acción dados utilizando la fórmula de Q-learning. Toma el valor Q anterior, la recompensa actual y una estimación de las recompensas futuras.
- Utiliza la tasa de aprendizaje `alpha` para actualizar el valor Q.

#### `best_future_reward(self, state)`
- Calcula la mejor recompensa futura posible para un estado dado considerando todas las acciones disponibles. Devuelve el valor Q más alto entre las acciones posibles.
- Si no hay acciones disponibles en el estado, devuelve 0.

#### `choose_action(self, state, epsilon=True)`
- Elige una acción para un estado dado. Si `epsilon` es `True`, la IA sigue una estrategia de exploración y puede elegir una acción aleatoria con probabilidad `epsilon` o la mejor acción con probabilidad `1 - epsilon`.
- Si `epsilon` es `False`, la IA elige siempre la mejor acción disponible según los valores Q.

## Uso

Para entrenar a la IA, simplemente llama a la función `train(n)` con el número deseado de partidas de entrenamiento. Una vez entrenada, puedes utilizar la función `play` para jugar contra la IA.

```python
ai = train(10000)  # Entrenar con 10,000 partidas
play(ai, human_player=0)  # Jugar contra la IA, con el humano como primer jugador
