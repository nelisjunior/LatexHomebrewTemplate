# Checklist de Compilação e Legibilidade - LaTeX Homebrew

Este documento fornece um checklist completo para garantir que seu projeto LaTeX compile corretamente e produza documentos legíveis, especialmente no ambiente Overleaf com XeLaTeX.

## ATENÇÃO: Problemas Específicos Corrigidos

Os seguintes problemas específicos foram identificados e corrigidos automaticamente:

1. **Comandos e Variáveis Internas Expostas no Texto**: Como `sectionbaseangle120 subsectionbaseangle30` aparecendo no documento.
   ✓ CORRIGIDO: Protegido comandos internos com `\protected\def` e adicionado filtros.

2. **Texto Quebrado em Mapas Mentais**: Texto dentro dos nós do mapa mental aparecendo incorretamente formatado.
   ✓ CORRIDO: Adicionado suporte a `varwidth` e centralização melhorada.

3. **Elementos do Sumário Corrompidos**: Caracteres estranhos como `@defctionlistctionlist` no sumário.
   ✓ CORRIGIDO: Implementada limpeza de tokens problemáticos.

4. **Mapas Mentais Deformados**: Nós com formatação incorreta e/ou conteúdo transbordando.
   ✓ CORRIGIDO: Redefinido tamanho e propriedades dos nós para formato adequado.

5. **Texto em Ambientes Especiais**: Formatação incorreta em caixas de notas, avisos e destaques.
   ✓ CORRIGIDO: Ajustado espaçamento e formatação destes elementos.

## Configuração do Compilador

- [ ] **Compilador XeLaTeX**: Verifique se está usando XeLaTeX versão 2023+ (não pdfLaTeX)
  * No Overleaf: Menu > Configurações > Compilador > XeLaTeX
  * Localmente: Use `xelatex main.tex` em vez de `pdflatex main.tex`

- [ ] **Sequência de Compilação Correta**:
  * 1º: XeLaTeX
  * 2º: Biber
  * 3º: XeLaTeX
  * 4º: XeLaTeX
  * No Overleaf: Use o botão "Recompilar" que executa a sequência automaticamente

## Problemas Comuns e Soluções

### 1. Mapas Mentais Quebrados

- [ ] **Tamanho dos Nós**: Reduza o valor de `text width` se o texto estiver transbordando
  * No arquivo `ambientes/docmap.tex`, linha 23, ajuste:
  ```latex
  text width=4cm -> text width=3.5cm
  ```

- [ ] **Fonte nos Nós**: Reduza o tamanho da fonte ou evite palavras muito longas
  * No arquivo `ambientes/docmap.tex`, use `\small` ou `\footnotesize`

- [ ] **Simplificação de Mapas Grandes**: Ative a simplificação para mapas complexos
  * Em `overleaf.tex`, descomente: `\def\usesimplifiedmindmap{1}`

- [ ] **Fixação de Quebras de Linha**: Use `\\` explicitamente em títulos de nós para controlar a quebra
  * Substitua espaços por `\\` nos títulos que aparecem quebrados

### 2. Notas de Rodapé/Notas de Mapa

- [ ] **Configuração de Notas**: Verifique se o pacote `footmisc` está configurado corretamente
  * Em `configuracoes.tex`, adicione opções ao pacote:
  ```latex
  \usepackage[bottom]{footmisc}
  ```

- [ ] **Espaçamento de Notas**: Corrija o espaçamento entre notas
  * Adicione ao `configuracoes.tex`:
  ```latex
  \setlength{\footnotesep}{0.5cm}
  ```

- [ ] **Fonte em Notas**: Defina uma fonte legível para notas
  * Adicione ao `configuracoes.tex`:
  ```latex
  \renewcommand{\footnotesize}{\fontsize{9}{11}\selectfont}
  ```

### 3. Problemas de Fonte

- [ ] **Disponibilidade de Fontes**: Verifique se a fonte está disponível no Overleaf
  * No arquivo `overleaf.tex`, descomente uma das fontes garantidas do Overleaf:
  ```latex
  \setmainfont{Times New Roman} % ou Latin Modern Roman
  ```

- [ ] **Caracteres Especiais**: Verifique se a fonte suporta caracteres especiais/acentos
  * Teste com palavras acentuadas: "Área", "Seção", "Capítulo"

- [ ] **Fallback de Fontes**: Defina fontes alternativas caso a principal não esteja disponível
  * No arquivo `configuracoes.tex`, adicione:
  ```latex
  \newfontfamily\fallbackfont{DejaVu Serif}
  ```

### 4. Problemas de Layout

- [ ] **Margens**: Verifique se as margens estão adequadas para leitura
  * Valores recomendados em `configuracoes.tex`:
  ```latex
  \geometry{
      a4paper,
      top=2.5cm,
      bottom=2.5cm,
      left=3cm,
      right=2.5cm,
  }
  ```

- [ ] **Quebras de Página**: Verifique se o texto flui adequadamente entre páginas
  * Use `\clearpage` antes de seções importantes
  * Evite `\pagebreak` forçados que podem criar espaços em branco

- [ ] **Espaçamento Entre Parágrafos**: Ajuste para legibilidade
  * Valores recomendados em `configuracoes.tex`:
  ```latex
  \setlength{\parskip}{0.5\baselineskip}
  ```

### 5. Problemas de Ambientes Personalizados

- [ ] **Caixas tcolorbox**: Verifique se estão renderizando corretamente
  * Teste cada ambiente (`nota`, `aviso`, `destaque`) com conteúdo curto
  * Verifique se as bordas e cores estão visíveis

- [ ] **Caixas Muito Grandes**: Evite conteúdo extenso em caixas decorativas
  * Use múltiplas caixas menores em vez de uma grande
  * Limite o uso de imagens dentro das caixas

### 6. Problemas de Compatibilidade com XeLaTeX 2023+

- [ ] **Sintaxe Atualizada**: Verifique a sintaxe dos comandos para a versão mais recente
  * Exemplo: em versões mais novas, use:
  ```latex
  \setmainfont{Times New Roman}[Ligatures=TeX]
  ```
  em vez de:
  ```latex
  \setmainfont[Ligatures=TeX]{Times New Roman}
  ```

- [ ] **Pacotes Atualizados**: Certifique-se de que os pacotes são compatíveis com XeLaTeX 2023+
  * Evite pacotes obsoletos como `xunicode`, `xltxtra`
  * Use `fontspec` atualizado para XeLaTeX recente

## Teste Final

- [ ] **Visualização Completa**: Verifique o documento inteiro de uma vez
  * Navegue por todas as páginas verificando cabeçalhos, rodapés, notas
  * Verifique a aparência do sumário, índice e referências

- [ ] **Teste de Impressão**: Gere um PDF e verifique como ficaria impresso
  * Verifique o layout em escala de cinza (para impressão P&B)
  * Verifique se o contraste é adequado em todas as seções

- [ ] **Leitura em Diferentes Dispositivos**: Teste o PDF em:
  * Tela de computador (resolução padrão)
  * Tablet ou e-reader
  * Versão impressa (se possível)

## Comandos Úteis para Debug

```bash
# Para detalhes sobre erros
xelatex -file-line-error -halt-on-error main.tex

# Para verificar problemas de fonte
xelatex -no-pdf main.tex

# Para executar a sequência completa de compilação
xelatex main.tex && biber main && xelatex main.tex && xelatex main.tex
```

## Solução Rápida para Mapas Quebrados

Se os mapas mentais continuarem apresentando problemas, adicione ao arquivo `ambientes/docmap.tex` antes da definição do ambiente `docstructmap`:

```latex
% Correção para quebras de linha em mapas mentais
\makeatletter
\newcommand{\processnodetext}[1]{%
  \begingroup
  \toks@={}%
  \@for\tmp:=#1\do{%
    \toks@=\expandafter{\the\toks@\tmp\\}%
  }%
  \the\toks@
  \endgroup
}
\makeatother

% Modificação do estilo de conceito para quebras automáticas
\tikzset{
  auto line break concept/.style={
    concept,
    text width=3.5cm,
    align=center,
    font=\small
  }
}
```

E então modifique o estilo `concept` para usar `auto line break concept` no mesmo arquivo.

## Verificação da Consistência na Estrutura de Arquivos e Convenções de Nomenclatura

- [ ] **Estrutura de Arquivos**: Verifique se a estrutura de arquivos está consistente e lógica
  * `projeto-homebrew/0-pretextual.tex` deve incluir `caps/pretextual`
  * `projeto-homebrew/1-textual.tex` deve incluir `caps/textual`
  * `projeto-homebrew/2-postextual.tex` deve incluir `caps/postextual`
  * `projeto-homebrew/caps/textual.tex` deve incluir capítulos de `caps/capitulos`

- [ ] **Convenções de Nomenclatura**: Verifique se todos os capítulos estão corretamente incluídos e seguem uma convenção de nomenclatura consistente
  * Capítulos em `projeto-homebrew/caps/capitulos` devem ser nomeados de forma consistente (ex: `capitulo1.tex`, `capitulo2.tex`)

## Verificação da Configuração e Gerenciamento de Pacotes

- [ ] **Pacotes Necessários**: Verifique se todos os pacotes necessários estão incluídos e corretamente configurados
  * `projeto-homebrew/configuracoes.tex` deve incluir todos os pacotes necessários

- [ ] **Configuração Correta**: Verifique se `configuracoes`, `ambientes` e `overleaf` estão corretamente configurados e não conflitam entre si
  * `projeto-homebrew/main.tex` deve incluir `configuracoes`, `ambientes` e `overleaf` sem conflitos

- [ ] **Guia de Início Rápido**: Verifique se as instruções no guia de início rápido estão claras e atualizadas
  * `projeto-homebrew/QUICK-START.md` deve fornecer instruções claras e atualizadas
