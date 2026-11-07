# Simulador de EDO: Fondo de Ahorro Comunitario
**Desafío Individual: Modelar un problema real con Ecuaciones Diferenciales Ordinarias**  
**Materia:** Ecuaciones Diferenciales / Métodos Numéricos  
**Estudiante:** Arvin Yael Vargas Condori  
**Fecha límite:** 6 de noviembre de 2026  

---

## 1. Propósito y Contexto del Proyecto

El objetivo de este proyecto es modelar la evolución temporal del capital acumulado en un **Fondo de Ahorro Comunitario y Capital de Trabajo** orientado a otorgar microcréditos a emprendedores de una junta vecinal.

Mediante una Ecuación Diferencial Ordinaria (EDO) de primer orden con condición inicial, se analiza la sostenibilidad del fondo a lo largo del tiempo, contrastando la **Solución Analítica Exacta** frente a dos métodos numéricos de discretización: el **Método de Heun (RK2)** y el **Método de Runge-Kutta de 4.º Orden (RK4)**.

---

## 2. Modelo Matemático

### Ecuación Diferencial Ordinaria (EDO)
$$\frac{dC}{dt} = A - k \cdot C, \quad C(0) = C_0$$

### Definición de Variables y Parámetros
* **$C(t)$ [Bs]:** Variable dependiente. Representa el capital acumulado en la caja de ahorro en el instante $t$.
* **$t$ [meses]:** Variable independiente. Tiempo transcurrido desde el inicio del fondo.
* **$A$ [Bs/mes]:** Tasa constante de ingresos por aportes comunitarios periódicos de los socios.
* **$k$ [1/mes]:** Tasa proporcional de salida de capital destinada al otorgamiento de microcréditos y gastos de gestión.
* **$C_0$ [Bs]:** Condición inicial. Capital con el que arranca el fondo en el mes cero ($t = 0$).

### Solución Analítica Exacta
Resolviendo la EDO lineal por el método de separación de variables o factor integrante:

$$C(t) = \frac{A}{k} + \left(C_0 - \frac{A}{k}\right) \cdot e^{-k \cdot t}$$

#### Estado Estacionario (Equilibrio Financiero):
$$\lim_{t \to \infty} C(t) = \frac{A}{k}$$

---

## 3. Métodos Numéricos Implementados

1. **Método de Heun (Runge-Kutta de Orden 2):**
   * Predictor (Euler): $C_{i+1}^* = C_i + h \cdot f(t_i, C_i)$
   * Corrector: $C_{i+1} = C_i + \frac{h}{2} \cdot \left[ f(t_i, C_i) + f(t_{i+1}, C_{i+1}^*) \right]$

2. **Método de Runge-Kutta de 4.º Orden (RK4):**
   * $k_1 = f(t_i, C_i)$
   * $k_2 = f\left(t_i + \frac{h}{2}, C_i + \frac{h}{2} k_1\right)$
   * $k_3 = f\left(t_i + \frac{h}{2}, C_i + \frac{h}{2} k_2\right)$
   * $k_4 = f(t_i + h, C_i + h k_3)$
   * $C_{i+1} = C_i + \frac{h}{6} (k_1 + 2k_2 + 2k_3 + k4)$

---

## 4. Análisis Comparativo de Errores

El modelo evalúa automáticamente los siguientes indicadores de precisión para cada paso iterativo frente a la solución analítica:

* **Error Absoluto:** $E_{abs} = |C_{exacto}(t_i) - C_{aprox}(t_i)|$
* **Error Relativo Porcentual:** $E_{rel} (\%) = \left| \frac{C_{exacto}(t_i) - C_{aprox}(t_i)}{C_{exacto}(t_i)} \right| \times 100$

Se incluye la comparación con al menos dos tamaños de paso ($h$ principal e $h_2$ secundario) para estudiar la sensibilidad de la discretización.

---

## 5. Aplicación Web Interactiva

La simulación web se encuentra desplegada y no requiere instalación previa:

* **Enlace a la Simulación Web:** `[INSERTA_TU_URL_AQUÍ]` *(ej. GitHub Pages / Vercel)*
* **Video Explicativo (1 minuto):** `[INSERTA_TU_ENLACE_DE_YOUTUBE_O_VIMEO_AQUÍ]`

### Características de la Aplicación:
* **Entradas interactivas:** Ajuste de $C_0$, $A$, $k$, $T$ (tiempo), $h$ y $h_2$.
* **Gráficas dinámicas:** Renderizadas con Chart.js contrastando la curva analítica con Heun y RK4.
* **Gráfica de convergencia del error:** Evolución del error absoluto temporal.
* **Tabla iterativa:** Visualización del paso a paso con opción de exportación a `.csv`.

---

## 6. Estructura del Repositorio

```text
.
├── index.html     # Aplicación web principal e interfaz de usuario
├── styles.css     # Estilos CSS (Tema Dark / Responsivo)
├── app.js         # Lógica de cálculo numérico (Heun, RK4, Analítica) y gráficas
└── README.md      # Documentación del proyecto y explicación del modelo
```

---

## 7. Instrucciones de Ejecución Local

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/TU_USUARIO/EDO-Fondo-Ahorro-Comunitario.git
   ```
2. **Navegar a la carpeta del proyecto:**
   ```bash
   cd EDO-Fondo-Ahorro-Comunitario
   ```
3. **Ejecutar:**  
   Simplemente abre el archivo `index.html` en cualquier navegador web moderno (Google Chrome, Mozilla Firefox, Microsoft Edge, Safari). No requiere ningún entorno ni servidor ejecutable adicional.