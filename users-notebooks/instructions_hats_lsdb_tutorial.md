Instruções para criar o ambiente virtual para rodar o notebook de tutorial do HATS / LSDB no Jupyter sobre Kubernetes do LIneA.
Última atualização: 01 de novembro de 2024.

1) Limpar os ambientes de forma geral.
```bash
conda clean --all
```
```bash
pip cache purge
```

2) Confira se você tem o canal conda-forge na sua lista de canais.
```bash
conda config --show channels
```
Se você não tiver, adicione-o na lista de canais.
```bash
conda config --append channels conda-forge
```

3) Criar o ambiente e ativar.
```bash
conda create -p $HOME/.conda/envs/lsdb_env python=3.12.7
```
```bash
conda activate lsdb_env 
```
OU
```bash
source activate lsdb_env
```

4) Instalar pacotes necessários com conda.
```bash
conda install -c conda-forge --override-channels \
    pathlib astropy bokeh holoviews geoviews cartopy \
    matplotlib pandas dask distributed ipykernel pyogrio \
    pyviz_comms jupyter_bokeh \
    hats=0.4.2 hats-import=0.4.1 lsdb=0.4.1
```
Obs.: Esse passo demora bastante! Leva cerca de 10 a 20 minutos para o conda resolver o ambiente.

5) Instalar pacotes necessários com pip.
```bash
pip install dblinea
```

6) Fazer com que o ambiente seja disponibilizado como um kernel.
```bash
python -m ipykernel install --user --name=lsdb_env
```

7) Instalar a extensão "jupyter-bokeh" no menu de extensões do Jupyter Lab (barra lateral esquerda, símbolo de quebra-cabeças) e dar um refresh na página.

8) Instalar a extensão "pyviz-comms" no menu de extensões do Jupyter Lab (barra lateral esquerda, símbolo de quebra-cabeças) e dar um refresh na página.

9) Rodar o notebook.

Obs.: Se os gráficos não reenderizarem de primeira ao rodar o notebook, recomento que reinicie o seu servidor (STOP SERVER / START SERVER) e repita os passos 7, 8 e 9.