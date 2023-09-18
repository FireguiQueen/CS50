# Algorítimos e seus problemas
Imagine que você está jogando um jogo de computador e, de repente, seu personagem fica preso em uma parede, incapaz de se mover. Esse é um exemplo de um bug. Um bug é um erro ou problema no código de software que faz com que ele não funcione como deveria. 
Sendo assim, podemos considerá-lo nada mais do que problemas lógicos que ocorrem devido à falta de um raciocínio preciso. _Lembre-se de que as máquinas precisam de todos os detalhes possíveis para executar um programa corretamente, sem ambiguidades._

Essa falta de raciocínio preciso não ocorre somente quando nós, desenvolvedores em geral, estamos escrevendo nosso código, mas também pode ocorrer para os desenvolvedores de tecnologias. Por exemplo, você está fazendo uso da tecnologia X e seu código está 100% lógico e preciso, porém, ocorre um bug em seu software. Neste caso, podemos imaginar que o bug ocorreu devido a um raciocínio impreciso na tecnologia que foi utilizada durante a construção do nosso software.

</br>

# Debugging (depuração)
A depuração é o processo de identificar, analisar e corrigir erros, falhas ou bugs em um programa de computador. O objetivo da depuração é garantir que o programa funcione conforme o esperado, produzindo resultados corretos e evitando comportamentos indesejados. Para realizar a depuração, existem ferramentas específicas criadas para esse fim, mas também podemos contar com soluções que, embora não tenham sido originalmente desenvolvidas para a depuração, podem servir a esse propósito.

## `printf()` 
Vamos pensar em um algoritmo no qual você precisa imprimir o caractere '%' cinco vezes. 
Para construí-lo, é bastante simples, basta usar um loop.
```c
    for(int i = 0; i <= 5; i++)
    {
        printf("$ \n");
    }
```
> Após usar o algorítimo acima, veremos o caractere "$" sendo repetido seis vezes, e não cinco.

```
$       // uma vez
$       // duas vezes
$       // três..
$       // quatro..
$       // cinco..
$       // seis..
```

Bem, queríamos o cifrão se repetisse cinco vezes, e não seis. O importante agora é pensar em voz alta: "Isso é um bug". O que fazer para resolvê-lo? 
Para a depuração, existe uma ferramenta "antiga" porém muito útil quando se trabalha com programas simples, ela é a famosa função `printf()` da biblioteca `stdio.h`. 
Neste caso em específico, podemos imprimir o valor da nossa variável de controle "i" toda vez que nosso "for" for executado, por exemplo:
```c
    for(int i = 0; i <= 5; i++)
    {
        printf("O valor de I é: %i \n", i);  // Variável 'i' sendo chamada.
        printf("$ \n");                      // nosso caractere sendo printado. 
    }
```

Após compilar e executar o código acima, teremos o seguinte resultado em nosso terminal:
```
O valor de I é: 0 
$

O valor de I é: 1 
$

O valor de I é: 2 
$

O valor de I é: 3 
$

O valor de I é: 4 
$

O valor de I é: 5 
$ 
```

Agora ficou muito simples solucionar o nosso bug. Podemos observar que o valor de "i" variou de 0 a 5, e a cada valor diferente, o caractere "$" é impresso. Fazendo uma contagem rápida, temos um total de seis números como resultado: 0, 1, 2, 3, 4, 5, e, como resultado, o "$" é repetido seis vezes.

Vamos analisar o algoritimo feito:
- Inciar um loop
    1. Definir uma variável de inicialização: I = 0    (variável i recebe zero);
    2. Definir uma condição: Enquanto I for menor ou igual a 5 continue o loop (I <= 5);
    3. Se a condição acima for verdadeira (ou seja, se I for menor ou igual a 5), printe o caractere '$' no terminal.
    4. Por fim, adicionar +1 a nossa variável de controle. Na segunda vez que o "for" ser executado, o valor da nossa variável de inicialização será '1'. 

Vemos que o resultado no terminal nos mostrou que o valor de 'i' variou de 0 até 5, e isso ocorreu devido à segunda etapa do nosso algoritmo, onde a condição era 'i <= 5'. Quando utilizamos 'i <= 5', estamos dizendo que o loop deve continuar enquanto 'i' for menor ou igual a 5. No entanto, na última iteração do loop, o valor de 'i' é igual a 5.
Aqui está o ponto crucial: a condição '5 <= 5' é considerada verdadeira, porque 5 não é menor que 5, mas é igual a 5. Isso significa que o loop continua a ser executado mesmo quando 'i' é igual a 5, o que não era a nossa intenção original.
Para resolver o nosso bug e garantir que o caractere '$' seja impresso apenas cinco vezes, precisamos ajustar a condição para 'i < 5'. Dessa forma, o loop será executado enquanto 'i' for estritamente menor que 5, indo de 0 a 4, como desejado
```c
    for(int i = 0; i < 5; i++)
    {
        printf("$ \n");              
    }
```

</br>
</br>

## Debug
Ao contrário da função printf() (que foi originalmente projetada para saída de dados, mas é frequentemente usada para depurar programas simples), o "debug" é uma ferramenta específica para depuração que nos permite utilizar uma variedade de recursos para depurar nosso código.
Um exemplo disso é que, com o 'debug', podemos fazer com que nosso programa seja executado passo a passo, linha por linha, o que nos permite acompanhar o que está acontecendo.

Suponhamos que temos um loop for simples em nosso código:
```c
    for (int i = 1; i <= 5; i++) 
    {
        // Algum código aqui
    }
```
Usando uma ferramenta de depuração, como um ambiente de desenvolvimento integrado (IDE) ou um depurador de linha de comando, podemos adicionar pontos de interrupção (breakpoints) dentro do loop for. Quando o programa é executado no modo de depuração e atinge um ponto de interrupção, ele pausa a execução e nos permite inspecionar o valor da variável "i" naquele momento.

Isso é particularmente útil para entender como as variáveis mudam à medida que o programa é executado, permitindo-nos identificar problemas e corrigir possíveis erros em nosso código de maneira mais eficiente. Durante a depuração, podemos observar o valor de "i" em cada iteração do loop e garantir que ele está se comportando conforme o esperado.

</br>
</br>

## Rubber duck debugging