# Remoção de Fundo de Imagens — ComfyUI

Um workflow simples de **Background Removal para o ComfyUI**, utilizando o modelo **BiRefNet**.

Este projeto foi criado como um ponto de partida para **remoção automática de fundo de imagens com Inteligência Artificial**, experimentação com segmentação de alta precisão via **BiRefNet** e aprendizado sobre uso de subgraphs/nós customizados no ComfyUI.

---

##  Sobre o Projeto

Este repositório contém um workflow pronto para o ComfyUI, permitindo remover o fundo de imagens localmente utilizando a arquitetura BiRefNet.

A proposta é manter o pipeline simples e fácil de entender, tornando o projeto adequado para:

* Aprender a utilizar o ComfyUI para pós-processamento e edição de imagens
* Experimentar modelos de segmentação de fundo de alta precisão (BiRefNet)
* Gerar imagens com fundo transparente
* Executar remoção de fundo localmente

> **Observação:** Os pesos do modelo de remoção de fundo não estão incluídos neste repositório.

---

##  Funcionalidades

*  Remoção automática de fundo de imagens
*  Utilização do modelo BiRefNet (`BiRefNet-general.safetensors` / `birefnet.safetensors`)
*  Visualização direta do resultado final via nó `PreviewImage`
*  Estrutura simples, local e fácil de integrar em outros pipelines

---

##  Modelo

Este workflow utiliza o **BiRefNet** (Bilateral Reference Network), um modelo topo de linha para segmentação de alta resolução e remoção precisa de fundos de objetos e sujeitos.

**Modelo:** BiRefNet (General)  
**Tarefa:** Background Removal / Image Segmentation  

🔗 [BiRefNet no Hugging Face (Comfy-Org)](https://huggingface.co/Comfy-Org/BiRefNet)

O modelo **não está incluído** neste repositório.

Após realizar o download, coloque o arquivo `.safetensors` na seguinte pasta:

```text
ComfyUI/models/background_removal/
```

> **Nota:** Caso a pasta `background_removal` não exista dentro de `models/`, crie-a manualmente. Verifique sempre a licença e os termos de uso do modelo na página original antes de utilizá-lo.

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

Como o BiRefNet executa inferências levemente pesadas dependendo da resolução da imagem de entrada, a GPU de **6 GB de VRAM** processa perfeitamente imagens em alta definição de forma ágil.

---

##  Instalação

### 1. Instale o ComfyUI

Siga o tutorial para instalação do ComfyUI Portable: https://docs.comfy.org/installation/comfyui_portable_windows

### 2. Instale os nós customizados necessários

Garante que o nó de remoção de fundo/BiRefNet esteja disponível em seu ComfyUI (por exemplo, via ComfyUI Manager buscando por `BiRefNet` ou `ComfyUI-BiRefNet-Nodetree`).

### 3. Baixe o modelo BiRefNet

Faça o download do checkpoint do BiRefNet através da fonte oficial: [BiRefNet no Hugging Face](https://huggingface.co/Comfy-Org/BiRefNet/resolve/main/background_removal/birefnet.safetensors)

### 4. Instale o modelo

Coloque o arquivo `birefnet.safetensors` ou `BiRefNet-general.safetensors` dentro da pasta:

```text
ComfyUI/
└── models/
    └── background_removal/
        └── birefnet.safetensors
```

### 5. Carregue o workflow

Abra o ComfyUI com o arquivo `run_nvidia_gpu` se você tiver uma GPU da NVIDIA ou com `run_cpu`. Em seguida, carregue o arquivo JSON do workflow presente neste repositório.

### 6. Carregue sua imagem

No nó **Load Image**, selecione ou faça o upload da imagem que deseja remover o fundo.

### 7. Verifique o modelo

Garante que o nó do subgraph **Remove Background (BiRefNet)** esteja apontando para o modelo `birefnet.safetensors` baixado.

### 8. Execute o workflow

Clique em **Queue Prompt** para iniciar o processamento e visualizar a imagem sem o fundo no nó **PreviewImage**.

---

##  Observações

Este repositório contém **apenas os arquivos de configuração do workflow e sua documentação**.

Os pesos dos modelos de IA **não estão incluídos**.

O BiRefNet e quaisquer outros modelos, extensões ou recursos de terceiros utilizados com este workflow possuem suas próprias licenças e termos de uso.

Verifique sempre as condições de uso dos modelos antes de utilizar as imagens geradas comercialmente ou redistribuir qualquer recurso de terceiros.

---

##  Licença

A licença deste repositório se aplica aos arquivos de workflow e à documentação disponibilizada aqui.

Modelos de IA, checkpoints e outros recursos de terceiros **não estão cobertos pela licença deste repositório** e continuam sujeitos às respectivas licenças de seus autores.
