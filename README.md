# TFM — Sistema de planificación nutricional para deportistas de resistencia

Proyecto práctico del Máster de Formación Permanente en Inteligencia Artificial Aplicada al Deporte (Universidad Europea).

A partir del perfil del deportista y su plan semanal, el sistema genera un plan nutricional individualizado: kilocalorías y macronutrientes por día, distribución en comidas según la hora de entreno, pauta intra-entreno, protocolo pre-competición y feedback post-sesión.

## Arquitectura

Motor dual: reglas fisiológicas (fuente de verdad, con trazabilidad bibliográfica) + modelos de ML entrenados sobre dataset sintético generado a partir de las reglas. Diseño API-ready: la lógica de dominio vive en funciones serializables; Streamlit actúa como capa fina.

Cinco módulos:

- M1 — Planificación diaria (kcal + macros por tipo de día).
- M2 — Distribución en comidas según hora de entreno.
- M3 — Recomendación intra-entreno (CHO/h, líquidos, sodio, riesgo GI).
- M4 — Protocolo pre-competición (D-3 a Día D).
- M5 — Feedback del deportista con reglas de ajuste.

## Stack

Python · SQLAlchemy + SQLite · scikit-learn + XGBoost + LightGBM · SHAP · Plotly · Streamlit · Jinja2 · python-docx · fitparse · pytest.

## Estructura

```
data/           # Datos crudos (alimentos.csv, perfiles_demo.json)
src/
  core/         # Dataclasses de dominio
  rules/        # Motor de reglas (un archivo por módulo)
  ml/           # Dataset sintético, entrenamiento, evaluación, SHAP
  db/           # SQLAlchemy
  fit/          # Importación .FIT
  export/       # HTML y .docx
  ui/           # Streamlit
templates/      # Plantillas Jinja2
notebooks/      # EDA
tests/          # pytest
docs/           # Documentación
```

## Instalación

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Documentación del proyecto

- [CLAUDE.md](CLAUDE.md): contexto operativo para sesiones de desarrollo.
- [TFM_ESPECIFICACION_COMPLETA.md](TFM_ESPECIFICACION_COMPLETA.md): especificación íntegra del proyecto.

## Autor

Mario Godoy — fisioterapeuta y nutricionista deportivo especializado en deportistas de resistencia.

## Licencia

Uso académico. Pendiente de licenciamiento formal.
