# O que é JavaScript?

## Compilado ou interpretado:

O JS é entregue em seu formato original (código) escrito aos navegadores (normalmente transpilado e minificado, mas ainda assim código JS) e isso faz parecer uma linguagem interpretada, porém está errado.
JS é compilado antes da execução pelo motor JS. Depois de recebido pelo navegador, o código é parseado (transformado em AST, sintaxe de arvore abstrata), compilado e então executado.
Portanto, antes de ser executado o código temos retorno de erros de syntax (principalmente se o modo estrito estiver ativo).

A diferença entre o JS e uma linguagem como GoLang (usando esse exemplo por que eu tenho mais familiaridade) é que no Go após o termino de um código o programador executa a compilação e publica apenas o resultado dela, ou seja, não é possível publicar um código com erro desde que o programador compile ele antes de publicar.
No Js a compilação vai ser feita no browser, então o programador para presenciar o build precisa executar o código no navegador (não diferencia muito de executar um compilador na maquina, mas parece que não existe compilação pois quem inicia isso é o próprio navegador quando recebe o arquivo js). Em suma, se o programador executar o código no navegador, é possível antecipar os erros. Linters fazem o papel de informar erros de compilação antecipadamente também.

## WASM:

É um projeto que visa levar outras linguagens para a web, funciona criando binários compatíveis com o motor JS dos navegadores, dessa forma o código WASM gerado pula a etapa de parse do motor e vai direto para compilação e execução.
WASM não é linguagem, é um alvo de compilação para outras linguagens serem executadas pelo motor JS.

## Modo estrito:

O modo estrito surgiu em 2009 com o ES5. Ele pode ser ativado no topo de cada arquivo com a string “use strict”; (não pode haver nada além de comentários antes da flag) ou dentro de funções (também no topo).
Com o modo estrito ativado, o compilador vai ser mais rigoroso com erros que não necessariamente são de sintax mas que causariam anormalidades retornando um erro na hora do build. O modo estrito também altera alguns comportamentos do runtime, como o this que passa a ser undefined por padrão ao invés do objeto global (window em browsers).
