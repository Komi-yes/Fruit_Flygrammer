# Fruit_Flygrammer

Simulación del cerebro de la mosca de la fruta (*Drosophila melanogaster*) con el
modelo de Shiu et al. 2024 (Brian2), con el objetivo de conectarlo más adelante al
cuerpo 3D de [flygym](https://github.com/NeLy-EPFL/flygym) (NeuroMechFly v2).
Por ahora solo está el cerebro.

El modelo original vive en `brain/` como submódulo de git
([philshiu/Drosophila_brain_model](https://github.com/philshiu/Drosophila_brain_model));
no se modifica.

## Estructura

- `brain/`: submódulo con el modelo de Shiu et al.
- `src/`: código propio.
- `notebooks/`: experimentos.
- `results/`: salidas de simulaciones (ignorado por git).

## Clonar

```bash
git clone --recursive https://github.com/Komi-yes/Fruit_Flygrammer.git
```

Si ya lo clonaste sin `--recursive`: `git submodule update --init`.

## Crear el entorno

Requiere [conda](https://docs.conda.io/en/latest/miniconda.html) (Miniconda o Anaconda).

```bash
conda env create -f brain/environment.yml   # crea el entorno "brian2"
conda activate brian2
conda install "setuptools<81" "cython<3.1"  # compatibilidad con brian2 2.5.1
python -m ipykernel install --user --name brian2 --display-name "Python (brian2)"
```

En Windows, para que Brian2 compile código (más rápido) hacen falta las
*Visual Studio Build Tools* con la carga de trabajo "Desarrollo para el escritorio con C++".

## Correr el ejemplo

```bash
cd brain
jupyter nbconvert --to notebook --execute example.ipynb \
  --output-dir ../results --output example_executed.ipynb
```

O abre `brain/example.ipynb` en Jupyter con el kernel "Python (brian2)".
