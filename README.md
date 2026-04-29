# Qualidade de Software: Fundamentos

Este repositório reúne documentação técnica introdutória sobre os conceitos fundamentais de qualidade e teste de software. O conteúdo foi organizado de forma progressiva, partindo da definição do que é software até os princípios que orientam como o teste deve ser conduzido na prática.

---

## Estrutura do Repositório

### 1. Fundamentos de Teste de Software

> `fundamentos-de-teste-de-software.md`

Ponto de entrada do repositório. Apresenta o que é software, como ele se classifica e por que testá-lo é uma prática de engenharia, não uma etapa opcional. Cobre os principais tipos e níveis de teste e contextualiza o impacto financeiro e operacional da ausência de qualidade no processo de desenvolvimento.

---

### 2. Erro, Defeito e Falha

> `erro-defeito-falha.md`

Detalha três termos centrais da qualidade de software que, apesar de serem usados como sinônimos no dia a dia, possuem definições técnicas distintas e uma relação causal bem definida:

Erro (humano) --> Defeito (no artefato) --> Falha (no comportamento)

Compreender essa cadeia é essencial para comunicação precisa em análises de causa raiz, relatórios de incidente e registros em ferramentas de gestão de defeitos.

---

### 3. Os 7 Princípios do Teste de Software

> `7-principios-do-teste.md`

Apresenta os sete princípios estabelecidos pelo ISTQB que fundamentam qualquer abordagem séria de teste.

Entre os temas abordados: por que o teste exaustivo é impossível, como os defeitos se distribuem no sistema, por que testes repetidos perdem eficácia ao longo do tempo e por que a ausência de falhas não é sinônimo de qualidade.

---

### 4. Níveis de Teste de Software

> `niveis-de-teste.md`

Detalha os principais níveis de teste — unitário, integração, sistema, aceitação e regressão — explicando o escopo, o propósito e o momento adequado de aplicação de cada um. Apresenta o modelo V como referência estrutural e discute a relação entre os níveis de teste e pipelines de integração contínua.

Indicado para quem já compreende o que é teste e quer entender como organizar o esforço de qualidade ao longo do ciclo de desenvolvimento.

## Ordem de Leitura Recomendada

Os documentos foram escritos de forma independente, mas seguem uma progressão lógica:

Fundamentos de Teste  -->  Erro, Defeito e Falha  -->  Os 7 Princípios do Teste --> Níveis de Teste

Seguir essa sequência garante que os conceitos de base estejam estabelecidos antes dos temas mais específicos.

---

## Sobre o Conteudo

Todo o material é baseado em referências consolidadas da indústria, incluindo o syllabus do ISTQB Foundation Level, normas IEEE e bibliografia clássica de engenharia de software. As referências completas estão listadas ao final de cada documento.

O repositório será expandido com novos tópicos ao longo do tempo, mantendo o mesmo padrão de linguagem técnica, objetiva e acessível.

---

## Contribuições

Contribuições são bem-vindas. Se você identificar imprecisões conceituais, quiser propor novos tópicos ou sugerir melhorias na clareza do conteúdo, abra uma issue ou envie um pull request com a descrição da alteração proposta.

---

## Referências Gerais

- ISTQB. *Syllabus Foundation Level*. International Software Testing Qualifications Board, 2023.
- IEEE Std 1044. *Standard Classification for Software Anomalies*. IEEE, 2009.
- IEEE Std 829. *Standard for Software and System Test Documentation*. IEEE, 2008.
- MYERS, Glenford J.; SANDLER, Corey; BADGETT, Tom. *The Art of Software Testing*. 3. ed. Wiley, 2011.
- PRESSMAN, Roger S. *Engenharia de Software: Uma Abordagem Profissional*. 8. ed. McGraw-Hill, 2016.
- KANER, Cem; BACH, James; PETTICHORD, Bret. *Lessons Learned in Software Testing*. Wiley, 2001.
