# Sistema-Banc-rio-em-Python
Criação de um sistema simples para realização de depósitos, saques e exibições de extrato.


Segue abaixo código de composição do sistema!
Caso vejam alguma possibilidade de melhoria e desenvolvimento do projeto,estou aberta à sugestões!

Código em Python: 

menu = """

Escolha a opção desejada:

[d] Depósito 
[s] Saque
[e] Extrato
[q] Sair



"""

saldo = 0
extrato = ''
nsaques = 0
ndepositos = 0
saqueshistorico = []
depHist = []

while True:
    opcao = input(menu)
    opcao = opcao.lower()
    if opcao == 'd':
        print('Depósito')
        valor = float(input("Digite o valor que deseja depositar: "))
        if valor <= 0:
            print("Valor inválido! ")
        else:
            saldo += valor
            ndepositos += 1
        depHist.append(f"Depósito {ndepositos}: R${valor}")
    elif opcao == 's':
        print("Saque") 
        valorSaque = float(input("Digite o valor que deseja sacar: "))
        if valorSaque > 500:
            print('O limite dos valores de saque é R$ 500 por saque, tente novamente!')
        elif nsaques >= 3:
            print("O limite de saques diários é 3, tente novamente amanhã! ")
        elif saldo < valorSaque:
            print("Não foi possível realizar o saque devido à saldo insuficiente")
        else:
            nsaques += 1
            saldo -= valorSaque
        saqueshistorico.append(f" Saque {nsaques}: R${valorSaque}")
    elif opcao == "e":
        print("Extrato")
        print(depHist)
        print(saqueshistorico)
        print(f"Saldo atual: R${saldo}")
    elif opcao == 'q':
        print("Saindo...")
        break
    else:
        print('Opção inválida, tente novamente')
