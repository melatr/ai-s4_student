# Deep Learning (AI-S4)


(c) 2024 Hogeschool Utrecht  
Auteurs: David Isaacs Paternostro en Tijmen Muller

In deze repository staan algemene documenten voor semester 4 van AI, zoals 
templates, oefeningen en (code)voorbeelden.


## Conda environment

Als er nog geen [conda environment](
https://docs.conda.io/) genaamd `ai-s4` is, creëer deze dan door in de Anaconda
Prompt (`conda`) naar de directory van deze repository te gaan. De omgeving die
je moet installeren hangt af van of je gebruik kan en wil maken van je GPU om
je neurale netwerken op te trainen. Als je een configuratie hebt met een 
grafische kaart van NVidia is dit wel aan te raden, omdat het veel sneller gaat
dan trainen op je CPU. Je kan hier controleren of je GPU wordt ondersteund: 
https://developer.nvidia.com/cuda-gpus.

* Als je geen ondersteunde grafische kaart hebt of je wil hier geen gebruik van
maken, gebruik dan `conda env create -f ai-s4_conda_cpu.yaml`.
* Als je wél gebruik wil maken van je GPU, gebruik dan
`conda env create -f ai-s4_conda_gpu.yaml`.

Voor meer informatie over (handmatig) installeren, zie onder.

### Interpreter instellen in VSCode

- Klik rechtsonder in de GUI waar je 'Python' ziet staan. Er komt midden bovenin je
   scherm een dropdown menu, kies daar: `ai-s4-g|cpu`.

### Interpreter instellen in PyCharm

1. Ga naar File >> Settings >> Project: _projectnaam_ >> Project Interpreter en dan:
   - kies `ai-s4-g|cpu` in het dropdown menu; of
   - ga naar Add Interpreter >> Add Local Interpreter >> Conda Environment >>
      Use Existing Environment >> selecteer `ai-s4-g|cpu` in het dropdown menu.
2. Klik rechtsonder in de GUI waar je 'Python' ziet staan.


## Installatie PyTorch 

Als je gebruik wil maken van de mogelijkheid om neurale netwerken te trainen op je NVidia GPU, 
installeer dan PyTorch met CUDA 12.8 (zie https://pytorch.org/get-started/locally/). Je kan hier
controleren of je GPU wordt ondersteund: https://developer.nvidia.com/cuda-gpus.

### CPU

Je installeert PyTorch (zonder GPU support) als volgt:

```
pip3 install torch torchvision torchaudio torchmetrics --index-url https://download.pytorch.org/whl/cpu
```

Je kan controleren of de installatie is gelukt door `python` te starten in je terminal en
dan de volgende instructies uit te voeren:

```
Python 3.13.9 | packaged by conda-forge | (main, Oct 22 2025, 23:33:35) [GCC 14.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> torch.__version__
'2.9.0+cpu'
>>> torch.cuda.is_available()
False
```

### GPU (met CUDA)

Je installeert PyTorch met CUDA support als volgt:

```
pip3 install torch torchvision torchaudio torchmetrics --index-url https://download.pytorch.org/whl/cu128
```

Je kan controleren of de installatie is gelukt door `python` te starten in je terminal en
dan de volgende instructies uit te voeren:

```
Python 3.13.9 | packaged by conda-forge | (main, Oct 22 2025, 23:33:35) [GCC 14.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
Ctrl click to launch VS Code Native REPL
>>> import torch
>>> torch.__version__
'2.9.0+cu128'
>>> torch.cuda.is_available()
True
>>> torch.cuda.get_device_name(0)
'NVIDIA RTX A1000 6GB Laptop GPU'
```

Let op! Als je PyTorch langs deze weg installeerd, zorg dan dat je updates en extra modules ook via `pip` installeert en _niet_ via `conda`!
