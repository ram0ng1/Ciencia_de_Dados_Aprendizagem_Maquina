<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# Autoavaliação e conferência da entrega

## Identificação

- Estudante ou equipe: **Ramon Guilherme Marques do Nascimento**
- Turma: **Turma de Ciência de Dados – UDF — Sistemas de Informação**
- Data de realização: **16/10/2026**
- Integrantes e contribuições (se em equipe): **Atividade individual: fiz todas as atividades do módulo.**

## Checklist

- [x] Diferenciei IA, Ciência de Dados e ML com um exemplo.
- [x] Completei o quadro supervisionado/não supervisionado.
- [x] Justifiquei pelo menos cinco situações-problema.
- [x] Registrei a investigação da biblioteca.
- [x] Identifiquei atributos, alvo, unidade e momento da previsão.
- [x] Executei e documentei a prática em Python ou Orange.
- [x] Escolhi configurações usando treino/validação.
- [x] Mantive o teste fora do ajuste e da seleção.
- [x] Interpretei acurácia, matriz, MAE e R².
- [x] Comparei com uma referência e discuti erros.
- [x] Registrei limitações, dados sintéticos, privacidade e vieses.
- [x] Formulei recomendações de apoio com revisão humana.
- [x] Respondi às questões individuais.
- [x] Conferi os links e os arquivos de evidências.
- [x] Substituí os campos PREENCHER ou justifiquei os não aplicáveis.

## Reflexão individual

- O que aprendi e consigo explicar: **Consigo explicar a diferença entre escrever regras e aprender regras com exemplos, e classificar um problema como classificação, regressão ou agrupamento olhando para o alvo (e não para o nome do problema). Consigo montar um fluxo honesto de avaliação: separar o teste primeiro, deixar a imputação e o TF-IDF dentro do `Pipeline`, escolher parâmetros só com validação cruzada e abrir o teste uma vez. Sei ler uma matriz de confusão e tirar dela acurácia (117/150 = 0,78), sensibilidade (42/61 ≈ 0,689) e precisão (42/56 = 0,75), e sei explicar MAE (28,59 empréstimos/semana) e R² (0,877) sem chamar R² de "porcentagem de acerto". Também consegui levar isso para o meu projeto: a sugestão de categoria de ocorrências é classificação multiclasse, e o experimento mostrou que a qualidade dos rótulos limita o modelo.**
- Qual foi minha principal dificuldade: **Resistir à vontade de "melhorar" o modelo depois de ver o teste. No laboratório, a grade de `min_samples_leaf` e o experimento de limiar mostraram configurações com números um pouco melhores, e entender por que eu não deveria adotá-las sem um teste novo (e que as diferenças estavam dentro do desvio entre dobras) foi o ponto que mais me fez pensar.**
- Qual evidência mostra meu avanço: **O [notebook do laboratório](notebooks/laboratorio-ramon.ipynb) com os exercícios executados em código, o [registro do laboratório](03-aula2-laboratorio.md) com os cálculos manuais e o [experimento de ocorrências](07-aplicacao-ocorrencias.md), em que escolhi o modelo por validação cruzada (F1 macro 0,8457), testei uma vez (acurácia 0,8625) e escolhi o limiar de confiança no treino antes de confirmar no teste.**
- Como contribuímos com a equipe: **O trabalho deste módulo foi individual. Fiz todas as atividades e liguei o conteúdo ao projeto que desenvolvo com Arthur Rodrigues de Souza Vieira (livro de ocorrências digital), no qual sou responsável pelos dados e pela análise. O experimento da [atividade 07](07-aplicacao-ocorrencias.md) mostra como a categorização em dupla que planejamos afeta um futuro modelo de classificação.**
- O que preciso revisar: **Validação com divisão temporal (vou precisar dela se aplicar ML ao livro de ocorrências real), calibração de probabilidades e métodos de agrupamento, que ainda não pratiquei em código.**
- Ferramentas de apoio utilizadas, incluindo IA quando houver, e como verifiquei as respostas: **Python 3.13, Jupyter e Google Colab, scikit-learn 1.9.1, pandas 3.0.5, NumPy 2.5.3 e matplotlib 3.11.2, além da documentação oficial do scikit-learn. Conferi os números executando os notebooks do início ao fim com semente 42, comparando a saída com os arquivos `resultados_execucao.json` e `resultados_ocorrencias.json` e refazendo à mão os cálculos de acurácia, sensibilidade e MAE.**

## Critérios de avaliação

Escala sugerida do material: nível 3 consistente, 2 adequado com lacunas, 1 parcial, 0 ausente/incoerente. Nota do critério = peso × nível/3. A professora pode ajustar a aplicação.

| Critério | Peso aula 1 | Peso aula 2/PBL |
| --- | --- | --- |
| Problema e conceitos | 3,0 | 2,0 |
| Dados e justificativa | 2,0 | 2,0 |
| Método e avaliação | 1,0 | 3,0 |
| Interpretação e responsabilidade | 2,0 | 2,0 |
| Clareza e colaboração | 2,0 | 1,0 |
| Total | 10,0 | 10,0 |

Na aula 1, método corresponde à avaliação proposta. Na aula 2, inclui execução e interpretação. A maior acurácia isolada não assegura a melhor avaliação da atividade.

## Fontes de apoio

- SCIKIT-LEARN. *User Guide*. https://scikit-learn.org/stable/user_guide.html.
- SCIKIT-LEARN. *Common pitfalls and recommended practices*. https://scikit-learn.org/stable/common_pitfalls.html.
- ORANGE DATA MINING. *Test and Score*. https://orangedatamining.com/widget-catalog/evaluate/testandscore/.

Referências indicadas no material didático do módulo, consultadas em 16 out. 2026.

[Voltar ao início](README.md).
