# Quer ficar comigo? 💖

Uma página interativa e responsiva criada com **HTML, CSS e JavaScript**. Ela apresenta a pergunta “Quer ficar comigo?” e dois botões:

- o botão **Sim** permanece disponível e exibe uma mensagem especial após o clique;
- o botão **Não** foge para posições seguras quando a pessoa aproxima o mouse ou tenta tocá-lo.

O projeto funciona em computadores, tablets e celulares e não precisa de bibliotecas externas.

## Demonstração do funcionamento

1. A página apresenta um cartão central com a pergunta.
2. No computador, o botão **Não** se afasta quando o cursor se aproxima.
3. No celular ou tablet, ele muda de posição quando a pessoa tenta tocá-lo.
4. O botão permanece sempre visível, respeitando uma margem de segurança nas bordas.
5. Ao selecionar **Sim**, aparece a mensagem:

> Parabéns! Agora você é a segunda pessoa mais feliz do mundo. A primeira é Mário. 💖

## Tecnologias utilizadas

- **HTML5:** estrutura e conteúdo da página;
- **CSS3:** cores, organização, animações e responsividade;
- **JavaScript:** movimentação do botão e exibição da mensagem.

## Estrutura do projeto

```text
projeto-quer-ficar-comigo/
├── index.html
└── README.md
```

Todo o CSS e o JavaScript estão dentro do arquivo HTML. Essa escolha facilita o estudo e permite executar o projeto sem instalar dependências.

## Como executar

1. Baixe ou clone este repositório.
2. Localize o arquivo `index.html`.
3. Clique duas vezes no arquivo para abri-lo no navegador.

Também é possível usar a extensão **Live Server** no Visual Studio Code:

1. abra a pasta do projeto no VS Code;
2. instale a extensão Live Server, caso ainda não a tenha;
3. clique com o botão direito sobre o arquivo HTML;
4. selecione **Open with Live Server**.

## Como o botão “Não” funciona

O JavaScript identifica a posição do cursor ou do toque e compara essa posição com o centro do botão. Quando a distância fica pequena, o botão começa a fugir.

Para impedir que ele desapareça, o código calcula oito posições seguras: os quatro cantos e quatro pontos centrais das laterais. Todas essas posições consideram:

- o tamanho real do botão;
- a largura e a altura visíveis do navegador;
- uma margem de segurança de 24 pixels;
- a posição atual do cursor.

O código descarta posições muito próximas da localização atual e escolhe o ponto seguro mais distante do cursor. A animação acontece entre dois pontos que já estão dentro da tela, impedindo que o botão ultrapasse as bordas.

A função `manterBotaoNaTela()` realiza uma verificação adicional ao final da animação. Ela também é executada quando a janela é redimensionada ou quando a orientação do celular muda.

Os eventos utilizados são:

- `pointermove`: acompanha o movimento do mouse;
- `pointerenter`: detecta quando o ponteiro entra na área do botão;
- `pointerdown`: detecta a tentativa de clique ou toque;
- `resize`: recalcula os limites quando o tamanho da janela muda;
- `click`: mostra a mensagem após selecionar **Sim**.

## Responsividade

A página utiliza:

- a meta tag `viewport`, que ajusta a escala em dispositivos móveis;
- medidas flexíveis, como `vw`, `dvh`, `clamp()` e porcentagens;
- uma media query para telas com até `480px`;
- eventos de ponteiro, compatíveis com mouse, caneta e toque.
- cálculo da área visível com `clientWidth` e `clientHeight`.

## Como personalizar

### Alterar a pergunta

No HTML, modifique o conteúdo da tag `<h1>`:

```html
<h1>Quer ficar comigo?</h1>
```

### Alterar a mensagem final

No JavaScript, edite o texto atribuído a `mensagem.textContent`:

```javascript
mensagem.textContent = 'Digite aqui a sua mensagem';
```

### Alterar as cores

As principais cores estão nas regras `body`, `#sim`, `#nao` e `#mensagem`, dentro da tag `<style>`.

### Alterar a distância de fuga

Modifique o valor da constante:

```javascript
const distanciaDeFuga = 125;
```

Um valor maior faz o botão fugir mais cedo. Um valor menor permite que o cursor chegue mais perto.
