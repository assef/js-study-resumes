# Tipos de variáveis

## var:

Quando declaramos uma variável com var, ela fica disponível para todo o código, mesmo que você declare var dentro de uma condição ( if, while, etc), ela pode ser acessada fora.

## let:

Por outro lado só é acessado no escopo em que é definido, portanto declarar let dentro de uma condição ou loop não permite que ele seja acessado fora.

## const:

Define uma variável que não pode ser reatribuida, ou seja, não é possível depois de iniciar fazer, constante = novo valor. Porém, objetos e arrays podem ser manipulados mesmo quando definidos como const, pois a manipulação de objetos não depende de reatribuição. Nesse caso, não é possível fazer:

```javascript
const objeto = {};
objeto = { a: 1 };
```

Mas é possível fazer:

```javascript
const objeto = {}
objeto[“a”] = 1
```

## Funções:

Funções são um tipo de objeto, existem duas formas principais de declarar uma função:

```javascript
function nomeDaFuncao(parametros) {}
```

Nesse caso o nome (nomeDaFuncao) é atribuído a seu valor (código a ser executado) durante a compilação. Ou seja, a função fica disponivel desde o início da execução, pois o compilador move ela para o topo, isso é chamado de hoisting.

```javascript
const nomeDaFuncao = function (parametros) {};
```

Nesse caso, o nome da função é atribuído ao seu valor quando o código chega nessa linha (no runtime), ou seja, a função fica disponivel para uso depois que o código é executado.
