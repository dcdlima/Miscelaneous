# Miscelaneous
**Códigos variados sem um propósito específico**  

1. Father_Day_Game :arrow_right: Jogo que sorteia perguntas para ser usado em uma aula de conversação de língua inglesa no Dia dos Pais
2. Codificação ➡️ código para detectar a codificação de um documento ou site. Útil na criação de um sistema de recuperação para que seja possível ler o documento.
3. Buscador de Artigos Científicos com Operadores Lógicos (Leia descrição abaixo)

# 📚 Buscador de Artigos Científicos com Operadores Lógicos

## Requisitos

### Dependências Python
```bash
pip install requests
```

**Nota**: O script utiliza apenas bibliotecas padrão do Python (`json`, `csv`, `datetime`, `urllib`, `time`, `xml`) além de `requests`, que é a única dependência externa necessária.

## Como Usar

### 1. Executar o Script Básico

```bash
python busca_artigos_cientificos.py
```

### 2. Usando em Seu Próprio Código

```python
from busca_artigos_cientificos import BuscadorArtigosCientificos

# Criar instância do buscador
buscador = BuscadorArtigosCientificos()

# Definir grupos de termos para busca
grupos = (
    ["Technological Foresight", "Technology Prospecting"],  # Grupo 1 (OR)
    ["RAG", "Large Language Model", "LLM"],                  # Grupo 2 (OR)
    ["Scientific Literature", "Text Mining"]                 # Grupo 3 (OR)
)

# Executar busca (resultado será AND entre grupos)
artigos = buscador.executar_busca(grupos, top_n=20)

# Gerar relatórios
buscador.gerar_relatorio_texto('resultado.txt')
buscador.gerar_relatorio_csv('resultado.csv')
buscador.gerar_relatorio_json('resultado.json')
```

## Recursos

### 🔍 Fontes de Dados
- **arXiv**: Preprints de física, CS, matemática, etc.
- **CrossRef**: Base de dados com milhões de artigos com DOI
- **Europe PMC**: Literatura biomédica e científica

### 📊 Formatos de Saída
1. **TXT**: Relatório formatado para leitura
2. **CSV**: Importável em Excel ou análise de dados
3. **JSON**: Para integração com outras aplicações

### 🎯 Características
- ✅ Operadores lógicos AND/OR
- ✅ Remoção automática de duplicatas
- ✅ Classificação por relevância
- ✅ Múltiplas fontes de dados
- ✅ Tratamento robusto de erros
- ✅ Respeito aos rate limits
- ✅ Relatórios em 3 formatos diferentes

## Exemplo de Query Gerada

Para os grupos do exemplo padrão, a query executada será:

```
("Technological Foresight" OR "Technology Prospecting" OR ...) 
AND 
("Retrieval-Augmented Generation" OR "RAG" OR "Large Language Model" OR ...) 
AND 
("Scientific Literature" OR "Systematic Review" OR "Bibliometric" OR ...)
```

## Customização

### Alterar Número de Resultados
```python
artigos = buscador.executar_busca(grupos, top_n=50)  # Retorna top 50
```

### Adicionar Mais Fontes
```python
def buscar_scopus(self, query: str, limit: int = 50):
    # Implementar busca no Scopus
    pass
```

## Notas Importantes

⚠️ **Rate Limiting**: O script aguarda 1 segundo entre requisições para respeitar os limites de taxa das APIs.

⚠️ **Qualidade dos Resultados**: A qualidade depende da disponibilidade das APIs no momento da busca.

⚠️ **Conexão**: Requer conexão com a internet ativa.

## Estrutura dos Artigos Retornados

Cada artigo contém:
```python
{
    'titulo': str,           # Título do artigo
    'autores': str,          # Primeiros 3 autores
    'ano': int,              # Ano de publicação
    'doi': str,              # DOI ou identificador
    'resumo': str,           # Abstract/Resumo
    'fonte': str,            # CrossRef, arXiv ou Europe PMC
    'url': str,              # Link direto para o artigo
    'relevancia': float      # Score de relevância (0-1)
}
```

## Troubleshooting

### Erro: "No module named 'requests'"
```bash
pip install requests
```

### Sem resultados encontrados
- Verifique sua conexão com a internet
- Tente com termos mais amplos
- As APIs podem estar temporariamente indisponíveis

### Muito lento
- Isso é normal! APIs públicas têm rate limits
- Você pode ajustar o número de requisições

## Próximas Melhorias Sugeridas

- [ ] Suporte a Semantic Scholar API
- [ ] Filtro por data de publicação
- [ ] Cálculo de h-index de autores
- [ ] Integração com MongoDB para cache
- [ ] Interface web com Streamlit
- [ ] Análise de coautoria
- [ ] Visualização de networks

---

**Desenvolvido para busca eficiente de literatura científica com operadores lógicos avançados.**
