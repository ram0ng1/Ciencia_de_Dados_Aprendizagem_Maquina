<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# Questões de revisão — Registro individual

## Identificação

- Estudante ou equipe: **Ramon Guilherme Marques do Nascimento**
- Turma: **Turma de Ciência de Dados – UDF — Sistemas de Informação**
- Data de realização: **16/10/2026**
- Integrantes e contribuições (se em equipe): **Registro individual.**

Responda com suas palavras e apresente os cálculos quando solicitados. Os números dos exercícios manuais não são os resultados do laboratório.

## 1. Explique a diferença entre regra programada para bloquear uma palavra e modelo de spam treinado com exemplos.

**Resposta:** Na regra, o critério é meu: eu escrevo "se o assunto contém 'prêmio', mande para o spam". É transparente e previsível, mas só pega o que eu imaginei: "pr3mio" passa, e o e-mail da faculdade sobre o "prêmio de iniciação científica" é bloqueado. No modelo, eu não escrevo o critério; forneço milhares de mensagens já marcadas como spam ou legítimas, e o algoritmo descobre quanto cada pista pesa (palavras, links, remetente, horário, formatação). Ele generaliza para mensagens que nunca viu e pode ser retreinado quando os golpes mudam, mas herda os erros dos rótulos e é mais difícil de explicar por que bloqueou uma mensagem específica.

## 2. Por que codificar evadiu/permaneceu como 1/0 não transforma classificação em regressão?

**Resposta:** Porque os números 0 e 1 são só etiquetas; eu poderia ter usado "A" e "B" e nada mudaria. O que define a tarefa é a natureza do alvo: são duas categorias, sem valor intermediário (ninguém "evade 0,4") e sem ordem numérica com significado. Por isso, avalio com matriz de confusão, sensibilidade e acurácia, e não com MAE. Quando o modelo dá 0,7 para a classe 1, isso é uma estimativa de chance, e não uma "quantidade de evasão".

## 3. Uma biblioteca quer estimar empréstimos e descobrir perfis. Que tarefas correspondem a cada pergunta?

**Resposta:** Estimar empréstimos é **regressão** (supervisionado): o alvo é uma quantidade conhecida no histórico, como no laboratório, em que obtive MAE de 28,59 empréstimos por semana. Descobrir perfis de usuários é **agrupamento** (não supervisionado): não existe uma coluna "perfil" para aprender; os grupos são descobertos a partir dos padrões de uso e depois interpretados pela equipe.

## 4. O que são atributo, alvo e unidade de análise no laboratório educacional?

**Resposta:** A **unidade de análise** é cada linha da tabela: um estudante fictício em um semestre. Os **atributos** são o que se sabe sobre ele no momento da previsão (fim da semana 4): `frequencia_sem4`, `nota_sem4` e `entregas_sem4`. O **alvo** é o que se quer prever e que só se conhece depois: `evasao_fim_semestre` (0 = permaneceu, 1 = evadiu).

## 5. Por que calcular a mediana antes de dividir os dados pode invalidar a avaliação?

**Resposta:** Porque a mediana calculada com os 600 registros inclui os 150 do teste. O valor usado para preencher as ausências do treino passaria a carregar informação do teste, o que é vazamento de dados. É pouco, mas o princípio é o que importa: o teste deveria representar estudantes que ainda não existem no momento do treino, e ninguém consegue calcular uma mediana com dados do futuro. Por isso, coloquei o `SimpleImputer` dentro do `Pipeline`: ele aprende a mediana só com o treino (e só com a parte de treino de cada dobra) e apenas a aplica ao teste.

## 6. Em uma matriz didática com TN=80, FP=5, FN=10, TP=5, calcule acurácia e sensibilidade. O resultado é suficiente para aprovar o modelo?

**Resposta:**

- Total = 80 + 5 + 10 + 5 = 100.
- Acurácia = (TN + TP) / total = (80 + 5) / 100 = **0,85**.
- Sensibilidade = TP / (TP + FN) = 5 / (5 + 10) = 5 / 15 ≈ **0,333**.
- Para completar, a precisão = TP / (TP + FP) = 5 / 10 = 0,50.

**Não é suficiente.** Há 15 positivos em 100 casos; um modelo que respondesse sempre "negativo" teria exatamente a mesma acurácia (85 / 100 = 0,85) sem esforço nenhum. Ou seja, a acurácia não mostra ganho sobre a referência, e o modelo perde 10 dos 15 positivos (dois em cada três). Antes de aprovar, eu precisaria saber o custo de um falso negativo nesse contexto, comparar com a referência em sensibilidade e precisão e testar em outros dados.

## 7. Valores reais 100, 120, 140 e previsões 110, 115, 130. Calcule MAE e informe a unidade se o alvo for vendas em reais.

**Resposta:**

| Real | Previsto | Erro absoluto |
| --- | --- | --- |
| 100 | 110 | 10 |
| 120 | 115 | 5 |
| 140 | 130 | 10 |

MAE = (10 + 5 + 10) / 3 = 25 / 3 ≈ **R$ 8,33**. A unidade do MAE é a mesma do alvo: em média, cada previsão se afasta cerca de R$ 8,33 do valor real, para mais ou para menos.

## 8. Um R² de -0,2 significa “20% de acertos negativos”? Explique.

**Resposta:** Não. O R² não conta acertos. Ele compara o erro quadrático do modelo com o erro quadrático de prever sempre a média dos valores avaliados: R² = 1 − (erro do modelo / erro da média). Se R² = −0,2, então erro do modelo / erro da média = 1,2: o modelo erra 20% **mais** do que a estratégia trivial de chutar a média. É sinal de um modelo inútil ou de algo errado (atributos sem relação com o alvo, extrapolação, dados de teste muito diferentes do treino).

## 9. Uma árvore tem acurácia 1,00 no treino e 0,65 na validação. Que hipótese investigar e como?

**Resposta:** A hipótese principal é **sobreajuste**: a árvore cresceu até isolar cada registro de treino, decorando inclusive o ruído, e não generaliza. Para investigar, eu faria o que fiz no laboratório: validação cruzada no treino com árvores mais restritas (menor `max_depth`, maior `min_samples_leaf`), acompanhando se a distância treino–validação diminui e se a validação melhora. No meu experimento, a distância caiu de 0,154 (folha 5, profundidade livre) para 0,047 (folha 40). Eu também verificaria se há algum atributo que "entrega" a resposta só no treino (vazamento, identificadores), se há poucos dados e como a árvore se compara com a referência.

## 10. Por que escolher a profundidade pelo teste prejudica a estimativa final?

**Resposta:** Porque, a partir do momento em que o teste influencia uma escolha, ele vira parte do processo de ajuste. Ao testar várias profundidades e ficar com a que acertou mais no teste, eu escolho também a que teve mais "sorte" com aqueles 150 registros específicos. A acurácia final fica otimista, e não sobra nenhum dado independente para medir o desempenho real. Por isso, escolho na validação do treino e abro o teste uma única vez, no fim. Pelo mesmo motivo, no laboratório não apliquei ao teste o limiar 0,3 nem os pesos balanceados que testei depois.

## 11. Baixa frequência associada à evasão demonstra causa? Proponha explicação alternativa.

**Resposta:** Não. Associação mostra que as duas coisas aparecem juntas, e não que uma provoca a outra. Explicação alternativa: um estudante que começou a trabalhar em um horário que conflita com as aulas passa a faltar **e** acaba trancando ou abandonando. A causa comum é o emprego, e a frequência é só um sinal. Também pode haver causalidade reversa: quem já decidiu sair (por mudança de cidade, por exemplo) simplesmente para de ir às aulas.

## 12. Um modelo sinaliza um estudante como possível evasão. Que ação responsável pode ser adotada?

**Resposta:** Uma pessoa da equipe de apoio revisa o caso e, se fizer sentido, envia um convite pessoal e opcional para uma conversa, apresentando monitoria, orientação e auxílios, sem usar a expressão "risco de evasão". O estudante pode recusar, pedir explicação e corrigir dados. A sinalização não entra em nenhuma decisão acadêmica, fica com acesso restrito e é apagada no fim do semestre.

## Fontes adicionais consultadas

**Material da disciplina (Módulo IV) e o meu [notebook do laboratório](notebooks/laboratorio-ramon.ipynb); SCIKIT-LEARN. *User Guide* (Model evaluation; Decision Trees) e *Common pitfalls and recommended practices*. Disponível em: https://scikit-learn.org/stable/. Acesso em: 16 out. 2026. Ferramentas usadas: Python, Jupyter/Colab, scikit-learn e pandas, para conferir os cálculos das questões 6 e 7. As respostas são minhas.**

[Voltar ao início](README.md).
