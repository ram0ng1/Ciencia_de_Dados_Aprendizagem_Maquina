# Ciência de Dados e Aprendizagem de Máquina

Repositório de atividades da disciplina **Ciência de Dados e Aprendizagem de Máquina**.

**Aluno:** Ramon Guilherme
**Curso:** Sistemas de Informação

## Estrutura

```
BigData/                              Unidade I — Introdução a Big Data
  Atividade.md                        registro das aulas e conceitos
  Atividade_Aula01.md                 atividade da aula 01
  Big_Data_Introducao.pdf             material de referência da disciplina

Unidade2_Analise_e_Ciencia_de_Dados/  Unidade II — Análise e Ciência de Dados
  Atividades.md                       registro das aulas
  aula_pandas_ciencia_dados.md        plano de aula — Pandas (material da disciplina)
  chamados_suporte_ti.csv             dataset usado nas atividades de Pandas
  Capitulo2_Python.ipynb              Python para Ciência de Dados
  Ciencia_Dados.ipynb                 notebook de Ciência de Dados
  PythonCienciaDeDados.ipynb          exercícios de Python aplicado
  PythonParaCienciaDeDados_Analise_e_Interpretacao.pdf

Unidade_3_Gestao_de_Projetos_em_Ciencia_de_Dados/  Unidade III — Gestão de Projetos
  Definicao-Projeto-Ciencia-de-Dados.md  definição do projeto (livro de ocorrências digital)

Projeto_Ciencia_de_Dados/             Parte prática do projeto (A1) — CRISP-DM
  README.md                           resultados, SQL, notebook e dashboard
  notebooks/crispdm_livro_ocorrencias.ipynb   notebook (abre no Colab)
  livro_ocorrencias.sql               validações, base limpa e KPIs
  Livro_Ocorrencias_Analise_SQL.pdf   consultas com os resultados
  Dashboard/                          dashboard em Python (3 páginas)

Aprendizado_de_Maquina/               Módulo IV — Aprendizado de Máquina
  README.md                           atividades 01 a 07
  notebooks/                          laboratório e aplicação ao projeto (abrem no Colab)
```

## Unidades

### Unidade I — Big Data

Conceitos de Big Data: volume, velocidade e variedade, e por que dados em escala
exigem infraestrutura e técnicas próprias.

### Unidade II — Análise e Ciência de Dados

Pipeline de Ciência de Dados (problema → coleta → preparação → análise →
interpretação → decisão), análise exploratória e manipulação de dados tabulares
com Pandas: carregamento, inspeção, seleção, filtros, transformação e agregação.

### Unidade III — Gestão de Projetos

Definição do projeto em dupla com Arthur Rodrigues de Souza Vieira: um livro de ocorrências digital para
condomínios residenciais do DF, a partir da análise do livro de ocorrências em papel.

### Projeto de Ciência de Dados (A1)

Aplicação das seis fases do CRISP-DM ao livro de ocorrências: validações em SQL, notebook em Python e dashboard.
[![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ram0ng1/Ciencia_de_Dados_Aprendizagem_Maquina/blob/main/Projeto_Ciencia_de_Dados/notebooks/crispdm_livro_ocorrencias.ipynb)
Ver [Projeto_Ciencia_de_Dados/README.md](Projeto_Ciencia_de_Dados/README.md). A base é simulada até a transcrição do
livro real; o formulário com os moradores e a coleta dos dados são etapas pendentes.

### Módulo IV — Aprendizado de Máquina

Conceitos, laboratório supervisionado (classificação e regressão), PBLs, revisão, autoavaliação e aplicação ao projeto.
Ver [Aprendizado_de_Maquina/README.md](Aprendizado_de_Maquina/README.md).

## Dataset

`chamados_suporte_ti.csv` — 18 chamados de suporte de TI com 10 variáveis
(setor, categoria, prioridade, status, tempo de resolução, satisfação, reabertura
e analista). Usado nas atividades de Pandas da Unidade II, incluindo a análise de
cumprimento de SLA.

## Referências

- CARVALHO, A. C.; MENEZES, A.; BONIDIA, R. *Ciência de Dados — Fundamentos e Aplicações.*
  <https://bonidia.github.io/cd-fundamentos/cp2.html>
- LANEY, D. *3D Data Management: Controlling Data Volume, Velocity and Variety.*
  META Group (Gartner), 2001.

## Licença

Ver [LICENSE](LICENSE).
