# INTRODUÇÃO AO CSS

**CSS signfica Cascading Style Sheets - Folhas de Estilo em Cascata**
- É uma linguagem usada para definir a aparência dos elementos HTML de uma página web
- Com CSS é possível controlar cores, fontes, tamanho, espaçamentos, bordas e muito mais.

## O que é uma regra CSS?
- Uma regra CSS é composta por um seletor e um bloco de declarações.
- O seletor indica quais elementos HTML serão estilizados.
- O bloco de declarações fica entre chave e contém uma ou mais declarações.
- Cada declaração é formada por uma propriedade, dois-pontos, um valor e ponto e virgula

Exemplo de regra CSS:

```css
p {
    color: blue;
    font-size: 16px;
}
```
- Nesse exemplo, p é o seletor, color e font-size são propriedades, blue e 16xp são os valores.

## **TIPOS DE SELETORES**
- Existem três tipos fundamentais de seletores CSS.

### Seletor de Tipo
- **O seletor de tipo usa diretamente o nome da tag HTML**
- Ele afeta todos os elementos daquele tipo que existirem na página
- *Possui a menor especificidade entre os três tipos*
- Exemplos de seletor de tipo:
    - h1{ }
    - p{ }
    - a{ }
    - li{ }
- A regra acima com h1 afetará todos os títulos h1 da página e assim por diante.

### Seletor de Classe
- **O seletor de classe usa um ponto seguido do nome da classe.**
- Ele afeta apenas os elementos que possuem o atributo class com aquele nome.
- Uma mesma classe pode ser aplicada a vários elementos diferentes.
- Um mesmo elemento pode ter mais de uma classe ao mesmo tempo.
- *Possui especificidade intermediária - maior que o seletor de tipo*
- Exemplos de seletor de classe:
  - .destaque{ }
  - .alerta{ }
  - .secundario{ }
  
### Seletor de ID
- **O seletor de ID usa uma cerquilha (#) seguida do nome do id**
- Ele afeta somente o elemento que possui aquele id.
- Um id deve ser único na página - não pode se repetir.
- Possui maior especificade entre os três tipos
- Exemplo de seletor de ID:
    - #cabecalho{ }
    - #rodape{ }
  
## Especificidade
  - Quando dois seletores disputam a mesma propriedade em um elemento, vence o de maior especificidade.
  - A ordem de especificade do maior para o menor é: ID, classe e Tipo
  - Em valores numéricos: ID vale 100, Classe vale 10, Tipo vale 1.