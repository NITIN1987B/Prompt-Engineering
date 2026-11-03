# Prompt-Engineering
Prácticas del Máster de IA - Prompt Engineering

## Estructura

```
├─ pyproject.toml · uv.lock · .python-version · requirements.txt
├─ .env.example
├─ ejercicio_1/   notebook y CSV del Ejercicio 1 (Airbnb, Gemini)
└─ ejercicio_2/   notebook, CSV de entrada y CSV de resultados del Ejercicio 2 (reseñas de videojuegos, pipeline con dos LLMs)
```

## Instalación

Requiere [uv](https://docs.astral.sh/uv/). Desde la raíz del repositorio:

```bash
uv sync
```

Crea `.venv` con Python 3.12 e instala las dependencias de `uv.lock`
(`pandas`, `python-dotenv`, `google-genai`, `pydantic`, `ipykernel`).

Sin uv (necesita Python 3.12 o superior): `python -m venv .venv`, activarlo y
`pip install -r requirements.txt`.

## Clave de API

```bash
cp .env.example .env    # PowerShell: Copy-Item .env.example .env
```

Rellena `GOOGLE_API_KEY` en `.env` (clave de [Google AI Studio](https://aistudio.google.com/)).
`.env` está ignorado por git: no lo subas.

El notebook lee la clave de `.env` con `load_dotenv()`. No la escribas nunca en el notebook:
el repositorio es público.

## Ejecución

Abre `ejercicio_1/Ejercicio_1_Gemini_Groq.ipynb` o `ejercicio_2/Ejercicio 2.ipynb` en VS Code
o Jupyter y elige el kernel de `.venv`. Las rutas de los CSV son relativas al notebook y las
celdas se ejecutan en orden.

Ambos notebooks llaman a la API de Gemini con tu `GOOGLE_API_KEY` (el Ejercicio 2 hace unas 30
llamadas). El Ejercicio 2 guarda cada respuesta en `ejercicio_2/cache_llm.json` (ignorado por git)
para no repetir llamadas al reejecutar. Los modelos Flash devuelven a veces 503 por alta demanda;
el notebook reintenta con espera creciente.

Si cambias dependencias, regenera `requirements.txt`:

```bash
uv export --no-hashes --no-dev --no-emit-project -o requirements.txt
```
