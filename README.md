# Medication Classification Query

Consulta SQL para normalizar princípios ativos e classificar medicamentos em categorias clínicas e operacionais.

## Objetivo

A query parte de uma base de insumos medicamentosos, normaliza descrições conhecidas e aplica regras de classificação por princípio ativo. Entre as categorias produzidas estão:

- imunoterapia imunobiológica;
- imunoterapia não imunobiológica;
- medicamento de suporte;
- medicamento de suporte imunobiológico;
- quimioterápico;
- terapia-alvo;
- terapia endócrina;
- itens que exigem revisão manual.

Também são aplicadas regras para classificação da via de acesso.

## Arquivo

- `qry.sql`: consulta principal, estruturada com CTEs para preparação, normalização e classificação.

## Estrutura lógica

```text
Insumo original
    ↓
Normalização do princípio ativo
    ↓
Regras de classificação por CASE
    ↓
Classificação final e indicação de revisão
```

## Técnicas SQL demonstradas

- Common Table Expressions;
- normalização com `UPPER`;
- regras de negócio com `CASE`;
- tratamento de exceções conhecidas;
- classificação baseada em listas de domínio;
- anonimização de tabelas e identificadores.

## Como reutilizar

1. substitua as referências anonimizadas pelas tabelas do ambiente de destino;
2. valide os nomes e códigos dos campos;
3. revise as listas de medicamentos com especialistas do domínio;
4. execute primeiro como `SELECT` antes de materializar resultados;
5. monitore os registros classificados como `REVER`.

## Limitações

- as listas de domínio estão incorporadas diretamente na query;
- novos medicamentos exigem manutenção manual;
- regras clínicas devem ser validadas por responsáveis de negócio;
- a consulta não possui testes automatizados;
- algumas observações no arquivo representam hipóteses de desenvolvimento.

## Evolução recomendada

Uma evolução natural é mover as regras para uma tabela de referência versionada, permitindo manutenção por dados em vez de alterações em grandes blocos `CASE`.