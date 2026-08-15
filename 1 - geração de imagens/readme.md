#  JuggernautXL modelo simples de geração de imagens — ComfyUI

Um workflow simples de **Text-to-Image para o ComfyUI**, utilizando o modelo **Juggernaut XL**.

Este projeto foi criado como um ponto de partida para **geração local de imagens com Inteligência Artificial**, experimentação com **Stable Diffusion XL (SDXL)** e aprendizado dos fundamentos de criação de workflows no ComfyUI.

---

##  Sobre o Projeto

Este repositório contém um workflow pronto para o ComfyUI, permitindo gerar imagens localmente utilizando o JuggernautXL.

A proposta é manter o pipeline simples e fácil de entender, tornando o projeto adequado para:

* Aprender a utilizar o ComfyUI
* Experimentar modelos SDXL
* Testar diferentes prompts
* Entender os parâmetros de amostragem
* Executar geração de imagens localmente
* Criar uma base para workflows mais avançados

> **Observação:** Os pesos do modelo não estão incluídos neste repositório.

---

##  Funcionalidades

*  Geração de imagens a partir de texto (Text-to-Image)
*  Utilização do modelo JuggernautXL / SDXL
*  Prompt positivo configurável
*  Prompt negativo configurável
*  Parâmetros do KSampler ajustáveis
*  Resolução padrão de 1080 × 1080
*  Geração totalmente local
*  Documentação dos parâmetros diretamente no workflow
*  Estrutura simples e fácil de modificar

---

##  Modelo

Este workflow utiliza o **Juggernaut XL**, um modelo baseado na arquitetura **Stable Diffusion XL (SDXL)**, desenvolvido para geração de imagens de alta qualidade.

**Modelo:** Juggernaut XL
**Arquitetura:** Stable Diffusion XL (SDXL)

🔗 [Juggernaut XL no Civitai](https://civitai.com/models/133005/juggernaut-xl)

O modelo **não está incluído** neste repositório.

Após realizar o download, coloque o arquivo `.safetensors` na seguinte pasta:

```text
ComfyUI/models/checkpoints/
```

Verifique sempre a licença e os termos de uso do modelo na página original antes de utilizá-lo.

---

##  Configurações Padrão

| Parâmetro  |       Valor |
| ---------- | ----------: |
| Resolução  | 1080 × 1080 |
| Batch Size |           1 |
| Steps      |          20 |
| CFG        |           8 |
| Sampler    |       Euler |
| Scheduler  |      Normal |
| Denoise    |         1.0 |

Esses valores servem como ponto de partida e podem ser modificados de acordo com o resultado desejado e com o hardware disponível.

---

##  Estrutura do Workflow

O pipeline de geração foi desenvolvido de forma simples:

```text
Checkpoint
     ↓
CLIP Text Encode
     ↓
KSampler
     ↓
VAE Decode
     ↓
Save Image
```

O workflow também possui **notas em Markdown dentro do próprio ComfyUI**, explicando os principais parâmetros utilizados e as especificações do hardware.

---

##  Hardware

O workflow foi desenvolvido e testado utilizando:

| Componente          | Especificação                  |
| ------------------- | ------------------------------ |
| Notebook            | Dell G15 5530                  |
| CPU                 | Intel Core i5-13450HX          |
| RAM                 | 16 GB                          |
| GPU                 | NVIDIA GeForce RTX 4050 Mobile |
| VRAM                | 6 GB                           |
| Sistema Operacional | Windows 11                     |

Como a GPU possui **6 GB de VRAM**, workflows mais complexos ou modelos maiores podem exigir ajustes de resolução, batch size ou outras configurações para evitar falta de memória.

---

## Instalação

### 1. Instale o ComfyUI

siga o tutorial para instalação do comfyUI portable: https://docs.comfy.org/installation/comfyui_portable_windows

### 2. Baixe o JuggernautXL

Faça o download do checkpoint do JuggernautXL através da fonte original: [Juggernaut XL — Civitai](https://civitai.com/models/133005/juggernaut-xl)

### 3. Instale o checkpoint

Coloque o arquivo `.safetensors` dentro da pasta:

```text
ComfyUI/
└── models/
    └── checkpoints/
        └── JuggernautXL.safetensors
```

> O nome do arquivo pode ser diferente dependendo da versão do modelo baixada.

### 4. Carregue o workflow

Abra o ComfyUI com o arquivo "run_nvidia_gpu" se voce tiver uma GPU da nvidia ou com "run_cpu". e depois carregue o arquivo JSON do workflow presente neste repositório.

### 5. Selecione o modelo

No nó **Load Checkpoint**, selecione o checkpoint do JuggernautXL instalado anteriormente.

### 6. Configure o prompt

Digite a descrição desejada no **Positive Prompt**.

Caso necessário, utilize o **Negative Prompt** para especificar características que devem ser evitadas na geração.

### 7. Gere a imagem

Clique em **Queue Prompt** para iniciar a geração.

---

##  Estrutura do Projeto

```text
JuggernautXL-Simple-Image-Generation/
│
├── workflow/
│   └── juggernautxl_workflow.json
│
├── examples/
│   └── ...
│
├── README.md
└── LICENSE
```

> A estrutura pode variar dependendo dos arquivos adicionados ao projeto.

---

##  Exemplo de Prompt

Um prompt simples para testar o workflow:

```text
masterpiece, best quality, highly detailed portrait of a futuristic warrior,
cinematic lighting, detailed armor, dramatic atmosphere, realistic face
```

### Negative Prompt

```text
low quality, worst quality, blurry, distorted, deformed, bad anatomy,
extra fingers, extra limbs, duplicate, watermark, text
```

Os prompts acima são apenas exemplos e podem ser substituídos por qualquer descrição desejada.

---


##  Objetivo

O principal objetivo deste projeto é fornecer uma **base simples e fácil de entender para geração local de imagens utilizando ComfyUI**.

Em vez de começar diretamente com workflows complexos, o projeto busca facilitar o entendimento dos principais componentes de um pipeline de geração baseado em SDXL.

A partir dessa base, novos recursos podem ser adicionados gradualmente para criar workflows mais completos e avançados.

---

##  Observações

Este repositório contém **apenas os arquivos de configuração do workflow e sua documentação**.

Os pesos dos modelos de IA **não estão incluídos**.

O JuggernautXL e quaisquer outros modelos, LoRAs, ControlNets ou recursos de terceiros utilizados com este workflow possuem suas próprias licenças e termos de uso.

Verifique sempre as condições de uso dos modelos antes de utilizar as imagens geradas comercialmente ou redistribuir qualquer recurso de terceiros.

---

## Licença

A licença deste repositório se aplica aos arquivos de workflow e à documentação disponibilizada aqui.

Modelos de IA, checkpoints, LoRAs, ControlNets e outros recursos de terceiros **não estão cobertos pela licença deste repositório** e continuam sujeitos às respectivas licenças de seus autores.
