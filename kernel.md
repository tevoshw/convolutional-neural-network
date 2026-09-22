
# Dados

os dados em visão computacional basicamente são

(CANAIS, ALLTURA, LARGURA)


Canais são (1 = preto ou branco) ou (3, RGB)


# Kernels

**Kernels são filtros que encontram características, são os 'neurônios' das redes neurais**

Sâo basicamente filtros que vão pegar uma imagem identificar caracteristicas e depois gerar outra matriz (imagem) transformadas, com aquelas características. Possuem pesos que são aprendidos

Cada kernel: É uma matriz (x, x)


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


Audio
- Reconhecimento de fala — transcrever áudio em texto
- Classificação de som — identificar tipo de som (latido, sirene, tiro, etc)
- Reconhecimento de música/gênero
- Detecção de palavra-chave — "Hey Siri", "OK Google"
- Identificação de locutor (quem está falando)