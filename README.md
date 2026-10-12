# Qwen Image Edit 2511 en ComfyUI — flujos en español

> 🦖 **Este flujo es gratis.** Si te sirvió, suscríbete a **El Dino Porthos** en YouTube para más tutoriales: **https://www.youtube.com/@eldinoporthos**

Flujos del tutorial **«Crea CUALQUIER imagen con IA gratis en tu PC»** de **El Dino Porthos** (YouTube: @eldinoporthos).
Crea imágenes desde cero (solo con texto) o retoca tus fotos, gratis y sin límites, en tu propio computador.

| Archivo | Qué es |
|---|---|
| **`qwen_edit_2511_receta_porthos_es.json`** | El recomendado: con los tres trucos (modo turbo, atención INT8 y «solo texto»), en español |
| `qwen_edit_2511_plantilla_es.json` | La plantilla oficial de ComfyUI, solo traducida (para comparar) |

## Cómo usarlo
1. Haz clic en **`qwen_edit_2511_receta_porthos_es.json`** (arriba) y pulsa **«Download raw file»** (la flechita ⬇ arriba a la derecha).
2. Abre **ComfyUI** y **arrastra el archivo** desde tu carpeta de Descargas encima del lienzo. Al soltarlo, el flujo aparece.
3. Descarga estos cuatro archivos y ponlos en `ComfyUI/models/` (no hace falta cuenta):

| Carpeta | Archivo | Peso | Dónde |
|---|---|---|---|
| `diffusion_models` | qwen_image_edit_2511_int8_convrot.safetensors | 20,5 GB | huggingface.co/Comfy-Org/Qwen-Image-Edit_ComfyUI (split_files/diffusion_models) |
| `text_encoders` | qwen_2.5_vl_7b_fp8_scaled.safetensors | 9,4 GB | huggingface.co/Comfy-Org/Qwen-Image_ComfyUI (split_files/text_encoders) |
| `vae` | qwen_image_vae.safetensors | 0,25 GB | huggingface.co/Comfy-Org/Qwen-Image_ComfyUI (split_files/vae) |
| `loras` | Qwen-Image-Edit-2511-Lightning-4steps-V1.0-bf16.safetensors | 0,85 GB | huggingface.co/lightx2v/Qwen-Image-Edit-2511-Lightning |

4. Dale a **Ejecutar**. Viene listo con el ejemplo del video (el anuncio «FRÍO PERFECTO», semilla 7).

## Opciones de la cajita grande
- **`solo_texto`** · `true` = crea desde cero en un lienzo de `ancho` × `alto` (la imagen cargada se ignora, pero tiene que
  haber alguna). `false` = retoca la imagen 1 **a su propio tamaño** (si la retocas con otro tamaño, sale como pintada).
- **`atajo_4_pasos`** · `true` = modo turbo (4 pasos). `false` = como la plantilla original (40 pasos, mucho más lento).
- **`semilla`** · el «número de la suerte»: cámbialo para otra versión; déjalo igual para repetir la misma imagen.
- **`imagen_2`, `imagen_3`** · opcionales, para combinar varias imágenes.

Medidas para crear: **1664×928** (horizontal) · **928×1664** (vertical) · **1328×1328** (cuadrada).

## Qué cambia frente a la plantilla oficial
1. **Modo turbo**: `enable_turbo_mode` → `true` (LoRA Lightning de 4 pasos, cfg 1).
2. **Atención INT8**: nodo «Backend de atención del modelo» → `comfy kitchen attention`, entre el interruptor del modelo y el muestreador.
3. **Solo texto**: dos interruptores «Si/Si no» de ComfyUI que cambian la imagen 1 (nada) y el lienzo (vacío, de ancho × alto).

## Consejos
- Escribe el pedido en inglés (qué es · dónde está · la luz · el estilo); el texto que debe salir escrito, entre comillas y en español.
- Para publicidad pide el producto «unbranded, no logos».
- Con un personaje tuyo: una sola foto de referencia, con fondo limpio, y descríbelo siempre con las mismas palabras.
- Los textos largos escritos a mano pueden salir con errores: revísalos.

Medido en: AMD Radeon RX 9070 XT 16 GB · Ryzen 9 9950X3D · 48 GB de RAM · Windows 11 (ComfyUI con ROCm). Con NVIDIA el proceso es el mismo.
La misma imagen (1664×928): **2 min 25 s como viene → 23 s con la receta** (la primera tras abrir; las siguientes, unos 16 s).
También probado limitando la tarjeta a 12 y a 8 GB de memoria de video: misma imagen, casi el mismo tiempo (usa más RAM).

Modelos: Qwen-Image-Edit-2511 (Apache 2.0) · LoRA Lightning de lightx2v. Libre para usar y compartir.

¿Te sirvió? Suscríbete a El Dino Porthos en YouTube: https://www.youtube.com/@eldinoporthos
