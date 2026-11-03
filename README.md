# Prompt-Engineering
Prácticas del Máster de IA - Prompt Engineering

## Estructura

```
├─ pyproject.toml · uv.lock · .python-version · requirements.txt
├─ .env.example
└─ ejercicio_1/   notebook y CSV del Ejercicio 1 (Airbnb, Gemini)
```

## Instalación

Requiere [uv](https://docs.astral.sh/uv/). Desde la raíz del repositorio:

```bash
uv sync
```

Crea `.venv` con Python 3.12 e instala las dependencias de `uv.lock`
(`pandas`, `python-dotenv`, `google-genai`, `ipykernel`).

Sin uv (necesita Python 3.12 o superior): `python -m venv .venv`, activarlo y
`pip install -r requirements.txt`.

## Clave de API

```bash
cp .env.example .env    # PowerShell: Copy-Item .env.example .env
```

Rellena `GOOGLE_API_KEY` en `.env` (clave de [Google AI Studio](https://aistudio.google.com/)).
`.env` está ignorado por git: no lo subas.

El notebook original todavía define la clave en una celda (`'XXXX...'`) y no lee `.env`;
se cambiará a `load_dotenv()` al resolver el ejercicio. Hasta entonces, no pegues
una clave real en el notebook: el repositorio es público.

## Ejecución

Abre `ejercicio_1/Ejercicio_1_Gemini_Groq.ipynb` en VS Code o Jupyter y elige el kernel
de `.venv`. Las rutas de los CSV son relativas al notebook.

Si cambias dependencias, regenera `requirements.txt`:

```bash
uv export --no-hashes --no-dev --no-emit-project -o requirements.txt
```
