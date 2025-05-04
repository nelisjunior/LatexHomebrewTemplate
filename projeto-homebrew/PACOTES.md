# Documentação de Pacotes - Projeto LaTeX Homebrew

Este documento detalha os pacotes LaTeX utilizados no projeto, sua função e configurações específicas.

## Pacotes Básicos

| Pacote | Função | Observações |
|--------|--------|-------------|
| `geometry` | Configuração de margens e layout | Margens adaptadas para estilo RPG |
| `hyperref` | Links clicáveis | Configurado com cores temáticas |
| `graphicx` | Inclusão de imagens | |
| `fancyhdr` | Cabeçalhos e rodapés personalizados | |
| `titlesec` | Formatação de títulos | Personalizado para estilo Homebrewery |
| `xcolor` | Suporte a cores | Paleta de cores RPG predefinida |
| `microtype` | Melhorias tipográficas | Melhora a aparência do texto justificado |
| `lipsum` | Texto placeholder | Para testes e demonstrações |
| `tcolorbox` | Caixas coloridas personalizadas | Base para ambientes RPG |
| `enumitem` | Listas personalizadas | |
| `booktabs` | Tabelas de alta qualidade | |
| `array` | Recursos adicionais para tabelas | |
| `multicol` | Múltiplas colunas | Para layout de texto em estilo RPG |
| `afterpage` | Controle de quebra de página | |
| `tikz` | Desenhos vetoriais | Base para mapas mentais |
| `setspace` | Espaçamento entre linhas | |
| `bookmark` | Gerenciamento de favoritos PDF | |
| `float` | Controle de posicionamento de floats | |
| `lastpage` | Referência à última página | |
| `mdframed` | Caixas e molduras | Para estilo de notas RPG |
| `subfig` | Subfiguras | |
| `csquotes` | Citações avançadas | |
| `url` | Formatação de URLs | |
| `tabularx` | Tabelas com colunas de largura ajustável | |
| `verbatim` | Texto literal | |
| `tocbibind` | Inclusão de elementos no sumário | |
| `newfloat` | Novos ambientes flutuantes | |
| `datetime2` | Formatação de data e hora | |
| `ragged2e` | Alinhamento de texto avançado | |
| `marginnote` | Notas de margem | |
| `pifont` | Símbolos decorativos | Para marcadores em estilo RPG |
| `etoolbox` | Ferramentas para programação LaTeX | Para recursos avançados |

## Pacotes para Mapa Mental

| Pacote | Função | Observações |
|--------|--------|-------------|
| `mindmap` (TikZ) | Criação de mapas mentais | Biblioteca principal para mapas mentais |
| `trees` (TikZ) | Estruturas em árvore | Para hierarquia de mapas mentais |
| `shadows` (TikZ) | Efeitos de sombra | Efeitos visuais nos mapas |
| `arrows` (TikZ) | Personalização de setas | Conexões entre nós do mapa |
| `positioning` (TikZ) | Posicionamento preciso | Alinhamento de elementos |
| `decorations.pathmorphing` (TikZ) | Decorações de caminho | Efeitos visuais nas linhas |
| `decorations.markings` (TikZ) | Marcações em caminhos | Indicadores nas conexões |
| `shapes.geometric` (TikZ) | Formas geométricas | Nós com formas personalizadas |

## Pacotes para Línguas e Localização

| Pacote | Função | Observações |
|--------|--------|-------------|
| `babel` | Suporte a múltiplos idiomas | Configurado para português brasileiro |
| `useregional` (datetime2) | Formatos regionais de data | |

## Pacotes para Bibliografia e Referências

| Pacote | Função | Observações |
|--------|--------|-------------|
| `biblatex` | Sistema de bibliografia | Configurado com backend biber |
| `imakeidx` | Criação de índice remissivo | |
| `glossaries` | Criação de glossário | |

## Pacotes para Fontes

| Pacote | Função | Observações |
|--------|--------|-------------|
| `fontspec` | Suporte a fontes OpenType/TrueType | Necessário para XeLaTeX |
| `Latin Modern Roman` | Fonte principal | Compatível com Overleaf |

## Conflitos de Pacotes e Soluções

- `xcolor` vs. `color`: O pacote `xcolor` estende `color` e deve ser preferido
- Múltiplos pacotes que modificam `\section`: O pacote `titlesec` tem prioridade
- Incompatibilidades de classe `memoir` vs. `article`: Resolvidas com configurações específicas para `article`

## Configurações Específicas para Overleaf

O arquivo `overleaf.tex` contém ajustes para garantir compatibilidade com a plataforma Overleaf:

- Simplificação de mapas mentais para evitar timeout
- Ajustes de fontes específicos para disponibilidade no Overleaf
- Otimizações de memória para documentos complexos
- Detecção automática do ambiente Overleaf

## Requisitos para Compilação

Para compilar este projeto são necessários:

- XeLaTeX (não pdfLaTeX)
- Biber (não BibTeX)
- Pacotes TikZ com suporte a mindmap
- Suporte a Unicode e fontes TrueType/OpenType

## Dependências entre Pacotes

- `fontspec` requer XeLaTeX ou LuaLaTeX
- Bibliotecas TikZ dependem do pacote `tikz`
- Mapas mentais requerem bibliotecas específicas do TikZ
- `biblatex` requer o backend `biber` para funcionalidade completa