# Atendente de WhatsApp — Demonstração

Demonstração interativa de um **atendente automático de WhatsApp para oficina mecânica**. A pessoa abre no celular e conversa com o atendente como se fosse um cliente real — pergunta preço, horário, formas de pagamento e agendamento, e recebe resposta na hora. É um **projeto de demonstração de portfólio**: a oficina ("Oficina São Jorge") é fictícia, e a tela deixa isso claro com o selo *DEMONSTRAÇÃO*.

**No ar:** https://atendente-whatsapp-demo.vercel.app

## Para que serve

Oficina pequena perde cliente quando a mensagem chega fora do horário: "quanto custa a troca de óleo?", "tá aberto sábado?", "fazem alinhamento?" ficam sem resposta e o cliente procura outra. A ideia desta demonstração é mostrar, de forma concreta e testável, como um atendente automático responde essas dúvidas no mesmo instante e encaminha o agendamento — antes de o cliente decidir contratar.

O objetivo é comercial: em vez de descrever o serviço, o dono da oficina **testa o atendente com as próprias perguntas** e vê funcionando.

## O que a demonstração faz

- **Conversa de verdade na tela**, no visual de um chat de WhatsApp, com indicador de "digitando" e respostas automáticas.
- **Entende as perguntas por palavra-chave**, ignorando acentos e maiúsculas — então "Oleo", "óleo" e "troca de oleo" caem na mesma resposta.
- **Responde os assuntos mais comuns de oficina:** troca de óleo, freio/pastilha, alinhamento, revisão, diagnóstico/scanner, orçamento, agendamento, horário, endereço, formas de pagamento e garantia.
- **Botões de resposta rápida** para o visitante testar sem precisar digitar.
- **Encaminhamento educado para um humano** quando a pergunta foge do roteiro, em vez de responder errado.

## Detalhes técnicos

- HTML, CSS e JavaScript puros, sem framework e sem etapa de build. Um único arquivo, `index.html`.
- As respostas são decididas por um comparador de palavras-chave com normalização de acentos, tudo no próprio navegador — não envia nada para servidor nenhum.
- Layout responsivo, pensado primeiro para o celular.
- Modo claro e escuro automático, de acordo com a preferência do sistema do visitante.

## Como adaptar para uma oficina real

Os dados da oficina ficam reunidos em um único objeto no topo do `<script>`:

```js
const OFICINA = {
  nome: "Oficina São Jorge", sigla: "SJ",
  horario: "Seg a sex 8h às 18h, sábado 8h às 12h",
  endereco: "Rua das Oficinas, 240 — a 2 quadras do metrô"
};
```

- Troque nome, horário e endereço por lá.
- Preços e textos das respostas ficam nas regras de palavra-chave logo abaixo, fáceis de ajustar.
- Numa aplicação real, o mesmo roteiro pode ser ligado à API oficial do WhatsApp (WhatsApp Business) para responder de verdade, sem ninguém na tela.

## Como rodar localmente

Não precisa instalar nada. Basta abrir o `index.html` no navegador, ou servir a pasta com qualquer servidor estático:

```bash
npx serve .
```

## Publicação

O projeto está conectado à Vercel. Cada commit na branch `main` publica uma nova versão automaticamente.
