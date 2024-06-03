# Sistema-Banc-rio
Desafio DIO

import time

deposito = 0
saque = 0
extrato_deposito = []
limite_saque_diário = 3
conte_saque_diário = 0
limite_para_saque = 500
extrato_saque = []
extrato = []
saldo_deposito = 0
saldo_sacar = 0

def menu():
    print(''' 
    MENU
          
[1] Deposito
[2] Saque
[3] Extrato
[4] Sair          ''')


while True:
    menu()

    opção = int(input('Escolha uma opção: '))

    if opção == 1:
        depositar = float(input('Quanto deseja depositar? R$ '))

        if depositar > 0:
            print('Depositando...') 
            time.sleep(2)
            print(f'Deposito Realizado! Valor do deposito R$ {depositar:.2f}')
            extrato_deposito.append(depositar)
            extrato.append(f'Deposito: R$ {depositar:.2f} ')
            saldo_deposito += depositar
        else:
            print('Nenhum deposito foi realizado!')

    if opção == 2:
        conte_saque_diário += 1

        sacar = float(input('Quanto deseja sacar? R$ '))

        if sacar <= saldo_deposito:
            if sacar > limite_para_saque:
                print('Limite máximo é de R$ 500 .')
            elif sacar <= 0:
                print('Não foi possivel realizar o saque!')
            elif sacar > 0 and sacar <= limite_para_saque:
                if conte_saque_diário > limite_saque_diário:
                    print('Limite de saque diário atingido!')
                    conte_saque_diário -= 1
                else:
                    print('Realizando o saque....')
                    time.sleep(2)
                    print(f'Saque realizado! Valor de R$ {sacar:.2f}')
                    extrato_saque.append(sacar)
                    extrato.append(f'Saque: R$ {sacar:.2f}')
                    saldo_sacar += sacar
                    
        else:
            print('Saldo insuficiente.') 

    if opção == 3:
        print('='*15, 'EXTRATO' ,'='*15)
        if not extrato:
            print('Nenhuma movimentação realizada!')
        else:
            for item in extrato:
                print(item)
        saldo_total = saldo_deposito - saldo_sacar
        print(f'Saldo: R$ {saldo_total:.2f}')
        print('='*39)
        break
    if opção == 4:
        break

print('Saindo... Obrigado!!')