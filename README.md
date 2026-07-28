# fruitin

MVP estático mobile-first para descobrir preferências de frutas por gestos.

## Fluxo principal

* Arraste para a direita ou use `+` para **gostei**.
* Arraste para a esquerda ou use `×` para **não gostei**.
* Arraste para cima ou use `↑` para **não experimentei**.
* Abra `histórico` para consultar as três listas de decisões.
* As decisões são mantidas no `localStorage` do navegador.

## Catálogo e representação visual

O catálogo contém **100 frutas** em `data/fruits.json`. Cada item sem emoji correspondente possui um campo `visual` com `type: "color-grid"` e exatamente quatro cores. A interface renderiza essas cores como quatro círculos em uma grade 2x2, evitando que o valor `null` apareça na tela. Itens com emoji usam o campo `emoji`.

O fallback equivalente em `app.js` continua disponível quando o JSON local não puder ser carregado. Nesse caminho, a função visual também rejeita explicitamente strings vazias e o texto `null` antes de renderizar qualquer emoji.

## Histórico

O menu de histórico agora apresenta separadamente:

* gostei;
* não gostei;
* não experimentei.

Cada grupo mostra sua contagem e suas frutas. Grupos sem itens exibem um estado vazio específico.

## Executar localmente

Não há dependências nem etapa de build. Para consultar o JSON local, execute na raiz:

```bash
python3 -m http.server 8000
```

Abra `http://localhost:8000`. Ao abrir `index.html` diretamente, o navegador pode bloquear o `fetch`; nesse caso, o fallback embutido mantém o fluxo funcionando.

## GitHub Pages

Em **Settings > Pages**, selecione **Deploy from a branch**, escolha `main` e `/ (root)`.

## Decisões e limitações

* HTML, CSS e JavaScript sem framework.
* Pointer Events funcionam com toque e mouse; setas do teclado também funcionam.
* Não há backend, autenticação, API externa ou recomendação nutricional.
* As cores são aproximações visuais e não identificações botânicas.
* A persistência é local ao navegador e dispositivo.

A página https://ronanrodrigo.dev/notes/tags/ foi acessada antes da implementação. As notas encontradas eram sobre IA, automação, ferramentas e recursos, sem referência diretamente pertinente ao MVP de frutas; por isso, nenhuma referência externa foi incorporada.

## Próximos passos

Testar com 5 a 8 pessoas sem instruções, observar a compreensão dos três gestos, medir o uso do histórico e só depois avaliar detalhes, personalização ou recomendações.
