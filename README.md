# TP04 -- Estruturas Condicionais

**Disciplina:** Programacao e Sistemas de Informacao (PSI) -- Modulo 3
**Trabalho Pratico:** 04
**Turma:** 1.o I -- N.o 14785
**Ano Letivo:** 2025/2026

Introducao as estruturas `if / elif / else` em quatro cenarios progressivamente mais complexos: multibanco, classificacao etaria, maior de tres numeros e sistema de desconto.

---

## Ficheiros

| Ficheiro | Enunciado |
|---|---|
| `01.1.py` | Multibanco -- saldo e levantamento dinamicos |
| `01.2.py` | Multibanco -- saldo fixo de 100 euros com detalhe do valor em falta |
| `02.py` | Classificacao etaria: Crianca / Jovem / Adulto / Senior |
| `03.py` | Maior de 3 numeros sem usar `max()` |
| `04.py` | Sistema de desconto automatico e personalizado |

---

## Exercicios

### 01.1.py -- Multibanco (Valores Dinamicos)

Enunciado: Pedir saldo e valor a levantar; autorizar ou rejeitar.

```python
saldo = float(input("Indique o valor do saldo: "))
valor_a_levantar = float(input("Indique o valor a levantar: "))
if saldo >= valor_a_levantar:
    print("Saldo positivo, aprovado!")
else:
    print("Saldo negativo, reprovado!")
```

---

### 01.2.py -- Multibanco (Saldo Fixo com Detalhe)

Enunciado: Saldo fixo de 100 euros -- mostrar exatamente quanto falta se insuficiente.

```python
saldo = 100
valor_a_levantar = float(input("Indique o valor a levantar: "))
saldo_restante = saldo - valor_a_levantar
if saldo >= valor_a_levantar:
    print(f"O valor restante e {saldo_restante}euros")
else:
    print("Saldo negativo!")
    print("A Operacao nao foi concedida!")
    print(f"Para completar a operacao, o Sr. precisa de {saldo_restante*-1}euros")
```

Nota: `saldo_restante * -1` converte o valor negativo em positivo para mostrar o montante em falta.

---

### 02.py -- Classificacao Etaria

Enunciado: Pedir a idade e classificar em quatro faixas.

```python
idade = int(input("Idade: "))
if idade <= 0:
    print("A tua idade humana e impossivel")
elif idade <= 13:
    print("Tu es uma Crianca")
elif idade <= 17:
    print("Tu es um Jovem")
elif idade <= 64:
    print("Tu es um Adulto")
else:
    print("Tu es um Senior")
```

| Faixa | Categoria |
|---|---|
| <= 0 | Invalida |
| 1 a 13 | Crianca |
| 14 a 17 | Jovem |
| 18 a 64 | Adulto |
| 65 ou mais | Senior |

---

### 03.py -- Maior de 3 Numeros

Enunciado: Pedir 3 numeros e mostrar o maior, sem usar `max()`.

```python
num1 = int(input("1.o Numero: "))
num2 = int(input("2.o Numero: "))
num3 = int(input("3.o Numero: "))
print("---")
if num1 > num2 and num1 > num3:
    print(f"O maior numero e {num1}")
elif num2 > num1 and num2 > num3:
    print(f"O maior numero e {num2}")
elif num3 > num2 and num3 > num1:
    print(f"O maior numero e {num3}")
else:
    print("Nao insire valores repetidos")
    print("Insire valores corretos")
```

Nota: o ramo `else` captura o caso em que dois ou mais valores sao iguais.

---

### 04.py -- Sistema de Desconto

Enunciado: Pedir o valor de compra e aplicar desconto automatico ou personalizado.

```python
compra = float(input("Valor da compra: "))
desconto_input = float(input("Valor de aplicacao de desconto (em %, digite 0 para desconto automatico): "))
print("---")
valor_desconto = 0

if desconto_input == 0:
    if compra >= 100:
        valor_desconto = compra * 0.10   # 10% de desconto
    elif compra >= 50:
        valor_desconto = compra * 0.05   # 5% de desconto
    else:
        valor_desconto = 0               # Sem desconto
else:
    valor_desconto = compra * (desconto_input / 100)

compra_total = compra - valor_desconto
if valor_desconto > 0:
    print(f"O valor da compra com desconto de {valor_desconto:.2f}euros e de: {compra_total:.2f}euros")
else:
    print(f"O valor da compra sem desconto e de: {compra_total:.2f}euros")
```

| Valor da compra | Desconto automatico |
|---|---|
| >= 100 euros | 10% |
| >= 50 euros | 5% |
| < 50 euros | 0% |
| Personalizado | percentagem definida pelo utilizador |

---

## Conceitos Abordados

| Conceito | Descricao |
|---|---|
| `if / else` | Bifurcacao entre dois caminhos |
| `if / elif / else` | Multiplas condicoes exclusivas |
| `if` aninhado | Condicionais dentro de condicionais |
| `and` | Duas condicoes verdadeiras em simultaneo |
| `float()` | Suporta valores monetarios decimais |
| f-string `:.2f` | Formatacao para 2 casas decimais |

---

## Como Executar

```bash
git clone https://github.com/a14785-oficina/Trabalho-Pratico-04-M3.git
cd Trabalho-Pratico-04-M3
python3 01.1.py
```

---

## Navegacao -- Modulo 3

| Posicao | Repositorio |
|---|---|
| Anterior | [TP03 -- Operadores](https://github.com/a14785-oficina/Trabalho-Pratico-03-M3) |
| Seguinte | [EXPA01 -- Estruturas Condicionais em Python](https://github.com/a14785-oficina/Estruturas-Condicionais-em-Python) |
| Portfolio | [oficina-jpc](https://github.com/a14785-oficina/oficina-jpc) |

---

*PSI -- Modulo 3 -- Programacao Estruturada -- OFICINA -- 2025/2026*
