# Projeto Homebrew: Modelo LaTeX Modular com Estética RPG

Este projeto oferece uma estrutura modular de LaTeX combinando a estética visual de livros de RPG (inspirado no Homebrewery) com a organização estrutural de documentos acadêmicos (inspirado no Overleaf).

## Estrutura de Diretórios

```
📂 projeto-homebrew
├── 📂 ambientes
│   ├── docmap.tex
│   └── auto-docmap.tex
├── 📂 caps
│   ├── 📂 capitulos
│   │   ├── capitulo1.tex
│   │   ├── capitulo2.tex
│   │   ├── capitulo3.tex
│   │   ├── capitulo-mapamental.tex
│   │   └── ...
│   ├── 📂 pretextual
│   │   ├── docmap.tex
│   │   ├── titulo.tex
│   │   └── ...
│   ├── pretextual.tex
│   ├── textual.tex
│   └── postextual.tex
├── 📂 docs
│   └── tutorial-mapamental.md
├── 📂 exemplos
│   ├── exemplo-mapamental.tex
│   ├── mapas-rpg.tex
│   └── ...
├── 📂 imgs
│   └── logo.png
├── 0-pretextual.tex
├── 1-textual.tex
├── 2-postextual.tex
├── ambientes.tex
├── configuracoes.tex
├── referencias.bib
├── main.tex
└── README.md
```

## Descrição dos Arquivos

- **main.tex**: Arquivo principal que compila todos os componentes
- **configuracoes.tex**: Contém os pacotes e configurações do documento
- **ambientes.tex**: Define os ambientes personalizados com tcolorbox
- **0-pretextual.tex**: Carrega os elementos pré-textuais
- **1-textual.tex**: Carrega os elementos textuais
- **2-postextual.tex**: Carrega os elementos pós-textuais
- **ambientes/docmap.tex**: Comandos para criação de mapas mentais
- **ambientes/auto-docmap.tex**: Sistema automático de geração de mapas
- **caps/pretextual.tex**: Conteúdo adicional dos elementos pré-textuais
- **caps/textual.tex**: Gerencia a inclusão dos capítulos
- **caps/postextual.tex**: Conteúdo dos elementos pós-textuais
- **caps/capitulos/**: Diretório com os arquivos de cada capítulo
- **caps/pretextual/docmap.tex**: Mapa mental pré-definido
- **exemplos/**: Contém exemplos completos de uso do modelo
- **docs/tutorial-mapamental.md**: Tutorial detalhado de uso dos mapas mentais
- **imgs/**: Diretório para armazenar imagens

## Como Compilar

### Compilação Local

Este projeto deve ser compilado usando o XeLaTeX para suportar as fontes personalizadas:

```
xelatex main.tex
biber main
xelatex main.tex
xelatex main.tex
```

A compilação em múltiplas passagens é necessária para processar corretamente as referências cruzadas, a bibliografia e o sumário.

**Observação:** Este projeto não pode ser compilado diretamente no Replit devido à falta de pacotes LaTeX necessários no ambiente. Recomendamos usar o Overleaf ou uma instalação local do LaTeX.

### Compilação no Overleaf (Recomendado)

Para facilitar a compilação, você pode usar o Overleaf:

1. Faça download deste projeto como ZIP
2. Crie um novo projeto no Overleaf e faça upload do ZIP
3. Configure o compilador para XeLaTeX
4. Clique em "Recompilar" para gerar o PDF

#### Solução de Problemas no Overleaf

Se encontrar problemas ao compilar no Overleaf, especialmente relacionados aos mapas mentais:

1. Abra o arquivo `main.tex`
2. Descomente a linha `\input{overleaf-setup}` para carregar configurações de compatibilidade
3. Se ainda tiver problemas, use a versão simplificada dos mapas mentais:
   - Comente as linhas do sistema completo e descomente as linhas do sistema simplificado
   - Recompile o documento

Para problemas específicos, consulte o guia detalhado em `docs/troubleshooting-overleaf.md`

#### Exemplos Independentes

Para testar funcionalidades específicas, o projeto inclui exemplos independentes:

- `exemplos/mapa-mental-simples.tex` - Exemplo simplificado de mapa mental
- `exemplos/exemplo-mapamental.tex` - Exemplo completo de uso dos mapas mentais
- `exemplos/mapas-rpg.tex` - Exemplos de mapas mentais para contextos de RPG

## Personalização

O modelo pode ser facilmente personalizado:

1. Para adicionar novos capítulos, crie um arquivo .tex na pasta caps/capitulos/ e inclua-o em caps/textual.tex
2. Para alterar as cores, modifique as definições em configuracoes.tex
3. Para adicionar novos ambientes estilizados, edite o arquivo ambientes.tex
4. Para incluir referências bibliográficas, adicione-as ao arquivo referencias.bib

## Ambientes Disponíveis

- `spell` - Para descrição de feitiços e magias
- `character` - Para estatísticas e descrição de personagens
- `dmnote` - Para notas do mestre (DM)
- `rule` - Para destacar regras importantes
- `magicitem` - Para descrever itens mágicos
- `rpgtable` - Para tabelas estilizadas
- `quotebox` - Para citações destacadas
- `highlight` - Para conteúdo em destaque

## Comandos Especiais

- `\rpgnote{}` - Para notas de margem
- `\rpgsection{}` - Para cabeçalhos de seção estilizados
- `\rpgtitle{}` - Para títulos destacados
- `\stat{nome}{valor}` - Para estatísticas de personagem
- `\attrbar{nome}{valor}` - Para barras de atributos

## Mapas Mentais da Estrutura do Documento

O modelo inclui funcionalidades para criar mapas mentais que visualizam a estrutura do documento:

### Comandos para Mapas Mentais

- `\generateautodocmap` - Gera um mapa mental automático baseado na estrutura do documento
- `\generatecomplexdocmap` - Gera um mapa mental detalhado pré-definido

### Ambiente para Mapas Personalizados

```latex
\begin{docstructmap}
    \docmaproot{Título Principal}
    \docmaplevelone{id1}{ângulo}{Nível 1}
    \docmapleveltwo{id2}{id1}{ângulo}{Nível 2}
    \docmaplevelthree{id3}{id2}{ângulo}{Nível 3}
\end{docstructmap}
\docmaplegend{Texto explicativo sobre o mapa mental}
```

### Exemplo Completo

Veja o arquivo `exemplos/exemplo-mapamental.tex` para um exemplo completo de uso dos mapas mentais.

## Requisitos

- Sistema LaTeX atualizado com XeLaTeX
- Gerenciador de bibliografia Biber
- Pacotes LaTeX listados em configuracoes.tex
- Pacotes TikZ para mapas mentais: mindmap, trees, shadows, arrows
- Suporte a fontes especiais (opcional)

