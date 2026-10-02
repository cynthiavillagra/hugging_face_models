# Modelos de Hugging Face: `pipeline` vs. `InferenceClient`

Material del **Seminario de Actualización** (Tecnicatura Superior en Ciencia de Datos e IA, IFTS N.º 18).
Docente: Cynthia M. Villagra.

Una notebook con ejemplos progresivos para entender dos formas de usar un modelo de Hugging Face:

| | `transformers` + `pipeline` | `InferenceClient` |
|---|---|---|
| Dónde corre el modelo | en tu compu (o en Colab) | en los servidores de Hugging Face |
| Se bajan los pesos | sí | no |
| Qué necesitás | `transformers` + `torch`, memoria y disco | `huggingface_hub`, internet y un token |

## Contenido

- `pipeline_vs_inferenceclient.ipynb`
  - **Parte A**: `pipeline` con solo la tarea, solo el modelo, tarea + modelo; otras tareas (fill-mask, zero-shot) y los tres pasos a mano (tokenizador → modelo → softmax).
  - **Parte B**: los mismos ejemplos con `InferenceClient`, y dónde quedó cada paso.
  - **Parte C**: comparación lado a lado (tareas de `pipeline` ↔ métodos de `InferenceClient`).
  - **Parte D**: actividad, cuatro apps (Gradio y Streamlit, con cada enfoque).
- `requirements_local.txt`: para las apps con `pipeline`.
- `requirements_api.txt`: para las apps con `InferenceClient` (sin `torch`).

## Cómo usarla

**En Google Colab**: *Archivo → Abrir notebook → GitHub* y pegá la URL de este repo.

**En tu compu**:

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate   ·   Linux/Mac: source .venv/bin/activate
pip install -r requirements_local.txt jupyter huggingface_hub
jupyter notebook
```

Para la Parte B necesitás un token de Hugging Face (*Settings → Access Tokens*, con permiso
"Make calls to Inference Providers"). **Nunca lo subas al repo**: la notebook lo pide sin mostrarlo,
o lo lee de la variable de entorno `HF_TOKEN`.

## Modelos usados

Todos livianos (menos de 350 MB) y disponibles en la Inference API:

- `distilbert/distilbert-base-uncased-finetuned-sst-2-english` — sentimiento
- `j-hartmann/emotion-english-distilroberta-base` — emociones
- `distilbert/distilbert-base-uncased` — completar la palabra que falta
- `typeform/distilbert-base-uncased-mnli` — zero-shot
