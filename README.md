# Projeto de Coleta e Análise de Links

<div align="center">

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-4-green?style=for-the-badge&logo=python)
![Plotly](https://img.shields.io/badge/Plotly-5.x-purple?style=for-the-badge&logo=plotly)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter)

Sistema de coleta e análise de links de páginas web utilizando web scraping. Desenvolvido com Python, BeautifulSoup e Plotly para visualização de dados.

[Funcionalidades](#funcionalidades) • [Tecnologias](#tecnologias) • [Instalação](#instalação) • [Uso](#uso) • [Contribuir](#contribuindo)

</div>

---

## Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Funcionalidades](#funcionalidades)
- [Tecnologias](#tecnologias)
- [Instalação](#instalação)
- [Uso](#uso)
- [Exemplos](#exemplos)
- [Contribuindo](#contribuindo)
- [Licença](#licença)

---

## Sobre o Projeto

O **Projeto de Coleta e Análise de Links** é uma aplicação de web scraping que permite extrair, filtrar e analisar links de páginas web específicas. O projeto foi desenvolvido com foco em boas práticas de scraping, tratamento de dados e visualização interativa de resultados.

### Principais Características

- **Web Scraping** - Coleta automatizada de links de páginas web
- **Filtragem de Links** - Filtra links que começam com 'http' ou 'https'
- **Análise de Dados** - Processamento e categorização de links coletados
- **Visualização Interativa** - Gráficos e dashboards com Plotly
- **Exportação de Dados** - Salva links coletados em arquivo de texto
- **Jupyter Notebook** - Interface interativa para análise

---

## Funcionalidades

### Coleta de Dados

- Requisição HTTP para páginas web
- Parsing de HTML com BeautifulSoup
- Extração de todos os links da página
- Tratamento de erros de conexão
- Validação de URLs

### Processamento de Links

- Filtragem de links válidos (http/https)
- Remoção de duplicatas
- Categorização por domínio
- Análise de estrutura de URLs
- Exportação em diferentes formatos

### Visualização e Análise

- Gráficos interativos com Plotly
- Estatísticas sobre links coletados
- Análise de domínios mais frequentes
- Dashboard de visualização
- Exportação de relatórios

---

## Tecnologias

### Python e Bibliotecas

| Tecnologia         | Versão | Descrição                |
| ------------------ | ------ | ------------------------ |
| **Python**         | 3.x    | Linguagem de programação |
| **requests**       | 2.x    | Requisições HTTP         |
| **BeautifulSoup4** | 4.x    | Parsing de HTML          |
| **Plotly**         | 5.x    | Visualização de dados    |
| **Jupyter**        | -      | Ambiente interativo      |
| **re**             | -      | Expressões regulares     |

---

## Instalação

### Pré-requisitos

- **Python 3.x** - [Download](https://www.python.org/downloads/)
- **pip** - Gerenciador de pacotes Python (incluído no Python)

### Instalação das Dependências

#### 1. Clone o repositório

```bash
git clone https://github.com/nevesmarcos42/Projeto-de-Coleta-e-Analise-de-Links.git
cd Projeto-de-Coleta-e-Analise-de-Links
```

#### 2. Instale as bibliotecas necessárias

```bash
pip install requests beautifulsoup4 plotly jupyter
```

#### 3. Inicie o Jupyter Notebook

```bash
jupyter notebook
```

Pronto! O Jupyter Notebook estará rodando em: `http://localhost:8888`

---

## Uso

### Executando o Script

#### 1. Abra o Jupyter Notebook

```bash
jupyter notebook Coletando_Dados_na_interenet_com_BeautifulSoup.ipynb
```

#### 2. Execute as células

- Execute as células sequencialmente
- Modifique a URL da página para coletar links de diferentes sites
- Visualize os resultados nas células de output

#### 3. Salvar os dados

Os links coletados serão salvos automaticamente em arquivo de texto na mesma pasta.

---

## Exemplos

### Exemplo de Uso Básico

```python
import requests
from bs4 import BeautifulSoup
import re

# URL da página para coleta
url = 'https://example.com'

# Fazer requisição
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')

# Extrair links
links = soup.find_all('a', href=True)
filtered_links = [link['href'] for link in links if link['href'].startswith('http')]

# Salvar em arquivo
with open('links_coletados.txt', 'w') as file:
    for link in filtered_links:
        file.write(link + '\n')

print(f"Total de links coletados: {len(filtered_links)}")
```

### Exemplo de Visualização com Plotly

```python
import plotly.express as px
import pandas as pd

# Criar dataframe com os links
df = pd.DataFrame({'links': filtered_links})
df['dominio'] = df['links'].apply(lambda x: x.split('/')[2])

# Contar links por domínio
domain_counts = df['dominio'].value_counts()

# Criar gráfico
fig = px.bar(x=domain_counts.index, y=domain_counts.values,
             labels={'x': 'Domínio', 'y': 'Quantidade de Links'})
fig.show()
```

---

## Contribuindo

Contribuições são bem-vindas! Siga os passos:

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

### Padrões de Código

#### Python

- Seguir convenções PEP 8
- Usar type hints quando apropriado
- Documentar funções com docstrings
- Escrever código limpo e legível
- Adicionar comentários explicativos

---

## Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

Desenvolvido como projeto de estudo em Web Scraping e Análise de Dados

---

**Autor**: Marcos Neves

**Email**: nevesmarcos42@gmail.com

**LinkedIn**: [linkedin.com/in/nevesmarcos](https://linkedin.com/in/nevesmarcos)

**Versão**: 1.0.0

**Última Atualização**: Novembro 2025
