# Tipos de dados

## Tipos primitivos

- Number
- String
- Boolean
- Null
- Undefined

Menos comuns mas existem no JS moderno:

- Symbol (ES6)
- BigInt (ES2020)

## Tipos de objetos:

- Array
- Objetos
- Funções

Para checar o tipo de uma variável usamos typeof, porém esse método retorna "object" para null (é um bug que não pode ser corrigido por conta da retrocompatibilidade), objetos e arrays, o que o torna util apenas para comparar primitivos (com excessão de null), para null devemos usar: variável === null.

Existe a função Object.is() que funciona como um comparador super estrito (====), comparando valores e tipos como o === mas nesse caso +0 e -0 são considerados diferentes e NaN e NaN não são iguais.
