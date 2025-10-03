# Respuestas: Inteligencia Artificial y Programación Lógica

## 1. ¿Qué es la inteligencia artificial?

La **Inteligencia Artificial (IA)** es una rama de la informática que se ocupa de crear sistemas capaces de realizar tareas que normalmente requieren inteligencia humana. Estos sistemas pueden:

- Aprender de la experiencia
- Reconocer patrones
- Tomar decisiones
- Resolver problemas
- Comprender lenguaje natural
- Percibir su entorno

La IA busca desarrollar máquinas que puedan simular procesos cognitivos humanos como el razonamiento, el aprendizaje, la percepción y la resolución de problemas.

## 2. Enumere las diferencias y similitudes entre inteligencia artificial simbólica y conexionista

### **Diferencias:**

| Aspecto | IA Simbólica | IA Conexionista |
|---------|--------------|-----------------|
| **Representación** | Símbolos y reglas | Redes neuronales |
| **Procesamiento** | Lógico-deductivo | Estadístico-paralelo |
| **Conocimiento** | Explícito (reglas) | Implícito (pesos) |
| **Aprendizaje** | Manual (programación) | Automático (entrenamiento) |
| **Interpretabilidad** | Alta | Baja |
| **Ejemplos** | Sistemas expertos, PROLOG | Perceptrones, redes profundas |

### **Similitudes:**
- Ambas buscan simular procesos inteligentes
- Pueden resolver problemas complejos
- Requieren representación de conocimiento
- Son complementarias en sistemas híbridos

## 3. ¿Qué es un programa en el paradigma lógico?

Un **programa en el paradigma lógico** es un conjunto de declaraciones lógicas que describen relaciones entre objetos y reglas de inferencia. Se caracteriza por:

- **Declarativo**: Describe QUÉ se quiere lograr, no CÓMO
- **Basado en lógica**: Utiliza la lógica matemática como fundamento
- **Hechos y reglas**: Consta de hechos (datos) y reglas (lógica)
- **Inferencia automática**: El sistema deduce respuestas automáticamente

**Ejemplo en PROLOG:**
```prolog
padre(juan, maria).
padre(juan, carlos).
abuelo(X, Y) :- padre(X, Z), padre(Z, Y).
```

## 4. ¿Qué es una base de conocimiento y cuáles son las partes que la componen?

Una **base de conocimiento** es un repositorio estructurado de información que contiene el conocimiento necesario para resolver problemas en un dominio específico.

### **Partes que la componen:**

1. **Hechos (Facts)**: Declaraciones verdaderas sobre el dominio
   ```prolog
   capital(españa, madrid).
   capital(francia, paris).
   ```

2. **Reglas (Rules)**: Relaciones lógicas entre hechos
   ```prolog
   pais_europeo(X) :- capital(X, Y), continente(europa, Y).
   ```

3. **Metaconocimiento**: Conocimiento sobre el conocimiento mismo
4. **Procedimientos**: Algoritmos para resolver problemas específicos
5. **Ontologías**: Estructuras que definen conceptos y relaciones

## 5. ¿Qué tipos de consultas existen en PROLOG? ¿Cuál es la diferencia entre ellas?

### **Tipos de consultas en PROLOG:**

1. **Consultas de verificación (Yes/No)**:
   ```prolog
   ?- padre(juan, maria).
   ```
   Responde: `Yes` o `No`

2. **Consultas de instanciación**:
   ```prolog
   ?- padre(juan, X).
   ```
   Responde: `X = maria` (encuentra valores que satisfacen)

3. **Consultas de generación**:
   ```prolog
   ?- padre(X, Y).
   ```
   Responde: Todas las combinaciones posibles

4. **Consultas de existencia**:
   ```prolog
   ?- \+ padre(juan, maria).
   ```
   Verifica si NO existe la relación

### **Diferencias:**
- **Verificación**: Confirma si algo es verdadero
- **Instanciación**: Encuentra valores específicos para variables
- **Generación**: Produce todas las soluciones posibles
- **Existencia**: Verifica negaciones o ausencias

## 6. Realizar la base de conocimiento de lo siguiente: Necesitamos saber si un individuo es un personaje de ficción. Por ejemplo Dr. House, Martín Fierro y Superman.

```prolog
% Base de conocimiento sobre personajes de ficción

% Hechos: personajes de ficción
personaje_ficcion(dr_house).
personaje_ficcion(martin_fierro).
personaje_ficcion(superman).
personaje_ficcion(harry_potter).
personaje_ficcion(sherlock_holmes).

% Hechos: personajes reales
personaje_real(leonardo_davinci).
personaje_real(marie_curie).
personaje_real(einstein).

% Regla para determinar si alguien es personaje de ficción
es_personaje_ficcion(X) :- personaje_ficcion(X).

% Regla para determinar si alguien es personaje real
es_personaje_real(X) :- personaje_real(X).

% Regla para verificar que alguien NO es personaje de ficción
no_es_personaje_ficcion(X) :- personaje_real(X).

% Consultas de ejemplo:
% ?- es_personaje_ficcion(dr_house).     % Yes
% ?- es_personaje_ficcion(superman).     % Yes
% ?- es_personaje_ficcion(einstein).     % No
% ?- es_personaje_ficcion(X).            % X = dr_house; X = martin_fierro; etc.
```

## 7. Ejemplifique un agente inteligente

**Ejemplo: Agente de Recomendación de Películas**

```prolog
% Base de conocimiento del agente
genero(accion).
genero(comedia).
genero(drama).
genero(ciencia_ficcion).

pelicula(avengers, accion).
pelicula(deadpool, comedia).
pelicula(titanic, drama).
pelicula(star_wars, ciencia_ficcion).

actor(tom_hanks, drama).
actor(robert_downey, accion).
actor(ryan_reynolds, comedia).

% Reglas del agente
recomendar_pelicula(Usuario, Pelicula) :-
    genero_preferido(Usuario, Genero),
    pelicula(Pelicula, Genero).

genero_preferido(juan, accion).
genero_preferido(maria, comedia).

% El agente puede:
% 1. Percibir: Preferencias del usuario
% 2. Actuar: Recomendar películas
% 3. Aprender: Actualizar preferencias
% 4. Razonar: Usar reglas lógicas
```

## 8. ¿Qué es y para qué se utiliza un agente resolvente-problemas?

Un **agente resolvente-problemas** es un tipo de agente inteligente que:

### **Definición:**
- Identifica problemas específicos
- Busca soluciones sistemáticamente
- Utiliza algoritmos de búsqueda
- Optimiza recursos y tiempo

### **Utilidades:**
- **Navegación**: Encontrar rutas óptimas
- **Planificación**: Secuenciar acciones
- **Optimización**: Minimizar costos/maximizar beneficios
- **Diagnóstico**: Identificar causas de problemas
- **Juegos**: Estrategias en ajedrez, damas, etc.

### **Componentes:**
1. **Formulación del problema**: Estado inicial, objetivo, acciones
2. **Estrategia de búsqueda**: Algoritmo para explorar soluciones
3. **Función de evaluación**: Medir calidad de soluciones

## 9. ¿Cómo puede medirse el rendimiento de la resolución de un problema?

### **Métricas de rendimiento:**

1. **Completitud**: ¿Encuentra solución si existe?
2. **Optimalidad**: ¿Encuentra la mejor solución?
3. **Complejidad temporal**: Tiempo de ejecución
4. **Complejidad espacial**: Memoria utilizada
5. **Factor de ramificación**: Número promedio de sucesores
6. **Profundidad de solución**: Longitud del camino óptimo

### **Fórmulas:**
- **Complejidad temporal**: O(b^d) donde b=factor ramificación, d=profundidad
- **Complejidad espacial**: O(bd) para búsqueda en anchura
- **Eficiencia**: Soluciones encontradas / tiempo invertido

## 10. ¿De qué depende el rendimiento de los algoritmos de búsqueda?

### **Factores que influyen:**

1. **Factor de ramificación (b)**: Número de sucesores por nodo
2. **Profundidad de solución (d)**: Distancia al objetivo
3. **Profundidad máxima (m)**: Límite del árbol de búsqueda
4. **Calidad de la heurística**: Precisión de estimaciones
5. **Estructura del problema**: Tipo de espacio de estados
6. **Complejidad del dominio**: Número de variables/restricciones

### **Relaciones:**
- **Tiempo**: O(b^d) - exponencial con la profundidad
- **Espacio**: O(bd) - lineal con la profundidad
- **Heurística**: Mejor heurística = menos nodos explorados

## 11. ¿Qué es un agente racional?

Un **agente racional** es un agente que:

### **Definición:**
- Toma decisiones óptimas basadas en su conocimiento
- Maximiza su medida de rendimiento esperada
- Actúa de manera lógica y coherente
- Se adapta a diferentes entornos

### **Características:**
1. **Omnisciente**: Conoce completamente el entorno
2. **Lógico**: Razonamiento deductivo correcto
3. **Autónomo**: Toma decisiones independientes
4. **Adaptativo**: Aprende de la experiencia

### **Tipos:**
- **Agente reactivo simple**: Respuesta directa a percepciones
- **Agente reactivo basado en modelos**: Mantiene modelo interno
- **Agente basado en objetivos**: Planifica para alcanzar objetivos
- **Agente basado en utilidad**: Optimiza utilidad esperada

## 12. ¿Qué es el entorno cuando hablamos de agentes inteligentes? Ejemplifique

El **entorno** es el mundo externo donde el agente opera y con el cual interactúa.

### **Características del entorno:**

1. **Observable vs No observable**: ¿Puede percibir todo el estado?
2. **Determinista vs Estocástico**: ¿Las acciones tienen resultados predecibles?
3. **Episódico vs Secuencial**: ¿Las acciones son independientes?
4. **Estático vs Dinámico**: ¿Cambia mientras el agente actúa?
5. **Discreto vs Continuo**: ¿Estados y acciones son finitos?
6. **Agente único vs Multiagente**: ¿Hay otros agentes?

### **Ejemplos:**

**Entorno de ajedrez:**
- Observable, determinista, secuencial, estático, discreto, multiagente

**Entorno de conducción:**
- Parcialmente observable, estocástico, secuencial, dinámico, continuo, multiagente

**Entorno de diagnóstico médico:**
- No observable, estocástico, episódico, estático, discreto, agente único

## 13. ¿Cuál es la diferencia entre un agente reactivo simple vs. uno reactivo basado en modelos?

### **Agente Reactivo Simple:**

```prolog
% Respuesta directa a percepciones
accion(percepcion) :- condicion(percepcion), respuesta_accion.
```

**Características:**
- Respuesta directa percepción → acción
- No mantiene historial
- No tiene modelo del mundo
- Muy rápido pero limitado

### **Agente Reactivo Basado en Modelos:**

```prolog
% Mantiene modelo interno del mundo
actualizar_modelo(Modelo_Anterior, Percepcion, Modelo_Nuevo) :-
    procesar_percepcion(Percepcion, Cambios),
    aplicar_cambios(Modelo_Anterior, Cambios, Modelo_Nuevo).

accion(Modelo_Actual) :- 
    evaluar_situacion(Modelo_Actual),
    seleccionar_accion(Modelo_Actual).
```

**Características:**
- Mantiene modelo interno del mundo
- Puede manejar entornos parcialmente observables
- Más complejo pero más capaz
- Puede planificar a corto plazo

### **Diferencias clave:**
| Aspecto | Simple | Basado en Modelos |
|---------|--------|-------------------|
| **Memoria** | No | Sí (modelo interno) |
| **Observabilidad** | Requiere completa | Maneja parcial |
| **Complejidad** | Baja | Media |
| **Capacidades** | Limitadas | Extendidas |

## 14. ¿Cuál es la diferencia entre una cláusula y un predicado en el paradigma lógico?

### **Predicado:**
- **Definición**: Nombre de una relación lógica
- **Sintaxis**: `padre/2` (nombre/aridad)
- **Función**: Define qué relación representa
- **Ejemplo**: `padre` es un predicado que relaciona dos personas

### **Cláusula:**
- **Definición**: Instancia específica de un predicado
- **Sintaxis**: `padre(juan, maria).`
- **Función**: Declara un hecho específico o regla
- **Ejemplo**: `padre(juan, maria)` es una cláusula que afirma que Juan es padre de María

### **Relación:**
- **Predicado** = Plantilla/Esquema
- **Cláusula** = Instancia específica

```prolog
% Predicado: padre/2
% Cláusulas:
padre(juan, maria).           % Hecho
padre(X, Y) :- padre(Y, X).   % Regla
```

## 15. Explique qué es un hecho y qué es una regla en el paradigma lógico

### **Hecho (Fact):**
- **Definición**: Declaración verdadera sobre el dominio
- **Sintaxis**: `predicado(argumentos).`
- **Función**: Establece información básica
- **Características**: Siempre verdadero, no tiene condiciones

**Ejemplos:**
```prolog
capital(españa, madrid).
padre(juan, maria).
color(cielo, azul).
```

### **Regla (Rule):**
- **Definición**: Relación lógica entre hechos
- **Sintaxis**: `conclusion :- condiciones.`
- **Función**: Define inferencias y relaciones
- **Características**: Tiene condiciones, permite deducción

**Ejemplos:**
```prolog
abuelo(X, Y) :- padre(X, Z), padre(Z, Y).
pais_europeo(X) :- capital(X, Y), continente(europa, Y).
hermano(X, Y) :- padre(Z, X), padre(Z, Y), X \= Y.
```

### **Diferencias:**
| Aspecto | Hecho | Regla |
|---------|-------|-------|
| **Estructura** | Simple | Condicional |
| **Inferencia** | Directa | Indirecta |
| **Flexibilidad** | Fija | Variable |
| **Uso** | Datos básicos | Lógica derivada |

## 16. Escribir una base de conocimiento sobre países

```prolog
% Base de conocimiento sobre países

% Hechos dados
pais(argentina).
pais(uruguay).
provincia(santa_cruz).
departamento(canelones).

% Hechos adicionales para las consultas
pais(marruecos).
pais(estonia).
lago(ganges).
ciudad(estonia).

% Reglas para clasificar entidades
es_pais(X) :- pais(X).
es_provincia(X) :- provincia(X).
es_departamento(X) :- departamento(X).
es_lago(X) :- lago(X).
es_ciudad(X) :- ciudad(X).

% Consultas y respuestas:

% ¿Es Marruecos un país?
% ?- es_pais(marruecos).
% Respuesta: Yes

% ¿Es Ganges un lago?
% ?- es_lago(ganges).
% Respuesta: Yes

% ¿Es Estonia una ciudad?
% ?- es_ciudad(estonia).
% Respuesta: Yes

% Consultas adicionales:
% ?- es_pais(estonia).     % No (Estonia es ciudad, no país en esta base)
% ?- es_pais(argentina).   % Yes
% ?- es_provincia(santa_cruz). % Yes
```

## 17. ¿Qué es una estrategia de búsqueda no informada?

Una **estrategia de búsqueda no informada** (también llamada ciega) es un algoritmo que:

### **Definición:**
- No utiliza información específica del problema
- Solo conoce la estructura del espacio de estados
- No tiene conocimiento sobre qué tan cerca está del objetivo
- Explora sistemáticamente sin guía heurística

### **Tipos principales:**

1. **Búsqueda en anchura (BFS)**:
   - Explora nivel por nivel
   - Garantiza solución óptima
   - Complejidad: O(b^d)

2. **Búsqueda en profundidad (DFS)**:
   - Explora hasta el fondo antes de retroceder
   - Menor uso de memoria
   - Complejidad: O(b^m)

3. **Búsqueda de costo uniforme**:
   - Considera costos de las acciones
   - Encuentra solución de menor costo
   - Complejidad: O(b^(C*/ε))

4. **Búsqueda bidireccional**:
   - Busca desde inicio y objetivo simultáneamente
   - Más eficiente en tiempo
   - Complejidad: O(b^(d/2))

### **Características:**
- **Ventaja**: Simplicidad y garantías teóricas
- **Desventaja**: Ineficiencia en problemas grandes
- **Uso**: Problemas pequeños o cuando no hay heurísticas disponibles

## 18. ¿Qué tipos de problemas encontramos, como consecuencia de la búsqueda con información parcial?

### **Problemas de información parcial:**

1. **Problema de observabilidad parcial**:
   - El agente no puede percibir todo el estado
   - Debe mantener creencias sobre estados posibles
   - Ejemplo: Navegación con sensores limitados

2. **Problema de incertidumbre**:
   - Acciones tienen resultados inciertos
   - Múltiples resultados posibles
   - Ejemplo: Diagnóstico médico con síntomas ambiguos

3. **Problema de adversarios**:
   - Otros agentes con objetivos opuestos
   - Estrategias competitivas
   - Ejemplo: Juegos de estrategia

4. **Problema de recursos limitados**:
   - Tiempo y memoria finitos
   - Decisiones bajo presión temporal
   - Ejemplo: Planificación en tiempo real

5. **Problema de objetivos múltiples**:
   - Múltiples objetivos en conflicto
   - Necesidad de compromisos
   - Ejemplo: Optimización multiobjetivo

### **Soluciones:**
- **Algoritmos de búsqueda probabilística**
- **Teoría de juegos**
- **Algoritmos de aproximación**
- **Técnicas de satisfacción de restricciones**

## 19. ¿Por qué se considera a la inteligencia artificial como un nuevo factor de producción?

La **IA como factor de producción** se debe a su capacidad de:

### **Razones económicas:**

1. **Automatización inteligente**:
   - Reemplaza trabajo humano en tareas cognitivas
   - Aumenta productividad exponencialmente
   - Reduce costos operativos

2. **Escalabilidad**:
   - Puede procesar grandes volúmenes de datos
   - No se fatiga ni requiere descanso
   - Disponibilidad 24/7

3. **Innovación disruptiva**:
   - Crea nuevos productos y servicios
   - Transforma industrias tradicionales
   - Genera ventajas competitivas

4. **Optimización de recursos**:
   - Mejora eficiencia en procesos
   - Reduce desperdicios
   - Optimiza asignación de recursos

### **Impacto económico:**
- **Crecimiento del PIB**: Contribución directa al crecimiento económico
- **Nuevos mercados**: Creación de industrias basadas en IA
- **Transformación laboral**: Cambio en la naturaleza del trabajo
- **Inversión**: Atrae capital de riesgo y desarrollo

### **Ejemplos:**
- **Manufactura**: Robots inteligentes
- **Servicios**: Chatbots y asistentes virtuales
- **Finanzas**: Algoritmos de trading
- **Salud**: Diagnóstico asistido por IA

## 20. ¿Cuál es la estrategia que utilizan los algoritmos genéticos para establecer sus búsquedas?

Los **algoritmos genéticos** utilizan una estrategia inspirada en la evolución biológica:

### **Estrategia evolutiva:**

1. **Población inicial**:
   - Genera conjunto aleatorio de soluciones candidatas
   - Cada individuo representa una posible solución
   - Codificación genética del problema

2. **Evaluación (Fitness)**:
   - Calcula calidad de cada solución
   - Asigna puntuación de aptitud
   - Identifica mejores individuos

3. **Selección**:
   - Selecciona individuos para reproducción
   - Probabilidad basada en aptitud
   - Mejores individuos tienen mayor probabilidad

4. **Reproducción**:
   - **Cruzamiento (Crossover)**: Combina genes de padres
   - **Mutación**: Introduce variaciones aleatorias
   - Genera nueva generación

5. **Reemplazo**:
   - Nueva generación reemplaza a la anterior
   - Mantiene diversidad genética
   - Preserva mejores soluciones

### **Características clave:**

```prolog
% Pseudocódigo del algoritmo genético
algoritmo_genetico :-
    generar_poblacion_inicial(Poblacion),
    repetir_evolucion(Poblacion, Generaciones).

repetir_evolucion(Poblacion, 0) :- 
    mejor_solucion(Poblacion, Solucion),
    mostrar_resultado(Solucion).

repetir_evolucion(Poblacion, N) :-
    evaluar_aptitud(Poblacion, PoblacionEvaluada),
    seleccionar_padres(PoblacionEvaluada, Padres),
    reproducir(Padres, NuevaGeneracion),
    NuevaN is N - 1,
    repetir_evolucion(NuevaGeneracion, NuevaN).
```

### **Ventajas:**
- **Exploración global**: Evita óptimos locales
- **Robustez**: Funciona con funciones no diferenciables
- **Paralelización**: Fácil implementación paralela
- **Adaptabilidad**: Se adapta a diferentes problemas

### **Aplicaciones:**
- Optimización de rutas
- Diseño de redes neuronales
- Programación de tareas
- Optimización de portafolios financieros