menu = '''
[1] Depositar
[2] Sacar
[3] Extrato
[4] Sair
>>> '''

deposito = 0
saldo = 0
saque = 0
limite = 500
extrato = ""
numero_saques = 0
limite_saque = 3

while True:
    opcao = input(menu)
    if opcao == '1':
        deposito = float(input('Valor do depósito: '))
        if deposito > 0:
            saldo += deposito
            extrato += f'Depósito de R${deposito:.2f}\n'
            print(f'Depósito de R${deposito:.2f} realizado com sucesso! ')
        else:
            print('Falhou! O valor informado é inválido!')

    elif opcao == '2':
            saque = int(input('Informe o valor do saque: '))

            excedeu_saldo = saque > saldo

            excedeu_limite = saque > limite

            excedeu_saques = numero_saques >= limite_saque

            if excedeu_saldo:
                print('Saldo insuficiente!')
            elif excedeu_limite:
                print('Ultrapassou o limite de R$500.00 por saque, tente novamente!')
            elif excedeu_saques:
                print('Você já atingiu o limite de 3 saques diário! Tente novamente amanhã!')
            elif saque > 0:
                saldo -= saque
                extrato += f'Saque: R${saque:.2f}\n'
                numero_saques += 1
                print(f'Saque de R${saque:.2f} realizado com sucesso!')
            else:
                print('Algo deu errado! Tente novamente!')
    elif opcao == '3':

        print('Extrato'.center(40, ' '))
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f'Saldo: R${saldo:.2f}')

    elif opcao == '4':
        print('Volte sempre!')
        break
    else:
        print('Operação inválida, tente novamente!')
