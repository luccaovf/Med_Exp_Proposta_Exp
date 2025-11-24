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

## 1.4 Datas

- Criação: 23/11/2025
- Última atualização: 23/11/2025

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

- O1: Medir quantos casos de borda são corretamente tratados com e sem TDD.
- O2: Medir o número de erros descobertos posteriormente relacionados a bordas.
- O3: Comparar a cobertura de testes focada em cenários extremos.
- O4: Medir o esforço de retrabalho para correção de falhas de borda.

## 3.3 Questões de Pesquisa / de Negócio

- Q1: TDD resulta em maior cobertura de casos de borda?
- Q2: TDD reduz o número de falhas de validação em cenários extremos?
- Q3: TDD reduz o retrabalho relacionado a correções desses casos?
- Q4: TDD aumenta a precisão das regras implementadas nos limites?

## 3.4 Métricas Associadas

| Questão | Métrica                         | Definição                                                   | Unidade  | Fonte                        |
| ------- | ------------------------------- | ----------------------------------------------------------- | -------- | ---------------------------- |
| Q1      | **Cobertura de Casos de Borda** | Proporção de casos de borda definidos vs testados           | %        | Matriz de casos / testes     |
| Q2      | **Falhas de Borda Detectadas**  | Quantidade de cenários extremos com comportamento incorreto | Contagem | Testes manuais/automatizados |
| Q3      | **Tempo de Retrabalho**         | Horas gastas corrigindo falhas de borda                     | Horas    | Log de tempo                 |
| Q4      | **Precisão das Validações**     | Taxa de respostas corretas em cenários limite               | % acerto | Resultados dos testes        |
