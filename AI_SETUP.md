# Configuração da correção inteligente

A versão atual permanece no GitHub Pages; **a chave da OpenAI nunca deve ser colocada em HTML, JavaScript do navegador ou no repositório**.

## Publicação do corretor

1. Crie uma conta/projeto Cloudflare Workers, instale Wrangler e faça login (`npx wrangler login`).
2. Ajuste `worker/wrangler.toml`, em especial `ALLOWED_ORIGIN` para a origem exata do site (sem barra final). Para GitHub Pages normalmente é `https://alfranior.github.io`.
3. No diretório `worker`, execute `npx wrangler secret put OPENAI_API_KEY`. Digite a chave em ambiente seguro; **não a envie em conversas**.
4. Publique com `npx wrangler deploy`.
5. No aplicativo, preencha o endereço HTTPS do Worker, sem `/api/correct`, e use **Corrigir com IA** após escrever a frase.

**Segurança:** CORS não constitui autenticação. Antes de disponibilizar a ferramenta em endereço público, aplique autenticação de acesso (por exemplo, Cloudflare Access, com um fluxo de autenticação compatível com o navegador), limites de taxa e orçamento máximo na OpenAI. Um Worker público sem essas proteções pode gerar custos por uso indevido. Evite inserir dados pessoais ou corporativos sensíveis nos exercícios.

## O que a IA corrige

- Concordância, gramática e tempo verbal selecionado
- Uso da palavra-alvo, significado e naturalidade
- Explicação em português e sugestão de frase em inglês

A avaliação é contextual: **não** depende de a frase ser idêntica à planilha. Pode haver respostas válidas diferentes. Correções de IA podem conter erros; a nota deve ser tratada como orientação, não avaliação definitiva.

## Teste básico

Selecione **Simple Past**, escreva `Yesterday I go to the bank.` e solicite a correção. A resposta esperada é que a frase precise de ajuste, sugerindo `Yesterday I went to the bank.`, desde que a palavra selecionada e o tempo verbal permitam tal frase.

Se a configuração não estiver pronta, **Conferir referência** e a autoavaliação continuam funcionando. O progresso segue armazenado no navegador; exporte um backup para transferi-lo.

## Próxima etapa

Integrar a avaliação da IA à fila de revisão e permitir visualizar o histórico das correções por frase.
