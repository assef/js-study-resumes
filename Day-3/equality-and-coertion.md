# Igualdade e coerção

## Igualdade:

Existem dois operadores de igualdade, == (igual com coerção) e === (igual, sem coerção). No primeiro caso, se os tipos comparados forem diferente (string == number) o compilador converte os valores para o mesmo tipo e os compara, enquanto a comparação estrita (===) compara o valor e o tipo, sem converte-los.
Usar === não garante 100% de prevenção de falha, por exemplo NaN === NaN //retorna false e 0 === -0 retorna true, isso também vale para objetos, comparar dois objetos com as mesmas chaves irá retornar false, pois o js não compara o conteúdo do objeto, apenas a referência de memória. Ou seja:

```javascript
Const a = {a: 42}
Const b = a; //A é igual a B, pois B foi definido copiando A (as duas variáveis acessam o mesmo endereço de memória, e isso pode gerar problemas, alterar b também altera a)

a === b //retorna true
```

Enquanto:

```javascript
Const a = {a: 42}
Const b = {a: 42}

a === b //retorna false (apesar do conteudo igual, foram atribuídos endereços de memória diferentes para cada uma).
```

Comparadores de grandeza não possuem comparação estrita, ou seja <, >, <=, ou >= sempre vão fazer coerção, e é necessário alguns cuidados pois por exemplo “10” < “9” retorna true, pois como os dois tipos são iguais, não há conversão e o js compara como ordem alfabética, a vem antes de 9 (como Ana, vem antes de Leonardo) então esta numa posição menor (nesse caso 1 está antes na tabela ASCII do que 9).

A coerção de comparação (quando envolve um operador de igualdade) sempre tentar converter para números, portando “1” = 1, “1” é convertido para 1 e retorna true.
Null e undefined são considerados iguais, porém null ou undefined se comparados com qualquer outro valor é false, isso é estranho pois pela lógica null == 0 seria true, pois Number(null) é 0, mas na árvore de decisão do JS, essas duas regras vem antes da regra de conversão para number, então o código retorna nesse ponto.

Na comparação de objetos com outro tipo, o JS tenta converter o objeto primeiro com valueOf (object.valueOf()) e depois com toString (object.toString), por exemplo:

```javascript
[10] == 10 //true
[10].valueOf() //retorna [10]
[10].toString() //retorna “10”
Number(“10”) //retorna 10, e finalmente 10 == 10.
```

Mas:

```javascript
[10, 10] == 1010 //false
[10,10].valueOf() //retorna [10,10]
[10,10].toString() //retorna “10,10”
Number(“10,10”) //retorna NaN que é diferente de 1010.
```

A coerção também funciona para condições (if, else, while, etc), mas de forma diferente, nesse caso temos os termos **truthy** e **falsy**, sendo:

### Falsy:

- null
- undefined
- false
- NaN
- 0
- -0
- 0n
- ""
- document.all

### Truthy:

- Tudo que não é falsy.

É importante notar que isso só é válido para estruturas condicionais:

```javascript
const arrayvazio = [];

if (arrayvazio) {
  //entra na condição
}
```

Mas:

```javascript
const arrayvazio = [];

if (arrayvazio == true) {
  //não entra
}
```

Isso acontece por que:

```javascript
[] == true,

//convertendo a esquerda para number
[].valueOf() //retorna [],
[].toString() //retorna “”,
Number(“”) //retorna 0.

//convertendo a direita para number
0 == true,
Number(true) //retorna 1,
0 == 1, //retorna false.
```
