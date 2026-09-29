# 🧠 Recursive Self-Improvement Lab

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)](https://colab.research.google.com/)
[![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=for-the-badge)](https://matplotlib.org/)
[![Artificial Intelligence](https://img.shields.io/badge/Artificial%20Intelligence-Conceptual-9B8CFF?style=for-the-badge)](#)
[![AI Safety](https://img.shields.io/badge/AI%20Safety-Exploration-42E3B4?style=for-the-badge)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

</div>

### 🔁 Una simulación controlada de automejora recursiva en Inteligencia Artificial

> **¿Qué ocurre cuando un sistema puede generar variaciones de su propia estrategia, evaluarlas, conservar la mejor... y repetir el proceso?**
>
> Este proyecto convierte una idea que suele parecer ciencia ficción en algo que podemos **observar, medir y experimentar**.

---

## 🌱 ¿Qué es este proyecto?

**Recursive Self-Improvement Lab** es un laboratorio educativo construido en **Python + Jupyter Notebook** para visualizar, de forma sencilla y controlada, uno de los mecanismos que aparecen cuando hablamos de **automejora recursiva en IA**.

La idea se reduce deliberadamente a un ciclo pequeño:

```text
        ┌───────────────────────┐
        │   🧠 ESTRATEGIA       │
        │       ACTUAL          │
        └───────────┬───────────┘
                    ↓
             🧬 Generar
               variantes
                    ↓
             📊 Evaluarlas
                    ↓
             🏆 Seleccionar
               la mejor
                    ↓
        ┌───────────────────────┐
        │   ✨ NUEVA ESTRATEGIA │
        └───────────┬───────────┘
                    │
                    └──────────────↺
```

Y entonces...

**lo volvemos a hacer.**

Una generación produce la siguiente.
La siguiente vuelve a generar variantes.
Y el ciclo continúa. 🔄

---

# 🚀 ¿Por qué importa?

Cuando escuchamos **"recursive self-improvement"**, es fácil imaginar una IA superinteligente que se reescribe a sí misma durante la noche y despierta siendo mucho más poderosa.

🚫 **Este notebook no hace eso.**

Y precisamente ahí está su valor.

El experimento aísla una idea mucho más pequeña:

> **Un sistema puede generar una nueva versión de su estrategia, medir si funciona mejor, conservar esa mejora y utilizarla como punto de partida para la siguiente iteración.**

Eso ya es suficiente para observar el mecanismo básico de una mejora iterativa.

La verdadera dificultad aparece cuando imaginamos ese mismo patrón aplicado a sistemas con:

* 🧠 capacidades de razonamiento mucho mayores
* 💻 acceso a software e infraestructura computacional
* 🔬 herramientas científicas y técnicas
* 🤖 capacidad de tomar decisiones con menor supervisión
* ⚙️ posibilidad de modificar componentes cada vez más complejos
* 🌍 acceso a sistemas del mundo real

Ahí aparecen preguntas mucho más difíciles sobre:

**alineamiento · evaluación · seguridad · gobernanza · control**

---

# 🎯 ¿Qué demuestra el laboratorio?

El experimento se apoya en cuatro operaciones fundamentales:

| Operación         | Qué ocurre                                                                      |
| ----------------- | ------------------------------------------------------------------------------- |
| 🧬 **Variación**  | El sistema genera estrategias alternativas                                      |
| 📊 **Evaluación** | Cada candidata se mide mediante una métrica objetiva                            |
| 🏆 **Selección**  | Se conserva la candidata con mejor desempeño                                    |
| 🔁 **Iteración**  | La versión seleccionada se convierte en el punto de partida del siguiente ciclo |

En forma de bucle:

```text
🧬 Variación
      ↓
📊 Evaluación
      ↓
🏆 Selección
      ↓
✨ Mejora
      ↓
🧬 Variación
      ↓
📊 Evaluación
      ↓
🏆 Selección
      ↓
✨ Mejora
      ↓
        ... y el ciclo continúa
```

---

# 🧪 El experimento

El notebook crea un pequeño modelo matemático que intenta aproximar una **función objetivo**.

El modelo comienza prácticamente vacío:

```text
Modelo 0
   ↓
Estrategia muy simple
   ↓
Desempeño pobre
```

A partir de ahí comienza la búsqueda. En cada generación, el sistema produce diferentes variantes de la estrategia actual.

Una candidata puede:

### 🔧 Cambiar sus parámetros

Por ejemplo:

```text
weight = 0.35
```

podría convertirse en:

```text
weight = 0.52
```

---

### 🧩 Cambiar su estructura

Puede incorporar nuevas características:

```text
x
```

puede evolucionar hacia:

```text
x + sin(x)
```

o:

```text
x + x² + sin(2x)
```

---

### ✂️ Simplificarse

Una característica que no aporta suficiente valor también puede ser eliminada.

Por lo tanto, el sistema **no está obligado a crecer**. Está buscando una configuración que consiga un mejor resultado.

---

# ⚙️ El corazón del proceso

El ciclo central puede resumirse así:

```python
for generation in range(GENERATIONS):

    candidates = generate_variants(current_model)

    best = select_best(
        current_model,
        candidates
    )

    current_model = best
```

Y hay una línea especialmente importante:

```python
current_model = best
```

Porque la mejor versión **no desaparece** después de ser evaluada. Se convierte en la nueva versión de referencia.

Después:

```text
Modelo 0
   ↓
mejorarlo
   ↓
Modelo 1
   ↓
mejorarlo
   ↓
Modelo 2
   ↓
mejorarlo
   ↓
Modelo 3
   ↓
...
```

Ahí aparece la idea de **recursividad**. 🔁

---

# 🧠 ¿Cómo está representado el modelo?

Cada modelo contiene tres elementos:

```python
Modelo(
    features=[...],
    pesos=[...],
    bias=...
)
```

El espacio de búsqueda incluye características como:

```text
x
x²
x³
sin(x)
sin(2x)
cos(x)
```

Esto proporciona un pequeño universo de posibilidades donde el sistema puede explorar diferentes estrategias.

---

# 📏 ¿Cómo sabemos si una versión es mejor?

El laboratorio utiliza:

## Mean Squared Error — MSE

Conceptualmente:

```text
MSE = promedio((predicción - valor_real)²)
```

Cuanto menor sea el MSE:

```text
📉 menor error
      ↓
🎯 mejor aproximación
      ↓
🏆 mejor candidata
      ↓
✅ sobrevive
```

Así obtenemos una regla de selección extremadamente sencilla:

> **Conservar la estrategia que obtiene un mejor resultado según la métrica definida.**

---

# 🔬 Training vs. Validation

Una parte importante del experimento es separar:

```text
🧪 Datos de entrenamiento
          ↓
   Representan el problema


🔍 Datos de validación
          ↓
Comprueban la generalización
```

¿Por qué?

Porque **mejorar una métrica no significa automáticamente mejorar el sistema en el mundo real**.

Un sistema puede volverse extremadamente bueno optimizando:

> el objetivo equivocado.

Y esa pequeña diferencia abre una conversación enorme sobre **AI Safety**.

---

# 📈 ¿Qué deberías observar?

A medida que avanzan las generaciones, el error de validación debería tender a disminuir.

Visualmente:

```text
Error
│
│ ████
│ ███
│ ██
│ ██
│ █
│ █
│
└──────────────────────────→ Generaciones
```

La trayectoria exacta puede variar porque las mutaciones se generan de forma estocástica.

Pero el patrón conceptual es:

```text
Generación 0
      ↓
Generación 1
      ↓
Generación 2
      ↓
Generación 3
      ↓
Generación 4
      ↓
...
```

Cada generación aceptada se convierte en el punto de partida de la siguiente.

---

# 🔄 ¿Por qué llamarlo "recursivo"?

Porque **la salida de una iteración se convierte en la entrada de la siguiente**.

Formalmente:

```text
Modeloₙ
   ↓
Generar candidatas
   ↓
Evaluar
   ↓
Seleccionar
   ↓
Modeloₙ₊₁
   ↓
Generar candidatas
   ↓
Evaluar
   ↓
Seleccionar
   ↓
Modeloₙ₊₂
   ↓
...
```

O, de forma compacta:

```text
Mₙ → Improve(Mₙ) → Mₙ₊₁
          ↑
          │
          └──── mismo proceso
```

El sistema aplica repetidamente un proceso de mejora sobre el resultado obtenido en la iteración anterior.

---

# 🧩 ¿Esto realmente es "automejora"?

### ✅ Sí, en un sentido específico y controlado.

El sistema:

* ✅ modifica su propia representación de estrategia
* ✅ evalúa las modificaciones
* ✅ conserva las modificaciones exitosas
* ✅ utiliza la nueva versión en iteraciones posteriores

Pero hay una distinción fundamental.

### 🚫 Este proyecto NO es:

* ❌ AGI
* ❌ inteligencia artificial consciente
* ❌ superinteligencia autónoma
* ❌ un sistema que reescribe arbitrariamente software de producción
* ❌ una demostración de extinción humana
* ❌ una prueba de que la automejora recursiva ocurrirá en IA avanzada
* ❌ una simulación completa de los riesgos de sistemas frontier

Es algo mucho más concreto:

> **Un modelo experimental para visualizar el mecanismo de iteración, evaluación, selección y mejora.**

---

# 🛡️ Una distinción importante

Es fácil saltar de:

```text
"Un sistema puede mejorar su estrategia"
```

a:

```text
"Una IA se volverá inevitablemente incontrolable"
```

Pero ese salto **no está justificado por este experimento**.

Entre ambas ideas existen muchos problemas y condiciones adicionales:

```text
Optimización
      ↓
Mayor capacidad
      ↓
Autonomía
      ↓
Mejores herramientas
      ↓
Acceso a recursos
      ↓
Interacción con sistemas reales
      ↓
Problemas de control y alineamiento
```

Este notebook demuestra únicamente el comienzo conceptual de esa cadena. Y eso es exactamente lo que pretende hacer.

---

# 🧪 Experimenta tú misma

El laboratorio está pensado para ejecutarse directamente en **Google Colab**.

📓 [Abrir el notebook](./automejora_recursiva_colab.ipynb)

No necesitas:

* ❌ datasets externos
* ❌ API keys
* ❌ modelos comerciales
* ❌ GPUs
* ❌ servicios de pago

El experimento utiliza únicamente Python y las librerías incluidas en el notebook.

---

# 🎛️ Experimentos para jugar

Aquí empieza la parte divertida. 😏

## 1️⃣ Aumenta el número de candidatas

Busca:

```python
CANDIDATOS_POR_GENERACION = 250
```

y prueba:

```python
CANDIDATOS_POR_GENERACION = 1000
```

Más candidatas significan más exploración.

Pero también:

```text
Más candidatas
      ↓
Más evaluaciones
      ↓
Más cómputo
```

La optimización también tiene un precio. ⚙️

---

## 2️⃣ Aumenta las mutaciones estructurales

Prueba diferentes valores para:

```python
prob_estructural = 0.18
```

Observa con qué frecuencia el sistema cambia su estructura. Esto ayuda a visualizar una diferencia interesante entre:

```text
🔧 Optimización de parámetros
           vs.
🧩 Modificación estructural
```

---

## 3️⃣ Introduce sobreajuste

Haz que el sistema seleccione usando los datos de entrenamiento:

```python
x_train
y_train
```

en lugar del conjunto de validación. Después compara ambos resultados.

Puedes encontrarte con algo muy interesante:

> **Un sistema puede mejorar mucho su métrica sin mejorar realmente su capacidad de generalización.**

Y de repente la pregunta deja de ser únicamente: **"¿Qué tan bien optimiza?"** y empieza a ser: **"¿Qué estamos optimizando exactamente?"** 👀

---

## 4️⃣ Añade un presupuesto de cómputo

Puedes introducir una restricción:

```python
MAX_EVALUATIONS = 5000
```

y detener el proceso cuando se alcance ese límite.

Ahora aparece otra dimensión:

```text
🧠 Capacidad
      +
💻 Cómputo
      +
⏱️ Tiempo
      +
💰 Costo
```

Porque ningún proceso de mejora ocurre en un vacío infinito.

---

# 🧠 El aprendizaje más profundo

Este experimento es intencionalmente pequeño. Y precisamente por eso resulta útil. No necesitamos una red neuronal gigantesca para observar el mecanismo:

```text
CREAR
  ↓
EVALUAR
  ↓
MEJORAR
  ↓
CONSERVAR
  ↓
REPETIR
```

La existencia de este patrón no es, por sí sola, extraordinaria. Lo fascinante aparece cuando pensamos qué podría ocurrir si el sistema que estamos mejorando:

```text
se vuelve más capaz
       ↓
puede mejorar herramientas
       ↓
puede modificar componentes importantes
       ↓
dispone de más recursos
       ↓
y necesita cada vez menos intervención humana
```

Ahí entran en escena preguntas sobre:

🛡️ Seguridad
🧭 Alineamiento
📊 Evaluación
⚙️ Control
🏛️ Gobernanza
🌍 Impacto en el mundo real

---

# 🌱 Del modelo de juguete al mundo real

Este laboratorio funciona como un **puente conceptual**. Toma una idea compleja y abstracta como la automejora recursiva y la convierte en una secuencia que podemos observar:

```text
Versión 0
   ↓
Versión 1
   ↓
Versión 2
   ↓
Versión 3
   ↓
Versión 4
   ↓
...
```

Podemos ver al sistema buscando estrategias progresivamente mejores. Eso no responde todas las preguntas.

Pero nos permite formularlas mejor. Y a veces, en tecnología, **una buena pregunta vale más que una respuesta apresurada**.

---

# 🔑 Conceptos explorados

<div align="center">

🧠 Artificial Intelligence
🔁 Recursive Self-Improvement
🧬 Mutation
📊 Evaluation
🏆 Selection
📉 Optimization
🧪 Generalization
⚠️ Overfitting
🛡️ AI Alignment
⚙️ Compute Constraints
🌍 AI Safety

</div>

---

# 🛠️ Stack tecnológico

| Tecnología              | Uso                         |
| ----------------------- | --------------------------- |
| 🐍 **Python**           | Lógica del experimento      |
| 📓 **Jupyter Notebook** | Laboratorio interactivo     |
| ☁️ **Google Colab**     | Ejecución en la nube        |
| 🔢 **NumPy**            | Cálculos numéricos          |
| 📊 **Matplotlib**       | Visualización de resultados |

---

# 📁 Estructura del proyecto

```text
recursive-self-improvement-lab/
│
├── 📓 automejora_recursiva_colab.ipynb
├── 📖 README.md
└── 📄 LICENSE
```

---

# 👩🏻‍💻 Desarrolladora

## Orli

**Systems Engineer · Full Stack Developer · AI & Data Explorer · Community Builder**

Creo en aprender haciendo, compartir lo aprendido y hacer preguntas incómodas cuando vale la pena. Este laboratorio nace con una intención muy simple:

> **Entender antes de opinar. Experimentar antes de asumir.**

💙 **Code with heart — create with soul.**

**Construimos. Aprendemos. Compartimos.**

---

# 📄 Licencia

Este proyecto está publicado bajo la **MIT License**. Eso significa que puedes:

✅ usarlo
✅ copiarlo
✅ modificarlo
✅ distribuirlo
✅ utilizarlo con fines educativos
✅ utilizarlo incluso en proyectos comerciales

siempre manteniendo el aviso de copyright y la licencia correspondiente.

---

# ⭐ Reflexión

> **La parte más interesante de la IA no es solamente lo que podemos construir.**
>
> **También es entender qué ocurre cuando aquello que construimos comienza a participar en la construcción de su siguiente versión.** 🔁🧠

No hace falta imaginar máquinas de ciencia ficción para empezar a estudiar la pregunta.

A veces basta con unas cuantas líneas de Python. Y un bucle:

```text
Crear
 ↓
Evaluar
 ↓
Mejorar
 ↓
Repetir
```

**¿Dónde termina la optimización y dónde empieza la automejora?** Esa pregunta queda abierta. 🌱

---

<div align="center">

### 💙 Built to learn. Built to question. Built to share.

**Construimos. Aprendemos. Compartimos.**

🧠 `recursive-self-improvement-lab`

</div>
