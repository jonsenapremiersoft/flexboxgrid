# Guia Completo de Layout CSS: Flexbox e Grid

## Flexbox

O Flexbox (Flexible Box Layout) é ideal para layouts unidimensionais - seja em linha ou coluna. É perfeito para:
- Menus de navegação
- Cards alinhados
- Elementos que precisam ser distribuídos em uma única direção
- Layouts responsivos simples

### Propriedades Principais do Flexbox

#### Container Flex (Pai)
```css
.container {
    display: flex;
    /* ou display: inline-flex */

    /* Direção dos itens */
    flex-direction: row | row-reverse | column | column-reverse;

    /* Quebra de linha */
    flex-wrap: nowrap | wrap | wrap-reverse;

    /* Alinhamento horizontal */
    justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;

    /* Alinhamento vertical */
    align-items: stretch | flex-start | flex-end | center | baseline;

    /* Alinhamento de múltiplas linhas */
    align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```

#### Itens Flex (Filhos)
```css
.item {
    /* Ordem de exibição */
    order: 0;

    /* Capacidade de crescer */
    flex-grow: 0;

    /* Capacidade de encolher */
    flex-shrink: 1;

    /* Tamanho base */
    flex-basis: auto;

    /* Shorthand para grow, shrink e basis */
    flex: 0 1 auto;

    /* Auto-alinhamento */
    align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

### Exemplo Prático de Flexbox

```html
<div class="navbar">
    <div class="logo">Logo</div>
    <nav class="menu">
        <a href="#">Home</a>
        <a href="#">Sobre</a>
        <a href="#">Contato</a>
    </nav>
</div>
```

```css
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
}

.menu {
    display: flex;
    gap: 1rem;
}
```

## Grid

O Grid é ideal para layouts bidimensionais - trabalhando com linhas e colunas simultaneamente. É perfeito para:
- Layouts de página completos
- Galerias de imagens
- Interfaces complexas
- Qualquer design que necessite controle em duas dimensões

### Propriedades Principais do Grid

#### Container Grid (Pai)
```css
.container {
    display: grid;
    /* ou display: inline-grid */

    /* Define colunas */
    grid-template-columns: 200px 1fr 1fr;
    /* ou usando repeat */
    grid-template-columns: repeat(3, 1fr);

    /* Define linhas */
    grid-template-rows: auto 200px auto;

    /* Espaçamento */
    gap: 20px;
    /* ou separadamente */
    column-gap: 20px;
    row-gap: 20px;

    /* Alinhamento horizontal de todos os itens */
    justify-items: start | end | center | stretch;

    /* Alinhamento vertical de todos os itens */
    align-items: start | end | center | stretch;
}
```

#### Itens Grid (Filhos)
```css
.item {
    /* Posicionamento por linha */
    grid-row: 1 / 3;
    /* ou */
    grid-row-start: 1;
    grid-row-end: 3;

    /* Posicionamento por coluna */
    grid-column: 1 / 3;
    /* ou */
    grid-column-start: 1;
    grid-column-end: 3;

    /* Shorthand para row e column */
    grid-area: 1 / 1 / 3 / 3;

    /* Auto-alinhamento */
    justify-self: start | end | center | stretch;
    align-self: start | end | center | stretch;
}
```

### Exemplo Prático de Grid

```html
<div class="gallery">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
    <div class="item item3">3</div>
    <div class="item item4">4</div>
</div>
```

```css
.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    padding: 20px;
}

.item {
    background-color: #f0f0f0;
    padding: 20px;
    border-radius: 8px;
    min-height: 200px;
}

/* Item destacado */
.item1 {
    grid-column: span 2;
    grid-row: span 2;
}
```

## Quando Usar Cada Um?

### Use Flexbox quando:
- Precisar alinhar elementos em uma única direção (linha ou coluna)
- Trabalhar com layouts menores ou componentes individuais
- Precisar de flexibilidade na distribuição de espaço
- Criar navegações, cabeçalhos, listas de items
- Alinhar elementos dentro de containers

### Use Grid quando:
- Precisar trabalhar com layouts em duas dimensões
- Criar layouts complexos de página
- Desenvolver interfaces que dependem de tanto linhas quanto colunas
- Precisar de mais controle sobre o posicionamento dos elementos
- Criar galerias ou grids de produtos
- Implementar layouts responsivos complexos

## Dicas de Uso

1. **Combinação**: Você pode (e deve) combinar Flexbox e Grid no mesmo layout
2. **Responsividade**: 
   - Use unidades flexíveis como fr, %, vh/vw
   - Aproveite minmax() e auto-fit/auto-fill no Grid
   - Use flex-wrap no Flexbox para quebra de linha
3. **Performance**: 
   - Grid é mais pesado que Flexbox, use com moderação em elementos muito dinâmicos
   - Prefira Flexbox para alterações frequentes de layout

## Suporte dos Navegadores

Tanto Flexbox quanto Grid têm excelente suporte nos navegadores modernos:
- Flexbox: ~98% de suporte global
- Grid: ~95% de suporte global

Para verificar compatibilidade específica, consulte [caniuse.com](https://caniuse.com).
