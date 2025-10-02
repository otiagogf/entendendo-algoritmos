# Binary Search

### Vamos supor que você tem uma tabela de 100 id de forma ordenada, e você quer saber se o id 77 está na tabela.

### Existem duas formas de fazer isso, a primeira é percorrer a tabela do início ao fim, mas isso é muito custoso, pois você precisa percorrer todos os 100 elementos da tabela. A segunda forma é usar a pesquisa binária, sendo uma forma de dividir o problema em subproblemas menores, e depois combinar as soluções desses subproblemas para obter a solução do problema original.

### A pesquisa binária funciona da seguinte forma:
* Comece no meio da tabela.
* Se o id do meio for o que você está procurando, você acabou.
* Se o id do meio for maior do que o que você está procurando, repita a pesquisa na metade da tabela à esquerda.
* Se o id do meio for menor do que o que você está procurando, repita a pesquisa na metade da tabela à direita.
* Repita até que você encontre o id ou até que a tabela esteja vazia.

## Exemplo

### Você está procurando uma palavra no dicionário. Nesse dicionário existem 240 mil palavras. No pior dos casos você teria que olhar todas as 240 mil palavras para encontrar a palavra que você está procurando.
### De quantas etapas você precisa para encontrar a palavra que está procurando?

### Se formos fazer a pesquisa simplesmente do início ao fim, precisaríamos de 240 mil etapas, o que é muito custoso.

### Agora vamos usar a pesquisa binária:

### A cada etapa da pesquisa binária, você está reduzindo o número de palavras que você precisa olhar pela metade.
* 240K → 120K → 60K → 30K → 15K → 7.5K → 3.75K → 1.875K → 938 → 469 → 235 → 118 → 59 → 30 → 15 → 8 → 4 → 2 → 1.

### Nele, você precisa de 18 etapas para encontrar a palavra que você está procurando. Repare que a pesquisa binária é muito mais rápida do que a pesquisa simples.
### Em uma lista de X elementos, a pesquisa binária precisa de log2(X) etapas para encontrar o elemento que você está procurando.
### Logaritmos são o inverso da exponenciação.
### Se você tem um número X elevado a uma potência Y, você pode tirar a potência Y do número X para obter o logaritmo de X na base Y.
* 102 = 100 → log10(100) = 2
* 103 = 1000 → log10(1000) = 3
* 23 = 8 → log2(8) = 3
* 24 = 16 → log2(16) = 4 25 = 32 → log2(32) = 5

```java
public class PesquisaBinariaExemplo {

    public static int pesquisaBinaria(int[] lista, int item) {
        int baixo = 0;
        int alto = lista.length - 1;

        while (baixo <= alto) {
            int meio = (baixo + alto) / 2;
            int chute = lista[meio];

            if (chute == item) {
                return meio;
            }
            if (chute > item) {
                alto = meio - 1;
            } else {
                baixo = meio + 1;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] minhaLista = {1, 3, 5, 7, 9};

        System.out.println(pesquisaBinaria(minhaLista, 3));
        System.out.println(pesquisaBinaria(minhaLista, -1));
    }
}
```

### Uma coisa que você deve ter notado é que a lista precisa estar ordenada para que a pesquisa binária funcione. Se a lista não estiver ordenada, você pode ordená-la primeiro e depois fazer a pesquisa binária.

## Tempo de execução

### Algo citado no livro é sobre o tempo de execução de um algoritmo.
* Com a pesquisa binária, o tempo de execução é O(log n).
* Com a pesquisa simples, o tempo de execução é O(n).

### Isso gera muita economia no processamento e torna a pesquisa muito mais poderosa e eficiente.
