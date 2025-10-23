## RELATORIO
* 
# Análise de Sincronização de Threads em Java

## Atividade Prática 01

### Detalhes das Execuções
- **Primeira Execução (`log1.txt`):**
  - Comando: `java MeuDadoThreadsJava > log1.txt`
  - Saída observada:
Produtor: 0
Consumidor: 0
Consumidor: 0
Consumidor: 0
Consumidor: 0
Produtor: 1
Consumidor: 1
Consumidor: 1
Consumidor: 1
Consumidor: 1
Produtor: 2
Produtor: 3
Consumidor: 3
Produtor: 4
Consumidor: 4
Consumidor: 4
Produtor: 5
Consumidor: 5
Produtor: 6
Consumidor: 6
Produtor: 7
Consumidor: 7
Produtor: 8
Produtor: 9
Produtor: 10
Consumidor: 10
Produtor: 11
Produtor: 12
Produtor: 13
Consumidor: 13
Produtor: 14
Consumidor: 14
Produtor: 15
Consumidor: 15
Produtor: 16
Consumidor: 16
Consumidor: 16
Produtor: 17
Consumidor: 17
Produtor: 18
Consumidor: 18
Produtor: 19
Consumidor: 19
Produtor: 20
Consumidor: 20
Consumidor: 20
Produtor: 21
Consumidor: 21
Consumidor: 21
Produtor: 22
Produtor: 23
Produtor: 24
Consumidor: 24
Produtor: 25
Produtor: 26
Produtor: 27
Consumidor: 27
Consumidor: 27
Produtor: 28
Produtor: 29


*- Observação: O produtor armazenou valores de 0 a 29, enquanto o consumidor leu esses valores. O consumidor leu alguns valores várias vezes devido à sobreescrita do valor `Dado` pelo produtor antes da leitura, indicando uma condição de corrida.

- **Segunda Execução (`log2.txt`):**
- Comando: `java MeuDadoThreadsJava > log2.txt`
- Saída observada:
Produtor: 0
Consumidor: 0
Produtor: 1
Produtor: 2
Consumidor: 2
Consumidor: 2
Produtor: 3
Consumidor: 3
Produtor: 4
Consumidor: 4
Produtor: 5
Produtor: 6
Consumidor: 6
Consumidor: 6
Consumidor: 6
Consumidor: 6
Produtor: 7
Consumidor: 7
Produtor: 8
Produtor: 9
Consumidor: 9
Consumidor: 9
Produtor: 10
Consumidor: 10
Produtor: 11
Produtor: 12
Consumidor: 12
Produtor: 13
Consumidor: 13
Produtor: 14
Produtor: 15
Consumidor: 15
Produtor: 16
Consumidor: 16
Produtor: 17
Consumidor: 17
Consumidor: 17
Produtor: 18
Consumidor: 18
Produtor: 19
Consumidor: 19
Produtor: 20
Consumidor: 20
Produtor: 21
Produtor: 22
Consumidor: 22
Produtor: 23
Consumidor: 23
Produtor: 24
Consumidor: 24
Produtor: 25
Produtor: 26
Consumidor: 26
Consumidor: 26
Produtor: 27
Consumidor: 27
Consumidor: 27
Produtor: 28
Produtor: 29
Consumidor: 29


*- Observação: A ordem das operações mudou, com o consumidor lendo menos valores duplicados para alguns casos e mais para outros , refletindo diferentes condições de corrida.

- **Comparação (`diff log1.txt log2.txt`):**
- Resultado do diff:
3,5d2
< Consumidor: 0
< Consumidor: 0
< Consumidor: 0
7,10d3
< Consumidor: 1
< Consumidor: 1
< Consumidor: 1
< Consumidor: 1
11a5,6

Consumidor: 2
Consumidor: 2
16d10
< Consumidor: 4
18d11
< Consumidor: 5
20a14,16
Consumidor: 6
Consumidor: 6
Consumidor: 6
24a21,22
Consumidor: 9
Consumidor: 9
28a27
Consumidor: 12
32d30
< Consumidor: 14
37d34
< Consumidor: 16
39a37
Consumidor: 17
46d43
< Consumidor: 20
48,49d44
< Consumidor: 21
< Consumidor: 21
50a46
Consumidor: 22
51a48
Consumidor: 23
55a53,54
Consumidor: 26
Consumidor: 26
60a60
Consumidor: 29
