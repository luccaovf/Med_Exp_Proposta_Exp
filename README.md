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
| v4.0   | 26/11/2025 | Lucca Oliveira Vasconcelos de Faria | Seções 10 - 12 |

## 1.4 Datas

- Criação: 23/11/2025
- Última atualização: 01/12/2025

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

# 10. População, Sujeitos e Amostragem

## 10.1 População-alvo

A população real que o experimento pretende representar é:

Desenvolvedores backend (nível júnior a pleno) que implementam APIs REST em ambientes de produto ou protótipo, especialmente aqueles que lidam com validações financeiras (limites de transação).

Essa população inclui estudantes avançados de engenharia de software, estagiários e desenvolvedores em início de carreira que usam tecnologias como Java/Spring Boot, Node/Express ou similares.

## 10.2 Critérios de inclusão de sujeitos

Caso o estudo seja ampliado e veja a necessidade de adicionar participantes além do próprio pesquisador. Para ser elegível como participante, o sujeito deve atender a todos os requisitos abaixo:

- Ser estudante de graduação em Engenharia de Software (ou desenvolvedor júnior/pleno) com interesse em participar do estudo;
- Ter conhecimento básico de programação backend (capacidade de implementar endpoints REST);
- Ter conhecimento básico de testes unitários (conhecer JUnit, pytest, jest ou similar) e controle de versão (Git);
- Disponibilidade para dedicar o período necessário (ex.: 4–8 semanas) conforme cronograma do experimento;
- Aceitar os termos do experimento e assinar/aceitar um termo de consentimento.

## 10.3 Critérios de exclusão de sujeitos

Não poderão participar:

- Pessoas com conflito de interesse direto (por exemplo, co-orientadores que avaliarão o TCC formalmente em nota);
- Indivíduos sem conhecimento mínimo de programação ou testes (por exemplo, sem experiência em Git ou sem noções de REST);
- Pessoas que não possam se comprometer com o cronograma ou com a disponibilidade exigida;

## 10.4 Tamanho da amostra planejado (por grupo)

Opção primária (realista para TCC — execução individual)

- Total: 1 participante (o aluno autor do TCC).
- Justificativa: recursos e tempo limitados; desenho within-subject permite comparação direta entre TDD e não-TDD para o mesmo executor.

Opção estendida (recomendado para replicação / trabalho futuro)

- Total sugerido para maior validade: 12–24 participantes (cada um executando um subconjunto balanceado), dividido em:
  - Grupo A (TDD primeiro) = 6–12
  - Grupo B (Não-TDD primeiro) = 6–12
- Justificativa: tamanho típico para estudos experimentais em engenharia de software que buscam maior poder (~0.6–0.8 dependendo do efeito esperado). Requer mais recursos e coordenação.

## 10.5 Método de seleção / recrutamento

Para o TCC (n=1): autor do TCC executa o experimento.

Para replicação/estudo ampliado: amostragem de conveniência e convite em turmas/disciplina do curso de Engenharia de Software, listas de divulgação acadêmicas, e grupos de pesquisa. Usar formulário de inscrição (Google Forms) com triagem pelos critérios de inclusão. Se houver mais candidatos que vagas, selecionar por ordem de inscrição mantendo equilíbrio de experiência.

## 10.6 Treinamento e preparação dos sujeitos

Para nivelar conhecimento e reduzir viés por falta de habilidade:

- Sessão de treinamento (presencial ou gravada — ≈4 horas):
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

O plano estatístico dependerá do tamanho da amostra:

### Cenário A — Amostra muito pequena / 1 participante (TCC realista)

- Análise descritiva estruturada: médias, medianas, boxplots, gráficos temporais, radar charts.
- Comparações par-a-par dentro do próprio sujeito:
  - Diferença absoluta e percentual entre tratamentos.
  - Efeito simples de magnitude (Cohen’s d adaptado para n pequeno).
- Interpretação baseada em lógica de diferenças sistemáticas, não em significância estatística formal.

### Cenário B — Amostra moderada/maior (replicações futuras com 12–24 participantes)

Caso seja replicado futuramente:

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
