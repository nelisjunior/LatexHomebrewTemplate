# Tutorial: Como usar o Modelo LaTeX com Estilo RPG

Este tutorial apresenta como utilizar o modelo LaTeX modular com estilo visual inspirado em RPGs. Vamos explorar os recursos disponíveis e exemplos de uso.

## 1. Primeiros Passos

### 1.1 Configuração no Overleaf

Recomendamos o uso do Overleaf para compilar este projeto, já que ele fornece um ambiente LaTeX completo na nuvem:

1. Baixe este projeto como um arquivo ZIP
2. Acesse [Overleaf](https://www.overleaf.com) e crie uma conta gratuita (ou faça login)
3. Clique em "New Project" > "Upload Project"
4. Faça upload do arquivo ZIP
5. No menu superior do Overleaf, altere o compilador para XeLaTeX (Menu > Compiler > XeLaTeX)
6. Clique em "Recompilar" para gerar o PDF

### 1.2 Configuração Local

Se preferir compilar localmente, você precisará:

1. Instalar uma distribuição TeX como TeX Live, MiKTeX ou MacTeX
2. Garantir que tenha o XeLaTeX e o Biber instalados
3. Compilar usando os comandos:
   ```
   xelatex main.tex
   biber main
   xelatex main.tex
   xelatex main.tex
   ```

## 2. Estrutura do Projeto

O projeto está organizado de forma modular:

- **main.tex**: Arquivo principal que compila o documento
- **configuracoes.tex**: Pacotes e configurações gerais
- **ambientes.tex**: Ambientes personalizados estilo RPG
- **0-pretextual.tex**: Elementos pré-textuais (capa, sumário, etc.)
- **1-textual.tex**: Elementos textuais (capítulos)
- **2-postextual.tex**: Elementos pós-textuais (referências, glossário, etc.)
- **caps/**: Pasta com os componentes separados por tipo
  - **caps/pretextual/**: Componentes pré-textuais detalhados
  - **caps/capitulos/**: Arquivos de cada capítulo 
  - **caps/postextual/**: Componentes pós-textuais detalhados
- **imgs/**: Pasta para imagens
- **referencias.bib**: Arquivo com as referências bibliográficas

## 3. Ambientes Personalizados

### 3.1 Principais Ambientes

```latex
\begin{spell}
\textbf{Nome do Feitiço}
Descrição do feitiço...
\end{spell}

\begin{character}
\textbf{Nome do Personagem}
Descrição e estatísticas...
\end{character}

\begin{rule}
\textbf{Título da Regra}
Detalhes da regra...
\end{rule}

\begin{magicitem}
\textbf{Nome do Item Mágico}
Descrição do item...
\end{magicitem}

\begin{dmnote}
Informações para o mestre/professor/orientador...
\end{dmnote}

\begin{rpgtable}
Conteúdo de tabela estilizada...
\end{rpgtable}

\begin{quotebox}
Citação destacada...
\end{quotebox}

\begin{highlight}
Conteúdo em destaque...
\end{highlight}
```

### 3.2 Comandos Especiais

```latex
% Notas de margem
\rpgnote{Texto da nota de margem}

% Título de seção estilizado
\rpgsection{Título da Seção}

% Título destacado
\rpgtitle{Título Principal}

% Estatísticas de personagem
\stat{Nome}{Valor}

% Barras de atributos
\attrbar{Nome}{Valor}  % Valor entre 0-30

% Itens de lista estilizados
\begin{itemize}
\rpgitem{Primeiro item}
\rpgitem{Segundo item}
\end{itemize}

% Entradas de glossário
\glossaryentry{termo}{definição}

% Referenciar termo do glossário
\gls{termo}

% Indexar termo
\index{termo}
```

## 4. Personalizando o Modelo

### 4.1 Alterar Cores

Edite o arquivo `configuracoes.tex` para modificar as cores do modelo:

```latex
\definecolor{pergaminho}{RGB}{249, 240, 181}
\definecolor{capa}{RGB}{121, 26, 25}
\definecolor{titulo}{RGB}{72, 26, 19}
\definecolor{boxbg}{RGB}{253, 245, 196}
\definecolor{boxborder}{RGB}{190, 150, 86}
\definecolor{secaotitulo}{RGB}{140, 26, 20}
\definecolor{spell}{RGB}{70, 26, 100}
\definecolor{magicitem}{RGB}{26, 70, 100}
\definecolor{rule}{RGB}{140, 20, 20}
\definecolor{note}{RGB}{20, 100, 120}
```

### 4.2 Adicionar Novos Capítulos

1. Crie um arquivo .tex na pasta `caps/capitulos/` (ex: `capitulo4.tex`)
2. Adicione o conteúdo desejado
3. Inclua-o no arquivo `caps/textual.tex`:
   ```latex
   \input{caps/capitulos/capitulo4}
   ```

### 4.3 Adicionando Referências Bibliográficas

Adicione suas referências no arquivo `referencias.bib` seguindo o formato BibTeX:

```bibtex
@book{chave,
  title={Título do Livro},
  author={Sobrenome, Nome},
  year={Ano},
  publisher={Editora},
  address={Cidade}
}
```

Para citar, use:
```latex
\cite{chave}
```

## 5. Exemplos Práticos

### 5.1 Exemplo de Página de Estatísticas de Personagem

```latex
\rpgtitle{Estatísticas de Personagem}

\begin{character}
\textbf{Gandalf, o Cinzento}\\
\textit{Humano Mago 12}

\stat{FOR}{10} \stat{DES}{12} \stat{CON}{14}
\stat{INT}{18} \stat{SAB}{16} \stat{CAR}{15}

\rpgsection{Atributos}
\attrbar{Conhecimento Arcano}{25}
\attrbar{Diplomacia}{18}
\attrbar{Percepção}{20}

\rpgsection{Habilidades}
\begin{itemize}
\rpgitem{Especialista em magias de fogo e luz}
\rpgitem{Resistência a magias}
\rpgitem{Conhecimento vasto sobre história e criaturas}
\end{itemize}
\end{character}
```

### 5.2 Exemplo de Descrição de Item Mágico

```latex
\begin{magicitem}
\textbf{Vara do Poder Arcano}\\
\textit{Cajado, lendário (requer sintonização por um mago)}

Este cajado de madeira antiga emite uma tênue aura azulada. Ele contém propriedades mágicas poderosas:

\begin{itemize}
\rpgitem{+2 de bônus em jogadas de ataque com magias}
\rpgitem{Você pode gastar 1 carga para conjurar \textit{Mísseis Mágicos} (nível 3)}
\rpgitem{Você pode gastar 3 cargas para conjurar \textit{Bola de Fogo} (nível 5)}
\end{itemize}

O cajado tem 10 cargas e recupera 1d6+4 cargas diariamente ao amanhecer.
\end{magicitem}

\rpgnote{Este item é adequado para personagens de nível 10 ou superior, pois seu poder pode desbalancear encontros de nível mais baixo.}
```

## 6. Dicas e Solução de Problemas

- Sempre compile o documento várias vezes, especialmente quando usar referências cruzadas, índice ou bibliografia
- Use `\clearpage` para forçar uma quebra de página quando necessário
- Em caso de problemas com imagens, verifique se estão na pasta `imgs/` e se o caminho está correto
- Se encontrar erros de compilação, tente comentar partes do código para isolar o problema

Esperamos que este tutorial ajude você a utilizar este modelo. Para mais informações, consulte a documentação do LaTeX ou entre em contato com o desenvolvedor do modelo.