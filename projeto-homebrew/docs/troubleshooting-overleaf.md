# Guia de Solução de Problemas para Compilação no Overleaf

Este guia oferece soluções para problemas comuns encontrados ao compilar o Projeto Homebrew no Overleaf, especialmente relacionados à funcionalidade de mapas mentais.

## Problemas Comuns e Soluções

### 1. Erro: "undefined control sequence" para comandos TikZ

**Problema**: Mensagens sobre comandos indefinidos relacionados ao TikZ.

**Solução**:
1. Abra o arquivo `main.tex`
2. Descomente a linha `\input{overleaf-setup}`
3. Recompile o documento

### 2. Erro: Problemas com os mapas mentais

**Problema**: Erros específicos relacionados aos mapas mentais, como nós mal posicionados ou links quebrados.

**Solução**:
1. Abra o arquivo `main.tex`
2. Comente as linhas do sistema completo:
   ```latex
   % \input{configuracoes}
   % \input{ambientes}
   ```
3. Descomente as linhas do sistema simplificado:
   ```latex
   \input{configuracoes}
   \input{ambientes}
   \input{ambientes/docmap-simple}
   ```
4. Recompile o documento

### 3. Erro: "File ... not found"

**Problema**: Erro indicando que arquivos não foram encontrados.

**Solução**:
- Verifique se a estrutura de diretórios no Overleaf está igual à do projeto original
- Certifique-se de que todos os arquivos foram carregados, especialmente:
  - `ambientes/docmap.tex`
  - `ambientes/auto-docmap.tex`
  - `ambientes/docmap-simple.tex`
  - `overleaf-setup.tex`

### 4. Erro: Problemas com pacotes específicos

**Problema**: Mensagens sobre pacotes ausentes ou conflitos.

**Solução**:
1. Edite o arquivo `configuracoes.tex`
2. Comente temporariamente pacotes problemáticos
3. Para mapas mentais, certifique-se de que o TikZ e suas bibliotecas estão disponíveis

## Desativação Seletiva de Funcionalidades

Se ainda encontrar problemas, você pode desativar seletivamente partes do sistema:

### Desativar apenas a geração automática de mapas

Edite o arquivo `overleaf-setup.tex` e descomente esta linha:
```latex
\newcommand{\generateautodocmap}{\textbf{[Mapa mental automático desativado temporariamente]}}
```

### Desativar ambiente completo de mapas mentais

Edite o arquivo `overleaf-setup.tex` e descomente o bloco que inicia com:
```latex
\renewenvironment{docstructmap}[1][]
  {\begin{center}\textbf{[Visualização de mapa mental]}\\}
  ...
```

## Verificação do Compilador

Certifique-se de que está usando o compilador correto no Overleaf:

1. Clique no botão "Menu" no canto superior esquerdo
2. Escolha "Settings"
3. Defina o compilador para "XeLaTeX"
4. Ative a opção "Use bibliografia (biber)"

## Upload de Projeto Zipado

Ao fazer upload do projeto para o Overleaf:

1. Baixe todo o projeto como ZIP
2. No Overleaf, crie um novo projeto
3. Escolha a opção "Upload Project"
4. Selecione o arquivo ZIP completo

Isso garante que todos os arquivos e a estrutura de diretórios sejam mantidos corretamente.

## Usando os Exemplos Individuais

Se você estiver tendo problemas com o projeto completo, tente compilar os exemplos individuais:

1. No Overleaf, crie um novo projeto
2. Faça upload apenas dos arquivos em `exemplos/`
3. Tente compilar os exemplos individualmente para isolar o problema

## Suporte Adicional

Se continuar enfrentando problemas:

1. Verifique os logs de erro completos no Overleaf (clique em "Logs and Output Files")
2. Procure por mensagens específicas de erro relacionadas a pacotes ou comandos
3. Para problemas específicos com os mapas mentais, tente usar a versão mais simples em `ambientes/docmap-simple.tex`