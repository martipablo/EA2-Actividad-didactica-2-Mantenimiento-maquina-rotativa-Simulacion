# Simulación de la degradación de una máquina rotativa con un modelo oculto de Markov discreto

Proyecto de la asignatura **Simulación** (Módulo 2, Actividad didáctica 2).\
Autor: Pablo Martínez Ortiz · IU Digital de Antioquia / Ingeniería de software y Datos · 2026

## Descripción

Simulación Monte Carlo de la degradación de una máquina rotativa mediante un HMM discreto de tres estados ocultos (normal, degradación moderada, degradación crítica) y tres niveles de vibración observados (baja, media, alta). El algoritmo de Viterbi estima los estados a partir de las observaciones, y como la secuencia real se conoce, se mide qué tan bien se recuperan.

**Los datos son sintéticos.** Los parámetros son supuestos de diseño, no estimaciones de una máquina real.

## Contenido del repositorio

```
├── README.md
└── Simulacion_HMM_mantenimiento_maquina_rotativa.ipynb   # código, resultados, tablas y figuras
```


## Ejecución

**En Google Colab (recomendado)**

1. Abre el cuaderno: [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1bDQZkprsj5WhotmJV-r_y-ykR6uv8VNW/view?usp=sharing) (Cuaderno exclusivo para miembros de la IU Digital de Antioquia)
2. Ejecuta *Entorno de ejecución → Ejecutar todo*.


Forward y Viterbi están implementados con NumPy.

## Configuración y parámetros

Todo el experimento se controla desde el diccionario `CONFIG` (celda 1):

| Parámetro | Valor |
| :--- | :--- |
| Instantes por trayectoria (`T`) | 100 |
| Réplicas por escenario (`R`) | 1000 |
| Semilla base | 10000 (la réplica *r* usa `10000 + r`) |
| Semillas de reproducibilidad | 10000, 20000, 30000, 40000, 50000 |
| Nivel de confianza | 95 % |

Escenarios (celda 2), definidos por sus matrices de transición **A**, emisión **B** y distribución inicial **π**:

| Escenario | Descripción |
| :--- | :--- |
| E0 | Base |
| E1 | Degradación rápida |
| E2 | Degradación lenta |
| E3 | Emisión poco informativa |
| E4 | Emisión muy informativa |
| E5 | Inicio parcialmente degradado |
| E6 | Modelo mal especificado (datos con B de E0, decodificación con B de E3) |

## Estructura del cuaderno

1. Configuración · 2. Escenarios · 3. Validación y valores teóricos · 4. Simulación · 5. Forward y Viterbi · 6. Métricas por réplica · 7. Funciones estadísticas · 8. Ejecución completa · 9–12. Tablas 1 a 4 · 13–16. Figuras.

## Reproducibilidad

Con la misma configuración y las mismas versiones de las librerías, los resultados son idénticos. Entorno de la ejecución reportada: Python 3.13.18, NumPy 2.4.6, pandas 2.2.3, SciPy 1.16.3, Matplotlib 3.10.0 (Google Colab, Linux).

## Autoría y uso

Proyecto académico. Si reutilizas el código, cita este repositorio.
