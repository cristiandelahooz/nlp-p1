# Análisis del Nivel Básico - MIT Restaurant Corpus

## Objetivo de la Tarea
**Puntuación máxima:** 5 puntos

### Tareas a realizar:
1. **Limpieza y preparación de los datos**
2. **Extracción de palabras clave (KPE)**
3. **Reconocimiento de entidades relevantes (NER)** con modelos heurísticos y pre-entrenados para reconocer al menos 3 tipos de entidades

## Plan de Implementación

### 1. Limpieza y preparación de los datos

#### Análisis del código actual:
- La función `read_file()` ya implementada lee el archivo en formato BIO
- Extrae solo los tokens (palabras) ignorando las etiquetas BIO
- Une los tokens en oraciones completas

#### Mejoras necesarias:
- Preservar las etiquetas BIO para análisis posterior
- Implementar limpieza adicional (eliminación de caracteres especiales, normalización)
- Crear estructuras de datos más eficientes

### 2. Extracción de palabras clave (KPE)

#### Métodos a implementar:
- **TF-IDF** para identificar términos importantes
- **Análisis de frecuencia** de términos específicos del dominio gastronómico
- **Extracción basada en patrones** usando expresiones regulares

### 3. Reconocimiento de entidades (NER)

#### Entidades objetivo (mínimo 3):
1. **LOCATION** - Ubicaciones geográficas
2. **CUISINE** - Tipos de cocina/comida
3. **PRICE** - Indicadores de precio
4. **RESTAURANT_NAME** - Nombres de restaurantes (opcional)
5. **DISH** - Platos específicos (opcional)

#### Enfoques a implementar:

##### A) Modelos heurísticos:
- **Patrones regex** para detectar ubicaciones (ej: "in Boston", "near downtown")
- **Listas de palabras clave** para tipos de cocina
- **Patrones de precio** (cheap, expensive, $, $$)

##### B) Modelos pre-entrenados:
- **spaCy en_core_web_trf** para NER general
- **Evaluación y comparación** con las entidades del corpus MIT

## Estructura de datos esperada

```python
# Formato BIO original
token_with_labels = [
    ("I", "O"),
    ("want", "O"),
    ("Chinese", "B-Cuisine"),
    ("food", "O"),
    ("in", "O"),
    ("Boston", "B-Location")
]

# Entidades extraídas
entities = {
    "cuisine": ["Chinese"],
    "location": ["Boston"],
    "keywords": ["want", "food"]
}
```

## Métricas de evaluación

1. **Precisión** en la extracción de entidades
2. **Recall** comparado con las etiquetas gold standard
3. **F1-score** para cada tipo de entidad
4. **Análisis cualitativo** de los resultados

## Pasos siguientes

1. Mejorar la función de lectura para preservar etiquetas BIO
2. Implementar limpieza de datos
3. Desarrollar extractores de palabras clave
4. Crear modelos heurísticos para NER
5. Aplicar modelos pre-entrenados de spaCy
6. Evaluar y comparar resultados
7. Generar análisis e interpretaciones