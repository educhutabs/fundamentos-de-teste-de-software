# Fundamentos de Teste de Software

Este documento apresenta os conceitos fundamentais de software e teste de software, servindo como referência introdutória para desenvolvedores, analistas e times que estão iniciando ou consolidando sua cultura de qualidade.

---

## O que é software

Software é um conjunto de instruções lógicas, dados e documentação que, em conjunto, permitem a um computador executar tarefas específicas. Diferente do hardware, que é a parte física da máquina, o software é intangível: existe como código, reside em memória e se manifesta por meio do comportamento do sistema.

Do ponto de vista técnico, o software pode ser classificado em três grandes categorias:

- **Software de sistema**: responsável por gerenciar os recursos do hardware e fornecer uma plataforma para outros programas. Exemplos: sistemas operacionais (Linux, Windows), drivers e firmware.
- **Software de aplicação**: projetado para atender necessidades específicas do usuário final. Exemplos: ERPs, aplicativos web, sistemas de e-commerce.
- **Software embarcado**: integrado a dispositivos físicos, com recursos limitados e requisitos rígidos de tempo de resposta. Exemplos: software de roteadores, painéis de automóveis e eletrodomésticos inteligentes.

Independentemente da categoria, todo software é desenvolvido para resolver um problema dentro de um contexto determinado. Essa premissa é central para entender por que testá-lo é indispensável.

---

## O que é teste de software

Teste de software é o processo de avaliação de um sistema ou componente com o objetivo de verificar se ele satisfaz os requisitos especificados e identificar defeitos antes que cheguem ao ambiente de produção.

Testar não significa apenas "rodar o sistema e ver se funciona". É uma disciplina estruturada que envolve planejamento, modelagem de casos de teste, execução, registro de resultados e análise de evidências.

---

## Objetivo e Importância do Teste

#### Objetivo

O objetivo principal do teste de software é **reduzir o risco de falhas em produção**, garantindo que o sistema se comporte de acordo com o esperado sob as condições definidas. Isso implica:

- Verificar se os requisitos funcionais foram implementados corretamente.
- Validar que requisitos não funcionais (desempenho, segurança, usabilidade) estão sendo atendidos.
- Detectar defeitos o mais cedo possível no ciclo de desenvolvimento, quando o custo de correção é menor.
- Fornecer informações objetivas para que stakeholders tomem decisões embasadas sobre a entrega do software.

Uma citação amplamente utilizada na indústria resume bem essa lógica:

> "O teste não pode provar a ausência de defeitos, mas pode demonstrar a presença deles."
> -- Edsger W. Dijkstra

#### Importância

A ausência de testes estruturados tem custos diretos e indiretos que frequentemente superam o investimento que seria feito na qualidade desde o início.

**Custo de correção tardia**: estudos do setor, como os conduzidos pelo NIST e pelo IBM Systems Sciences Institute, demonstram que o custo de corrigir um defeito encontrado em produção pode ser de 10 a 100 vezes maior do que se ele fosse identificado durante o desenvolvimento.

**Impacto no negócio**: falhas em produção causam indisponibilidade de serviço, perda de receita, danos à reputação da marca e, em sistemas críticos (saúde, aviação, financeiro), podem representar risco à segurança de pessoas.

**Qualidade como cultura**: times que investem em testes automatizados e processos de qualidade bem definidos entregam software com maior previsibilidade, menor taxa de retrabalho e ciclos de deploy mais rápidos. Isso está alinhado com práticas modernas como CI/CD e DevOps.

**Conformidade e auditoria**: em domínios regulados (financeiro, saúde, defesa), os testes são exigidos por normas e regulamentações como ISO 25010, IEC 62304 e LGPD. A ausência de evidências de teste pode resultar em penalidades legais.

## Resumindo

Testar software não é uma etapa opcional ou burocrática do desenvolvimento. É uma prática de engenharia que protege o negócio, aumenta a confiança da equipe nas mudanças realizadas e melhora a experiência do usuário final. Quanto mais cedo e de forma mais sistemática os testes forem incorporados ao processo, maior será o retorno sobre esse investimento.

---

## Referências

- ISTQB. *Syllabus Foundation Level*. International Software Testing Qualifications Board, 2023.
- MYERS, Glenford J.; SANDLER, Corey; BADGETT, Tom. *The Art of Software Testing*. 3. ed. Wiley, 2011.
- IEEE Std 829. *Standard for Software and System Test Documentation*. IEEE, 2008.
- ISO/IEC 25010. *Systems and software Quality Requirements and Evaluation (SQuaRE)*. ISO, 2011.
