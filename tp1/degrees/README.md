# Documentación para el código de "degrees.py"

Este archivo es una implementación de un programa llamado "degrees.py" que calcula el grado de separación entre dos actores o actrices de la industria cinematográfica utilizando el conjunto de datos de películas de IMDb. El programa está escrito en Python y utiliza archivos CSV para cargar y analizar datos de personas, películas y sus relaciones.

## Archivos de set de datos
- people.csv: Contiene información sobre personas, incluyendo su nombre, fecha de nacimiento y las películas en las que participaron.
- movies.csv: Contiene información sobre películas, incluyendo el título y el año de lanzamiento.
- stars.csv: Relaciona personas con las películas en las que participaron.

## Uso
Para ejecutar el programa, use el siguiente comando en su terminal:

```
python degrees.py [directory]
```

- `[directory]` (opcional): El directorio que contiene los archivos CSV. Si no se proporciona, se utilizará el directorio "large" por defecto.

## Funcionalidad
El programa "degrees.py" proporciona las siguientes funciones:

1. **load_data(directory):** Carga los datos de los archivos CSV en la memoria. Esto incluye cargar información sobre personas, películas y las relaciones entre ellas.

2. **shortest_path(source, target):** Encuentra el grado de separación más corto entre dos personas (source y target) en términos de las películas en las que han participado. Devuelve una lista de películas y personas que conectan a las dos personas.

3. **person_id_for_name(name):** Devuelve el ID de IMDb de una persona basándose en su nombre. En caso de ambigüedad, permite al usuario seleccionar el ID correcto.

4. **neighbors_for_person(person_id):** Obtiene las películas y las personas con las que una persona dada ha trabajado en el pasado.

## Ejecución
Al ejecutar el programa, primero se cargan los datos desde los archivos CSV. Luego, el programa le pedirá que ingrese el nombre de las dos personas de las que desea calcular el grado de separación. Después de calcular el resultado, mostrará el grado de separación y las películas en las que las dos personas han trabajado juntas.