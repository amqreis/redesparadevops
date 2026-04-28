# 🛠️ Ferramentas de Redes: ss & nc (Netcat)

Este documento contém o registro dos comandos fundamentais de diagnóstico de rede estudados.

---

## 1. Comando `ss` (Socket Statistics)
O `ss` é a ferramenta moderna para visualizar estatísticas de sockets no Linux. Ele é muito mais rápido que o antigo `netstat` e traz informações detalhadas do kernel.

### Comandos Praticados:
- `ss`: Lista conexões ativas.
- `ss -a`: Exibe todos os sockets (ouvindo e não ouvindo).
- `ss -l`: Mostra apenas sockets em estado **Listening** (portas abertas).
- `ss -n`: Modo numérico (não resolve nomes de portas/IPs, sendo mais rápido).
- `ss -ln`: Atalho comum para listar portas abertas numericamente.
- `ss -u`: Filtra apenas sockets do protocolo **UDP**.
- `ss -lnt`: Mostra portas **TCP** abertas e ouvindo.
- `ss -lntp`: Exibe portas TCP e o **Processo (PID)** que as está usando.
- `sudo ss -lntp`: Comando definitivo (com privilégio root) para identificar qual serviço é dono de cada porta no sistema.

---

## 2. Comando `nc` (Netcat)
O Netcat é conhecido como o "canivete suíço" do TCP/IP, essencial para testar conectividade entre serviços.

### Principais Casos de Uso:
- **Testar se uma porta remota está aberta:**
  ```bash
  nc -zv [IP_DO_SERVIDOR] [PORTA]

  Escaneamento UDP:

Bash
nc -zuv [IP_DO_SERVIDOR] [PORTA]
Abrir uma porta para escuta (Modo Servidor):

Bash
nc -l -p [PORTA]
Transferência rápida de arquivos:

No destino: nc -l -p 1234 > arquivo_recebido.txt

Na origem: nc [IP_DESTINO] 1234 < arquivo_enviar.txt

💡 Insight de DevOps
ss: Utilize para olhar para dentro do seu servidor (verificar se o serviço subiu).

nc: Utilize para olhar para fora (verificar se o seu servidor consegue chegar em outro serviço ou se o firewall está bloqueando).