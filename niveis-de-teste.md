# Níveis de Teste de Software

Este documento apresenta os principais níveis de teste de software e descreve seu propósito, escopo, objetivos e aplicação ao longo do ciclo de desenvolvimento. A compreensão correta desses níveis é essencial para estruturar uma estratégia de qualidade consistente, evitar lacunas de cobertura e reduzir sobreposição desnecessária entre atividades de teste.

Os níveis de teste organizam o esforço de verificação e validação conforme o objeto testado e a perspectiva adotada sobre o sistema. Em termos práticos, eles permitem responder com clareza o que está sendo testado, em que momento, com qual objetivo, por quem e com base em quais artefatos.

---

## Visão geral

Níveis de teste são agrupamentos de atividades que são planejadas e gerenciadas em conjunto, cada um focado em um escopo específico do produto. À medida que o desenvolvimento avança, o foco do teste se expande: parte-se de elementos menores e isolados, avança-se para integrações, evolui-se para o sistema completo e, por fim, valida-se sua aderência ao uso e às necessidades do negócio.

Em modelos sequenciais, os níveis de teste costumam ser relacionados ao V-Model, no qual cada etapa de especificação e construção possui uma contrapartida de verificação ou validação. Em abordagens iterativas e ágeis, essa relação continua válida como lógica conceitual, ainda que diferentes níveis coexistam dentro da mesma sprint, pipeline ou fluxo contínuo de entrega.

### Correspondência conceitual com o V-Model

- Requisitos de negócio e necessidades do usuário <-> Teste de aceitação.
- Requisitos de sistema <-> Teste de sistema.
- Arquitetura, interfaces e desenho de integração <-> Testes de integração.
- Design detalhado e implementação de componentes <-> Teste de componente.

Essa relação reforça um princípio importante da engenharia de qualidade: quanto mais cedo os testes forem pensados e preparados, menor tende a ser o custo de correção e menor o risco de propagação de defeitos para estágios posteriores.

---

## Estrutura de níveis

De acordo com o CTFL v4.0, os níveis descritos de forma explícita são:
- Teste de componente.
- Teste de integração de componentes.
- Teste de sistema.
- Teste de integração de sistemas.
- Teste de aceitação.

No uso cotidiano de times de engenharia, é comum encontrar uma simplificação desses níveis em quatro camadas clássicas: unitário, integração, sistema e aceitação. O arquivo original segue essa linha mais tradicional, o que é aceitável para fins introdutórios, mas em uma documentação de referência convém registrar a distinção mais precisa entre integração de componentes e integração de sistemas.

---

## Teste de componente

### Definição

O teste de componente, frequentemente chamado de teste unitário no uso cotidiano, verifica o comportamento de uma unidade isolada de software. Essa unidade pode ser uma função, método, classe, módulo ou outro elemento logicamente testável de forma independente.

Seu objetivo principal é confirmar que a menor parte verificável do sistema funciona corretamente conforme o comportamento esperado. Nesse nível, o foco está na lógica interna, nos fluxos de decisão, nos limites, nas exceções e nas saídas produzidas pela unidade testada.

### Características

- Costuma ser executado pelo próprio desenvolvedor.
- É rápido, frequente e altamente automatizável.
- Utiliza dublês de teste para isolar dependências externas.
- Favorece feedback imediato sobre alterações no código.

### Quando aplicar

Esse nível é especialmente eficaz quando implementado junto ao desenvolvimento ou antes dele, como ocorre em práticas como TDD. Quanto mais sólido for o teste de componente, menor tende a ser a propagação de defeitos simples para níveis superiores, nos quais o diagnóstico costuma ser mais caro e demorado [file:35].

---

## Teste de integração de componentes

### Definição

O teste de integração de componentes verifica a interação entre componentes que já foram individualmente testados. O foco deixa de ser o comportamento interno isolado de cada unidade e passa a ser a comunicação entre elas, incluindo troca de dados, contratos, chamadas, tratamento de erros e consistência do fluxo integrado.

Em muitos contextos, esse nível é chamado genericamente de teste de integração. Ainda assim, é útil manter a nomenclatura mais precisa quando se deseja diferenciar integrações internas entre componentes das integrações do sistema com soluções externas ou outros sistemas completos.

### Características

- Detecta defeitos de interface e acoplamento.
- Avalia contratos, serialização, mapeamento e orquestração entre componentes.
- Pode ser executado de forma incremental ou por blocos maiores de integração.
- Exige ambiente mais próximo do real do que o teste de componente.

### Exemplo

Em um serviço de pedidos, esse nível pode verificar se a camada de aplicação aciona corretamente o domínio, se os adaptadores persistem dados como esperado e se o retorno produzido mantém o contrato definido para o fluxo de negócio.

---

## Teste de sistema

### Definição

O teste de sistema verifica o comportamento do sistema completo e integrado, considerando-o como uma unidade única. Nesse nível, o interesse principal está no comportamento observável por interfaces externas, sem foco na implementação interna de cada componente.

Esse é o nível em que se avalia se o produto, como solução completa, atende aos requisitos especificados. Por isso, ele normalmente cobre tanto requisitos funcionais quanto atributos de qualidade não funcional, conforme o contexto do sistema.

### Características

- O objeto de teste é o sistema completo.
- A base de teste costuma derivar de requisitos de sistema e regras de negócio.
- É frequentemente conduzido por QA com maior independência em relação ao desenvolvimento.
- Pode incluir testes funcionais e não funcionais.

### Tipos frequentes neste nível

- Teste funcional.
- Teste de desempenho.
- Teste de segurança.
- Teste de usabilidade.
- Teste de compatibilidade.

### Leitura prática

Esse nível responde, em grande medida, à pergunta: “o sistema como um todo se comporta conforme o esperado?”. É um dos níveis mais importantes para validar comportamento fim a fim sob a perspectiva do produto em operação.

---

## Teste de integração de sistemas

### Definição

O teste de integração de sistemas verifica a interação entre o sistema sob teste e outros sistemas externos, internos ou de terceiros. Esse nível é explicitamente destacado no CTFL v4.0 e representa uma distinção importante em ambientes corporativos, nos quais integrações com ERPs, gateways, mensageria, plataformas legadas, provedores de autenticação e serviços externos são parte crítica da solução.

Enquanto a integração de componentes observa partes internas do mesmo sistema, a integração de sistemas concentra-se nas fronteiras entre soluções independentes. Nesse contexto, os riscos incluem incompatibilidade de contratos, latência, indisponibilidade, falhas de autenticação, inconsistência transacional e problemas de versionamento.

### Características

- Foca nas fronteiras entre sistemas independentes.
- Avalia protocolos, contratos, formatos, segurança e comportamento de integração.
- Costuma depender de ambientes compartilhados e maior coordenação entre equipes.
- É crítico em arquiteturas distribuídas, orientadas a serviços e baseadas em APIs.

### Exemplo

Uma plataforma de e-commerce que depende de gateway de pagamento, antifraude, ERP e transportadora precisa verificar não apenas o comportamento interno da aplicação, mas também a consistência de dados, as respostas dos provedores e os cenários de erro nessas integrações externas.

---

## Teste de aceitação

### Definição

O teste de aceitação verifica se o sistema atende às necessidades do negócio e se está apto para uso no contexto real ou esperado de operação. Nesse nível, a validação se orienta menos pela arquitetura técnica e mais pela aderência a processos, fluxos de trabalho, critérios de aceite e expectativas de usuários ou representantes do negócio.

Trata-se do nível mais diretamente relacionado à decisão de entrega. Em muitos contextos, sua aprovação funciona como condição formal para publicação, implantação ou aceite contratual do software.

### Características

- Envolve cliente, usuário final ou representante do negócio.
- Foca em fluxos de negócio e cenários de uso representativos.
- Pode ser manual, automatizado ou híbrido.
- Avalia prontidão para uso, e não apenas conformidade técnica.

### Formas frequentes de aceitação

- Teste de aceitação do usuário.
- Teste alfa.
- Teste beta.
- Teste de aceitação contratual.
- Teste de aceitação regulatória.

### Leitura prática

Esse nível responde à pergunta mais importante do ponto de vista de valor: “o software está adequado para ser usado, entregue ou aceito no contexto de negócio em que foi concebido?”.

---

## Teste de regressão

O teste de regressão não é, estritamente, um nível de teste no modelo do ISTQB, mas um tipo de teste relacionado a mudanças. Sua finalidade é detectar se defeitos foram introduzidos ou expostos em áreas que antes funcionavam corretamente após modificações no software, como correções, refatorações, novas funcionalidades ou alterações de configuração.

Por essa razão, ele é transversal e pode ser aplicado em qualquer nível: componente, integração de componentes, sistema, integração de sistemas ou aceitação. Em ambientes com CI/CD e alta cadência de entrega, a regressão automatizada assume papel central para reduzir risco de instabilidade contínua.

### Características

- É orientado a mudança.
- Pode ocorrer em qualquer nível de teste.
- Tem forte dependência de automação em ambientes de entrega frequente.
- Exige manutenção contínua da suíte para preservar relevância e eficiência.

---

## Critérios de distinção

Para evitar sobreposição entre níveis, recomenda-se diferenciá-los pelos seguintes atributos:
- Objeto de teste.
- Objetivo principal.
- Base de teste utilizada.
- Tipo de defeitos e falhas esperados.
- Responsáveis e grau de independência.
- Ambiente necessário para execução.

Essa separação é importante porque dois testes podem parecer semelhantes à primeira vista, mas pertencerem a níveis distintos em função do escopo real observado. Um mesmo fluxo de pedido, por exemplo, pode ser exercitado como teste de componente, integração de componentes, sistema, integração de sistemas ou aceitação, a depender do objeto avaliado e do propósito do teste.

---

## Visão consolidada

- **Teste de componente:** verifica unidades isoladas de código.
- **Teste de integração de componentes:** verifica interação entre componentes internos.
- **Teste de sistema:** valida o comportamento do sistema completo.
- **Teste de integração de sistemas:** valida a interação com sistemas externos ou independentes.
- **Teste de aceitação:** valida aderência ao negócio e prontidão para uso.
- **Teste de regressão:** protege qualquer nível contra efeitos colaterais de mudanças.

---

## Diretrizes conceituais

Para padronização neste repositório, adotam-se as seguintes diretrizes:
- “Teste unitário” pode ser usado como sinônimo operacional de “teste de componente”.
- “Teste de integração” deve ser qualificado quando necessário, distinguindo integração de componentes de integração de sistemas.
- “Teste de regressão” deve ser tratado como prática transversal, e não como nível formal.
- Estratégia de qualidade deve distribuir responsabilidade entre níveis, evitando concentração excessiva em testes de sistema ou aceitação.

---

## Encerramento

Os níveis de teste não são excludentes e não competem entre si. Em uma estratégia madura, eles se complementam para formar uma malha progressiva de detecção, prevenção e redução de risco ao longo do ciclo de vida do software.

A distribuição do investimento entre esses níveis depende do contexto do produto, da arquitetura, da frequência de mudança, da criticidade do domínio e da maturidade do time. Ainda assim, ignorar sistematicamente qualquer um desses níveis costuma deslocar risco e custo para momentos mais tardios, onde a correção tende a ser mais cara e mais impactante para o negócio.
