<img src="assets/logo-udf.jpg" alt="UDF Centro Universitário" width="230">

**Profa. Kadidja Valéria | UDF**  
Ciência de Dados e Aprendizado de Máquina · Sistemas de Informação · 2026.2

# PBL — Biblioteca em Foco

## Identificação

- Estudante ou equipe: **Ramon Guilherme Marques do Nascimento**
- Turma: **Turma de Ciência de Dados – UDF — Sistemas de Informação**
- Data de realização: **16/10/2026**
- Integrantes e contribuições (se em equipe): **Atividade individual: fiz a delimitação, o canvas e a conclusão.**

## Situação-problema

Uma biblioteca universitária enfrenta filas em horários específicos e baixa utilização de alguns serviços. A coordenação deseja melhorar o atendimento e planejar recursos. Este é um cenário didático.

**Público-alvo:** estudantes usuários, equipe de atendimento e gestão.

**Questão norteadora:** como os dados podem orientar o planejamento da biblioteca e a oferta de serviços sem identificar ou discriminar seus usuários?

## Investigação em equipe

1. Delimitem o problema e a decisão a apoiar.
2. Registrem o que já sabem e o que precisam investigar.
3. Formulem duas perguntas de negócio.
4. Definam a unidade de análise, os atributos e o alvo, quando houver.
5. Justifiquem a abordagem e indiquem se uma análise descritiva já seria suficiente.
6. Proponham avaliação, cuidados com os dados e limitações.

## Canvas da equipe

| Campo | Registro |
| --- | --- |
| Problema e decisão | Há dois problemas diferentes que não devem ser misturados: (a) filas que se formam em certos horários no balcão; (b) serviços com pouca procura (por exemplo, empréstimo de notebooks, salas de estudo em grupo, treinamento em bases de dados). Decisões: (a) em quais faixas de horário reforçar o balcão ou abrir o autoatendimento; (b) quais serviços divulgar melhor, mudar de horário ou encerrar. |
| Público-alvo | Estudantes (esperam menos e conhecem os serviços), equipe de atendimento (escala que acompanha a demanda) e gestão (justificativa para alocar pessoas e orçamento). |
| O que sabemos | As filas acontecem "em horários específicos", mas não sabemos quais nem com que frequência. Alguns serviços são pouco usados. O sistema da biblioteca já registra empréstimos e devoluções com data e hora, e a catraca registra entradas. |
| O que precisamos investigar | Quanto tempo as pessoas realmente esperam (não existe esse registro hoje); se a fila acompanha o calendário acadêmico (início do semestre, semana de provas, prazo de TCC); se a baixa procura vem de desconhecimento, de horário inadequado ou de falta de necessidade; se quem desiste da fila aparece em algum registro. |
| Pergunta de negócio 1 | Em cada dia da semana e faixa de 30 minutos, quantos atendimentos no balcão devemos esperar nas próximas semanas do semestre? |
| Pergunta de negócio 2 | Entre os serviços pouco usados, quais são pouco conhecidos pelos estudantes e quais são conhecidos, mas não procurados? |
| Unidade de análise e período | P1: uma faixa de 30 minutos em um dia (ex.: terça, 18h00–18h30), nos dois últimos semestres. P2: o serviço em um semestre, com respostas de pesquisa agregadas, sem identificar quem respondeu. |
| Atributos, unidades e origem pretendida | P1: dia da semana, faixa horária, semana do semestre e período do calendário (início/provas/férias), entradas na catraca na faixa (contagem), empréstimos e devoluções (contagem, sistema da biblioteca), atendentes escalados (pessoas). P2: uso registrado por serviço (contagem), respostas de pesquisa sobre conhecimento e interesse (escala 1–5), horário de oferta do serviço. |
| Alvo e momento em que será conhecido, ou ausência de alvo | P1: alvo = número de atendimentos no balcão na faixa, conhecido ao fim de cada faixa; a previsão é feita na sexta-feira para a semana seguinte. P2: não há alvo; é uma pergunta descritiva, respondida com contagens e pesquisa. |
| Abordagem e justificativa | Começo pela **análise descritiva**: um mapa de calor de atendimentos por dia × faixa horária, separado por período do calendário. A mesma técnica entra no meu projeto de ocorrências de condomínio (mapa de calor dia da semana × horário), e minha aposta é que, aqui também, ela resolve a maior parte da escala. Só depois testaria uma **regressão** para P1 e a adotaria apenas se ela tivesse MAE menor que a média histórica da mesma faixa. Para P2, não vejo ganho em ML: uma pesquisa curta e as contagens de uso respondem a pergunta. |
| Alternativa sem ML | Mapa de calor e tabela de médias por faixa horária e período do calendário, atualizados no painel da gestão; pesquisa de 5 perguntas sobre os serviços; teste de mudar o horário de um serviço por um mês. |
| Como avaliar a proposta | P1: MAE em atendimentos por faixa, calculado em semanas futuras que o modelo não viu (divisão temporal), comparado à média histórica. Efeito real: medir o tempo de fila por amostragem (cronometrar algumas faixas) antes e depois da nova escala. P2: uso dos serviços divulgados no semestre seguinte, comparado com o anterior. |
| Privacidade e limitações | Trabalhar só com contagens por faixa horária, sem matrícula, nome ou curso; pesquisa anônima; acesso aos dados brutos só para a equipe da biblioteca; descarte dos registros individuais da catraca após a agregação. Limitações: quem desistiu da fila não aparece em nenhum registro; o calendário muda de um semestre para outro; estudantes que nunca vão à biblioteca não respondem nem aparecem nos dados, então a pesquisa sobre serviços fica enviesada para quem já frequenta. |

## Registro de colaboração

| Integrante | Papel | Contribuição |
| --- | --- | --- |
| Ramon Guilherme Marques do Nascimento | Todos os papéis (atividade individual) | Delimitei os dois problemas, preenchi o canvas, defini unidade, atributos e alvo, propus a avaliação e os cuidados com privacidade e escrevi a conclusão. |

## Conclusão da equipe

**Proposta:** separar o problema das filas do problema dos serviços pouco usados. Para as filas, construir primeiro um mapa de calor de atendimentos por dia × faixa de 30 minutos e por período do calendário, e ajustar a escala com base nele. Uma regressão só entra se reduzir o MAE em relação à média histórica, avaliada em semanas futuras. Para os serviços, uma pesquisa anônima curta e as contagens de uso, sem ML. Em ambos os casos, os dados ficam agregados e sem identificação.

**Dúvida ainda aberta:** como estimar a demanda reprimida, ou seja, quem desistiu da fila? Uma ideia é contar, por amostragem, quantas pessoas entram na fila e quantas são atendidas em algumas faixas, mas isso exige observação presencial.

**Feedback recebido e melhoria realizada:** A registrar após a apresentação.

## Entrega

Canvas preenchido e síntese para apresentação de dois minutos. Avaliar coerência da pergunta, dados, abordagem, responsabilidade e colaboração. [Voltar ao início](README.md).
