# BANNER-GRABBING-EM-PYTHON3
código usa banner para conectar o serviço e consegue ver o banner ex: ftp, tcp, ssh ... ver serviço.

⚠️ Uso exclusivo para fins educacionais • Desenvolvido por M!ss s3c

📝 Guia: Criando e executando seu primeiro Banner Grabber em Python

1. Criar o arquivo do script

No terminal, crie o arquivo:

nano banner.py

2. Adicionar o código Python

Cole o seguinte código:

#!/usr/bin/python3
# Banner Grabber Educacional em Python
# Uso: python3 banner.py

import socket

# Solicita IP e porta
ip = input("Digite o IP: ")
porta = int(input("Digite a porta: "))

# Cria o socket TCP
meusocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
meusocket.settimeout(3)  # evita travamentos

# Conecta ao serviço
try:
    meusocket.connect((ip, porta))
    banner = meusocket.recv(1024)  # recebe o banner
    print(f"Banner recebido: {banner.decode().strip()}")
except Exception as e:
    print(f"Erro ao conectar: {e}")
finally:
    meusocket.close()


⚠️ Observação: Este script não deve ser usado em sistemas não autorizados. É apenas para aprendizado.

3. Dar permissão de execução (opcional)
chmod +x banner.py

4. Executar o script
python3 banner.py

5. Exemplo de execução
Digite o IP: 127.0.0.1
Digite a porta: 21
Banner recebido: 220 (vsFTPd 3.0.3)

Ou:

Digite o IP: 127.0.0.1
Digite a porta: 22
Banner recebido: SSH-2.0-OpenSSH_8.9p1 Debian-3

👉 O que você aprendeu aqui

socket.socket() → cria um socket TCP.

connect() → conecta ao serviço em IP e porta especificados.

recv(1024) → recebe dados do serviço (o banner).

settimeout() → evita travamentos em serviços que não respondem.

Sempre usar close() → libera recursos do socket.
