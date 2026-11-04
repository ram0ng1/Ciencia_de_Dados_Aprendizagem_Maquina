<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# Módulo IV — Exercícios realizados

Esta pasta reúne as atividades de introdução ao Machine Learning e de aprendizado supervisionado do Módulo IV. Cada arquivo mantém o enunciado da professora e traz as minhas respostas, com os números tirados dos notebooks que executei.

## Identificação do repositório

- Estudante: **Ramon Guilherme Marques do Nascimento** (trabalho individual)
- Turma: **Turma de Ciência de Dados – UDF — Sistemas de Informação**
- Repositório: **[ram0ng1/Ciencia_de_Dados_Aprendizagem_Maquina](https://github.com/ram0ng1/Ciencia_de_Dados_Aprendizagem_Maquina)** — conteúdo na pasta `Aprendizado_de_Maquina/`
- Projeto da disciplina usado como contexto: *Livro de ocorrências digital para condomínios residenciais do DF*, em dupla com Arthur Rodrigues de Souza Vieira ([definição do projeto](../Unidade_3_Gestao_de_Projetos_em_Ciencia_de_Dados/Definicao-Projeto-Ciencia-de-Dados.md))

## Atividades

| Arquivo | Entregável |
| --- | --- |
| [01-aula1-conceitos.md](01-aula1-conceitos.md) | Quadro comparativo e classificação justificada de pelo menos cinco problemas |
| [02-pbl-biblioteca.md](02-pbl-biblioteca.md) | Canvas da investigação |
| [03-aula2-laboratorio.md](03-aula2-laboratorio.md) | Registro do modelo, métricas, erros e experimentos em Python |
| [04-pbl-permanencia.md](04-pbl-permanencia.md) | Proposta de apoio educacional, com avaliação e limites |
| [05-revisao.md](05-revisao.md) | Respostas individuais às questões de revisão |
| [06-autoavaliacao.md](06-autoavaliacao.md) | Checklist, contribuições e reflexão final |
| [07-aplicacao-ocorrencias.md](07-aplicacao-ocorrencias.md) | Aplicação ao projeto do livro de ocorrências: sugestão automática da categoria de uma ocorrência a partir do texto |

## Arquivos de apoio

| Arquivo | O que é | Colab |
| --- | --- | --- |
| [notebooks/laboratorio.ipynb](notebooks/laboratorio.ipynb) | Notebook didático da professora, sem alterações | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ram0ng1/Ciencia_de_Dados_Aprendizagem_Maquina/blob/main/Aprendizado_de_Maquina/notebooks/laboratorio.ipynb) |
| [notebooks/laboratorio-ramon.ipynb](notebooks/laboratorio-ramon.ipynb) | Minha execução do laboratório, com interpretações e os exercícios de investigação em código | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ram0ng1/Ciencia_de_Dados_Aprendizagem_Maquina/blob/main/Aprendizado_de_Maquina/notebooks/laboratorio-ramon.ipynb) |
| [notebooks/ocorrencias-sugestao-categoria.ipynb](notebooks/ocorrencias-sugestao-categoria.ipynb) | Experimento da atividade 07 (gera os próprios dados sintéticos) | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ram0ng1/Ciencia_de_Dados_Aprendizagem_Maquina/blob/main/Aprendizado_de_Maquina/notebooks/ocorrencias-sugestao-categoria.ipynb) |

- [dados/educacionais-sinteticos.csv](dados/educacionais-sinteticos.csv): os 600 registros fictícios da prática de classificação (material da disciplina).
- [dados/ocorrencias_textos_sinteticos.csv](dados/ocorrencias_textos_sinteticos.csv): 960 ocorrências de condomínio fictícias, geradas pelo notebook da atividade 07.
- [notebooks/resultados_execucao.json](notebooks/resultados_execucao.json) e [notebooks/resultados_ocorrencias.json](notebooks/resultados_ocorrencias.json): números gravados pelas execuções.
- `assets/`: logomarca e figuras geradas pelos notebooks (matriz de confusão, árvore, gráficos da regressão e matriz da atividade 07).

**Todos os registros são sintéticos.** Não representam estudantes da UDF nem moradores ou ocorrências de condomínios reais.

## Como reproduzir

1. Clique em **Abrir no Colab** em um dos notebooks acima e use **Ambiente de execução > Executar tudo**. No Colab, as figuras são gravadas em `./assets/` e o CSV na pasta atual.
2. Localmente: `pip install numpy pandas matplotlib scikit-learn jupyter` e, dentro de `notebooks/`, rode `jupyter nbconvert --to notebook --execute --inplace laboratorio-ramon.ipynb`. Assim as figuras vão para `../assets/` e o CSV para `../dados/`.
3. A semente é 42 em todos os notebooks. Com as mesmas versões (Python 3.13, scikit-learn 1.9.1, pandas 3.0.5, NumPy 2.5.3), os números devem ser idênticos aos registrados nos relatórios.

## Convenções de registro

- Mantive os enunciados e acrescentei as respostas em negrito ou nas tabelas.
- Separo **resultado calculado**, **interpretação** e **hipótese**.
- Os valores citados nos relatórios são os das execuções salvas nos notebooks: versões, semente, divisão dos dados e configurações estão registradas.
- Não há matrículas, telefones, credenciais nem dados pessoais reais. Nas ocorrências sintéticas, unidades aparecem só como "apto XXX" e "bloco X".
- Fontes adicionais estão citadas em cada atividade.

## Situação das entregas

- [x] Aula 1: quadro comparativo e problemas justificados.
- [x] PBL Biblioteca em Foco.
- [x] Aula 2: notebook e relatório.
- [x] PBL Apoio à Permanência.
- [x] Revisão e autoavaliação.
- [x] Aplicação ao projeto da disciplina (livro de ocorrências digital).

## Fonte da atividade

Material do estudante do Módulo IV — Aprendizado de Máquina. Profa. Kadidja Valéria, UDF, 2026. Consulte as referências do material e a documentação oficial indicada nas atividades.
