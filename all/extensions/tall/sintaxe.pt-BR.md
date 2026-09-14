# TALL (Linguagem de Lógica Analógica Temporizada)
Extensão usada para declarar delays e funções baseadas no tempo.

## Delay simples
Para declarar que uma função simples demorará um certo tempo para mudar para um (o próximo) valor, usa-se `@` + número (inteiro ou fracional) + unidade de tempo antes do sinal de igual.

São aceitas as unidades:
| dia          | d  |
| hora         | h  |
| minuto       | m  |
| segundo      | s  |
| milisegundo  | ms |
| microsegundo | us |
| nanosegundo  | ns |
Exemplo:
```
a @2s= a + 1;
```
Onde o exemplo superior geraria a seguinte tabela:
| segundo | valor de a |
|---------|------------|
|    0    |      0     |
|    1    |      0     |
|    2    |      1     |
|    3    |      1     |
|    4    |      2     |
|    5    |      2     |
|    6    |      3     |

É possivel repetir o símbolo `@` para declarar um valor inicial:
```
A : 5;
b @2s@A= a + 1;
```
Aqui durante o segundo 0 `b` valerá 5.

## Função de onda
Adiciona-se `~` antes do `=`, com o tipo de aproximação que terá-se entre um valor e outro.

Aproximações aceitas:
- linear

Exemplo:
```
a @2s@15~linear= a ? 15, < 15, ! -15;
```
Vai gerar uma onda triangular de 4hz variando de 15 a -15.