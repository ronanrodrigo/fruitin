# fruitin

MVP estático de um app mobile-first para descobrir preferências de frutas por gestos.

## Objetivo e fluxo

O produto valida se uma pessoa entende um fluxo simples de classificação, sem cadastro ou explicações adicionais:

* arrastar para a direita registra **gostei** e cria um match;
* arrastar para a esquerda registra **não gostei**;
* arrastar para cima registra **nunca provei**;
* `matches` abre o histórico dos favoritos;
* as decisões ficam salvas no `localStorage` do navegador.

O público-alvo não foi definido no briefing, então a interface é ampla, direta e sem personalização.

## Executar localmente

Não há dependências nem etapa de build. Para consultar o JSON local, execute na raiz:

```bash
python3 -m http.server 8000
```

Abra `http://localhost:8000`. Também é possível abrir `index.html` diretamente: se o navegador bloquear o `fetch`, o fallback embutido no JavaScript mantém o fluxo funcionando.

## GitHub Pages

O repositório é estático e está preparado para publicação pela raiz. No GitHub, acesse **Settings > Pages**, selecione **Deploy from a branch**, escolha `main` e `/ (root)`.

## Atualização do catálogo

O catálogo agora contém **100 frutas**. Frutas que possuem um emoji apropriado usam o emoji. Para frutas sem um emoji específico, o card renderiza um círculo colorido — ou um círculo dividido em duas cores — com base nas cores naturais aproximadas da fruta. Isso mantém a interface visual e evita inventar emojis inadequados.

A fonte primária é `data/fruits.json`. O fallback equivalente em `app.js` também contém as 100 frutas, para preservar o funcionamento quando o JSON não puder ser carregado.

## Decisões técnicas

* HTML, CSS e JavaScript sem framework para reduzir o tempo de validação.
* Pointer Events permitem swipe com toque e mouse; as setas esquerda, cima e direita também acionam as decisões.
* `localStorage` mantém as decisões e os matches no navegador, sem backend, autenticação ou API externa.
* `overflow: hidden`, viewport configurado e layout responsivo fazem a tela principal parecer um app mobile e evitam scroll e zoom padrão.
* Estados implementados: carregamento, fallback, sucesso com toast, histórico vazio, jornada concluída e erro com tentativa de recarregar.

## Notas consultadas

A página https://ronanrodrigo.dev/notes/tags/ foi acessada antes da implementação. Ela reúne notas sobre inteligência artificial, automação, ferramentas e recursos. Não havia referência de interface ou implementação diretamente pertinente ao MVP de frutas; por isso, nenhuma referência externa da página foi incorporada. Essa limitação foi registrada para manter o escopo fiel ao briefing.

## Limitações e próximos passos

* Os dados são simulados e não representam catálogo, nutrição ou recomendação personalizada.
* A persistência é apenas local ao navegador e dispositivo.
* As cores dos círculos são representações visuais aproximadas, não identificação botânica.
* O gesto foi mantido simples para validar o conceito, não para ser um componente de produção.
* Testar com 5 a 8 pessoas sem instruções, medir entendimento dos três gestos, quantidade de matches e clareza do histórico.
* Só depois avaliar lista personalizada, detalhes das frutas ou recomendações.
