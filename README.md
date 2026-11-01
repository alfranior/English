# English House Drills

Aplicativo web de estudo de inglês a partir da planilha **[Alfranio] House Drills.xlsx**.

## Iniciar

Abra `index.html` no navegador ou publique o repositório com GitHub Pages (Settings → Pages → Deploy from a branch → master / root). Em seguida importe a planilha pelo campo de arquivo.

## Funcionalidades (v1)

- Importação da planilha Excel diretamente no navegador (sem enviar a terceiros).
- Seleção por módulo e fila de exercícios (pendentes, erros, novos e todos).
- Construção de uma frase por vez e comparação com a frase originalmente preenchida na planilha.
- Autoavaliação de cada resposta e histórico local de tentativas.
- Exportação e importação de backup JSON do progresso.
- Interface responsiva para celular e desktop.

## Limitações

A frase original da planilha pode conter erros. A v1 **não possui correção gramatical por IA**, nem login/sincronização entre aparelhos. O progresso é mantido em `localStorage` do navegador. Para preservar o histórico entre dispositivos, exporte/importe o backup JSON. O leitor Excel depende da biblioteca SheetJS via CDN; a página precisa de conexão no primeiro carregamento.

## Próximas etapas

1. Adicionar correção de respostas abertas por API com chave mantida somente no servidor.
2. Criar autenticação e sincronização opcional com banco de dados.
3. Implementar repetição espaçada e métricas por tempo verbal.
4. Adicionar testes automatizados para o mapeamento das abas da planilha.
