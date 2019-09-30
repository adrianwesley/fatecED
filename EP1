# VALE A PENA ORDENAR
# ADRIAN WESLEY
# CAIQUE FERNANDES
# FATEC - 3 - ADS A

from random import sample
from random import randint
import time

# -------------------- Variaveis globais -------------------- #

# Busca binária
contador_binaria = 0

# -------------------- Algoritmos de ordenaçao -------------------- #

# Insercao
def ord_insercao(v):
    for j in range(1, len(v)):
        x = v[j]
        i = j - 1
        while i >= 0 and v[i] > x:
            v[i+1] = v[i]
            i = i - 1
        v[i + 1] = x
    return v
# Fim Insercao

# Selecao
def ord_selecao(v):
    resp = []
    while len(v) > 0:
        m = min(v)
        resp.append(m)
        v.remove(m)
    return resp
# Fim Selecao


# Merge
def ord_merge(e, d):
    r = []
    i, j = 0, 0
    while i < len(e) and j < len(d):
        if e[i] <= d[j]:
            r.append(e[i])
            i += 1
        else:
            r.append(d[j])
            j += 1
    r += e[i:]
    r += d[j:]
    return r
# Fim Merge

# Quicksort
def ord_quicksort(v):
    if len(v) <= 1:
        return v

    pivot = v[0]
    equals = [x for x in v if x == pivot]
    smaller = [x for x in v if x < pivot]
    higher = [x for x in v if x > pivot]
    return ord_quicksort(smaller) + equals + ord_quicksort(higher)
# Fim Quicksort

# Mergesort
def ord_mergesort(v):
    if len(v) <= 1:
        return v
    else:
        m = len(v) // 2
        e = ord_mergesort(v[:m])
        d = ord_mergesort(v[m:])
        return ord_merge(e, d)
# Fim Mergesort

# Busca Binaria
def busca_binaria(x, v):
    global contador_binaria
    e = -1
    d = len(v)
    while e < d-1:
        m = (e + d) // 2
        contador_binaria = contador_binaria + 1
        if v[m] < x:
            e = m
        else:
            d = m
    return d
# Fim Busca Binaria

# Busca Sequencial
def busca_sequencial(v, x):
    for i in range(len(v)):
        if v[i] == x:
            return True
    return False
# Fim Busca Sequencial

# Resultado Criar Divisoria
def resultado_criar_divisoria(tracos):
    return "| {} |".format(tracos)
# Fim Resultado Criar Divisoria


# Criar a primeira linha tracejada - Cabeçalho
linha_tracejada1 = "".join(map(lambda x: x * 41, '-'))
# Criar a segunda linha tracejada - Fim cabeçalho
linha_tracejada2 = "".join(map(lambda x: x * 114, '-'))
# Criar a terceira linha tracejada - Qtde elementos vetor
linha_tracejada3 = "".join(map(lambda x: x * 13, '-'))
# Criar a quarta linha tracejada - Tempo de ordenação
linha_tracejada4 = "".join(map(lambda x: x * 48, '-'))
# Criar a quinta linha tracejada - Numero de buscas
linha_tracejada5 = "".join(map(lambda x: x * 47, '-'))

# Criar a primeira linha do resultado
print("| {} {} {}  |".format(linha_tracejada1,
                             '[EP 1 - Vale a pena ordenar?]', linha_tracejada1))

# Criar a linha incluindo os nomes dos alunos
print('|\tAluno: Adrian Wesley - 3 - ADS A,  Caique Fernandes - 3 - ADS A\t\t\t\t\t\t     |')

# Inserindo linha divisória
print(resultado_criar_divisoria(linha_tracejada2))

# Segundo Cabeçalho
print('|\t\t\t\t Tempo de ordenação\t\t\t\tNumero de buscas\t\t     |')
# Inserindo linha divisória
print(resultado_criar_divisoria(linha_tracejada2))
# Criar o terceiro cabeçalho
print('|\tn\t| Insercao\tSelecao\tMerge.\tQuick.\tS. Nativo  | Insercao\tSelecao\tMerge\tQuick\tS. Nativo    |')
print("| {} | {} | {} |".format(
    linha_tracejada3, linha_tracejada4, linha_tracejada5))

# Contador Binaria Sequencial Alg
def contador_binaria_sequencial_alg(vetor, resultado, tempo_ordenacao):
    contador = 0
    tempo_total = 0
    while tempo_total <= tempo_ordenacao:
        contador += 1
        r = randint(1, n)
        tempo_seq_i = time.time()
        busca_sequencial(vetor, r)
        tempo_seq_f = time.time()
        tempo_seq = tempo_seq_f - tempo_seq_i
        tempo_bi_i = time.time()
        busca_binaria(r, resultado)
        tempo_bi_f = time.time()
        tempo_bi = tempo_bi_f - tempo_bi_i
        tempo_total = tempo_total + (tempo_seq - tempo_bi)
    return contador, tempo_total
# Fim Contador Binaria Sequencial Alg

# Gerar Tempo de Ordenacao e Resultado
def gerar_tempo_ordenacao(vetor, funcao_ordenacao):
    tempo_inicio = time.time()
    vetor_copia = vetor[:]
    resultado = funcao_ordenacao(vetor_copia)
    tempo_fim = time.time()
    tempo = tempo_fim - tempo_inicio
    return resultado, tempo
# Fim Gerar Tempo de Ordenacao e Resultado

# -------------------- Criar os Resultados -------------------- #

# Quantidade de Passos
i = 1
while i <= 5:
    # Tamanho de Vetor
    n = 5000 * i

    # Quantidade de Passos
    i += 1

    # Gerar uma amostragem do vetor com a quantidade de passos
    vetor = sample(range(n), n)

    # Tempo Insercao
    resultado_insercao, tempo_insercao = gerar_tempo_ordenacao(
        vetor, ord_insercao)
    contagem_insercao, tempo_total_insercao = contador_binaria_sequencial_alg(
        vetor, resultado_insercao, tempo_insercao)

    # Tempo Selecao
    resultado_selecao, tempo_selecao = gerar_tempo_ordenacao(
        vetor, ord_selecao)
    contador_selecao, tempo_total_selecao = contador_binaria_sequencial_alg(
        vetor, resultado_selecao, tempo_selecao)

    # Tempo Tempo Merge Sort
    resultado_mergesort, tempo_mergesort = gerar_tempo_ordenacao(
        vetor, ord_mergesort)
    contador_merge_sort, tempo_total_merge_sort = contador_binaria_sequencial_alg(
        vetor, resultado_mergesort, tempo_mergesort)

    # Tempo Quick Sort
    resultado_quicksort, tempo_quicksort = gerar_tempo_ordenacao(
        vetor, ord_quicksort)
    contador_quick_sort, tempo_total_quick_sort = contador_binaria_sequencial_alg(
        vetor, resultado_quicksort, tempo_quicksort)

    # Tempo Sort Nativo
    inicio_sort_nativo = time.time()
    resultado_sort_nativo = vetor[:]
    resultado_sort_nativo.sort()
    fim_sort_nativo = time.time()
    tempo_sort_nativo = fim_sort_nativo - inicio_sort_nativo

    contador_sort_nativo, tempo_total_sort_nativo = contador_binaria_sequencial_alg(
        vetor, resultado_sort_nativo, tempo_sort_nativo)

    print(f'|\t{n}\t| {tempo_insercao:.2f}     \t{tempo_selecao:.2f}', end='')
    print(
        f'\t{tempo_mergesort:.2f}\t{tempo_quicksort:.2f}\t{tempo_sort_nativo:.6f}   |', end='')
    print(f' {contagem_insercao}\t{contador_selecao}\t{contador_merge_sort}\t{contador_quick_sort}\t{contador_sort_nativo}\t     |')
print('|', linha_tracejada2, '|')
