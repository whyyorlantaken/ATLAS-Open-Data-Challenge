
# Instalación de ROOT de CERN en Conda para Jupyter Notebook

Este documento describe cómo instalar Conda, configurar un entorno Conda para usar Jupyter Notebook, e instalar ROOT para su uso en Jupyter Notebook.

## Paso 0: Instalar Conda

1. **Descargar Anaconda**:
   - Visita la página oficial de [Anaconda](https://www.anaconda.com/products/distribution#download-section).
   - Descarga el instalador adecuado para tu sistema operativo (Windows, macOS o Linux).

2. **Instalar Anaconda**:
   - Sigue las instrucciones del instalador para tu sistema operativo.
   - Asegúrate de agregar Anaconda a tu PATH si se te solicita durante la instalación.

## Paso 1: Instalar Jupyter Notebook

1. **Abrir Anaconda Prompt o Terminal**:
   - En Windows, busca "Anaconda Prompt" en el menú de inicio.
   - En macOS o Linux, abre una terminal.

2. **Crear un entorno Conda básico**:
   ```sh
   conda create -n base_env python=3.8
   
   Puedes cambiar `base_env` por el nombre que prefieras y `3.8` por la versión de Python que necesites.

3. **Activar el entorno**:
   ```sh
   conda activate base_env
4. **Instalar Jupyter Notebook**:
    ```sh
   conda install jupyter

## Paso 2: Crear un Entorno Conda con ROOT

1. **Crear un nuevo entorno con ROOT preinstalado**:
   ```sh
   conda create -n my_root_env root -c conda-forge
   
## Paso 3: Activar el Entorno con ROOT

1. **Activar el entorno**:
   ```sh
   conda activate my_root_env
   
## Paso 4: Configurar el Canal Conda-forge

1. **Agregar el canal `conda-forge` a la configuración del entorno**:
   ```sh
   conda config --env --add channels conda-forge

## Paso 5: Configurar el Entorno para Jupyter Notebook

1. **Instalar el kernel de Jupyter para el entorno Conda**:
   ```sh
   conda install ipykernel

2. **Agregar el Entorno como un Kernel en Jupyter Notebook**:
   ```sh
   python -m ipykernel install --user --name=my_root_env --display-name "Python (my_root_env)"

## Paso 6: Ejecutar Jupyter Notebook

1. **Iniciar Jupyter Notebook**:
   ```sh
   jupyter notebook

## Paso 7: Usar ROOT en un Notebook

Para más información puedes visitar el sitio de [ROOT](https://root.cern/)

1. **Crear un nuevo notebook**:
   - En Jupyter Notebook, selecciona "New" y elige el kernel `Python (my_root_env)` que creaste.

2. **Probar ROOT en el notebook**:
   En una celda del notebook, prueba el siguiente código para asegurarte de que ROOT esté funcionando:

   ```python
   import ROOT

   # Crear un histograma simple
   h = ROOT.TH1F("h", "Mi Histograma;Eje X;Eje Y", 100, -4, 4)
   for i in range(10000):
       h.Fill(ROOT.gRandom.Gaus())
   
   # Mostrar el histograma
   c = ROOT.TCanvas()
   h.Draw()
   c.SaveAs("histograma.png")

   
   
   
   
   
