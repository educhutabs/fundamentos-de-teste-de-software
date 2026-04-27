# Erro, Defeito e Falha em Software

Este documento detalha três conceitos fundamentais da engenharia de qualidade de software que, embora frequentemente usados como sinônimos no dia a dia, possuem definições distintas e precisas. Compreender a diferença entre erro, defeito e falha é essencial para comunicação técnica clara dentro de times de desenvolvimento e qualidade.

---

## Visão Geral

Na prática, é comum ouvir frases como "encontrei um bug", "o sistema deu erro" ou "o software falhou" sendo usadas de forma intercambiável. Essa imprecisão, apesar de aceitável em conversas informais, pode gerar ambiguidade durante análises de causa raiz, relatórios de incidente e processos de auditoria.

O IEEE Std 1044 e o ISTQB definem cada um desses termos de maneira específica, estabelecendo uma cadeia causal que vai da ação humana até a manifestação observável no sistema:

Erro (humano) --> Defeito (no artefato) --> Falha (no comportamento)

Essa distinção permite que times de qualidade identifiquem não apenas o que quebrou, mas onde e por que quebrou, orientando tanto a correção quanto a prevenção.

---

## Erro

Um **erro** é uma ação humana que produz um resultado incorreto. É o ponto de origem da cadeia: algo que uma pessoa fez ou deixou de fazer durante o ciclo de desenvolvimento.

O erro não está no software em si, mas na mente ou na ação de quem o produziu. Pode ocorrer em qualquer fase do projeto: levantamento de requisitos, arquitetura, implementação, configuração de ambiente ou escrita de casos de teste.

**Causas comuns**

- Interpretação incorreta de um requisito
- Falta de conhecimento sobre a regra de negócio
- Fadiga, distração ou pressão por prazo
- Comunicação deficiente entre áreas (negócio, desenvolvimento, QA)
- Uso inadequado de uma linguagem, framework ou API

**Exemplo**

Um desenvolvedor interpreta que um campo de data deve aceitar o formato `DD/MM/YYYY`, mas a especificação define `YYYY-MM-DD`. Essa interpretação equivocada é o erro. Nenhum artefato foi comprometido ainda neste momento — o problema existe apenas como uma decisão incorreta.

---

## Defeito

Um **defeito** (também chamado de *bug* ou *fault*) é a representação concreta de um erro em um artefato de software. É o resultado de um erro que foi materializado: código, configuração, documentação, script de banco de dados, caso de teste, entre outros.

O defeito existe no artefato independentemente de ter sido executado. Ele pode estar presente no sistema por dias, semanas ou anos sem ser percebido, caso o caminho de código afetado nunca seja exercitado.

**Características**

- Pode estar em qualquer artefato, não apenas no código-fonte
- Nem todo defeito resulta em falha visível: depende das condições de execução
- Um único erro pode introduzir múltiplos defeitos
- Um defeito pode ser detectado por revisão estática (code review, análise de requisitos) antes mesmo de qualquer execução

**Exemplo**

Seguindo o exemplo anterior, o desenvolvedor implementa a validação do campo de data aceitando apenas o formato `DD/MM/YYYY`. O código está escrito, versionado e integrado à base. O defeito agora existe no artefato: a lógica de validação está incorreta em relação ao requisito original.

---

## Falha

Uma **falha** é o comportamento incorreto observado durante a execução do software como consequência de um defeito que foi ativado. É a manifestação visível do problema: o sistema faz algo diferente do que deveria fazer.

A falha é o que o usuário final, o testador ou o sistema de monitoramento percebe. Ela ocorre em tempo de execução e pode se manifestar de formas diversas: mensagem de erro, dado incorreto, travamento, comportamento inesperado ou ausência de resposta.

**Importante**

Nem todo defeito gera uma falha imediatamente. Um defeito só se manifesta como falha quando as condições necessárias para ativá-lo são satisfeitas: uma entrada específica, um volume de dados, uma combinação de estados do sistema ou um contexto de ambiente particular.

Isso explica por que sistemas com defeitos conhecidos podem operar aparentemente sem problemas por longos períodos.

**Exemplo**

Um usuário tenta cadastrar uma data no formato `2025-04-26`. O sistema rejeita a entrada com uma mensagem de erro informando que o formato é inválido. Essa rejeição indevida é a falha: o comportamento observado diverge do comportamento esperado pelo requisito.

---

## Implicações para o Processo de Qualidade

**Detecção antecipada**

Quanto mais cedo na cadeia o problema for identificado, menor o custo de correção. Técnicas de **verificação estática** como code review, linting, análise de requisitos e inspeção de documentos atuam antes que qualquer defeito chegue a se manifestar como falha.

**Análise de causa raiz**

Quando uma falha é encontrada em produção, a investigação deve percorrer o caminho inverso: da falha ao defeito, do defeito ao erro. Essa prática, conhecida como Root Cause Analysis (RCA), é o que diferencia times que corrigem sintomas de times que eliminam causas.

**Comunicação e registro**

Em ferramentas de gestão de defeitos (Jira, Azure DevOps, YouTrack), o registro adequado de um defeito deve descrever:

- A **falha observada**: o que aconteceu
- O **comportamento esperado**: o que deveria acontecer
- As **condições de reprodução**: como chegar até a falha
- O **artefato comprometido** (quando identificado): onde está o defeito

Usar os termos com precisão nesse contexto melhora a rastreabilidade e a eficiência da correção.

---

## Resumo

A distinção entre erro, defeito e falha não é meramente acadêmica. Ela fundamenta como times de qualidade comunicam problemas, conduzem investigações e estruturam melhorias de processo. Incorporar esses conceitos ao vocabulário do time é um passo concreto em direção a uma cultura de qualidade mais madura e eficaz.

---

## Referências

- IEEE Std 1044. *Standard Classification for Software Anomalies*. IEEE, 2009.
- ISTQB. *Syllabus Foundation Level*. International Software Testing Qualifications Board, 2023.
- MYERS, Glenford J.; SANDLER, Corey; BADGETT, Tom. *The Art of Software Testing*. 3. ed. Wiley, 2011.
- PRESSMAN, Roger S. *Engenharia de Software: Uma Abordagem Profissional*. 8. ed. McGraw-Hill, 2016.
