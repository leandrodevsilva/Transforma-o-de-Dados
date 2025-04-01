# Processamento do Rol de Procedimentos e Eventos em Saúde

Script Python para extrair, processar e exportar a tabela "Rol de Procedimentos e Eventos em Saúde" de um arquivo PDF para CSV compactado.

## Requisitos
- Python 3.7+
- Bibliotecas: `pandas`, `tabula-py`, `zipfile`, `os`, `pathlib`

## Instalação
```bash
pip install pandas tabula-py
```

## Como Usar
1.Configure o caminho do PDF:

Altere a variável "pdf_path" no código para apontar para seu arquivo PDF.

2.Execute o script:

```python processar_rol_procedimentos.py```

3.Saída gerada:

- Arquivo CSV processado (temporário)

- Arquivo ZIP final: Teste_{Leandro_Silva}.zip

## Funcionalidades
Identificação automática da tabela correta baseada em padrões de cabeçalho

Processamento dos dados:

Padronização de colunas (remoção de acentos/espaços)

Mapeamento de valores (ex: "S" → "Sim" para OD)

Geração de arquivo compactado

## Estrutura da Tabela Processada
```| Coluna       | Tipo        | Descrição                          | Valores Válidos                     | Exemplo                |
|--------------|-------------|------------------------------------|--------------------------------------|------------------------|
| **codigo**   | `string`    | Código do procedimento ANS         | Formato XXX.XXX ou XXXX.X           | "123.456", "0456.0"    |
| **descricao**| `string`    | Nome do procedimento               | Texto livre                         | "Consulta emergencial" |
| **od**       | `categorical`| Indicador Odontológico            | `Sim`/`Não`/`Não Aplicável`         | "Sim"                  |
| **amb**      | `categorical`| Nível de atendimento              | `Hospitalar`/`Ambulatorial`         | "Hospitalar"           |
| **porte**    | `string`    | (Opcional) Valor do procedimento   | Valores numéricos ou texto          | "R$ 120,50", "120.50"  |
```

## Observações
O script foi testado com a estrutura padrão da ANS, mas pode precisar de ajustes para PDFs com formatos diferentes.

Em caso de falha na identificação automática, o script exibirá amostras das tabelas encontradas para análise manual.
