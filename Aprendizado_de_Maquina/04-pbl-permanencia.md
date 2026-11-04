<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# PBL integrador — Apoio à Permanência

## Identificação

- Estudante ou equipe: **Ramon Guilherme Marques do Nascimento**
- Turma: **Turma de Ciência de Dados – UDF — Sistemas de Informação**
- Data de realização: **16/10/2026**
- Integrantes e contribuições (se em equipe): **Atividade individual: elaborei toda a proposta, a partir do meu notebook do laboratório.**

## Contexto

Uma instituição quer compreender sinais associados à evasão e oferecer apoio antes do fim do semestre. Público-alvo: estudantes matriculados e equipe de apoio acadêmico. O cenário é didático e a prática usa dados sintéticos.

**Questão norteadora:** como identificar situações que merecem atenção e oferecer apoio, reconhecendo erros do modelo e dificuldades que os dados não capturam?

## Proposta da equipe

### 1. Delimitação

- Problema e público: **Quando a coordenação percebe que um estudante abandonou o curso, normalmente já passou da metade do semestre e não há mais o que oferecer. O público beneficiado são os estudantes matriculados; quem usa a informação é a equipe de apoio acadêmico, que tem tempo limitado para contatos individuais.**
- Decisão que o resultado pode apoiar: **A ordem em que a equipe de apoio faz os contatos na semana 5: quem recebe primeiro o convite para uma conversa, monitoria ou orientação de estudos. O modelo não decide quem "merece" apoio; ele só ajuda a ordenar uma fila limitada.**
- Definição de evasão, unidade e horizonte: **Considero evasão o estudante que, no fim do semestre, não tem matrícula ativa nem frequência nas últimas semanas. Trancamento formal e transferência interna ficam fora dessa definição, porque são saídas planejadas com tratamento próprio. Unidade: estudante em um semestre. Horizonte: previsão feita com dados até a semana 4, para o desfecho no fim do semestre.**

### 2. Perguntas de negócio

1. **Considerando a capacidade de atendimento da equipe de apoio (a ser informada pela instituição), quais estudantes deveriam ser contatados primeiro com base em frequência, nota parcial e entregas até a semana 4?**
2. **Quanto da evasão a equipe alcança com essa capacidade, e quanto a sensibilidade melhora se a capacidade for ampliada?**

### 3. Dados necessários

| Dado | Papel no projeto | Disponível quando? | Origem pretendida | Necessidade e risco |
| --- | --- | --- | --- | --- |
| Frequência acumulada até a semana 4 (%) | Atributo | Fim da semana 4 | Diário de classe | Necessário (2º atributo mais importante na simulação). Faltas abonadas e atrasos no lançamento distorcem o valor. |
| Nota parcial até a semana 4 (0–10) | Atributo | Fim da semana 4 | Sistema acadêmico | Necessário (atributo mais útil na simulação). Pode estar ausente se a avaliação ainda não foi lançada; tratar como ausência, não como zero. |
| Atividades entregues até a semana 4 | Atributo | Fim da semana 4 | Ambiente virtual (AVA) | Útil. Depende de cada professor usar o AVA; disciplinas sem AVA ficariam com dado faltante. |
| Situação da matrícula no fim do semestre | Alvo | Fim do semestre | Secretaria acadêmica | Indispensável para treinar e avaliar. A definição de evasão tem de ser a mesma em todos os semestres. |
| Código pseudonimizado do estudante | Ligação entre as bases (fora do modelo) | Sempre | Secretaria | Necessário para unir diário, notas e AVA. A tabela que liga código e matrícula fica com uma única pessoa responsável. |
| Dados socioeconômicos, raça, deficiência, idade | Fora do modelo; só para auditoria de equidade, se aprovada | — | — | Risco alto de discriminação. Só com base legal, aprovação ética e uso exclusivo para verificar se o modelo erra mais com algum grupo. |

Diferencie dados usados na simulação e dados que seriam necessários para uma investigação real: **No laboratório, usei 600 estudantes fictícios, três atributos gerados por uma fórmula conhecida e um único "semestre" com registros independentes. Uma investigação real precisaria de vários semestres de histórico (para treinar no passado e testar no futuro), de uma definição institucional de evasão, de dados de turmas e cursos diferentes, de informações que permitam auditar grupos e da voz dos próprios estudantes sobre o que dificulta a permanência. Tudo isso com aprovação do comitê de ética e conformidade com a LGPD.**

### 4. Abordagem e algoritmo

- Classificação, regressão ou outra formulação, com justificativa: **Classificação binária supervisionada: o alvo é uma categoria (evadiu/permaneceu) conhecida no histórico. Como a decisão real é ordenar uma fila, uso também a estimativa da classe 1 para ranquear os estudantes, e não só a classe prevista.**
- Algoritmo introdutório escolhido: **Árvore de decisão com imputação pela mediana em pipeline (`max_depth=5`, `min_samples_leaf=10`). Escolhi a árvore porque consigo mostrar à equipe de apoio as perguntas que ela faz ("nota até 6,21? frequência até 64,40?"), o que facilita a revisão humana.**
- Referência simples: **`DummyClassifier` que sempre prevê "permaneceu". Também uso como referência mental a regra que a equipe já usaria sem modelo: contatar quem tem frequência abaixo de 75%.**

### 5. Avaliação

- Preparação, divisão e validação: **Holdout estratificado 75/25 (450 treino, 150 teste), semente 42; imputação aprendida só no treino; profundidade e tamanho de folha escolhidos por validação cruzada estratificada em 5 partes no treino; teste usado uma única vez. Com dados reais: treinar nos semestres anteriores e testar no semestre seguinte.**
- Métricas e razão da escolha: **Sensibilidade da classe 1 (quantas evasões a lista alcança), precisão da classe 1 (quantos contatos são de quem realmente evadiria) e matriz de confusão, sempre comparadas com a referência. A acurácia entra só como visão geral. O erro mais caro é o falso negativo, mas o número de falsos positivos define se a equipe dá conta da lista.**
- Resultados efetivamente calculados e link da evidência: **Validação: 0,7222 ± 0,0391. Teste: acurácia 0,780 (referência 0,593); TN = 75, FP = 14, FN = 19, TP = 42; sensibilidade 0,689; precisão 0,750. No experimento de limiar (validação no treino), baixar o corte de 0,5 para 0,3 elevou a sensibilidade de 0,676 para 0,800, mas aumentou os sinalizados de 190 para 251 em 450. Evidências: [notebook executado](notebooks/laboratorio-ramon.ipynb), [registro do laboratório](03-aula2-laboratorio.md), [matriz de confusão](assets/matriz-confusao.png).**
- Erros relevantes e consequências: **Os 19 falsos negativos representam 31% das evasões do teste: estudantes que não entrariam na lista prioritária. Os 14 falsos positivos receberiam um convite de que talvez não precisassem. Com essa taxa de falsos negativos, o modelo não pode ser o único caminho até o apoio.**

### 6. Limites e proteção

- Por que os resultados não demonstram causalidade? **Porque o modelo só aprendeu que certas combinações de nota, frequência e entregas aparecem junto com a evasão nesses dados. Ninguém alterou a nota de um estudante para ver o que acontecia. Nota baixa e evasão podem ter a mesma origem (jornada de trabalho, doença na família, dificuldade financeira), ou a relação pode ser inversa: quem já decidiu sair deixa de estudar. E, neste caso, a associação foi literalmente escrita na fórmula da simulação.**
- Por que dados sintéticos não validam uso institucional? **Porque eles só contêm as suposições de quem escreveu a simulação: três atributos uniformes, uma fórmula logística e ruído controlado. Uma turma real tem atributos correlacionados, registros faltando por motivos que importam, mudanças de um semestre para outro e grupos com realidades diferentes. Um bom resultado no sintético mostra que o procedimento funciona, e não que o modelo serviria para estudantes reais.**
- Que grupos podem ser mal representados? Como investigar isso com evidências apropriadas? **Estudantes do noturno que trabalham, ingressantes (que ainda não têm histórico), estudantes com deficiência (cuja frequência pode ser afetada por acessibilidade), cursos pequenos e quem cursa disciplinas sem AVA (sem dado de entregas). Para investigar, com dados reais autorizados, eu compararia por grupo a sensibilidade e a taxa de falsos positivos, verificaria se cada grupo tem casos suficientes para a comparação valer, e ouviria os próprios estudantes. O conjunto sintético não tem esses grupos, então não permite afirmar nada sobre equidade.**
- Como minimizar dados, restringir acesso e definir retenção? **Aplico o que já defini no meu projeto de ocorrências de condomínio: anonimizar na origem e mostrar só o necessário. Aqui, isso significa: usar só os três atributos; trabalhar com código pseudonimizado; dar acesso à lista apenas à equipe de apoio, com registro de quem consultou; não repassar a lista a professores; apagar as listas nominais no fim do semestre e guardar só os números agregados de desempenho para reavaliar o modelo (LGPD, princípios de finalidade e necessidade).**
- Como garantir revisão humana e contestação? **Antes de qualquer contato, uma pessoa da equipe revisa a lista e pode retirar ou acrescentar nomes com base no que sabe. O estudante é informado de que o convite é opcional e pode perguntar por que foi contatado, corrigir dados errados e pedir para não ser contatado de novo. Nenhuma decisão acadêmica (nota, bolsa, matrícula) usa a sinalização. O modelo é reavaliado a cada semestre.**

### 7. Recomendações de apoio

- Ação voluntária proposta: **Uma mensagem curta e acolhedora, assinada por uma pessoa da equipe e não pelo "sistema", convidando para uma conversa de 15 minutos e apresentando monitoria, grupos de estudo e auxílios disponíveis. O texto nunca menciona "risco de evasão".**
- Como acolher estudantes não sinalizados pelo modelo: **Divulgar os mesmos serviços para todas as turmas no início do semestre, manter um canal de autoencaminhamento sem burocracia e permitir que professores e colegas indiquem alguém. Como o modelo deixou de fora 31% das evasões no teste, esses caminhos são parte da solução, e não um complemento.**
- O que precisa ser verificado antes de aplicação real: **Desempenho com dados reais e divisão por semestre; auditoria de erros por grupo; aprovação ética e jurídica; definição oficial de evasão; capacidade real da equipe (que define o limiar); e um piloto em poucas turmas, medindo se o convite aumenta de fato a permanência, comparado a turmas sem o piloto.**

Previsões não são certezas. Priorize apoio e revisão humana, sem punições ou decisões automáticas prejudiciais.

## Apresentação de cinco minutos

| Tempo | Conteúdo | Responsável |
| --- | --- | --- |
| 1 minuto | Problema e dados | Ramon Guilherme Marques do Nascimento |
| 2 minutos | Método e resultados | Ramon Guilherme Marques do Nascimento |
| 1 minuto | Limitações | Ramon Guilherme Marques do Nascimento |
| 1 minuto | Recomendações de apoio | Ramon Guilherme Marques do Nascimento |

## Contribuições

| Integrante | Contribuição verificável |
| --- | --- |
| Ramon Guilherme Marques do Nascimento | Atividade individual: execução e interpretação do [notebook](notebooks/laboratorio-ramon.ipynb), incluindo o experimento de limiar usado na seção 5; redação de todas as seções desta proposta. |

[Voltar ao início](README.md).
