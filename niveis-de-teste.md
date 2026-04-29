# Níveis de Teste de Software

Este documento apresenta os principais níveis de teste de software, detalhando o propósito, o escopo e as características de cada um. Compreender em que nível cada tipo de teste atua é fundamental para planejar uma estratégia de qualidade eficaz e evitar tanto lacunas quanto sobreposições desnecessárias no esforço de teste.

---

## O que São Níveis de Teste

Níveis de teste são agrupamentos que organizam as atividades de teste de acordo com o estágio de desenvolvimento em que são realizadas e com o escopo do que está sendo verificado. Cada nível corresponde a uma perspectiva diferente sobre o sistema: desde a menor unidade de código isolada até o software completo em operação no ambiente do usuário.

A definição dos níveis está diretamente relacionada ao Modelo V (V-Model), que estabelece uma correspondência entre as fases de desenvolvimento e as fases de teste:

```
Requisitos de negócio    <-->  Teste de Aceitação
Requisitos de sistema    <-->  Teste de Sistema
Design de alto nivel     <-->  Teste de Integração
Design de baixo nível    <-->  Teste Unitário
                  [ Implementação ]
```

Essa correspondência reforça o princípio do teste antecipado: cada fase de desenvolvimento possui sua respectiva contrapartida de verificação e, quanto antes os testes são planejados, menor é o custo de correção de defeitos.

Na prática, os níveis não são estanques. Em metodologias ágeis, por exemplo, diferentes níveis de teste coexistem dentro de uma mesma iteração. O que permanece constante é a lógica de cada nível: o que ele verifica, quem o executa e quais artefatos são utilizados como base.

---

## Teste Unitário

**O que é**

O teste unitário verifica o comportamento de uma unidade isolada do sistema — tipicamente uma função, método ou classe — sem depender de outros componentes. O objetivo é garantir que cada parte do código funcione corretamente de forma independente, antes de sua integração ao restante do sistema.

**Características**

- Responsabilidade: É executado pelo próprio desenvolvedor durante a fase de implementação.

- Agilidade: É rápido de executar e de fácil automatização.

- Isolamento: Não depende de banco de dados, rede, sistemas de arquivos ou outras dependências externas; estas são substituídas por dublês de teste (mocks, stubs, fakes).

- Abrangência: Cobre caminhos lógicos, condições de contorno e casos de erro dentro da unidade testada.

**Quando aplicar**

O teste unitário é mais eficaz quando escrito simultaneamente ao código ou antes dele, como na prática do TDD (Test-Driven Development). A ausência de testes unitários eleva o custo de manutenção, pois qualquer alteração no código torna-se uma fonte de risco desconhecido.

**Exemplo**

Uma função que calcula o valor de desconto sobre um pedido deve ser testada com entradas variadas, como: percentual zero, percentual máximo permitido, valores negativos e valores acima do limite, verificando se o retorno corresponde exatamente ao esperado em cada cenário.

---

## Teste de Integração

**O que é**

O teste de integração verifica o comportamento do sistema quando dois ou mais componentes são combinados. O foco não reside na lógica interna de cada componente — responsabilidade do teste unitário —, mas sim na comunicação entre eles: troca de dados, contratos de interface e comportamento conjunto.

**Características**

- Detecção de falhas de interface: Identifica defeitos que só se manifestam na interação entre módulos, como incompatibilidades de contrato, falhas de serialização e problemas de sincronização.

- Abordagens variadas: Pode ser realizado de forma incremental (integrando componente a componente, como Top-down ou Bottom-up) ou de forma abrangente (Big Bang).

- Dependência de ambiente: Diferente do teste unitário, este nível depende de ambientes mais próximos do real, podendo envolver bancos de dados, APIs externas e sistemas de mensageria.

**Exemplo**

A comunicação entre um serviço de pedidos e um serviço de estoque: deve-se testar se, ao criar um pedido, o serviço de estoque é acionado corretamente, a quantidade de itens é reservada e a resposta retorna com o status esperado para o fluxo do sistema.

---

## Teste de Sistema

**O que é**

O teste de sistema avalia o comportamento do software como um todo, em um ambiente que simula ou replica as condições de produção. Neste nível, o software é tratado como uma caixa-preta: o foco reside no comportamento observável por meio de suas interfaces externas, sem considerar a implementação interna do código.

**Características**

- Abrangência: É realizado após a integração de todos os componentes e módulos.

- Multifuncionalidade: Cobre tanto requisitos funcionais quanto não funcionais (desempenho, segurança, usabilidade e confiabilidade).

- Independência: Executado, preferencialmente, por uma equipe de QA independente do time de desenvolvimento.

- Base de Teste: Utiliza casos de teste derivados diretamente das especificações de requisitos e regras de negócio.

**Tipos de teste frequentemente realizados neste nível**

- Teste Funcional: verifica se o sistema executa as funcionalidades conforme o especificado.

- Teste de Desempenho: avalia o tempo de resposta, o throughput e o comportamento sob carga.

- Teste de Segurança: identifica vulnerabilidades e valida os controles de acesso e proteção de dados.

- Teste de Usabilidade: avalia a facilidade de uso e a experiência do usuário na interação com a interface.

- Teste de Compatibilidade: verifica o comportamento em diferentes navegadores, sistemas operacionais ou dispositivos.

**Exemplo**

Um sistema de gestão de pedidos testado de ponta a ponta (End-to-End): desde a criação do pedido pelo cliente, passando pela validação de estoque, processamento de pagamento e geração de nota fiscal, até a atualização final do status. Todo o fluxo é verificado via interface do usuário (UI) ou por meio das APIs públicas.

---

## Teste de Aceitação

**O que é**

O teste de aceitação verifica se o sistema atende aos critérios definidos pelo negócio e se está pronto para ser entregue ao usuário final. É o último nível de validação antes da entrada em produção e tem como referência os requisitos de negócio, em vez da especificação técnica.

**Características**

- Envolvimento do cliente: Conduzido com a participação ativa do cliente, do usuário final ou de um representante do negócio (Product Owner).

- Foco no negócio: Prioriza fluxos de uso reais e processos operacionais, em vez de casos extremos ou detalhes puramente técnicos.

- Critério de saída: A aprovação neste nível é, em geral, uma condição formal e contratual para o deploy em produção.

- Flexibilidade: Pode ser executado de forma manual ou automatizada, dependendo da maturidade do processo e do contexto do projeto.

**Tipos de teste de aceitação**

- Teste de Aceitação do Usuário (UAT): Conduzido pelos usuários finais para validar se o sistema suporta os fluxos de trabalho diários.

- Teste Alfa: Realizado internamente por membros da organização (mas fora da equipe de desenvolvimento), antes de disponibilizar o software a usuários externos.

- Teste Beta: Realizado por um grupo restrito de usuários reais em um ambiente controlado, visando colher feedbacks antes do lançamento oficial.

- Teste de Aceitação Contratual: Verifica se o sistema atende aos critérios e obrigações definidos formalmente em contrato.

- Teste de Aceitação Regulatória: Verifica a conformidade com normas, leis e regulamentações aplicáveis ao setor (ex: LGPD, normas do Banco Central).

**Exemplo**

Antes do go-live de um sistema de RH, os gestores de pessoas da empresa executam os fluxos de admissão, férias e desligamento de funcionários. Eles confirmam se o sistema se comporta conforme os processos internos da organização e se a interface é intuitiva o suficiente para a operação.

---

## Teste de Regressão

**O que é**

O teste de regressão verifica se alterações realizadas no sistema — como correções de defeitos, novas funcionalidades ou refatorações — não introduziram novos erros em funcionalidades que já estavam operando corretamente. É uma prática de proteção: garante que a evolução do software não comprometa sua estabilidade prévia.

**Características**

- Transversalidade: Pode ser aplicado em qualquer nível de teste (unitário, integração ou sistema).

- Automação como pilar: É altamente dependente de automação; executar manualmente uma suíte de regressão completa a cada alteração torna-se inviável em projetos com ciclos de entrega frequentes.

- Manutenção da suíte: A suíte de regressão deve ser mantida atualizada; casos de teste obsoletos ou redundantes reduzem a eficiência sem agregar cobertura real.

- Criticidade: É essencial em sistemas legados e em projetos com alta frequência de deploys.

**Relação com CI/CD**

Em pipelines de Integração Contínua (CI) e Entrega Contínua (CD), os testes de regressão automatizados são executados a cada novo commit ou pull request. Essa prática reduz o tempo de feedback e impede que códigos com regressões avancem para ambientes de homologação ou produção.

```
Commit  -->  Build  -->  Testes Unitarios  -->  Testes de Integracao  -->  Regressao  -->  Deploy
```

**Exemplo**

Após a correção de um defeito no módulo de cálculo de frete, a suíte de regressão é executada para garantir que o módulo de pedidos, o de descontos e o fluxo de checkout — que dependem indiretamente do cálculo de frete — continuem funcionando conforme o esperado.

---

## Visão Consolidada

- Unitário: foca em funções, métodos ou classes de forma isolada.

- Integração: foca na comunicação, nos contratos e na troca de dados entre componentes.

- Sistema: avalia o sistema completo e integrado sob a perspectiva de caixa-preta.

- Aceitação: valida os fluxos de negócio e a prontidão do software para o usuário final.

- Regressão: abrange qualquer escopo ou nível que possa ter sido afetado por mudanças recentes.



---

## Conclusão

Os níveis de teste não são excludentes e, na prática, coexistem dentro do ciclo de desenvolvimento. Uma estratégia de qualidade madura utiliza todos os níveis de forma complementar: os testes unitários garantem a base do código; os testes de integração validam os contratos entre componentes; os testes de sistema cobrem o comportamento observável; os testes de aceitação confirmam a aderência ao negócio; e os testes de regressão protegem o sistema ao longo de toda a sua evolução.

A escolha de quanto investir em cada nível depende do contexto do projeto — risco, frequência de mudanças, criticidade do sistema e maturidade do time —, mas ignorar qualquer um deles por completo é uma decisão que, inevitavelmente, tende a se manifestar como um custo elevado no futuro.

---

## Referências

- ISTQB. *Syllabus Foundation Level*. International Software Testing Qualifications Board, 2023.
- MYERS, Glenford J.; SANDLER, Corey; BADGETT, Tom. *The Art of Software Testing*. 3. ed. Wiley, 2011.
- PRESSMAN, Roger S. *Engenharia de Software: Uma Abordagem Profissional*. 8. ed. McGraw-Hill, 2016.
- HUMBLE, Jez; FARLEY, David. *Continuous Delivery*. Addison-Wesley, 2010.
