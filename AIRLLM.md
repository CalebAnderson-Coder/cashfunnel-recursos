# AIRLLM — modelos grandes, requisitos reales
Fuentes oficiales verificadas 6-nov-2026, America/Caracas. Guía educativa; no es un benchmark propio.

## Qué es y qué no es
AirLLM es una biblioteca de inferencia por capas, no un nuevo modelo que supere a Claude.
Repo: https://github.com/lyogavin/airllm · instalación: `pip install airllm` en un entorno aislado.

El README documenta Llama 70B alrededor de 4 GB de **VRAM**. Eso NO equivale a 4 GB de RAM total ni prueba que cualquier laptop sirva. Sus cifras para Llama 405B (~8 GB) y DeepSeek-V3 (~12 GB) son perfiles distintos; no garantizan velocidad, RAM ni espacio de disco. Las cifras del mantenedor no son un benchmark nuestro.

## Antes de descargar
- Anota GPU/VRAM, RAM, sistema operativo y SSD libre; no confundas estas cuatro medidas.
- Revisa modelo exacto, arquitectura, versión de dependencias y licencia de sus pesos.
- Calcula almacenamiento: N parámetros × bytes por peso es solo el peso bruto. Por ejemplo 70B × 2 bytes ≈ 140 GB decimales antes de temporales; la compresión cambia esto.
- El primer uso descarga y separa pesos por capas: puede necesitar espacio para originales y derivados. `delete_original=True` elimina los pesos originales para recuperar espacio, según el README; no lo actives sin entender qué borra.
- SSD y transferencias son un cuello de botella. No hay una duración universal de 1–3 minutos por respuesta.
- macOS: requiere Apple Silicon + MLX/torch; actualmente solo LlamaForCausalLM y MistralForCausalLM. No prometas Kimi/DeepSeek en cualquier Mac.
- Offline solo después de descargar/preparar todo y comprobar que el flujo no hace llamadas remotas. Gratis de API no significa hardware, electricidad y tiempo gratis.

## Primera prueba controlada
1. Crea un entorno virtual de Python y guarda versiones (`python -m venv .venv`).
2. Lee Quickstart oficial antes de instalar; verifica dependencias de tu sistema.
3. Elige un modelo compatible más pequeño primero y revisa su licencia/acceso.
4. Usa `from airllm import AutoModel` y `AutoModel.from_pretrained("ID_DEL_MODELO_VERIFICADO")`, siguiendo el ejemplo completo del README. Este ID es un marcador deliberado, no un modelo inventado.
5. Limita la generación a 20 tokens. Mide tiempo de carga, tokens/segundo, VRAM pico, RAM y espacio antes/después.
6. No escales al modelo gigante hasta que la prueba termine. No se ejecutó inferencia en este recurso.

## Plantilla de medición
Modelo/revisión: ___ · SO: ___ · GPU/VRAM: ___ · RAM: ___ · SSD libre: ___
Dependencias: ___ · descarga: ___ · primer split: ___ · prompt: ___
20 tokens en ___ segundos · VRAM pico ___ · RAM pico ___ · disco final ___

Fuente primaria: https://github.com/lyogavin/airllm/blob/main/README.md
Licencia de biblioteca: Apache 2.0 (LICENSE oficial conservado); conserva avisos y licencia al redistribuir código. Marcas/logos no quedan automáticamente licenciados por esto. La licencia de cada modelo es independiente.
