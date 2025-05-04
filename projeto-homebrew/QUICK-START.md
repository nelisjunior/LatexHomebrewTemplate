# Guia de Início Rápido - Projeto LaTeX Homebrew

Este guia fornece informações essenciais para começar a usar o Projeto LaTeX Homebrew rapidamente.

## 1. Começando com o Overleaf

### Upload do Projeto
1. Faça o download deste projeto como ZIP
2. No Overleaf, clique em "New Project" > "Upload Project"
3. Selecione o arquivo ZIP baixado

### Configuração do Compilador
1. No menu do Overleaf, clique em "Menu" (ícone de hambúrguer)
2. Selecione "Settings"
3. Em "Compiler", escolha "XeLaTeX"
4. Clique em "Save"

## 2. Estrutura de Arquivos Principais

- **main.tex**: O arquivo principal que você compilará
- **0-pretextual.tex**: Elementos pré-textuais (capa, resumo, sumário)
- **1-textual.tex**: O corpo principal do documento (importa os capítulos)
- **2-postextual.tex**: Elementos pós-textuais (referências, apêndices)
- **caps/capitulos/**: Diretório onde você deve criar seus capítulos

## 3. Como Adicionar Novo Conteúdo

### Adicionar um Novo Capítulo
1. Crie um novo arquivo .tex em `caps/capitulos/` (ex: `capitulo3.tex`)
2. Adicione seu conteúdo no arquivo
3. Importe o arquivo em `1-textual.tex` com o comando:
   ```latex
   \input{caps/capitulos/capitulo3}
   ```

### Adicionar Referências Bibliográficas
1. Edite o arquivo `referencias.bib`
2. Adicione suas referências no formato BibTeX
3. Cite no texto usando `\cite{chave}` ou `\textcite{chave}`

## 4. Ambientes Personalizados

O modelo inclui ambientes estilizados que você pode usar em seu documento:

### Caixa de Nota
```latex
\begin{nota}{Título da Nota}
  Conteúdo da nota aqui.
\end{nota}
```

### Caixa de Aviso
```latex
\begin{aviso}{Título do Aviso}
  Conteúdo do aviso aqui.
\end{aviso}
```

### Caixa de Destaque
```latex
\begin{destaque}{Título de Destaque}
  Conteúdo em destaque aqui.
\end{destaque}
```

## 5. Mapas Mentais

Para incluir um mapa mental de capítulo:

```latex
\begin{docmap}{Título do Mapa}
  \node[concept] {Conceito Central}
    child[concept] {Conceito Secundário 1}
    child[concept] {Conceito Secundário 2}
    child[concept] {Conceito Secundário 3};
\end{docmap}
```

O documento também gera automaticamente um mapa da estrutura completa.

## 6. Solução de Problemas

Se encontrar problemas de compilação no Overleaf:

1. Verifique o arquivo `overleaf.tex` para configurações específicas
2. Para documentos muito grandes ou complexos, você pode precisar simplificar os mapas mentais
3. Consulte `OVERLEAF.md` para soluções detalhadas

## 7. Recursos Adicionais

- **Modelo de Capítulo**: Veja `caps/capitulos/capitulo1.tex`
- **Modelo de Mapa Mental**: Veja `exemplos/exemplo-mapamental.tex`
- **Documentação Completa**: Consulte os comentários nos arquivos .tex e nos documentos .md