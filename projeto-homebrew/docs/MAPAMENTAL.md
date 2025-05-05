# Tutorial de Mapas Mentais no Projeto Homebrew

Este tutorial explica como usar as funcionalidades de geração de mapas mentais para visualizar a estrutura do documento no Projeto Homebrew LaTeX.

## Índice

1. [Introdução aos Mapas Mentais](#introdução-aos-mapas-mentais)
2. [Tipos de Mapas Mentais Disponíveis](#tipos-de-mapas-mentais-disponíveis)
3. [Mapas Mentais Pré-definidos](#mapas-mentais-pré-definidos)
4. [Mapas Mentais Automáticos](#mapas-mentais-automáticos)
5. [Mapas Mentais Personalizados](#mapas-mentais-personalizados)
6. [Exemplos Práticos](#exemplos-práticos)
7. [Personalização Avançada](#personalização-avançada)
8. [Resolução de Problemas](#resolução-de-problemas)

## Introdução aos Mapas Mentais

Os mapas mentais são representações visuais que mostram a estrutura hierárquica do documento, ajudando leitores e autores a compreender a organização do conteúdo. No Projeto Homebrew, implementamos um sistema de geração de mapas mentais baseado em TikZ e seus módulos de mindmap.

Benefícios:
- Visualização clara da hierarquia do documento
- Orientação para leitores sobre o conteúdo
- Auxílio na organização do pensamento para autores
- Estética consistente com o estilo RPG do projeto

## Tipos de Mapas Mentais Disponíveis

O sistema oferece três tipos principais de mapas mentais:

1. **Mapas Pré-definidos**: Estruturas fixas que apresentam uma visão geral típica de um documento acadêmico
2. **Mapas Automáticos**: Gerados dinamicamente a partir da estrutura real do documento
3. **Mapas Personalizados**: Construídos manualmente pelo autor para visualizar conceitos específicos

## Mapas Mentais Pré-definidos

### Mapa Completo do Documento

Para incluir um mapa mental completo predefinido no seu documento:

```latex
\generatecomplexdocmap
```

Este comando gera um mapa mental detalhado que mostra a estrutura típica de um documento acadêmico com elementos pré-textuais, textuais e pós-textuais.

### Mapa Rápido

Para um mapa mental simples com um tema personalizado:

```latex
\quickdocmap{Título Personalizado}
```

## Mapas Mentais Automáticos

### Mapa Automático Completo

Para gerar um mapa mental baseado na estrutura real do documento:

```latex
\generateautodocmap
```

Este comando analisa a estrutura atual do documento (capítulos, seções, subseções) e cria um mapa mental correspondente.

### Mapa de Capítulo

Para gerar um mapa mental específico para o capítulo atual:

```latex
\generatesectiondocmap[Título do Capítulo]
```

O parâmetro opcional permite especificar um título personalizado para o mapa.

## Mapas Mentais Personalizados

Para criar mapas mentais completamente personalizados, use o ambiente `docstructmap`:

```latex
\begin{docstructmap}
    % Nó raiz
    \docmaproot{Título Principal}
    
    % Nós de primeiro nível
    \docmaplevelone{id1}{30}{Tópico 1}
    \docmaplevelone{id2}{150}{Tópico 2}
    \docmaplevelone{id3}{270}{Tópico 3}
    
    % Nós de segundo nível
    \docmapleveltwo{id1_1}{id1}{0}{Subtópico 1.1}
    \docmapleveltwo{id2_1}{id2}{150}{Subtópico 2.1}
    
    % Nós de terceiro nível
    \docmaplevelthree{id1_1_1}{id1_1}{30}{Detalhe 1.1.1}
    
    % Nós de quarto nível
    \docmaplevelfour{id1_1_1_1}{id1_1_1}{45}{Especificação 1.1.1.1}
\end{docstructmap}

\docmaplegend{Texto explicativo sobre este mapa mental.}
```

### Explicação dos Parâmetros

Para cada comando de nó, os parâmetros são:

- `\docmaproot{texto}`: Cria o nó raiz do mapa
- `\docmaplevelone{id}{ângulo}{texto}`: Cria um nó de nível 1
  - `id`: Identificador único para o nó
  - `ângulo`: Posição angular em graus (0-360)
  - `texto`: Conteúdo do nó
- `\docmapleveltwo{id}{id_pai}{ângulo}{texto}`: Cria um nó de nível 2
  - `id`: Identificador único para o nó
  - `id_pai`: ID do nó pai (ao qual este nó será conectado)
  - `ângulo`: Posição angular em graus
  - `texto`: Conteúdo do nó

Os comandos `\docmaplevelthree` e `\docmaplevelfour` seguem o mesmo padrão para criar nós de níveis 3 e 4.

## Exemplos Práticos

### Exemplo 1: Mapa da Estrutura de um Artigo Científico

```latex
\begin{docstructmap}
    \docmaproot{Artigo Científico}
    \docmaplevelone{introducao}{30}{Introdução}
    \docmaplevelone{metodos}{150}{Métodos}
    \docmaplevelone{resultados}{270}{Resultados e\\Discussão}
    
    \docmapleveltwo{contexto}{introducao}{0}{Contextualização}
    \docmapleveltwo{objetivo}{introducao}{60}{Objetivos}
    
    \docmapleveltwo{amostra}{metodos}{120}{Amostragem}
    \docmapleveltwo{analise}{metodos}{180}{Análise de Dados}
    
    \docmapleveltwo{achados}{resultados}{240}{Principais\\Achados}
    \docmapleveltwo{implica}{resultados}{300}{Implicações}
\end{docstructmap}
```

### Exemplo 2: Mapa de Conceitos Teóricos

```latex
\begin{docstructmap}
    \docmaproot{Teoria X}
    \docmaplevelone{conceitos}{30}{Conceitos\\Fundamentais}
    \docmaplevelone{aplicacoes}{150}{Aplicações}
    \docmaplevelone{limitacoes}{270}{Limitações}
    
    \docmapleveltwo{conc1}{conceitos}{0}{Conceito A}
    \docmapleveltwo{conc2}{conceitos}{60}{Conceito B}
    
    \docmaplevelthree{subconc1}{conc1}{30}{Subconceito A.1}
    \docmaplevelthree{subconc2}{conc1}{60}{Subconceito A.2}
\end{docstructmap}
```

Consulte o arquivo `exemplos/exemplo-mapamental.tex` para exemplos mais detalhados.

## Personalização Avançada

### Alterando Cores e Estilos

As cores dos nós em cada nível podem ser personalizadas modificando as definições no arquivo `ambientes/docmap.tex`:

```latex
\definecolor{level0color}{RGB}{121, 26, 25}  % Cor do nó raiz
\definecolor{level1color}{RGB}{70, 26, 100}  % Cor dos nós de nível 1
\definecolor{level2color}{RGB}{26, 70, 100}  % Cor dos nós de nível 2
\definecolor{level3color}{RGB}{140, 20, 20}  % Cor dos nós de nível 3
\definecolor{level4color}{RGB}{20, 100, 120} % Cor dos nós de nível 4
```

### Personalizando o Estilo dos Nós

O estilo dos nós pode ser modificado no ambiente `docstructmap` no arquivo `ambientes/docmap.tex`:

```latex
concept/.append style={
    text width=4cm,
    font=\bfseries,
    minimum size=2cm,
    fill=boxbg,
    text=secaotitulo,
    line width=1pt,
    draw=boxborder
}
```

## Resolução de Problemas

### O Mapa Mental Não Aparece

1. Verifique se os pacotes TikZ necessários estão instalados:
   ```latex
   \usepackage{tikz}
   \usetikzlibrary{mindmap,trees,shadows,arrows,positioning}
   ```

2. Certifique-se de que os arquivos `ambientes/docmap.tex` e `ambientes/auto-docmap.tex` estão sendo importados corretamente em `ambientes.tex`.

### O Mapa Mental Automático Não Mostra Todas as Seções

1. Verifique se está usando os comandos padrão de seção (`\section`, `\subsection`, etc.) em vez de comandos personalizados.

2. O sistema de mapeamento automático registra seções à medida que o documento é compilado. Se o mapa aparecer antes das seções no documento, ele não conterá essas seções. Coloque o comando `\generateautodocmap` após as seções que deseja incluir.

### Problemas de Compilação

Se encontrar erros de compilação relacionados aos mapas mentais:

1. Certifique-se de que todos os IDs de nós são únicos em todo o documento
2. Verifique se todos os nós de nível 2 e superiores referenciam IDs de nós pais existentes
3. Tente simplificar o mapa, reduzindo o número de nós para identificar possíveis conflitos

## Verificação da Consistência na Estrutura de Arquivos e Convenções de Nomenclatura

- **Estrutura de Arquivos**: Verifique se a estrutura de arquivos está consistente e lógica
  * `projeto-homebrew/0-pretextual.tex` deve incluir `caps/pretextual`
  * `projeto-homebrew/1-textual.tex` deve incluir `caps/textual`
  * `projeto-homebrew/2-postextual.tex` deve incluir `caps/postextual`
  * `projeto-homebrew/caps/textual.tex` deve incluir capítulos de `caps/capitulos`

- **Convenções de Nomenclatura**: Verifique se todos os capítulos estão corretamente incluídos e seguem uma convenção de nomenclatura consistente
  * Capítulos em `projeto-homebrew/caps/capitulos` devem ser nomeados de forma consistente (ex: `capitulo1.tex`, `capitulo2.tex`)

## Verificação da Configuração e Gerenciamento de Pacotes

- **Pacotes Necessários**: Verifique se todos os pacotes necessários estão incluídos e corretamente configurados
  * `projeto-homebrew/configuracoes.tex` deve incluir todos os pacotes necessários

- **Configuração Correta**: Verifique se `configuracoes`, `ambientes` e `overleaf` estão corretamente configurados e não conflitam entre si
  * `projeto-homebrew/main.tex` deve incluir `configuracoes`, `ambientes` e `overleaf` sem conflitos

- **Guia de Início Rápido**: Verifique se as instruções no guia de início rápido estão claras e atualizadas
  * `projeto-homebrew/QUICK-START.md` deve fornecer instruções claras e atualizadas
