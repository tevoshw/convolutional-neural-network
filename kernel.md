# Kernels


**Kernels (or filters) are small weight matrices that slide over the data, detecting specific patterns.**

They aren't literally "neurons," but at each position the kernel is applied, it produces an activation — somewhat like a neuron firing. The key difference from an MLP neuron is **weight sharing**: the same kernel (same weights) is reused across the entire input, instead of each position having its own weights.

## What it does

The kernel slides over the input (convolution), multiplying and summing values locally, producing a new matrix called a **feature map** — where each value indicates how strongly that specific pattern is present in that region.

- Early layers → detect simple patterns (edges, textures, colors)
- Deep layers → combine these patterns into more complex features (shapes, objects)

Kernel weights are **not hand-designed** — they're learned via backpropagation.

## Kernel shape

(C_out, C_in, kH, kW)


- **C_in** → input channels (e.g. 3 for RGB). The kernel always covers all input channels — it sums over them, but doesn't slide along this dimension.
- **C_out** → number of kernels (filters) chosen. Each kernel produces 1 output channel → becomes the number of output channels.
- **kH, kW** → spatial dimensions of the kernel (height, width) — the axes it slides over.

## General rule (ConvXD)

The "X" in Conv1D/2D/3D indicates **how many dimensions the kernel slides over**:

| Type | Kernel | Typical data |
|------|--------|--------------|
| Conv1D | (C_out, C_in, kT) | raw audio |
| Conv2D | (C_out, C_in, kH, kW) | image, spectrogram |
| Conv3D | (C_out, C_in, kD, kH, kW) | video, medical volume (CT/MRI) |

Channels (C) never slide — regardless of dimensionality, they're always summed/flattened within each kernel position.

## Multiple Channels

When we have more than 1 channel, like an RGB image (3 channels), each kernel is not just a single 2D matrix. Instead, each kernel acts as a 3D block, containing a distinct 2D weight matrix for **each** input channel.

If we use **10 kernels** and the input data has **3 channels**:

`10 kernels * 3 channels = 30 2D weight matrices` in total.

### How the math works under the hood:

1. **Intermediate Convolutions:** Each of the 10 kernels applies its 3 unique matrices to the corresponding input channels (Red, Green, and Blue). This generates 3 intermediate 2D matrices per kernel (30 intermediate matrices in total).
2. **Channel Summation (Reduction):** For each kernel, its 3 intermediate matrices are summed together element-wise to form a single 2D matrix. A bias term is usually added at this stage.
3. **Final Feature Maps:** Because the channels are summed and collapsed for each kernel, those 10 kernels will output exactly **10 final feature maps**. 

**In short:**
* **Input:** `3` channels
* **Kernels:** `10` 
* **Operation:** $30$ independent 2D matrices are calculated and then summed in groups of 3.
* **Output:** `10` feature maps (the new depth of your tensor is now 10).

> Always after the kernels, we apply the activation function (normally ReLU) in the features maps

# Stride


O quanto o kernel desliza pro lado e pra baixo


# Padding

A borda da imagem para manter a qualidade


# Pooling

Redução dos pixels, em um 'resumo'


# Flatten


Transforma imagem (matriz) em vetor


# Dense

Rede neural totalmente conectada




# Types 


Imagens
- Classificação de imagens — qual classe é a imagem
- Detecção de objetos — onde estão os objetos (bounding boxes)
- Segmentação semântica — qual classe é cada pixel
- Segmentação de instância — separa objetos individuais da mesma classe
- OCR — reconhecer texto em imagens
- Reconhecimento facial — identificar/verificar rostos
- Pose estimation — detectar posição de articulações/corpo
- Super-resolução — aumentar qualidade/resolução de imagem
- Style transfer — aplicar estilo artístico numa imagem
- Geração de imagens (GANs)
- Colorização automática (P&B → cor)
- Image-to-image translation (ex: mapa satélite → mapa rua)
- Detecção de anomalias (defeitos em produtos, inspeção industrial)
- Denoising (remoção de ruído)


Audio
- Reconhecimento de fala — transcrever áudio em texto
- Classificação de som — identificar tipo de som (latido, sirene, tiro, etc)
- Reconhecimento de música/gênero
- Detecção de palavra-chave — "Hey Siri", "OK Google"
- Identificação de locutor (quem está falando)
- Emotion recognition (detectar emoção na voz)