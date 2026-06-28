# EXPA04 — Sistema de Gestão de Stock

**Disciplina:** Programação e Sistemas de Informação (PSI) — Módulo 3
**Exercício Prático:** 04
**Código:** `1I-PSI-M3-14785-EXPA04`
**Turma:** 1.º I — N.º 14785
**Ano Letivo:** 2025/2026

Programa em Python que gere o stock de materiais escolares. Usa dicionários, funções e um menu interativo com seis opções. Inclui funcionalidade extra de exportação para ficheiro `.txt` com marca temporal, desenvolvida de forma autónoma além do enunciado original.

---

## Ficheiros

| Ficheiro | Descrição |
|---|---|
| `1I-PSI-M3-14785-EXPA04.py` | Programa completo |
| `2026.03.24.08.39.52-Stock_Export.txt` | Exemplo de exportação gerada pelo programa |
| `README.md` | Este ficheiro |

---

## Funcionalidades

| Opção | Ação |
|---|---|
| 1 | Adicionar material e quantidade inicial |
| 2 | Consultar stock de um material específico |
| 3 | Atualizar stock — adicionar (A) ou remover (R) unidades |
| 4 | Exibir estado geral do stock |
| 5 | Exportar stock para ficheiro `.txt` com marca temporal |
| 6 | Sair |

---

## Funções Implementadas

### `adicionar_material(stock)`

Regista um novo material no dicionário `stock`. Verifica se já existe antes de inserir. Valida que a quantidade inicial não é negativa e que é um número inteiro.

```python
def adicionar_material(stock):
    nome = input("Nome do material: ").capitalize()
    if nome in stock:
        print("O material ja existe no stock!")
    else:
        try:
            quantidade = int(input(f"Quantidade inicial de {nome}: "))
            if quantidade < 0:
                print("Quantidade nao pode ser negativa!")
                return
            stock[nome] = quantidade
            print(f"{nome} adicionado com sucesso!")
        except ValueError:
            print("Erro: Quantidade invalida! Deve ser um numero inteiro.")
```

---

### `consultar_stock(stock)`

Pesquisa um material no dicionário e mostra a quantidade disponível. Informa se o material não existe.

```python
def consultar_stock(stock):
    nome = input("Nome do material para consulta: ").capitalize()
    if nome in stock:
        print(f"O stock atual de {nome} e: {stock[nome]}")
    else:
        print(f"{nome} nao encontrado no stock.")
```

---

### `atualizar_stock(stock)`

Permite adicionar (`A`) ou remover (`R`) unidades de um material existente. Na remoção, verifica se há stock suficiente antes de subtrair.

```python
def atualizar_stock(stock):
    nome = input("Nome do material a atualizar: ").capitalize()
    if nome in stock:
        operacao = input("Deseja adicionar (A) ou remover (R)? ").upper()
        try:
            quantidade = int(input("Quantidade: "))
            if quantidade < 0:
                print("Erro: Quantidade nao pode ser negativa!")
                return
            if operacao == "A":
                stock[nome] += quantidade
            elif operacao == "R":
                if quantidade <= stock[nome]:
                    stock[nome] -= quantidade
                else:
                    print("Quantidade insuficiente em stock!")
            else:
                print("Operacao invalida!")
        except ValueError:
            print("Erro: Quantidade invalida! Deve ser um numero inteiro.")
    else:
        print(f"{nome} nao encontrado no stock.")
```

---

### `exibir_stock(stock)`

Mostra o estado geral do dicionário em formato tabular. Indica se o stock está vazio.

```python
def exibir_stock(stock):
    print("\nEstado Geral do Stock:")
    print("Material\tQuantidade")
    print("-" * 30)
    if not stock:
        print("Stock vazio.")
    else:
        for material, quantidade in stock.items():
            print(f"{material}\t\t{quantidade}")
```

---

### `file_export(stock)` — Funcionalidade Extra

Exporta o estado atual do stock para um ficheiro `.txt`. O nome do ficheiro inclui a data e hora exatas da exportação no formato `AAAA.MM.DD.HH.MM.SS-Stock_Export.txt`.

```python
def file_export(stock):
    if not stock:
        print("Stock vazio. Nada para exportar.")
        return
    now = datetime.datetime.now()
    formatted_time = now.strftime("%Y.%m.%d.%H.%M.%S")
    filename = f"{formatted_time}-Stock_Export.txt"
    try:
        with open(filename, "w", encoding="utf-8") as file:
            file.write("Material\tQuantidade\n")
            file.write("-" * 30 + "\n")
            for material, quantidade in stock.items():
                file.write(f"{material}\t\t{quantidade}\n")
        print(f"Stock exportado com sucesso para: {filename}")
    except IOError:
        print("Erro: Nao foi possivel criar o ficheiro.")
```

Exemplo de ficheiro gerado (`2026.03.24.08.39.52-Stock_Export.txt`):

```
Material    Quantidade
------------------------------
Cobre       110
Rodrigo     1
```

---

## Estrutura Geral do Programa

```
main()
|
+-- stock = {}              # dicionário vazio
|
+-- while True              # menu repetitivo
    |
    +-- opção 1 --> adicionar_material(stock)
    |
    +-- opção 2 --> consultar_stock(stock)
    |
    +-- opção 3 --> atualizar_stock(stock)
    |
    +-- opção 4 --> exibir_stock(stock)
    |
    +-- opção 5 --> file_export(stock)    # funcionalidade extra
    |
    +-- opção 6 --> break
```

---

## Conceitos Abordados

| Conceito | Aplicação |
|---|---|
| Dicionário (`dict`) | Estrutura chave-valor para o stock |
| `.capitalize()` | Normalização do nome do material |
| `in` | Verificar se chave existe no dicionário |
| `.items()` | Iterar sobre pares chave-valor |
| `try / except ValueError` | Tratamento de entrada não numérica |
| `datetime` | Marca temporal para nome do ficheiro |
| `open()` com `with` | Escrita de ficheiro com gestão automática |
| Funções | Uma responsabilidade por função |
| `if __name__ == "__main__"` | Ponto de entrada do programa |

---

## Diferença Face ao Enunciado Original

O enunciado previa quatro funções e um menu com quatro opções. Foram introduzidas duas melhorias autónomas:

1. Validação de entradas em `adicionar_material` e `atualizar_stock` com `try / except` — o original não validava o tipo nem valores negativos.
2. Função `file_export` com exportação para `.txt` com marca temporal — opção 5 adicionada ao menu.

---

## Como Executar

```bash
git clone https://github.com/a14785-oficina/sistema-gestao-stock.git
cd sistema-gestao-stock
python3 1I-PSI-M3-14785-EXPA04.py
```

---

## Navegação — Módulo 3

| Posição | Repositório |
|---|---|
| Anterior | [EXPA03 — Sistema de Gestão de Notas](https://github.com/a14785-oficina/sistema-gestao-notas) |
| Seguinte | Início do Módulo 17 |
| Portfólio | [oficina-jpc](https://github.com/a14785-oficina/oficina-jpc) |

---

*PSI — Módulo 3 — Programação Estruturada — OFICINA — 2025/2026*
