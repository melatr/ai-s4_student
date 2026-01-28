# Deep Learning (AI-S4)

[//]: # (HUGenerateStudentVersion=True)

(c) 2024 Hogeschool Utrecht  
Auteurs: David Isaacs Paternostro en Tijmen Muller

In deze repository staan algemene documenten voor semester 4 van AI, zoals 
templates, oefeningen en (code)voorbeelden.


## Conda environment

Als er nog geen [conda environment](
https://docs.conda.io/) genaamd `ai-s4` is, creëer deze dan door in de Anaconda
Prompt `conda` naar de directory van deze repository te gaan. Creëer vervolgens 
de omgeving met het volgende commando:

```bash
conda env create -f ai-s4_conda.yaml
```

Vervolgens moet je nog de juiste versie van PyTorch handmatig installeren, zie 
hiervoor de [instructies](#installatie-pytorch) hieronder.

### Interpreter instellen in VSCode

- Bij Python code klik je rechtsonder in de GUI waar je 'Python' ziet staan. 
  Er komt midden bovenin je scherm een dropdown menu, kies daar: `ai-s4`.
- Bij een Jupyter Notebook klik je rechtsboven in de GUI waar je
  'Select Kernel' ziet staan. Er komt midden bovenin je scherm een dropdown 
  menu, kies daar: `ai-s4`.

### Interpreter instellen in PyCharm

1. Ga naar File >> Settings >> Project: _projectnaam_ >> Project Interpreter en dan:
   - kies `ai-s4` in het dropdown menu; of
   - ga naar Add Interpreter >> Add Local Interpreter >> Conda Environment >>
      Use Existing Environment >> selecteer `ai-s4` in het dropdown menu.
2. Klik rechtsonder in de GUI waar je 'Python' ziet staan.


## Installatie PyTorch 

Voor het maken en trainen van neurale netwerken maken we in dit semester gebruik 
van de library [PyTorch](https://pytorch.org/). 

De versie van PyTorch die je moet installeren hangt af van of je gebruik kan en wil 
maken van je GPU om je neurale netwerken op te trainen. Als je een configuratie hebt 
met een grafische kaart van NVidia is dit wel aan te raden, omdat het veel sneller gaat
dan trainen op je CPU. Je kan hier controleren of je GPU wordt ondersteund: 
https://developer.nvidia.com/cuda-gpus. 

Als je een videokaart hebt die wordt 
ondersteund, volg dan de instructies onder het kopje [GPU](#gpu). Als je geen videokaart
hebt dit wordt ondersteund of je wil er geen gebruik van maken, volg dan de instructies
onder het kopje [CPU](#cpu).

Let op dat je PyTorch installeert in de juiste omgeving! Activeer de omgeving voor S4
dus eerst met onderstaand commando, voordat je de `pip install` commando's uitvoert.

```bash
conda activate ai-s4
```

### CPU

De installatie van PyTorch zonder GPU support (en dus zonder CUDA) gaat als volgt:

```bash
pip3 install torch==2.9.1 torchvision==0.24.1 torchaudio==2.9.1 torchmetrics==1.0.3 --index-url https://download.pytorch.org/whl/cpu
```

Je kan controleren of de installatie is gelukt door `python` te starten in je terminal en
dan de volgende instructies uit te voeren:

```
Python 3.12.12 | packaged by conda-forge | (main, Oct 22 2025, 23:25:55) [GCC 14.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> torch.__version__
'2.9.1'
>>> torch.cuda.is_available()
False
```

### GPU

Je installeert PyTorch met de CUDA Toolkit als volgt. Let op dat je hierbij de versie 
van CUDA selecteert die bij je videokaart past (in het voorbeeld hieronder wordt CUDA v12.8 geinstalleerd
voor een NVIDIA RTX A1000 videokaart).

```bash
pip3 install torch==2.9.1 torchvision==0.24.1 torchaudio==2.9.1 torchmetrics==1.0.3 --index-url https://download.pytorch.org/whl/cu128
```

Je kan controleren of de installatie is gelukt door `python` te starten in je terminal en
dan de volgende instructies uit te voeren:

```
Python 3.12.12 | packaged by conda-forge | (main, Oct 22 2025, 23:25:55) [GCC 14.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> torch.__version__
'2.9.1+cu128'
>>> torch.cuda.is_available()
True
>>> torch.cuda.get_device_name(0)
'NVIDIA RTX A1000 6GB Laptop GPU'
```

Let op! Als je PyTorch langs deze weg installeert, zorg dan dat je updates en extra modules ook via `pip install` installeert en _niet_ via `conda install`!
