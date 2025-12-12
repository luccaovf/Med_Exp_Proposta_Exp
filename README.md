# Proposta de Experimento para TCC

# 1. Identificação Básica

## 1.1 Título do Experimento

Impacto do TDD na Implementação Correta de Casos de Borda em Validações de APIs REST

## 1.2 ID / Código

EXP-TDD-REST-EDGECases-2025

## 1.3 Versão do Documento e Histórico de Revisão

| Versão | Data       | Responsável   | Descrição                              |
| ------ | ---------- | ------------- | -------------------------------------- |
| v1.0   | 23/11/2025 | Lucca Oliveira Vasconcelos de Faria | Criação do documento |
| v1.1   | 24/11/2025 | Lucca Oliveira Vasconcelos de Faria | Atualização do GQM |
| v2.0   | 24/11/2025 | Lucca Oliveira Vasconcelos de Faria | Seções 4 - 6 |
| v3.0   | 26/11/2025 | Lucca Oliveira Vasconcelos de Faria | Seções 7 - 9 |
| v4.0   | 01/12/2025 | Lucca Oliveira Vasconcelos de Faria | Seções 10 - 12 |
| v4.1   | 05/12/2025 | Lucca Oliveira Vasconcelos de Faria | Revisão do tamanaho do estudo |
| v5.0   | 05/12/2025 | Lucca Oliveira Vasconcelos de Faria | Seção 13 |
| v5.1   | 05/12/2025 | Lucca Oliveira Vasconcelos de Faria | Reescrita seção 13 |
| v6.0   | 12/12/2025 | Lucca Oliveira Vasconcelos de Faria | Seções 14 - 20 |




## 1.4 Datas

- Criação: 23/11/2025
- Última atualização: 12/12/2025

## 1.5 Autores

| Nome          | Área                   | Contato                                             |
| ------------- | ---------------------- | --------------------------------------------------- |
| Lucca Oliveira Vasconcelos de Faria  | Engenharia de Software | [lovfaria@sga.pucminas.br](mailto:lovfaria@sga.pucminas.br) |

## 1.6 Responsável Principal (PI / Dono do Experimento)

Lucca Oliveira Vasconcelos de Faria — Aluno responsável pelo experimento

Responsabilidades:

- Desenho e execução do experimento
- Coleta e análise de dados
- Redação dos resultados e defesa

## 1.7 Projeto / Iniciativa Relacionada

Experimento inscrito como parte do Trabalho de Conclusão de Curso (TCC) do curso de Engenharia de Software. O estudo será feito sobre um protótipo acadêmico (micro-módulo de API de um sistema de gestão simples, por exemplo, endpoint de cadastro de clientes/ordens) desenvolvido especificamente para o experimento.

# 2. Contexto e Problema

## 2.1 Descrição do Problema

Em APIs REST, uma grande proporção de erros ocorre porque validações não tratam corretamente casos de borda. Exemplos comuns:

- O sistema aceita valores "quase válidos"
- Regras funcionam no “caso típico”, mas falham nos extremos
- Inputs incomuns passam despercebidos
- Bugs só aparecem após integração com outros serviços

Esses defeitos não são triviais e geralmente só são percebidos tarde. A hipótese informal inicial seria: TDD pode aumentar o foco nesses cenários antes da implementação, reduzindo falhas.

## 2.2 Contexto Organizacional e Técnico

Este experimento será conduzido em um contexto acadêmico, com 12 a 24 estudantes de cursos de Engenharia de Software ou áreas correlatas, atuando como participantes no papel de desenvolvedores.

Esses participantes possuem formação heterogênea, variando entre iniciantes e intermediários, refletindo um perfil próximo ao de desenvolvedores iniciantes em cenários profissionais. O experimento será realizado em ambiente controlado de laboratório ou remoto, utilizando ferramentas gratuitas:

- Controle de versão: Git e GitHub
- Desenvolvimento: VS Code, IntelliJ Community ou outra IDE gratuita
- Testes: JUnit ou Pytest ou Jest
- Execução de API: Spring Boot, Express ou Django REST (à escolha da coordenação)
- Testes funcionais: Postman ou Newman
- Duas equipes (ou grupos) serão formadas para investigação experimental:
- Grupo TDD (Tratamento): 6 a 12 participantes
- Grupo Desenvolvimento Tradicional (Controle): 6 a 12 participantes

Cada grupo implementará os mesmos requisitos da API de gestão de limites de transações financeiras, mas usando técnicas distintas, permitindo comparação direta entre abordagens.

## 2.3 Trabalhos e Evidências Prévias (internos e externos)

Estudos gerais sobre TDD:

- Mostram que TDD tende a melhorar qualidade, mas resultados variam.
- Poucos estudos focam especificamente em casos de borda, embora autores como Beck (TDD by Example) enfatizem sua importância.

Lacuna identificada:

- Não há evidências empíricas específicas avaliando se TDD realmente aumenta a cobertura e correção de cenários extremos em validações REST.

## 2.4 Referencial Teórico e Empírico Essencial

- TDD — Red/Green/Refactor: foco no comportamento esperado antes do código.
- Casos de Borda: conforme Boundary Value Analysis e testes de particionamento.
- Validações REST: regras formais + regras de negócio + consistência.
- Qualidade de Testes: não basta testar o caso “feliz”; cenários limite têm alto poder de revelar defeitos.

# 3. Objetivos e Questões (Goal / Question / Metric — GQM)

## 3.1 Objetivo Geral

Analisar o uso de Test-Driven Development com o propósito de avaliar seu impacto na implementação correta e completa de casos de borda na perspectiva do desenvolvedor responsável no contexto de um protótipo acadêmico de API REST.

## 3.2 Objetivos Específicos

- O1: Avaliar a cobertura de casos de borda obtida durante o desenvolvimento.
- O2: Avaliar a ocorrência de falhas relacionadas a casos de borda.
- O3: Avaliar o esforço de retrabalho após detecção de problemas.
- O4: Avaliar a precisão e confiabilidade das validações em cenários-limite.

## 3.3 Tabela GQM

| **Objetivo**                                      | **Perguntas (Q)**                                                                    | **Métricas (M)**                                                             |
| ------------------------------------------------- | ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| **O1 - Cobertura de Casos de Borda**              | **Q1.1:** A implementação com TDD cobre mais casos de borda definidos?               | M1. Cobertura de Casos de Borda (%)<br>M2. Número de Testes de Borda         |
|                                                   | **Q1.2:** A implementação com TDD testa mais variações dentro de limites?            | M3. Variedade de Partições de Limite<br>M4. Densidade de Testes (%)          |
|                                                   | **Q1.3:** A implementação com TDD apresenta maior cobertura de código?               | M5. Cobertura de Código (%)<br>M6. Linhas de Código Exercitadas              |
| **O2 - Falhas em Casos de Borda**                 | **Q2.1:** A abordagem TDD reduz a quantidade de falhas em cenários-limite?           | M7. Falhas de Borda Detectadas<br>M8. Taxa de Falhas por Execução            |
|                                                   | **Q2.2:** As falhas de borda aparecem mais tarde no ciclo quando TDD não é usado?    | M9. Tempo até Detecção de Falhas<br>M10. Número de Falhas Pós-Entrega        |
|                                                   | **Q2.3:** A severidade média das falhas é menor com TDD?                             | M11. Severidade Média das Falhas<br>M12. Proporção de Falhas Críticas        |
| **O3 - Esforço de Retrabalho**                    | **Q3.1:** O TDD reduz o tempo gasto corrigindo falhas de borda?                      | M13. Tempo de Retrabalho (horas)<br>M14. Número de Commits de Correção       |
|                                                   | **Q3.2:** O TDD reduz o número total de correções necessárias?                       | M7. Falhas de Borda Detectadas<br>M14. Número de Commits de Correção         |
|                                                   | **Q3.3:** O TDD reduz o custo relativo por falha corrigida?                          | M13. Tempo de Retrabalho (horas)<br>M15. Custo por Falha Corrigida           |
| **O4 - Precisão e Confiabilidade das Validações** | **Q4.1:** As validações produzem respostas corretas com maior frequência usando TDD? | M16. Taxa de Respostas Corretas (%)<br>M17. Taxa de Falsos Negativos         |
|                                                   | **Q4.2:** A implementação com TDD reduz aceitação indevida de inputs inválidos?      | M18. Taxa de Falsos Positivos<br>M16. Taxa de Respostas Corretas (%)         |
|                                                   | **Q4.3:** A implementação com TDD cumpre melhor os requisitos funcionais de borda?   | M19. Conformidade com Requisitos (%)<br>M3. Variedade de Partições de Limite |

## 3.4 Tabela de Métricas

| **Métrica**                              | **Descrição**                                                  | **Unidade**     |
| ---------------------------------------- | -------------------------------------------------------------- | --------------- |
| **M1. Cobertura de Casos de Borda**      | Percentual de casos de borda planejados que foram testados.    | %               |
| **M2. Número de Testes de Borda**        | Quantidade total de testes automatizados voltados para bordas. | Contagem        |
| **M3. Variedade de Partições de Limite** | Número de partições de equivalência/límite distintas cobertas. | Contagem        |
| **M4. Densidade de Testes**              | Proporção de testes de borda por linhas de código.             | Testes/KLOC     |
| **M5. Cobertura de Código**              | Percentual de linhas executadas pelos testes.                  | %               |
| **M6. Linhas de Código Exercitadas**     | Linhas efetivamente executadas pelos testes.                   | Linhas          |
| **M7. Falhas de Borda Detectadas**       | Número total de falhas relacionadas a bordas.                  | Contagem        |
| **M8. Taxa de Falhas por Execução**      | Falhas detectadas a cada ciclo de teste.                       | Falhas/Execução |
| **M9. Tempo até Detecção de Falhas**     | Tempo entre implementação e descoberta da falha.               | Horas           |
| **M10. Falhas Pós-Entrega**              | Falhas encontradas após finalização inicial.                   | Contagem        |
| **M11. Severidade Média das Falhas**     | Média ponderada da severidade (ex: 1–5).                       | Escore          |
| **M12. Proporção de Falhas Críticas**    | Percentual de falhas classificadas como críticas.              | %               |
| **M13. Tempo de Retrabalho**             | Tempo gasto em correções.                                      | Horas           |
| **M14. Commits de Correção**             | Quantidade de commits dedicados a correções.                   | Contagem        |
| **M15. Custo por Falha Corrigida**       | Tempo total dividido pelo número de falhas corrigidas.         | Horas/Falha     |
| **M16. Taxa de Respostas Corretas**      | Proporção de respostas corretas em cenários-limite.            | %               |
| **M17. Taxa de Falsos Negativos**        | Casos inválidos aceitos como válidos.                          | %               |
| **M18. Taxa de Falsos Positivos**        | Casos válidos rejeitados indevidamente.                        | %               |
| **M19. Conformidade com Requisitos**     | Percentual de requisitos de borda cumpridos.                   | %               |

# 4 Escopo e contexto do experimento

## 4.1 Escopo Funcional / de Processo

### Incluído no Experimento

Implementação de uma API REST de Gestão de Limites de Transações Financeiras.

**Endpoints:**

- ```POST /usuarios```
- ```GET /usuarios/{id}```
- ```POST /transacoes```
- ```GET /usuarios/{id}/limite```

**Validações obrigatórias:**

- Valor da transação > 0.
- Valor ≤ limite diário restante.
- Limite diário deve ser > 0 ao criar usuário.
- Documento deve seguir formato válido (mínimo de caracteres).
- Bloqueio quando o limite é excedido.

**Processos avaliados:**

- Implementação com e sem TDD dos mesmos requisitos.
- Criação e execução de testes automatizados de borda.
- Registro e análise de falhas.

**Casos de borda explorados:**

- Limite zerado.
- Transações de valor mínimo e máximo.
- Somatório de transações excedendo limite.
- Inputs nulos, ausentes, negativos ou muito grandes.

### Excluído do Experimento

- Testes de carga, desempenho ou segurança.
- Desenvolvimento de interface gráfica ou aplicativo cliente.
- Envolvimento de equipes, clientes reais ou organizações externas.
- Deploy em ambiente corporativo ou cloud paga.
- Comparação entre múltiplos desenvolvedores (apenas um participante).
- Investigação de práticas ágeis fora do TDD (Scrum, Kanban, BDD, CI/CD etc.).
- Desenvolvimento de produto final ou comercial.

## 4.2 Contexto do Estudo

**Tipo de organização:** Atividade acadêmica com participação voluntária de alunos, sem vínculo com empresa.

**Tamanho:** Projeto médio, de 12 - 24 participantes.

**Tipo de projeto:** Protótipo educacional de API REST.

**Criticidade:** Média, sem uso comercial somente a nível de desenvolvimento acadêmico.

**Perfil do participante:** Estudante de Engenharia de Software com conhecimento básico/intermediário em programação e testes.

**Ambiente técnico:**

- Desenvolvimento local no computador pessoal.
- Controle de versão via Git.
- Execução e testes em ambiente local.
- Duração aproximada: 2 a 4 semanas.

## 4.3 Premissas

- Os estudantes possuem conhecimento inicial de TDD e testes unitários.
- As ferramentas necessárias estão instaladas e funcionando.
- O protótipo da API REST será simples o suficiente para ser implementado no tempo previsto.
- Os casos de borda podem ser definidos claramente antes da execução do experimento.
- Os computadores de desenvolvimento estará disponível durante o período do estudo.
- Os limites financeiros serão representados numericamente em valor monetário (ex.: decimal).
- Não haverá integração com sistemas reais de pagamento.
- Não haverá mudanças radicais no escopo após o início.

## 4.4 Restrições

- A disponibilidade de participantes deve permitir divisão equilibrada entre grupos.
- Diferenças de experiência podem introduzir variabilidade (serão medidas e controladas).
- Tempo limitado por semestre acadêmico.
- Apenas ferramentas gratuitas poderão ser utilizadas.
- Comunicação entre grupos sobre técnicas utilizadas deve ser evitada para evitar contaminação experimental.

## 4.5 Limitações Previstas

- Participantes são estudantes, o que pode limitar generalização para profissionais experientes.
- Diferenças de proficiência entre grupos podem afetar desempenho.
- O tempo disponível para treinamento em TDD pode não igualar experiência real.
- Tarefas de protótipo podem ser menos complexas que sistemas corporativos reais.

# 5. Stakeholders e Impacto Esperado

## 5.1 Stakeholders Principais

- Participantes do estudo (12–24 estudantes)
- Professor/orientador do TCC
- Faculdade/curso de Engenharia de Software
- Comunidade acadêmica
- Pesquisadores interessados em TDD

## 5.2 Interesses e Expectativas dos Stakeholders

| Stakeholder           | Interesse / Expectativa                                          |
| --------------------- | ---------------------------------------------------------------- |
| Participantes         | Aprender práticas de desenvolvimento e ter contato com TDD.      |
| Orientador            | Evidências claras, metodologia correta e resultados coerentes.   |
| Comunidade acadêmica  | Contribuição para o entendimento prático do TDD.                 |
| Futuros pesquisadores | Base para replicação, melhoria ou ampliação do estudo.           |

## 5.3 Impactos Potenciais no Processo / Produto

- A adoção do TDD pode aumentar o esforço inicial de desenvolvimento.
- O processo pode estender prazos, especialmente na fase de testes.
- Qualidade do protótipo pode melhorar em confiabilidade de validações.
- Pode gerar documentação extra (testes como especificação viva).
- Pode influenciar a percepção do estudante sobre práticas futuras.

# 6. Riscos, Premissas e Critérios de Sucesso

## 6.1 Riscos de Alto Nível

- **Técnicos:** Ferramentas incompatíveis, falhas no ambiente local, dificuldades com frameworks de teste.
- **Metodológicos:** Viés dos participantes na comparação entre métodos.
- **Cronograma:** Atrasos por carga acadêmica.
- **Escopo:** Protótipo mais complexo do que o previsto.
- **Motivação:** Perda de engajamento ao longo do estudo.

## 6.2 Critérios de Sucesso Globais (Go / No-Go)

O experimento será considerado bem-sucedido se:

- As métricas GQM forem coletadas integralmente.
- As duas abordagens (TDD e não-TDD) forem concluídas no protótipo.
- Existirem evidências mensuráveis que permitam comparação.
- O relatório final possibilitar conclusões úteis, mesmo que negativas.

Go: Se o planejamento, ferramentas e tempo estiverem garantidos.
No-Go: Se o escopo ou ferramentas não puderem ser executados conforme planejado.

## 6.3 Critérios de Parada Antecipada (Pré-execução)

O experimento deve ser adiado ou cancelado caso:

- Não haja computador funcional ou ambiente configurado.
- Os participantes não consigam implementar o protótipo mínimo.
- O cronograma acadêmico torne inviável a coleta de métricas.
- Haja perda de dados críticos sem possibilidade de reconstrução.
- Haja impedimento de saúde ou motivos maiores dos participantes durante ou brevemente anterior ao experimento.

# 7. Modelo Conceitual e Hipóteses

## 7.1 Modelo Conceitual do Experimento

O modelo conceitual do estudo assume que:

- A técnica de desenvolvimento utilizada (TDD vs. desenvolvimento tradicional) influencia:
  - a cobertura de testes e casos de borda,
  - a quantidade e severidade das falhas,
  - o esforço de retrabalho,
  - a precisão das validações da API.

**Pressupõe-se que:**

Quando o TDD é aplicado, os testes orientam o código desde o início, fazendo com que mais casos de borda sejam antecipados e corretamente tratados, reduzindo falhas e retrabalho.

**Enquanto:**

No desenvolvimento tradicional, o código é implementado antes e os testes depois, aumentando a chance de problemas passarem despercebidos e surgirem mais tarde.

Assim, o fator processo de desenvolvimento afeta diretamente as variáveis de qualidade e esforço.

## 7.2 Hipóteses Formais (H0 e H1)

**Hipóteses relacionadas ao Objetivo O1 – Cobertura de casos de borda**

- H0-O1: Não há diferença significativa na cobertura de casos de borda entre TDD e não-TDD.
- H1-O1: A cobertura de casos de borda é maior utilizando TDD.

**Hipóteses relacionadas ao Objetivo O2 – Falhas em cenários-limite**

- H0-O2: A quantidade e severidade das falhas em casos de borda não diferem entre TDD e não-TDD.
- H1-O2: O TDD reduz a quantidade e severidade das falhas em casos de borda.

**Hipóteses relacionadas ao Objetivo O3 – Esforço de retrabalho**

- H0-O3: O esforço de retrabalho não difere entre TDD e não-TDD.
- H1-O3: O esforço de retrabalho é menor com TDD.

**Hipóteses relacionadas ao Objetivo O4 – Precisão das validações**

- H0-O4: A precisão das validações em limites financeiros não difere entre TDD e não-TDD.
- H1-O4: A precisão das validações é maior com TDD.

## 7.3 Nível de Significância e Considerações de Poder

Será adotado nível de significância α = 0,05.

A amostra total prevista de 12 a 24 participantes, com 6 a 12 por grupo, permite:

- Poder estatístico estimado entre 0,60 e 0,80, dependendo da variabilidade entre participantes;
- Detecção de efeitos de magnitude moderada (Cohen’s d ≈ 0,5–0,7);

Embora a amostra não seja grande o suficiente para identificar efeitos muito pequenos, é adequada para detectar tendências significativas em métricas de qualidade e esforço.

# 8. Variáveis, Fatores, Tratamentos e Objetos de Estudo

## 8.1 Objetos de Estudo

Os objetos analisados no experimento serão:

- Código-fonte da API REST
- Casos de teste automatizados
- Requisitos de validação de limite financeiro
- Registros de falhas
- Commits de correção
- Execuções de testes
- Resultados das respostas da API

## 8.2 Sujeitos / Participantes

- 12 a 24 estudantes, variando entre novatos e intermediários.
- Serão distribuídos em dois grupos de mesmo tamanho.
- Critérios de inclusão/exclusão revisados para múltiplos participantes. Os participantes devem ter relativamente o mesmo nível de conhecimento de desenvolvimento com base em um pequeno questionário.

## 8.3 Variáveis Independentes (Fatores) e Níveis

**Fator principal:**

F1 – Abordagem de desenvolvimento

- Nível A: TDD
- Nível B: Desenvolvimento Tradicional (sem TDD)

## 8.4 Tratamentos (Condições Experimentais)

| Tratamento                           | Descrição                                                                                |
| ------------------------------------ | ---------------------------------------------------------------------------------------- |
| **T1 – TDD aplicado**                | Implementação da API seguindo ciclo Red-Green-Refactor, testes escritos antes do código. |
| **T2 – Desenvolvimento tradicional** | Implementação da API sem TDD, com testes escritos apenas após o código.                  |

## 8.5 Variáveis Dependentes (Respostas)

As variáveis dependentes são medidas associadas aos resultados:

1. Cobertura de testes (%)
  - Cobertura de linhas ou ramos obtida via ferramenta automática (ex.: JaCoCo).
2. Número de falhas detectadas
  - Quantidade total de falhas registradas durante a execução dos testes funcionais.
3. Esforço de retrabalho (tempo em minutos/hora)
  - Tempo dedicado a corrigir falhas após a primeira entrega da implementação.
4. Precisão das validações (proporção de respostas corretas)
  - Percentual de casos de teste (principalmente borda) que retornam valores corretos.

## 8.6 Variáveis de Controle / Bloqueio

- Requisitos: iguais para todos os participantes
- Tecnologias utilizadas: mesmo framework, mesma linguagem
- Tempo disponível: janela de execução igual para ambos os grupos
- Nível de experiência: balanceado entre grupos antes da divisão
- Treinamento prévio: mesmo treinamento para todos

## 8.7 Variáveis de Confusão Conhecidas

- Fadiga do participante
- Aprendizado entre uma abordagem e outra
- Motivação momentânea
- Preferência pessoal por método
- Ordem de implementação

Para minimizar impacto, os participantes terão uma breve introdução a desenvolvimento.

## 8.8 Tabela — Variáveis e Descrições

| Tipo             | Variável                     | Descrição                                  | Níveis / Valores               |
| ---------------- | ---------------------------- | ------------------------------------------ | ------------------------------ |
| **Independente** | Técnica de Desenvolvimento   | Método usado para implementar a API        | TDD / Tradicional              |
| **Dependente**   | Cobertura de Testes          | Percentual de linhas/ramificações cobertas | 0–100%                         |
| **Dependente**   | Falhas Detectadas            | Quantidade de falhas funcionais            | Contagem                       |
| **Dependente**   | Esforço de Retrabalho        | Tempo gasto corrigindo defeitos            | Minutos / horas                |
| **Dependente**   | Precisão das Validações      | Proporção de respostas corretas            | 0–1 (0–100%)                   |
| **Controle**     | Requisitos                   | Escopo da API                              | Fixo                           |
| **Controle**     | Experiência                  | Nivelamento prévio dos grupos              | Balanceado                     |
| **Controle**     | Ambiente Técnico             | Ferramentas e configurações                | Padronizado                    |
| **Controle**     | Tempo Disponível             | Janela de execução                         | Mesmo para todos               |
| **Confusão**     | Motivação                    | Variação de empenho individual             | Monitorado                     |
| **Confusão**     | Habilidade Técnica           | Capacidade individual                      | Medida via questionário        |

## 8.9 Tabela — Fatores, Tratamentos e Combinações

| Fator                        | Tratamentos   | Combinações Aplicadas                                       |
| ---------------------------- | ------------- | ----------------------------------------------------------- |
| Abordagem de desenvolvimento | TDD / Não-TDD | API implementada com TDD e a mesma API implementada sem TDD |

# 9. Desenho Experimental

## 9.1 Tipo de Desenho

Desenho entre-grupos (Between-Subjects) completamente randomizado

Justificativa:

- Apenas um participante disponível
- Permite comparar o mesmo sujeito em duas condições
- Minimiza variabilidade entre desenvolvedores

## 9.2 Randomização e Alocação

**O que será randomizado:**

Participantes serão distribuídos aleatoriamente com balanceamento pelo nível de experiência.

**Método de randomização:**

Ferramenta simples como random.org, planilha ou sorteio manual

## 9.3 Balanceamento e Contrabalanço

Estratégias adotadas:

- Questionário incial para ter uma faixa conhecida do conhecimento entre participantes.
- Balanceamento por experiência (iniciante/intermediário).
- Contrabalanço não é necessário, pois grupos são independentes.

## 9.4 Número de Grupos e Sessões

**Grupos:** 2 grupos, um tratamento para cada

**Sessões:** 2 ciclos completo de implementação

- Ciclo A — abordagem 1
- Ciclo B — abordagem 2

Justificativa:

- Mantém comparabilidade
- Reduz viés temporal
- Permite coleta completa de métricas

# 10. População, Sujeitos e Amostragem

## 10.1 População-alvo

A população real que o experimento pretende representar é:

Desenvolvedores backend (nível júnior a pleno) que implementam APIs REST em ambientes de produto ou protótipo, especialmente aqueles que lidam com validações financeiras (limites de transação).

Essa população inclui estudantes avançados de engenharia de software, estagiários e desenvolvedores em início de carreira que usam tecnologias como Java/Spring Boot, Node/Express ou similares.

## 10.2 Critérios de inclusão de sujeitos

 Para ser elegível como participante, o sujeito deve atender a todos os requisitos abaixo:

- Ser estudante de graduação em Engenharia de Software (ou desenvolvedor júnior/pleno) com interesse em participar do estudo;
- Ter conhecimento básico de programação backend (capacidade de implementar endpoints REST);
- Ter conhecimento básico de testes unitários (conhecer JUnit, pytest, jest ou similar) e controle de versão (Git);
- Disponibilidade para dedicar o período necessário (ex.: 2–4 semanas) conforme cronograma do experimento;
- Aceitar os termos do experimento e assinar/aceitar um termo de consentimento.

## 10.3 Critérios de exclusão de sujeitos

Não poderão participar:

- Pessoas com conflito de interesse direto (por exemplo, co-orientadores que avaliarão o TCC formalmente em nota);
- Indivíduos sem conhecimento mínimo de programação ou testes (por exemplo, sem experiência em Git ou sem noções de REST);
- Pessoas que não possam se comprometer com o cronograma ou com a disponibilidade exigida;

## 10.4 Tamanho da amostra planejado (por grupo)

- Total sugerido para maior validade: 12–24 participantes (cada um executando um subconjunto balanceado), dividido em:
  - Grupo A (TDD primeiro) = 6–12
  - Grupo B (Não-TDD primeiro) = 6–12
- Justificativa: tamanho típico para estudos experimentais em engenharia de software que buscam maior poder (~0.6–0.8 dependendo do efeito esperado). Requer mais recursos e coordenação.

## 10.5 Método de seleção / recrutamento

Amostragem de conveniência e convite em turmas/disciplina do curso de Engenharia de Software, listas de divulgação acadêmicas, e grupos de pesquisa. Usar formulário de inscrição (Google Forms) com triagem pelos critérios de inclusão. Se houver mais candidatos que vagas, selecionar por ordem de inscrição mantendo equilíbrio de experiência.

## 10.6 Treinamento e preparação dos sujeitos

Para nivelar conhecimento e reduzir viés por falta de habilidade:

- Sessão de treinamento (presencial ou gravada — 3 horas):
  - Introdução ao objetivo do experimento e à API de Gestão de Limites (endpoints, requisitos).
  - Breve revisão prática de TDD (ex.: ciclo Red-Green-Refactor com JUnit).
  - Guia rápido de uso das ferramentas: Git, execução de testes, geração de relatório JaCoCo, uso do template de time tracking.
  - Demonstração de um pequeno exemplo (ex.: criação de um endpoint simples com TDD).

Material preparatório (entregue antes):
- Documento com requisitos funcionais e lista de casos de borda (especificação da API).
- Guia passo-a-passo para configurar o ambiente (instalação JDK/Docker/IDE).
- Template de planilha para registro de tempo e template de issues no GitHub.
- Exemplos de testes unitários (boas práticas).
- Avaliação rápida de readyness: checklist que o sujeito preenche confirmando que ambiente está pronto e que compreendeu TDD mínimo.

# 11. Instrumentação e Protocolo Operacional

## 11.1 Instrumentos de coleta

Abaixo estão os instrumentos, sua função e formato esperado.

| Instrumento                                       | Descrição / Papel                                                                                               |
| ------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Repositório Git (GitHub)**                      | Armazena código, commits, branches e issues; usado para extrair número de commits, timestamps e mensagens.      |
| **JaCoCo (ou similar)**                           | Gera relatórios de cobertura de código (linhas/branches).                                                       |
| **Planilha de Time Tracking (CSV/Google Sheets)** | Registro manual de horas por tarefa (implementação, testes, correção).                                          |
| **GitHub Issues / arquivo de bugs**               | Registro das falhas encontradas (descrição, severidade, passo a passo, status).                                 |
| **Script de execução automatizada de testes**     | Script shell/Gradle/Maven que executa toda suíte de testes e gera saída padronizada; facilita coleta repetível. |
| **Google Forms / Questionário (pré e pós)**       | Questionário Likert para medir percepção de confiança, esforço percebido e observações qualitativas.            |
| **Matriz de Casos de Teste (CSV/Markdown)**       | Lista de todos os casos de borda planejados, com status (testado/não testado/ok/erro).                          |
| **Log de execução de testes (arquivo)**           | Saída dos runs de teste para auditoria (pass/fail, stacktrace).                                                 |
| **Ferramenta cloc**                               | Conta linhas de código (SLOC) para normalizar métricas por KLOC.                                                |
| **Planilha de métricas agregadas**                | Consolida métricas finais (falhas, cobertura, tempo, commits, taxas).                                           |

## 11.2 Materiais de suporte (instruções, guias)

Será fornecido o seguinte pacote de materiais:

- Guia do Experimento (PDF/Markdown): descrição do objetivo, cronograma, papel do participante, regras e boas práticas.
- Especificação da API (Markdown): endpoints, modelos de dados, regras de validação e lista de casos de borda obrigatórios.
- Tutorial TDD (PDF + exemplos de código): passo a passo do ciclo Red-Green-Refactor com exemplos na stack escolhida (Java/Spring Boot).
- Checklist de ambiente: verificação de ferramentas instaladas.
- Template de issue/bug (Markdown): campos exigidos (passos para reproduzir, entrada, saída esperada, severidade).
- Planilha de registro de tempo e métricas (Google Sheets): com guias de preenchimento.
- Formulários (Google Forms): pré-experiência (perfil), pós-experiência (Likert + comentários).
- Todos materiais estarão no repositório do experimento em uma pasta /docs.

## 11.3 Procedimento Experimental (Protocolo — passo a passo)

O protocolo abaixo descreve a operação completa, do preparo ao encerramento. Quem executar deve seguir fielmente e registrar desvios.

### Fase 0 — Preparação

- Configurar repositório Git com duas branches de trabalho (por exemplo tdd e tradicional) ou criar repositórios separados para cada tratamento.
- Preparar ambiente local conforme checklist e garantir que o script de testes e geração de cobertura funcionem.
- Preencher formulário pré-experiência (perfil).
- Carregar materiais de suporte e matriz de casos de borda no repositório.

### Fase 1 — Piloto 

Executar piloto (um endpoint simples) para verificar procedimentos.

### Fase 2 — Execução do Tratamento 1

- Definir quais endpoints serão implementados no ciclo 1 (por exemplo, POST /usuarios e GET /usuarios/{id}).
- Registrar hora inicial na planilha de time tracking.
- Implementar os endpoints seguindo a abordagem designada (TDD ou não-TDD conforme plano).
- TDD: escrever teste(s) de borda → executar (ver fail) → implementar código mínimo → executar testes → refatorar.
- Não-TDD: implementar código → escrever e executar testes após implementação.
- Para cada falha encontrada (durante testes locais ou execução posterior), abrir issue no GitHub com detalhe. Registrar tempo gasto em correções.
- Ao finalizar os endpoints do ciclo, rodar a suíte completa e gerar relatório JaCoCo e logs de teste. Registrar hora final.

### Fase 3 — Execução do Tratamento 2

- Pausa breve (min 24 horas) para reduzir fadiga; limpar estado local (migrations/data).
- Repetir passos 6–10 com o outro tratamento para os endpoints remanescentes (ou alternar ordem conforme contrabalanceamento).

### Fase 4 — Consolidação

- Consolidar métricas: extrair cobertura (JaCoCo), contar commits corretivos, somar horas de retrabalho, compilar lista de falhas.
- Preencher matriz de casos de borda com status final (ok/erro) e relacionar a qual tratamento pertence cada implementação.
- Aplicar questionário pós-experiência (Likert + comentários).

### Fase 5 — Análise e Relatório

- Calcular métricas definidas no GQM.
- Produzir relatórios descritivos (tabelas, gráficos) e análise qualitativa das observações.
- Documentar desvios do protocolo e lições aprendidas.

## 11.4 Plano de Piloto

- Objetivo do piloto: verificar validade do protocolo, funcionamento dos scripts de teste/relatório e se as instruções são claras.
- Escopo do piloto: implementar apenas um endpoint (ex.: POST /usuarios) com 3–5 casos de borda (nome, limite zerado, limite negativo).
- Participantes do piloto: o próprio autor (ou um colega voluntário, se disponível).
- Duração do piloto: 1–2 dias.
- Critérios de ajuste (com base no piloto):
- Se scripts de teste/relatório falharem → ajustar e reexecutar piloto.
- Se a especificação de casos de borda estiver ambígua → revisar e clarificar a lista.
- Se o tempo estimado para cada endpoint for muito maior/menor → ajustar cronograma e, se necessário, reduzir número de endpoints do experimento principal.
- Se o processo de registro de tempo for difícil → simplificar a planilha.

# 12. Plano de Análise de Dados (pré-execução)

## 12.1 Estratégia geral de análise (como responderá às questões)

A análise será conduzida seguindo diretamente o modelo GQM definido anteriormente.
Para cada questão de pesquisa, as métricas associadas serão utilizadas para produzir:

1. Análises descritivas (tabelas, gráficos, médias, medianas, desvios-padrão, distribuições);
2. Comparações entre tratamentos (TDD vs. Desenvolvimento Tradicional);
3. Testes estatísticos apropriados para verificar hipóteses formais (H0/H1);
4. Triangulação com dados qualitativos (questionários e observações registradas em logs/commits).

A estratégia geral é a seguinte:

### Q1 – Efetividade na cobertura de testes

- Usar métricas de cobertura de linha e de ramo (JaCoCo).
- Comparar o percentual obtido entre os tratamentos.
- Se mais de um endpoint for implementado, calcular média por endpoint e por tratamento.
- Responder a Q1 verificando se TDD produz maior cobertura inicial e maior aderência aos casos de borda.

### Q2 – Qualidade do software (defeitos introduzidos e retrabalho)

- Contar falhas registradas no GitHub, falhas pós-implementação e falhas detectadas nos casos de borda.
- Analisar a taxa de defeitos por KLOC.
- Comparar o retrabalho (tempo e commits corretivos) entre tratamentos.
- Concluir sobre a redução (ou não) de defeitos introduzidos ao seguir TDD.

### Q3 – Esforço e produtividade

- Analisar tempo total gasto para implementar cada endpoint, número de commits, tamanho do código produzido.
- Comparar a produtividade normalizada (ex.: tempo por caso de borda atendido).
- Responder se TDD aumenta tempo inicial, mas reduz retrabalho, ou se o esforço geral é maior/menor.

### Q4 – Robustez e completude de casos de borda

- Avaliar quantos casos de borda da matriz foram corretamente cobertos por cada abordagem.
- Verificar proporção de falhas críticas por tratamento.
- Relacionar com métricas de cobertura e com falhas encontradas durante testes complementares.

### Triangulação geral

- Cruzar resultados quantitativos com percepções qualitativas (esforço percebido, confiança e clareza).
- Observações sobre dificuldades específicas também serão usadas para interpretar anomalias nos dados.

O objetivo final é construir um conjunto coerente de evidências para suportar (ou rejeitar) as hipóteses sobre os efeitos de TDD na API de Gestão de Limites Financeiros.

## 12.2 Métodos estatísticos planejados

Testes paramétricos (se dados forem aproximadamente normais):
- t-test pareado (within-subject) para comparar TDD vs. Tradicional.
- ANOVA de medidas repetidas se houver mais de dois endpoints/tarefas.
- Testes não paramétricos (caso n pequeno ou distribuição não-normal):
- Wilcoxon signed-rank (within-subject).
- Mann–Whitney U (entre grupos, se houver grupo A/B).

Correlação:

- Spearman para relacionar métricas (ex.: cobertura × falhas).

Análise de efeito:

- Cohen’s d (tamanho do efeito).
- Cliff's Delta (para dados não paramétricos).

### Visualizações planejadas

- Boxplots por tratamento;
- Gráficos de barras para cobertura;
- Scatter plots para relação entre esforço e defeitos;
- Heatmaps mostrando acertos/falhas nos casos de borda.

## 12.3 Tratamento de dados faltantes e outliers

### Dados faltantes

Se ocorrerem dados ausentes:

1. Verificar causa: falha técnica, não preenchimento, perda de log.
2. Regra geral:

- Não imputar valores artificiais em métricas principais (cobertura, falhas, tempo).
- Se o dado faltar por falha técnica não recuperável, registrar explicitamente como “missing-technical”.
- Se faltar porque a tarefa não foi concluída, registrar como “missing-not-performed” e excluir da análise quantitativa, mantendo somente qualitativa.

3. Para questionários Likert ausentes: Excluir o item faltante da análise, manter o restante.

### Outliers

Outliers serão identificados usando:

  - Regra de IQR (1.5×IQR);
  - Z-score > 3, se aplicável.

- Outliers não serão removidos automaticamente; a regra é:
  - Manter, a menos que exista justificativa técnica clara (ex.: erro de medição, log corrompido).
- Se removido, será documentado com justificativa explícita no relatório.

### 12.4 Plano de análise para dados qualitativos

Dados qualitativos previstos:

- Comentários abertos no questionário pós-experimento;
- Observações registradas pelo executor (diário de bordo);
- Comentários em commits Git;
- Anotações do piloto;
- Observações sobre falhas e dificuldades percebidas.

### Técnica de análise planejada: Análise de Conteúdo Temática

1. Leitura aberta de todas as respostas e notas.
2. Codificação inicial: marcar trechos relacionados a temas como:
  - dificuldade percebida,
  - clareza dos requisitos,
  - percepção de esforço,
  - percepção de qualidade,
  - frustração,
  - fluidez do TDD,
  - vantagem percebida.

3. Agrupamento em categorias temáticas (ex.: “Esforço Percebido”, “Confiabilidade”, “Complexidade do Domínio”).
4. Matriz de apoio cruzando temas e tratamentos (TDD vs. Tradicional).
5. Interpretação relacionando temas qualitativos às métricas quantitativas.
  - Ex.: maior tempo em TDD → comentários sobre dificuldade;
  - Menos falhas → percepção de “confiança maior nos testes”.

### Resultado esperado da análise qualitativa

- Complementar as análises numéricas;
- Ajudar a interpretar efeitos onde métricas são inconclusivas;
- Destacar padrões comportamentais ou dificuldades que expliquem variações.

# 13. Avaliação de validade (ameaças e mitigação)
## 13.1 Validade de conclusão

A validade interna diz respeito à certeza de que diferenças observadas entre grupos são causadas pela técnica (TDD) e não por outros fatores.

**Possíveis ameaças**

- Amostra relativamente pequena (12–24 participantes), reduzindo poder estatístico.
- Violação de pressupostos estatísticos (normalidade, homocedasticidade).
- Erro de medida nas variáveis dependentes, especialmente tempo de retrabalho.
- Alta variabilidade entre participantes, afetando a detecção de efeitos reais.

**Mitigações planejadas**

- Uso de testes não paramétricos sempre que necessário.
- Coleta padronizada de métricas (scripts, logs e ferramentas automáticas).
- Balanceamento prévio dos grupos por nível de experiência.
- Reportar tamanhos de efeito (Cohen’s d, Cliff’s Delta) além de p-valor.

## 13.2 Validade interna

A validade interna diz respeito à certeza de que diferenças observadas entre grupos são causadas pela técnica (TDD) e não por outros fatores.

**Possíveis ameaças**

- História: eventos externos ao experimento podem afetar o desempenho dos participantes (ex.: interrupções).
- Maturação: participantes podem melhorar apenas pelo aprendizado natural ao longo do estudo.
- Seleção: diferenças iniciais entre grupos (experiência, familiaridade com testes).
- Difusão de tratamento: participantes de grupos diferentes trocam informações sobre as técnicas (TDD vs. não-TDD).
- Desempenho reativo: participantes podem agir de forma diferente porque sabem que estão sendo observados.

**Mitigações planejadas**

- Execução controlada em laboratório ou ambiente remoto monitorado.
- Atribuição aleatória aos grupos (random assignment).
- Treinamento padronizado antes da atividade, garantindo nivelamento inicial
- Instruções claras para evitar comunicação entre grupos durante a execução.
- Padronização da tarefa (mesmo backlog, mesma API a implementar).
- Equilíbrio da ordem (counterbalancing) caso participants executem mais de uma técnica.
- Redução de interferências externas com janelas de tempo definidas e ambiente silencioso.

## 13.3 Validade de constructo

**Possíveis ameaças**

- Cobertura de testes como substituto imperfeito de qualidade real.
- Precisão das validações pode depender de interpretação dos requisitos, não da técnica usada.
- Retrabalho medido em tempo, sujeito a pequenas variações individuais.
- Número de falhas depende da qualidade dos testes funcionais utilizados, que podem não ser exaustivos.

**Mitigações planejadas**

- Usar múltiplas medidas de qualidade (falhas + precisão + cobertura).
- Requisitos documentados de forma clara e exemplos fornecidos.
- Uso de testes funcionais padronizados, validados e idênticos para ambos os grupos.
- Coleta de retrabalho via logs automáticos, evitando autodeclaração.

## 13.4 Validade externa

Refere-se à capacidade de generalizar os resultados para outros contextos além do experimento.

**Possíveis ameaças**

- Participantes são estudantes, não desenvolvedores profissionais.
- Tarefas mais simples do que sistemas reais, limitando extrapolação.
- Ambiente acadêmico controlado, sem pressões de mercado.
- Baixa diversidade de domínios (apenas API financeira).

**Mitigações planejadas**

- Descrever detalhadamente o contexto para permitir replicações.
- Usar uma API com características próximas às reais (validações complexas).
- Comparar resultados com literatura existente com profissionais.
- Discutir limitações explicitamente no TCC para orientar generalização adequada.

## 13.5 Resumo das principais ameaças e estratégias de mitigação

| Validade       | Ameaças mais relevantes                                    | Mitigação                                                             |
| -------------- | ---------------------------------------------------------- | --------------------------------------------------------------------- |
| **Conclusão**  | Amostra pequena; variabilidade; erro de medida             | Testes não paramétricos; padronização; tamanhos de efeito             |
| **Interna**    | Diferença de habilidade; contaminação; ambiente inconsist. | Balanceamento; sessões separadas; checklist técnico                   |
| **Constructo** | Medidas imperfeitas; interpretação dos requisitos          | Múltiplas métricas; requisitos claros; testes funcionais padronizados |
| **Externa**    | Participantes estudantes; tarefas simples                  | Descrição detalhada; API próxima do real; comparação com literatura   |

# 14. Ética, Privacidade e Conformidade
## 14.1 Questões éticas (uso de sujeitos, incentivos, etc.)

O experimento envolve a participação de estudantes, o que requer atenção a possíveis questões éticas, tais como:

- Pressão para participar: estudantes podem sentir obrigação de participar caso a atividade seja aplicada em um ambiente educacional. Para mitigar esse problema, participação totalmente voluntária, sem impacto em notas, avaliações ou responsabilidades acadêmicas.
- Risco mínimo: as tarefas do experimento não envolvem risco físico, mas podem gerar ansiedade ou desconforto caso os participantes sintam desempenho inferior ao esperado. Como solução, reforço de que os resultados individuais serão anonimizados e não avaliativos.
- Incentivos e benefícios: incentivos simbólicos (ex.: certificado de participação) podem ser oferecidos, mas nenhum incentivo financeiro será utilizado para evitar viés ou coação.
- Uso de estudantes como sujeitos de pesquisa: há debate na literatura sobre sua representatividade. Sendo assim, transparência com os participantes sobre os objetivos e limitações do estudo, além de clara comunicação sobre sua liberdade de desistir.
- Exposição indevida de desempenho individual: resultados podem revelar níveis de habilidade. Logo, haverá a remoção de identificadores pessoais durante análise e apresentação dos resultados.

## 14.2 Consentimento informado

Todos os participantes receberão um Termo de Consentimento Livre e Esclarecido (TCLE) contendo:

- objetivo geral do experimento;
- descrição das atividades que serão executadas, duração prevista e ferramentas utilizadas;
- riscos potenciais (ex.: desconforto, carga cognitiva);
- benefícios indiretos (aprendizado sobre TDD, experiência prática em experimentos);
- esclarecimento de que a participação é voluntária e pode ser interrompida a qualquer momento;
- informações sobre uso, armazenamento e descarte dos dados;
- contato do responsável pelo estudo para dúvidas.

O consentimento será registrado por meio de assinatura física ou digital antes do início das atividades.

## 14.3 Privacidade e proteção de dados

Os seguintes tipos de dados serão coletados:

- informações de perfil (nível de experiência, familiaridade com testes);
- artefatos produzidos (código, testes, commits, logs);
- métricas automáticas (cobertura, falhas, tempo de retrabalho);
- respostas de questionários pós-atividade.

Medidas de proteção:

- Anonimização: cada participante receberá um identificador (P01, P02...).
- Separação de dados sensíveis: qualquer dado pessoal será armazenado separado das métricas.
- Controle de acesso: somente o pesquisador principal terá acesso à base completa.
- Criptografia e armazenamento seguro: arquivos hospedados em repositório privado ou armazenamento institucional protegido.
- Tempo de guarda: dados serão mantidos por até 12 meses após conclusão do estudo, sendo posteriormente excluídos.
- Nenhuma informação pessoal será divulgada em relatórios, artigos, apresentações ou TCC.

## 14.4 Aprovações necessárias

Dependendo das normas da instituição, o experimento pode exigir aprovações de:

- Comitê de Ética em Pesquisa (CEP): necessário se os participantes forem estudantes identificáveis e se houver coleta de dados pessoais.
- Professor orientador / coordenação do curso: aprovação obrigatória para realização em ambiente acadêmico.
- DPO (Encarregado de Proteção de Dados) da instituição: caso o experimento envolva coleta de dados pessoais conforme LGPD.

# 15. Recursos, Infraestrutura e Orçamento
## 15.1 Recursos humanos e papéis

Os papéis previstos no experimento são:

| Papel                                 | Responsabilidades                                                                     |
| ------------------------------------- | ------------------------------------------------------------------------------------- |
| **Pesquisador Principal (estudante)** | Planejamento, execução do experimento, coleta e análise dos dados, elaboração do TCC. |
| **Orientador**                        | Revisão metodológica, validação do desenho experimental, supervisão ética.            |
| **Apoio técnico (opcional)**          | Auxílio na configuração de ambiente ou suporte aos participantes durante a execução.  |
| **Participantes**                     | Execução das tarefas conforme tratamento atribuído e preenchimento de questionários.  |

## 15.2 Infraestrutura técnica necessária

Para execução do experimento, serão necessários:

- Ambientes de desenvolvimento individuais (VS Code, IntelliJ ou similar);
- Linguagem e framework do projeto (ex.: Java + Spring Boot);
- Ferramentas de teste (JUnit, Mockito);
- Ferramenta de cobertura de testes (JaCoCo ou equivalente);
- Repositório Git privado (GitHub, GitLab ou Bitbucket—versões gratuitas são adequadas);
- Scripts de coleta automática de logs e métricas;
- Ambiente padronizado para execução dos testes funcionais (Docker, Postman CLI ou Newman).

Toda a infraestrutura pode ser montada utilizando ferramentas gratuitas, adequadas ao contexto acadêmico.

## 15.3 Materiais e insumos

- Materiais necessários ao experimento incluem:
- Computadores pessoais ou laboratórios da instituição, todos com suporte à linguagem escolhida;
- Acesso à internet para uso de repositórios Git;
- Slides explicativos e guias para TDD, execução de testes e uso das ferramentas;
- Formulários digitais (Google Forms ou equivalentes) para consentimento e questionários;
- Documentação da API e requisitos funcionais padronizados em PDF;
- Scripts de validação e testes funcionais.

Não há necessidade de equipamento especializado ou licenças pagas.

## 15.4 Orçamento e custos estimados

O experimento foi planejado para custo zero ou custo mínimo, considerando o cenário acadêmico e uso de ferramentas gratuitas.
Entretanto, pequenos custos indiretos podem existir:

| Item                                       | Custo estimado                       |
| ------------------------------------------ | ------------------------------------ |
| Ferramentas de software                    | R$ 0 (todas gratuitas)               |
| Infraestrutura de laboratório              | R$ 0 (ofertado pela instituição)     |
| Impressão de documentos ou termos          | R$ 5–20                              |
| Certificados de participação (digitais)    | R$ 0                                 |
| Horas de trabalho do pesquisador           | Não monetizadas (trabalho acadêmico) |

Recursos próprios do estudante e infraestrutura da instituição de ensino.

# 16. Cronograma, Marcos e Riscos Operacionais
## 16.1 Macrocronograma (até o início da execução)

O cronograma abaixo apresenta uma visão realista das etapas necessárias desde a finalização do plano experimental até o início da coleta de dados.

| Etapa / Marco                                                 | Descrição                                                                            | Período Estimado |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ---------------- |
| **M1 — Finalização do plano do experimento**                  | Ajustes finais no documento, revisão metodológica e validação com orientador         | Semana 1         |
| **M2 — Submissão ao comitê de ética**                         | Envio do protocolo e dos materiais (TCLE, documentos, cronograma)                    | Semana 2         |
| **M3 — Aprovação ética**                                      | Análise pelo comitê e retorno com ajustes (se necessário)                            | Semanas 3–5      |
| **M4 — Preparação técnica**                                   | Configuração do ambiente, repositórios, scripts e testes funcionais                  | Semanas 4–6      |
| **M5 — Desenvolvimento e revisão do material de treinamento** | Slides, guias de execução, checklists                                                | Semanas 5–6      |
| **M6 — Rodada piloto**                                        | Execução reduzida com 2–3 participantes para validar tempo, instruções e ferramentas | Semana 7         |
| **M7 — Ajustes pós-piloto**                                   | Revisão de materiais e ferramentas com base em eventuais problemas identificados     | Semana 8         |
| **M8 — Início oficial da operação (coleta de dados)**         | Execução com os grupos TDD e Tradicional                                             | Semana 9         |

## 16.2 Dependências entre atividades

O andamento das atividades depende de uma sequência lógica que evita riscos de atrasos e falhas operacionais:

- Treinamento dos participantes depende da aprovação ética e da aprovação do orientador.
- Execução do piloto depende da preparação do ambiente técnico (repositórios, testes funcionais, scripts).
- Ajustes pós-piloto dependem da realização do piloto, pois só após essa etapa problemas de clareza, tempo e ferramentas são identificados.
- A execução oficial depende da conclusão de todas as atividades anteriores, especialmente aprovação ética e o piloto validado.
- Análise dos dados depende da finalização da coleta, incluindo verificação de integridade dos artefatos.

## 16.3 Riscos operacionais e plano de contingência

| Risco                                     | Descrição                                             | Prob. | Impacto | Contingência                                                          |
| ----------------------------------------- | ----------------------------------------------------- | ----- | ------- | --------------------------------------------------------------------- |
| **Indisponibilidade de participantes**    | Número de participantes abaixo do mínimo necessário   | Média | Alto    | Convites adicionais; ampliar turma; permitir participação remota      |
| **Atraso na aprovação ética**             | Comitê solicita revisões extensas                     | Média | Médio   | Submissão antecipada; responder rapidamente às demandas               |
| **Falhas técnicas no ambiente**           | Problemas com repositórios, IDEs ou scripts de coleta | Baixa | Alto    | Repetição do piloto; criação de ambientes espelhados de backup        |
| **Interferência no cronograma acadêmico** | Provas, eventos ou feriados impactam disponibilidade  | Alta  | Médio   | Ajustar datas; dividir execução em turnos flexíveis                   |
| **Contaminação entre grupos**             | Participantes compartilham soluções                   | Média | Médio   | Sessões separadas + reforço ético + monitoramento durante execução    |
| **Perda de dados ou logs incompletos**    | Falha de coleta automática                            | Baixa | Alto    | Verificação manual pós-sessão; backup secundário com coleta duplicada |

# 17. Governança do Experimento
## 17.1 Papéis e responsabilidades formais

A tabela abaixo define os papéis, responsabilidades e nível de autoridade conforme modelo RACI (Responsible, Accountable, Consulted, Informed).

| Papel                                 | Responsável (R)                          | Aprovador (A)            | Consultado (C)        | Informado (I)        |
| ------------------------------------- | ---------------------------------------- | ------------------------ | --------------------- | -------------------- |
| **Pesquisador Principal (estudante)** | Planejamento, execução, coleta e análise | —                        | Orientador            | Participantes        |
| **Orientador**                        | Suporte metodológico                     | Aprovação final do plano | Comitê de ética       | Coordenação do curso |
| **Comitê de Ética**                   | Revisão ética                            | Aprovação ética          | —                     | Instituição          |
| **Participantes**                     | Execução das tarefas                     | —                        | —                     | —                    |
| **Apoio técnico (opcional)**          | Suporte em ferramentas e ambiente        | —                        | Pesquisador Principal | —                    |

## 17.2 Ritos de acompanhamento pré-execução

Antes da fase operacional, serão adotados os seguintes ritos de acompanhamento:

- Reunião quinzenal com orientador
  - Revisão do cronograma
  - Ajustes metodológicos
  - Avaliação de riscos emergentes
- Checkpoints técnicos semanais
  - Verificação de scripts, repositórios, documentação
  - Teste contínuo do ambiente
- Revisão final pré-piloto
  - Simulação completa do fluxo
  - Conferência de checklists
  - Ajustes pontuais antes do piloto
- Revisão pós-piloto
  - Levantamento de falhas no fluxo
  - Identificação de inconsistências nos materiais
  - Avaliação de durações e instruções


## 17.3 Processo de controle de mudanças no plano

Qualquer alteração no plano experimental seguirá o processo abaixo:

1. Identificação da mudança
    - Problema detectado (ex.: tempo insuficiente, ambiguidade nos requisitos, falha no ambiente).

2. Registro formal
    - Descrição da mudança, motivo, impacto estimado e responsáveis.
    - Registro em documento de controle de versão (Markdown ou Google Docs).

3. Análise de impacto
    - Avaliação de como a mudança afeta cronograma, participantes, métricas e validade científica.

4. Aprovação
    - Mudanças metodológicas devem ser aprovadas pelo orientador.
    - Mudanças que envolvam coleta de dados ou sujeitos devem ser reenviadas ao Comitê de Ética.

5. Comunicação
    - Participantes e demais envolvidos serão informados antes da execução.

6. Implementação e registro final
    - Atualização da versão do plano e documentação do histórico de revisões.

# 18. Plano de Documentação e Reprodutibilidade
## 18.1 Repositórios e convenções de nomeação

A documentação do experimento será organizada em um conjunto de repositórios digitais que seguirão convenções padronizadas para garantir rastreabilidade, versionamento e facilidade de replicação. O repositório principal será hospedado em uma plataforma pública de controle de versão (como GitHub ou GitLab), porém definido como privado durante o período da pesquisa para evitar interferências externas.

Esse repositório será dividido em três diretórios principais:

- /docs – contendo o plano experimental, versões anteriores, guias e instruções.
- /scripts – com todos os scripts utilizados para coleta, medição, validação e automação dos testes.
- /artefacts – contendo exemplos de formulários, arquivos de configuração e materiais de apoio.

A convenção de nomeação seguirá o padrão snake_case, com prefixos que indicam a finalidade do documento. Por exemplo:

- ``plano_experimento_v1.md``
- ``script_coleta_metricas.py``
- ``checklist_ambiente_execucao.pdf``
- ``questionario_perfil_v2.docx``

Além disso, commits seguirão a estrutura “tipo: descrição” (ex.: fix: ajuste no script de cobertura ou docs: atualização do guia de TDD). Essa padronização visa manter transparência e facilitar auditorias ou reproduções futuras.

## 18.2 Templates e artefatos padrão

- A execução do experimento depende de um conjunto de artefatos estruturados previamente, garantindo uniformidade de coleta e consistência metodológica. Entre esses artefatos, destacam-se:
- Template do Termo de Consentimento Livre e Esclarecido (TCLE), contendo todos os itens exigidos pelo comitê de ética.
- Questionário de Perfil, aplicado antes da atividade para identificar nível de experiência, familiaridade com testes e conhecimento prévio de TDD.
- Checklist de Preparação do Ambiente, assegurando que todos os participantes tenham o mesmo ponto de partida técnico.
- Guia de Execução, contendo instruções padronizadas para cada grupo sobre como proceder durante a atividade.
- Formulário de Avaliação Pós-Experimento, reunindo impressões subjetivas e comentários adicionais dos participantes.
- Scripts padronizados para coleta de métricas (cobertura, falhas e tempo de retrabalho).

Todos esses modelos serão armazenados no diretório /templates, acompanhados de uma breve descrição de uso.

## 18.3 Plano de empacotamento para replicação futura

O experimento será preparado desde a concepção para permitir replicações futuras, seja por outros estudantes, por docentes ou por equipes de pesquisa. Para isso, será criado um package de replicação, composto pelos seguintes elementos:

- Descrição detalhada do experimento, com todas as seções do plano, incluindo objetivos, variáveis, desenho experimental e protocolos de execução.
- Scripts automatizados completamente documentados, permitindo que o ambiente seja recriado de forma idêntica independentemente da máquina utilizada.
- Conjunto de testes funcionais padronizados, garantindo que os critérios de validação sejam os mesmos em futuras execuções.
- Requisitos estáveis da API, congelados em uma versão específica, com changelog oficial para controle.
- Ambiente Docker opcional, reunindo em um único container todas as dependências necessárias.
- Tutorial de replicação, explicando passo a passo como recriar o contexto, desde o download dos materiais até a análise dos dados.


# 19. Plano de Comunicação
## 19.1 Públicos e mensagens-chave pré-execução

A comunicação do experimento será direcionada principalmente a quatro grupos: o orientador, o comitê de ética, os participantes e a coordenação do curso. Cada um deles receberá mensagens específicas e alinhadas ao seu papel no processo.

O orientador deve ser atualizado sobre o progresso do planejamento, incluindo ajustes metodológicos, riscos identificados e datas previstas de execução. Já o comitê de ética receberá informações formais sobre objetivos, métodos, instrumentos e cuidados adotados com os participantes.

Os participantes devem ser informados sobre o propósito do estudo, o escopo da atividade, a duração estimada, os requisitos técnicos e seus direitos, especialmente a voluntariedade. Por fim, a coordenação do curso deve ser comunicada sobre datas e alocação de infraestrutura, garantindo que o experimento não conflite com outras atividades acadêmicas.

## 19.2 Canais e frequência de comunicação

A comunicação ocorrerá prioritariamente por e-mail institucional, pela sua natureza formal e rastreável. No entanto, canais complementares como reuniões presenciais, Google Meet ou plataformas como Slack/Teams serão utilizados conforme a necessidade de comunicação rápida ou colaboração imediata.

A frequência seguirá o seguinte padrão:

- Orientador: reuniões quinzenais e e-mails semanais.
- Participantes: comunicação inicial com 2 semanas de antecedência, seguido de lembretes pontuais antes das sessões.
- Comitê de ética: comunicação apenas nos eventos formais (submissão, revisões e aprovação).
Coordenação: atualizações conforme necessidade de infraestrutura ou calendário.

## 19.3 Pontos de comunicação obrigatórios

Alguns eventos do experimento exigem comunicação formal, registrada e acompanhada, garantindo transparência e governança adequada. Os principais pontos obrigatórios incluem:

- Aprovação final do plano experimental, que deve ser comunicada ao orientador e registrada no repositório.
- Submissão e aprovação do comitê de ética, com armazenamento de pareceres e revisões.
- Alterações metodológicas relevantes, que precisam ser justificadas, registradas e aprovadas antes de serem implementadas.
- Adiamentos ou cancelamentos, caso ocorram, devendo ser comunicados aos participantes com antecedência adequada.
- Divulgação das instruções de execução, enviada formalmente para garantir que todos tenham acesso às mesmas informações.

# 20. Critérios de Prontidão para Execução (Definition of Ready)
## 20.1 Checklist de prontidão (itens que devem estar completos)

A execução do experimento somente poderá começar após a verificação de que todos os requisitos essenciais foram atendidos. Esse conjunto de condições representa a Definition of Ready e assegura que o estudo será conduzido de forma ética, consistente e com mínima exposição a riscos operacionais ou metodológicos.

Antes do início da operação, devem estar finalizados:

1. Plano completo do experimento
    - O documento deve estar revisado, versionado e aprovado pelo orientador. Todas as seções — objetivos, desenho, métricas, protocolo, análises e riscos — precisam estar concluídas.

2. Aprovação do Comitê de Ética
    - O parecer de aprovação ou de dispensa deve estar formalizado, com assinatura ou registro institucional. Nenhuma coleta de dados pode ocorrer sem essa etapa.

3. Instrumentos de coleta finalizados
    - Questionários, formulários, scripts de registro e extratores de métricas precisam estar testados e armazenados no repositório oficial.

4. Ambiente técnico totalmente configurado
    - Repositórios, container Docker (se houver), testes funcionais, ferramentas de cobertura e guias de execução devem estar operacionais e validados no piloto.

5. Documentação e templates padronizados
    - Checklists, guias de treinamento, arquivos de apoio e versões finais do TCLE devem estar disponibilizados no diretório apropriado.

6. Participantes confirmados e instruídos
    - O número mínimo de participantes por grupo deve estar confirmado, com disponibilidade validada e instruções prévias enviadas.

7. Comunicação oficial publicada
    - Informações de datas, horários, links, laboratório utilizado e instruções de preparação devem ter sido comunicadas a todos os envolvidos.

8. Ajustes pós-piloto aplicados
    - Qualquer inconsistência, sugestão ou problema identificado no piloto deve ter sido corrigido e registrado.

9. Acesso e permissões validadas
    - O pesquisador principal deve ter acesso pleno aos ambientes técnicos, e os participantes devem ter acesso às máquinas, ferramentas e repositórios necessários.

Somente quando todos os itens acima forem atendidos o experimento será formalmente considerado “pronto para execução”.

## 20.2 Aprovações finais para iniciar a operação

A autorização definitiva para iniciar a coleta de dados dependerá da validação formal de três agentes institucionais:

**Orientador Acadêmico**

É o responsável direto por garantir que o método, o escopo e os instrumentos sejam adequados para um trabalho de conclusão de curso. O orientador deve emitir um “OK final” por escrito, seja via e-mail institucional ou anotação registrada no repositório do experimento.

**Comitê de Ética em Pesquisa (CEP)**
Caso a instituição exija aprovação ética, o aceite formal deve estar registrado no parecer emitido pelo comitê. Esse documento deve ser armazenado no repositório /docs/etica/ e anexado ao plano.

**Coordenação do Curso (ou responsável equivalente)**
A coordenação deve validar a disponibilidade de laboratórios, horários e demais recursos institucionais necessários. O aceite pode ser registrado por mensagem institucional, formulário interno ou despacho de autorização.

O experimento somente poderá começar após os três registros estarem presentes, datados e anexados ao repositório oficial.