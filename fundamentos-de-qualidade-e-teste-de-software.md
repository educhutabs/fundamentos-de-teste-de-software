# Fundamentos de Teste de Software

Este documento apresenta os conceitos fundamentais de software e de teste de software. Seu objetivo é estabelecer uma base conceitual comum para desenvolvedores, analistas, testadores e demais integrantes de equipes de engenharia que desejam fortalecer sua cultura de qualidade e reduzir riscos ao longo do ciclo de vida de desenvolvimento.

---

## Visão geral

Software é um ativo lógico criado para atender necessidades específicas de negócio, operação ou experiência do usuário. Como qualquer produto de engenharia, ele está sujeito a falhas de especificação, implementação, integração e operação, o que torna o teste uma prática essencial para controle de risco e suporte à tomada de decisão sobre a entrega.

Teste de software não deve ser tratado como uma etapa isolada ao final do desenvolvimento. Em abordagens modernas de engenharia, ele compõe um conjunto de atividades contínuas de verificação, validação e geração de evidências sobre a qualidade do produto.

---

## O que é software

Software é o conjunto de programas, dados, regras e artefatos associados que permite a um sistema computacional executar funções específicas. Diferentemente do hardware, que representa os componentes físicos, o software se manifesta por meio de instruções lógicas, comportamento operacional e documentação de suporte.

Sob uma perspectiva prática, o software pode ser organizado em diferentes categorias, conforme sua finalidade e contexto de uso.

### Software de sistema

É o software responsável por gerenciar recursos computacionais e fornecer a base para execução de outros programas. Nessa categoria estão sistemas operacionais, drivers, utilitários de baixo nível e firmware [file:1].

Exemplos:
- Sistemas operacionais, como Linux e Windows.
- Drivers de dispositivos.
- Firmware embarcado em equipamentos.

### Software de aplicação

É o software construído para resolver necessidades específicas de usuários ou organizações. Normalmente está mais próximo do domínio de negócio e da experiência final de uso [file:1].

Exemplos:
- ERPs.
- Aplicações web.
- Plataformas de e-commerce.
- Sistemas corporativos internos.

### Software embarcado

É o software integrado a dispositivos físicos, geralmente com restrições de memória, processamento, energia ou tempo de resposta. Em muitos casos, opera em cenários críticos e exige alto grau de confiabilidade [file:1].

Exemplos:
- Roteadores.
- Painéis automotivos.
- Equipamentos médicos.
- Eletrodomésticos inteligentes.

Independentemente da categoria, todo software existe para resolver um problema dentro de um contexto específico. Por isso, avaliar seu comportamento esperado e seus riscos operacionais é uma necessidade de engenharia, e não uma formalidade de processo.

---

## O que é teste de software

Teste de software é o conjunto de atividades executadas para avaliar um sistema, componente ou artefato com o objetivo de identificar defeitos e verificar se os resultados observados estão aderentes aos requisitos, expectativas e critérios definidos. Em termos práticos, o teste gera evidências sobre o comportamento do produto e apoia decisões sobre sua liberação ou evolução.

Essa definição é importante porque testar não significa apenas executar funcionalidades manualmente para verificar se “parecem funcionar”. Teste é uma disciplina estruturada, com planejamento, projeto de casos de teste, preparação de dados, execução, comparação entre resultados esperados e obtidos, registro de evidências e análise de desvios.

Em linhas gerais, o teste de software contribui para:
- Identificar defeitos antes da entrada em produção.
- Verificar a aderência aos requisitos funcionais.
- Avaliar características de qualidade não funcional.
- Reduzir incerteza sobre a entrega.
- Apoiar decisões técnicas e de negócio com base em evidências.

---

## Objetivos do teste

O objetivo central do teste de software é reduzir o risco de falhas relevantes em produção. Isso significa produzir informações confiáveis sobre o comportamento do sistema para que a organização saiba o que está pronto, o que precisa ser corrigido e quais riscos ainda permanecem antes da liberação.

De forma mais específica, o teste busca:
- Verificar se os requisitos funcionais foram implementados corretamente.
- Validar se atributos de qualidade, como desempenho, segurança e usabilidade, estão sendo atendidos.
- Detectar defeitos o mais cedo possível no ciclo de desenvolvimento.
- Aumentar a confiança da equipe nas mudanças realizadas.
- Apoiar stakeholders na tomada de decisão sobre entrega, aceite e priorização.

É importante destacar que teste não prova a ausência total de defeitos. Em vez disso, ele reduz incerteza, expõe problemas relevantes e amplia a visibilidade sobre o nível de qualidade alcançado em determinado momento do produto.

---

## Importância para o negócio

A relevância do teste de software vai além da dimensão técnica. Em ambientes corporativos, falhas em produção geram impacto financeiro, operacional, reputacional e regulatório, especialmente quando afetam fluxos críticos de negócio ou experiência do cliente.

### Redução de custo de correção

Defeitos identificados tardiamente tendem a custar mais para corrigir do que defeitos encontrados em fases anteriores do ciclo de desenvolvimento. O relatório do NIST sobre infraestrutura inadequada para qualidade de software associa falhas e retrabalho a impactos econômicos expressivos, reforçando a importância de prevenção e detecção antecipada.

Em documentação corporativa, é recomendável tratar esse ponto com cautela: mais importante do que repetir um multiplicador fixo é registrar o princípio de que defeitos tardios ampliam custo, esforço de análise, retrabalho, risco operacional e impacto no cliente.

### Continuidade operacional

Quando o software falha em produção, o efeito pode incluir indisponibilidade de serviço, degradação de performance, perda de receita, aumento de chamados e desgaste na relação com usuários e clientes. Em sistemas críticos, o impacto pode extrapolar o negócio e atingir segurança, conformidade ou continuidade operacional.

### Qualidade como capacidade organizacional

Equipes que incorporam práticas consistentes de teste e automação tendem a operar com maior previsibilidade, menor retrabalho e ciclos de entrega mais confiáveis. Esse comportamento é compatível com práticas de integração contínua, entrega contínua e engenharia de qualidade orientada a risco.

### Conformidade e evidência

Em setores regulados, testar não é apenas uma boa prática, mas uma necessidade de conformidade. Modelos e normas de qualidade, como a ISO/IEC 25010, ajudam a estruturar critérios de avaliação; em domínios específicos, outras normas podem exigir evidências formais de verificação e validação.

---

## Qualidade e requisitos não funcionais

A avaliação da qualidade de um software não se limita ao funcionamento correto de regras de negócio. Um sistema pode executar a funcionalidade esperada e, ainda assim, falhar do ponto de vista de desempenho, segurança, confiabilidade, compatibilidade ou usabilidade.

A ISO/IEC 25010 organiza a qualidade de produto em características como adequação funcional, eficiência de desempenho, compatibilidade, usabilidade, confiabilidade, segurança, manutenibilidade e portabilidade. Esse modelo é útil para ampliar a visão sobre o que deve ser avaliado ao longo da estratégia de testes.

Na prática, isso significa que uma abordagem madura de teste considera, entre outros pontos:
- O que o sistema faz.
- Como o sistema se comporta.
- Em quais condições ele opera bem.
- Quais atributos de qualidade são críticos para o negócio.

---

## Papel do teste no ciclo de desenvolvimento

Teste de software é mais efetivo quando distribuído ao longo de todo o ciclo de desenvolvimento. Quanto antes a equipe valida premissas, requisitos e implementações, menor tende a ser o acúmulo de defeitos, retrabalho e risco na fase final de entrega.

Em um fluxo de engenharia moderno, o teste pode aparecer em diferentes momentos:
- Na revisão de requisitos e critérios de aceite.
- Na validação de componentes e integrações.
- Na execução de testes funcionais e não funcionais.
- Na coleta de evidências para aceite e liberação.
- No monitoramento pós-implantação para aprendizado contínuo.

Essa visão reforça que qualidade não é responsabilidade exclusiva de um papel ou área isolada. Ela depende de colaboração entre produto, desenvolvimento, testes, operações e gestão.

---

## Diretrizes conceituais

Para fins de alinhamento organizacional, este documento parte das seguintes diretrizes:

- Teste é uma atividade de engenharia orientada à redução de risco.
- Qualidade deve ser construída ao longo do processo, não apenas inspecionada no final.
- Evidências de teste apoiam decisões, mas não substituem julgamento técnico e de negócio.
- Requisitos funcionais e não funcionais devem ser considerados na estratégia de qualidade.
- A maturidade de testes contribui para previsibilidade, governança e sustentabilidade da entrega.

---

## Encerramento

Testar software é uma prática essencial para proteger o negócio, sustentar a evolução do produto e aumentar a confiança nas mudanças realizadas. Mais do que encontrar defeitos, o teste fornece visibilidade objetiva sobre riscos, aderência a requisitos e nível de qualidade disponível para entrega em um dado contexto.

Quando incorporado desde cedo e de forma sistemática, o teste fortalece a engenharia, reduz retrabalho e melhora a capacidade da organização de entregar software com consistência e responsabilidade.
