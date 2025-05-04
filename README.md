# Projeto LaTeX Homebrew - Template para Overleaf

Este é um projeto LaTeX modular com visual inspirado no estilo RPG (Homebrewery) e organização acadêmica (Overleaf). O documento foi projetado para compilação com XeLaTeX e possui uma estrutura de arquivos bem organizada para facilitar a edição e manutenção.

## Estrutura do Projeto

O modelo segue uma estrutura modular:

- `main.tex`: Arquivo principal que junta todos os componentes
- `0-pretextual.tex`, `1-textual.tex`, `2-postextual.tex`: Organizam as diferentes seções do documento
- `caps/capitulos/`: Contém os arquivos de cada capítulo individual
- `ambientes.tex`: Define os ambientes personalizados com tcolorbox
- `configuracoes.tex`: Contém pacotes e configurações gerais
- `overleaf.tex`: Contém ajustes específicos para o Overleaf

## Como Usar Este Projeto

### Uso no Overleaf (Recomendado)

Este projeto foi especialmente otimizado para o Overleaf:

1. Faça o download deste projeto como ZIP
2. No Overleaf, clique em "New Project" > "Upload Project"
3. Selecione o arquivo ZIP baixado
4. Configure o compilador para XeLaTeX nas configurações do projeto

Para mais detalhes, consulte o arquivo `projeto-homebrew/OVERLEAF.md`.

### Uso Local (Requer Instalação do TeXLive)

Para compilar este projeto localmente, você precisará:
- TeXLive com XeLaTeX
- Biber (para bibliografia)
- Pacotes adicionais para mapas mentais (TikZ, mindmap)

A sequência de compilação é:
1. XeLaTeX
2. Biber
3. XeLaTeX
4. XeLaTeX

## Características Especiais

- **Estilo RPG**: Ambientes personalizados com decorações no estilo Homebrewery
- **Mapas Mentais**: Geração automática de mapas de estrutura do documento usando TikZ
- **Bibliografia**: Suporte completo via BibLaTeX e Biber
- **Índice e Glossário**: Organização avançada do conteúdo
- **Compatibilidade com Overleaf**: Configurações automáticas para funcionamento no Overleaf
- **Otimização para XeLaTeX 2023+**: Correções específicas para mapas mentais e formatação

## Observações

Este é um projeto de template LaTeX, não um projeto de compilação. Os arquivos estão estruturados para serem transferidos para o Overleaf, onde a compilação LaTeX ocorrerá.

Para informações adicionais, consulte:
- `projeto-homebrew/OVERLEAF.md` - Instruções específicas para Overleaf
- `projeto-homebrew/QUICK-START.md` - Guia rápido de utilização
- `projeto-homebrew/PACOTES.md` - Documentação dos pacotes utilizados
- `projeto-homebrew/CHECKLIST.md` - **Importante**: Lista de verificação para compilação correta e legibilidade