# 🍬 Fábrica de Dulces

Juego web que enseña **lo básico de Python** programando a un robot: el jugador
escribe código real para mover un robot por una fábrica y recoger dulces en una
rejilla. Pensado para *aprender haciendo*, con mensajes amables para principiantes.

> Proyecto personal y creativo de **Fabián (Itosturre)**. No es una SaaS: la
> diversión y el "que el concepto se *sienta*" son el objetivo.

## ▶️ Cómo jugar

No hay nada que instalar ni compilar. Es **un solo archivo, sin dependencias**.

- **Opción rápida:** abre `index.html` en tu navegador.
- **Opción servidor local** (recomendada en Codespaces):
  ```bash
  python3 -m http.server 8000
  ```
  y abre <http://localhost:8000/index.html>.

Escribe el código en el editor de la derecha y pulsa **▶ Ejecutar**
(o `Ctrl/Cmd + Enter`). Usa **Tab** para indentar.

## 🎓 Qué enseña (niveles)

La dificultad de cada nivel está diseñada para *motivar* el concepto que enseña.

| Nivel | Título | Concepto |
|------:|--------|----------|
| 1 | El primer dulce | Secuencia |
| 2 | La esquina | Giros |
| 3 | Línea de producción | Ciclos `for` |
| 4 | El almacén en L | Combinar `for` + giros |
| 5 | Inspección salteada | Decisiones `if` + percepción `hay_dulce()` |
| 6 | El mismo plan, otro pasillo | Reutilizar el mismo programa |
| 7 | La clasificadora | `if` / `else` |
| 8 | El pasillo de largo desconocido | `while` + `puede_avanzar()` |
| 9 | Limpieza total | `while` + `not` |

*En construcción (roadmap):* `def` (funciones), variables y conteo, y parámetros.

## 🤖 Lenguaje del robot (mini-Python)

El juego incluye un intérprete que analiza el código **por indentación**, igual
que Python real.

**Comandos** (actúan): `avanzar()`, `girar_derecha()`, `girar_izquierda()`, `recoger()`

**Sensores** (leen el entorno, devuelven `True`/`False`): `hay_dulce()`, `puede_avanzar()`

**Estructuras:** `for _ in range(n):`, `if … :` / `else:`, `while … :`, y el prefijo `not`.

Ejemplo (Nivel 8):

```python
while puede_avanzar():
    avanzar()
    if hay_dulce():
        recoger()
```

## 🛠️ Arquitectura

Todo vive en `index.html` (HTML + CSS + JavaScript vanilla, Canvas 2D):

- **Niveles como datos:** array `NIVELES[]` con la rejilla, robot, dulces,
  obstáculos y textos de cada nivel.
- **Intérprete:** `parsear()` arma un árbol de instrucciones por indentación;
  `simular()` lo ejecuta sobre una copia del estado y graba *fotogramas* que
  `animar()` reproduce. Hay un tope de pasos anti-ciclo-infinito.
- **Render:** dibujo en Canvas 2D (robot, dulces, máquinas, rejilla).

## 📄 Licencia

Proyecto personal de aprendizaje. Úsalo y modifícalo con libertad.
