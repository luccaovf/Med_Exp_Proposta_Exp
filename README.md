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

## 1.4 Datas

- Criação: 23/11/2025
- Última atualização: 26/11/2025

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

**Equipe**: 1 executor (aluno)

**Sistema**: API REST protótipo contendo 1–3 endpoints com regras de validação com limites bem definidos (ex.: cadastro de usuário, pedido, agendamento etc.)

**Ferramentas gratuitas**:

- Java + Spring Boot
- PostgreSQL (opcional — pode ser substituído por H2)
- JUnit 5, Mockito, AssertJ
- JaCoCo (cobertura)
- Git + GitHub
- Swagger UI / Postman

**Tratamentos experimentais**:

1. TDD (testes definindo casos de borda antes do código)
2. Desenvolvimento tradicional (código primeiro; testes depois)

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

**Tipo de organização:** Atividade acadêmica individual, sem vínculo com empresa.

**Tamanho:** Projeto pequeno, desenvolvido por 1 estudante.

**Tipo de projeto:** Protótipo educacional de API REST.

**Criticidade:** Baixa, sem uso comercial ou impacto externo.

**Perfil do participante:** Estudante de Engenharia de Software com conhecimento básico/intermediário em programação e testes.

**Ambiente técnico:**

- Desenvolvimento local no computador pessoal.
- Controle de versão via Git.
- Execução e testes em ambiente local.
- Duração aproximada: 4 a 8 semanas.

## 4.3 Premissas

- O estudante possui conhecimento inicial de TDD e testes unitários.
- As ferramentas necessárias estão instaladas e funcionando.
- O protótipo da API REST será simples o suficiente para ser implementado no tempo previsto.
- Os casos de borda podem ser definidos claramente antes da execução do experimento.
- O computador de desenvolvimento estará disponível durante o período do estudo.
- Os limites financeiros serão representados numericamente em valor monetário (ex.: decimal).
- Não haverá integração com sistemas reais de pagamento.
- Não haverá mudanças radicais no escopo após o início.

## 4.4 Restrições

- **Recursos humanos:** Apenas um desenvolvedor disponível.
- **Tempo:** Agenda acadêmica limitada.
- **Orçamento:** Zero — ferramentas devem ser gratuitas.
- **Ambiente:** Sem servidores dedicados ou infraestrutura corporativa.
- **Dados:** Não será usado banco de dados real; preferencialmente dados simples ou memória local.
- **Imparcialidade:** O participante é também o executor, o que pode gerar viés.

## 4.5 Limitações Previstas

- Os resultados podem não generalizar para equipes profissionais.
- O desempenho pode refletir a habilidade individual do estudante.
- A API REST será pequena, o que pode reduzir variação de falhas.
- Os resultados podem não representar sistemas maiores ou críticos.
- A comparação entre TDD e não-TDD pode ser limitada por falta de múltiplos participantes.

# 5. Stakeholders e Impacto Esperado

## 5.1 Stakeholders Principais

- Estudante pesquisador (executor e analista).
- Orientador acadêmico / professor.
- Comunidade acadêmica (eventuais leitores do TCC).
- Futuros estudantes/pesquisadores interessados em TDD.

## 5.2 Interesses e Expectativas dos Stakeholders

| Stakeholder           | Interesse / Expectativa                                          |
| --------------------- | ---------------------------------------------------------------- |
| Estudante             | Aprender, comparar e validar o impacto do TDD em casos de borda. |
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
- **Metodológicos:** Viés do participante na comparação entre métodos.
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
- O participante não consiga implementar o protótipo mínimo.
- O cronograma acadêmico torne inviável a coleta de métricas.
- Haja perda de dados críticos sem possibilidade de reconstrução.
- Haja impedimento de saúde ou motivos maiores do participante.

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

**Nível de significância adotado:**
- α = 0,05

**Poder estatístico esperado:**

Como o experimento possui apenas um participante e um único artefato sendo comparado, o poder estatístico será:

- baixo para inferências populacionais
- adequado somente para estudo exploratório
- válido para observação e análise descritiva, não inferencial

**Portanto:**

Os resultados não permitirão generalizações estatísticas, mas gerarão evidências práticas e qualitativas úteis.

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

**Participante único:**

- Estudante de Engenharia de Software
- Experiência básica/intermediária em desenvolvimento
- Conhecimento introdutório de TDD
- Responsável por implementar ambas as abordagens

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

- Cobertura de casos de borda
- Cobertura de código
- Número de falhas
- Severidade das falhas
- Tempo de retrabalho
- Commits de correção
- Taxa de respostas corretas
- Taxa de falsos positivos
- Taxa de falsos negativos
- Conformidade com requisitos

## 8.6 Variáveis de Controle / Bloqueio

- Mesmo desenvolvedor
- Mesmo conjunto de requisitos
- Mesma API alvo
- Mesmo hardware e ambiente
- Mesmo tempo total máximo
- Mesmo framework de testes
- Mesmo banco de dados simples

## 8.7 Variáveis de Confusão Conhecidas

- Fadiga do participante
- Aprendizado entre uma abordagem e outra
- Motivação momentânea
- Preferência pessoal por método
- Ordem de implementação

Para minimizar impacto, a ordem dos tratamentos será invertida em endpoints parciais, reduzindo viés de aprendizado.

## 8.8 Tabela — Variáveis e Descrições

| Tipo         | Variável                     | Descrição                         |
| ------------ | ---------------------------- | --------------------------------- |
| Independente | Abordagem de desenvolvimento | Técnica aplicada (TDD vs não-TDD) |
| Dependente   | Cobertura de casos de borda  | Percentual de bordas testadas     |
| Dependente   | Falhas detectadas            | Número total de falhas            |
| Dependente   | Severidade das falhas        | Criticidade média ponderada       |
| Dependente   | Tempo de retrabalho          | Tempo gasto corrigindo            |
| Dependente   | Commits de correção          | Quantidade de commits corretivos  |
| Dependente   | Taxa de respostas corretas   | Proporção de respostas válidas    |
| Dependente   | Falsos positivos             | Rejeições indevidas               |
| Dependente   | Falsos negativos             | Aceitações indevidas              |
| Dependente   | Conformidade com requisitos  | Percentual atendido               |
| Controle     | Participante                 | Mantido constante                 |
| Controle     | Requisitos                   | Iguais nos dois tratamentos       |
| Confusão     | Aprendizado                  | Pode favorecer o segundo ciclo    |

## 8.9 Tabela — Fatores, Tratamentos e Combinações

| Fator                        | Tratamentos   | Combinações Aplicadas                                       |
| ---------------------------- | ------------- | ----------------------------------------------------------- |
| Abordagem de desenvolvimento | TDD / Não-TDD | API implementada com TDD e a mesma API implementada sem TDD |

# 9. Desenho Experimental

## 9.1 Tipo de Desenho

Desenho intra-sujeito (within-subjects) completamente randomizado

Justificativa:

- Apenas um participante disponível
- Permite comparar o mesmo sujeito em duas condições
- Minimiza variabilidade entre desenvolvedores

## 9.2 Randomização e Alocação

**O que será randomizado:**

Ordem de implementação de funcionalidades dentro da API

**Método de randomização:**

Ferramenta simples como random.org, planilha ou sorteio manual

## 9.3 Balanceamento e Contrabalanço

Estratégias adotadas:

- O participante implementará metade dos endpoints primeiro com TDD e metade primeiro sem TDD
- Os papéis serão invertidos na segunda rodada
- Reduz efeitos de aprendizagem e familiaridade

## 9.4 Número de Grupos e Sessões

**Grupos:** 1 participante, dois tratamentos

**Sessões:** 2 ciclos completos de implementação

- Ciclo A — abordagem 1
- Ciclo B — abordagem 2

Justificativa:

- Mantém comparabilidade
- Reduz viés temporal
- Permite coleta completa de métricas
