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

## Limitações do Overleaf e Compatibilidade com XeLaTeX 2023+

O Overleaf pode ter limitações de:

- **Tempo de compilação**: Para documentos muito grandes ou com muitos mapas mentais
- **Memória**: Para layouts complexos e muitos elementos TikZ
- **Bibliotecas de fontes**: Algumas fontes podem não estar disponíveis
- **Quebras de texto em mapas mentais**: Texto pode aparecer "quebrado" em nós de mapas mentais
- **Formatação de notas de rodapé**: Podem aparecer com formatação estranha

### Solução de Problemas com XeLaTeX 2023+

Este projeto já inclui correções para os problemas mais comuns do XeLaTeX 2023+:

1. **Mapas mentais quebrados**: O arquivo `overleaf.tex` já inclui correções automáticas que centralizam e ajustam o texto nos nós do mapa mental.

2. **Fontes incompatíveis**: O modelo usa fontes compatíveis com XeLaTeX 2023+ e inclui fallbacks.

3. **Checklist completo**: Consulte o arquivo `CHECKLIST.md` para uma lista completa de verificação antes da compilação final.

Se mesmo assim encontrar problemas, consulte `overleaf.tex` e descomente as linhas apropriadas nas seções relevantes.

## Recursos Adicionais

Para mais informações sobre:

- Mapas mentais: Consulte o arquivo `docs/MAPAMENTAL.md`
- Guia de início rápido: Consulte o arquivo `QUICK-START.md`
- Descrição geral do projeto: Consulte o arquivo `README.md`

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
