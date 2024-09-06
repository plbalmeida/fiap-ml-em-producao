# Modelo de ML em produção

Esse repositório é referente a Fase 4 do curso Pós Tech da FIAP de Data Analytics. Contém a implementação de um modelo de ML para prever preço do petróleo bruto do IPEA. 

> Para implementação do exercício do curso, seguir o `setup.md`, presente na raíz desse repositório

A solução do  consiste nos seguintes componentes:

- componente `model_training` para obtenção dos dados de preço do petróleo bruto do IPEA, transformação dos dados, treino do modelo, e geração de 1 arquivo com previsões D+15, e 1 arquivo com Importância de Features;

- a componente `streamlit` consome os dados de previsão gerados pelo `model_training` e gera visualizações dos mesmos que pode ser acessada localmente por uma URL fornecida nos logs de execução. 

O projeto foi desenvolvido com a seguinte stack:

- `Python`: para criação dos scripts e implementação da solução utilizando as bibliotecas `sci-kit learn`, `pandas`, `matplotlib`, `altair`, entre outras;
- `Docker`: para containerizar a solução;
- `git`: para versionamento de código;
- `GitHub Actions`: para esteira de CI;
- `Streamlit`: para servir os as previsões do modelo de ML treinado.

Estrutura do repo:

```bash
.
├── Dockerfile
├── README.md
├── docker-compose.yml
├── figures
│   ├── ci.png
│   ├── execucao.png
│   ├── preds1.png
│   ├── preds2.png
│   └── preds3.png
├── model_training
│   └── main.py
├── notebooks
│   ├── case.ipynb
│   └── nivelamento_tecnico.ipynb
├── requirements.txt
├── setup.md
├── src
│   ├── __init__.py
│   ├── feature_engineer.py
│   ├── model_train.py
│   └── utils.py
├── streamlit
│   ├── app.py
│   ├── importance_df.csv
│   └── preds_df.csv
└── tests
    ├── feature_engineer_test.py
    ├── model_train_test.py
    └── utils_test.py
```

Para executar a aplicação, na raíz do depositório executar:

```bash
docker-compose up --build
```

O script `model_training/main.py` para de treino do modelo será executado primeiro.

<div align="center">
  <figure>
    <img src="figures/execucao.png" alt="Logs de execução" width="300">
  </figure>
</div>

Com merge para brach `main` do repo, é esperado que a esteira de CI do GitHub Actions com jobs de `lint` e `test` seja executada:

<div align="center">
  <figure>
    <img src="figures/ci.png" alt="Logs de execução">
  </figure>
</div>

Após a conclusão da execução do script de treino e previsões, dois arquivos serão persistidos no diretório `streamlit`, que são `importance_df.csv` com a Importância de Features obtida com o treino do modelo, e o `preds_df.csv` com as previsões do preço do petróleoe respectivos erros, ambos são insumos para a aplicação do Streamlit.

Acessando a URL fornecida podemos ver o gráfico com as previsões:

<div align="center">
  <figure>
    <img src="figures/preds1.png" alt="Logs de execução">
  </figure>
</div>

A tabela com as previsões:

<div align="center">
  <figure>
    <img src="figures/preds2.png" alt="Logs de execução">
  </figure>
</div>

E o gráfico com importância de features:

<div align="center">
  <figure>
    <img src="figures/preds3.png" alt="Logs de execução">
  </figure>
</div>