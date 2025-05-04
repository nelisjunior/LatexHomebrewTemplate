# Usando o Projeto Homebrew no Overleaf

Este documento fornece instruções específicas para usar o modelo LaTeX Projeto Homebrew no Overleaf.

## Configuração Inicial no Overleaf

1. **Faça upload do projeto**:
   - Faça o download deste projeto como ZIP
   - No Overleaf, clique em "New Project" > "Upload Project"
   - Selecione o arquivo ZIP baixado

2. **Configure o compilador**:
   - No menu do Overleaf, clique em "Menu" (ícone de hambúrguer)
   - Selecione "Settings"
   - Em "Compiler", escolha "XeLaTeX"
   - Clique em "Save"

## Configuração Automática

O projeto já vem com configurações automáticas para o Overleaf. O arquivo `overleaf.tex` é carregado automaticamente e inclui:

- Otimizações básicas de memória
- Configurações para compilação mais rápida
- Ajustes básicos de compatibilidade

Na maioria dos casos, você não precisará fazer nenhuma alteração adicional.

## Resolvendo Problemas Específicos

Se, mesmo com as configurações automáticas, você encontrar problemas de compilação no Overleaf, siga estas etapas:

### 1. Problemas com Fontes

Se houver erros relacionados à fonte, edite o arquivo `overleaf.tex` e descomente uma das linhas na seção "AJUSTES DE FONTES". Por exemplo:

```latex
% Descomente apenas UMA das linhas abaixo:
\setmainfont{Times New Roman}
% \setmainfont{TeX Gyre Termes}
% \setmainfont{TeX Gyre Pagella}
% \setmainfont{Latin Modern Roman}
```

### 2. Problemas com Mapas Mentais

Se os mapas mentais causarem timeout ou erros de memória:

1. Edite o arquivo `overleaf.tex`
2. Descomente uma das opções na seção "SIMPLIFICAÇÃO DE MAPAS MENTAIS"
3. Inicie com a opção mais simples e vá tentando as outras conforme necessário

## Estrutura do Projeto

O modelo segue uma estrutura modular:

- `main.tex`: Arquivo principal que junta todos os componentes
- `0-pretextual.tex`, `1-textual.tex`, `2-postextual.tex`: Organizam as diferentes seções
- `caps/capitulos/`: Contém os arquivos de cada capítulo
- `ambientes.tex`: Define os ambientes personalizados com tcolorbox
- `configuracoes.tex`: Contém pacotes e configurações gerais
- `overleaf.tex`: Contém ajustes específicos para o Overleaf

## Compilação Correta

O documento deve ser compilado na seguinte sequência:

1. XeLaTeX
2. Biber
3. XeLaTeX
4. XeLaTeX

No Overleaf, isso é feito automaticamente quando você clica em "Recompilar".

## Limitações do Overleaf

O Overleaf pode ter limitações de:

- **Tempo de compilação**: Para documentos muito grandes ou com muitos mapas mentais
- **Memória**: Para layouts complexos e muitos elementos TikZ
- **Bibliotecas de fontes**: Algumas fontes podem não estar disponíveis

Se encontrar esses problemas, use as configurações em `overleaf.tex` para simplificar os elementos problemáticos.

## Recursos Adicionais

Para mais informações sobre:

- Mapas mentais: Consulte o arquivo `docs/MAPAMENTAL.md`
- Guia de início rápido: Consulte o arquivo `QUICK-START.md`
- Descrição geral do projeto: Consulte o arquivo `README.md`