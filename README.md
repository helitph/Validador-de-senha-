# Validador-de-senha-
Aplicativo simples em python que verifica a força de senhas com base em regras de segurança. Projeto para estudo de lógica, estrutura condicional e boas práticas em em python.


import re

def validar_senha(senha):
    erros = []

    if len(senha) < 8:
        erros.append("A senha deve ter pelo menos 8 caracteres.")
    
    if not re.search(r"[A-Z]", senha):
        erros.append("A senha deve conter pelo menos uma letra maiúscula.")
    
    if not re.search(r"[a-z]", senha):
        erros.append("A senha deve conter pelo menos uma letra minúscula.")
    
    if not re.search(r"\d", senha):
        erros.append("A senha deve conter pelo menos um número.")
    
    if not re.search(r"[!@#$%^&*()\-_=+{}\[\]|;:'\",.<>?/]", senha):
        erros.append("A senha deve conter pelo menos um caractere especial.")
    
    if re.search(r"\s", senha):
        erros.append("A senha não deve conter espaços.")

    return erros

print("Digite suas senhas para validar. Para sair, digite 'sair'.")

while True:
    senha = input("Digite a senha: ")
    if senha.lower() == "sair":
        print("Encerrando a validação. Até mais!")
        break

    erros = validar_senha(senha)
    if erros:
        print("Senha fraca! Corrija os seguintes pontos:")
        for e in erros:
            print(f"- {e}")
    else:
        print("Senha forte! ")

    print("-" * 30)  
