LIMITE_SAQUE = 3
deposito = 0
saque = 0
conta = 0
limite = 500
numero_saques = 0
extratoDeposito = []
extratoSaque = []
numero_depositos = 0

def depositar(valor):
    global conta, numero_depositos
    if valor >= 0:
        conta += valor
        extratoDeposito.append(valor)
        numero_depositos += 1
    else:
        print("Valor inválido")

def sacar(valor1):
    global conta, numero_saques
    if valor1 >= 0 and numero_saques < LIMITE_SAQUE and valor1 <= conta and valor1 <= limite:
        conta -= valor1
        extratoSaque.append(valor1)
        numero_saques += 1
    else:
        print("Valor em conta insuficiente, limite de saque atingido, ou valor de saque excede o permitido.")

def extrato():
    print("EXTRATO:")
    for idx, valor in enumerate(extratoDeposito):
        print(f"Depósito {idx + 1}: R${valor:.2f}")

    for idx, valor in enumerate(extratoSaque):
        print(f"Saque {idx + 1}: R${valor:.2f}")

    print(f"Saldo atual: R${conta:.2f}")

while True:
    opcao = input("Digite a ação que você quer fazer (d: depositar, s: sacar, e: extrato, q: sair): ")

    if opcao == "d":
        valor4 = float(input("Digite o valor que você deseja depositar: "))
        depositar(valor4)
    elif opcao == "s":
        valor5 = float(input("Digite o valor do saque: "))
        sacar(valor5)
    elif opcao == "e":
        extrato()
    elif opcao == "q":
        break
    else:
        print("Opção inválida, tente novamente.")
