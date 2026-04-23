# CSS - Externo, importado, interno e inline

## O que é CSS
CSS significa **Cascading Style Sheets** (*Folhas de Estilo em Cascata*).  
Ele é usado para definir a **aparência visual** das páginas HTML, como cores, fontes, tamanhos, margens, fundos e alinhamentos.

## Tipos de vinculação de CSS

### 1. CSS externo
É quando o código CSS fica em **um arquivo separado**, com extensão `.css`.  
Esse arquivo é conectado ao HTML pela tag `<link>` dentro do `<head>`.

**Vantagens:**
- pode ser reutilizado em várias páginas
- deixa o projeto mais organizado
- separa estrutura (HTML) de apresentação (CSS)

### 2. CSS importado
Funciona de forma parecida com o externo, mas o arquivo é trazido com a diretiva `@import`, dentro da tag `<style>` no `<head>`.

### 3. CSS interno
É quando o CSS é escrito dentro da própria página HTML, usando a tag `<style>` no `<head>`.  
Serve para estilizar apenas aquela página.

### 4. CSS inline
É quando o estilo é aplicado diretamente na tag HTML, usando o atributo `style`.

Exemplo:
```html
<p style="color: blue;">Texto azul</p>
```
Esse tipo não é o mais indicado, porque dificulta a organização e o reaproveitamento do código.

## Estrutura de uma regra CSS

Uma regra CSS tem 3 partes:

- Seletor: escolhe o elemento
- Propriedade: define o que será alterado
- Valor: informa como será alterado

Exemplo:
```css
body {
  color: white;
  font-size: 16pt;
  background-color: #3D3F40;
}
```

## Especificidade e precedência

Quando várias regras podem ser aplicadas ao mesmo elemento, o navegador escolhe a de maior prioridade.

Ordem geral de prioridade:
1. inline
2. interno (<style>)
3. externo (.css)
   
Prioridade dos seletores:
- seletor de elemento → menor prioridade
- seletor de classe → prioridade média
- seletor de id → maior prioridade

> Quanto mais específico for o seletor, maior a chance dele prevalecer.

## Agrupamento de seletores e comentários

Quando vários elementos têm o mesmo estilo, podemos agrupá-los:
```css
h1, h2, p {
  text-align: center;
  color: red;
}
```
Comentários em CSS são ignorados pelo navegador:
```css
/* Isso é um comentário */
```
## Principais usos do CSS

O CSS pode ser usado para estilizar:

- fontes
- textos
- margens
- bordas
- padding
- fundos
- links

## Propriedades de fonte e texto
### Fontes
- color → cor do texto
- font-family → tipo da fonte
- font-size → tamanho da fonte
- font-style → estilo da fonte
- font-weight → espessura da fonte
- font → forma abreviada
  
### Texto
- text-align → alinhamento
- text-decoration → decoração do texto
- text-indent → recuo da primeira linha
- text-transform → maiúsculas/minúsculas
- vertical-align → alinhamento vertical
- line-height → altura da linha

### Cores no CSS

As cores podem ser definidas de várias formas:

- por nome: red, blue
- por RGB
- por HEX
- por HSL
- por RGBA e HSLA

Exemplo:
  ```css
color: red;
color: rgb(255, 0, 0);
color: #ff0000;
```

### Background

As propriedades de fundo servem para estilizar o fundo dos elementos:

- background-color → cor de fundo
- background-image → imagem de fundo
- background-repeat → repetição da imagem
- background-attachment → define se o fundo fica fixo
- background-position → posição da imagem

### Unidades de medida no CSS
*Unidades absolutas*

Não dependem de outro valor:

- in
- cm
- mm
- pt
- pc

*Unidades relativas*

Dependem de um valor de referência:

- em
- rem
- ex
- px
- %

### Diferença entre em e rem
- em depende do tamanho da fonte do elemento atual
- rem depende do tamanho da fonte do elemento raiz (html)
  
Exemplo:
- 1em pode mudar conforme o elemento
- 1rem tende a permanecer fixo com base no <html>
