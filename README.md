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

## 1.4 Datas

- Criação: 23/11/2025
- Última atualização: 24/11/2025

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

