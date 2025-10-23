# Análise de Sincronização de Threads em Java  
**Disciplina:** Sistemas Distribuidos
**Atividade Prática 01 — Produtor/Consumidor sem Sincronização**

---

## 1. Detalhes das Execuções

### 1.1 Primeira Execução (`log1.txt`)
**Comando executado:**
```bash
java MeuDadoThreadsJava > log1.txt


Saída observada (trecho):

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

1.2 Segunda Execução (log2.txt)
java MeuDadoThreadsJava > log2.txt

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


diff log1.txt log2.txt


Saída (resumo):

3,5d2
< Consumidor: 0
< Consumidor: 0
< Consumidor: 0
...
60a60
Consumidor: 29


2. Análise Técnica

O código representa o problema do Produtor-Consumidor, implementado sem sincronização.
Dessa forma, as threads compartilham o mesmo objeto Dado sem coordenação, levando a uma série de efeitos colaterais:

O consumidor pode ler o mesmo valor várias vezes (quando o produtor demora a atualizar).

O produtor pode sobrescrever valores antes da leitura, causando perda de dados.

O resultado é não determinístico, variando a cada execução.

Em Java, o acesso a recursos compartilhados por múltiplas threads deve ser controlado com:

Blocos synchronized,

Métodos wait() e notify(), ou

Estruturas da biblioteca java.util.concurrent (como BlockingQueue).

A ausência desses mecanismos leva à inconsistência dos dados e perda da previsibilidade do programa.

3. Opinião Pessoal e Conclusões

Durante a observação das execuções, ficou evidente a importância da sincronização em programas concorrentes.
Mesmo que o programa "funcione", seus resultados são inconsistentes e não confiáveis.

A sincronização garante que:

O produtor não escreva enquanto o consumidor ainda não leu o dado anterior.

O consumidor espere até que um novo valor esteja disponível.

Sem esse controle, o comportamento das threads depende apenas da política de escalonamento do sistema operacional, o que explica as variações vistas entre os logs.

Conclusão: A sincronização é fundamental para garantir integridade de dados, ordem correta de execução e previsibilidade em programas multithread.
