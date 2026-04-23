# 🔍 Network Analysis & Packet Capture

Repositório dedicado ao estudo de análise de tráfego, protocolos de rede e monitoramento.

> **Status:** Em desenvolvimento (Migrado do repositório de Docker em Abril/2026)

## 🛠️ Ferramentas de Monitoramento
* **Wireshark:** Interface gráfica para análise profunda de pacotes.
* **TShark:** Versão CLI (linha de comando), essencial para automação e ambientes sem interface gráfica.

## ⚙️ Instalação e Configuração (WSL2)
Para capturar pacotes sem precisar de root o tempo todo:


sudo apt update && sudo apt install wireshark -y
sudo dpkg-reconfigure wireshark-common
sudo usermod -aG wireshark $USER

Laboratórios de Captura
Durante os estudos, analisei o tráfego entre Windows (Host) e Ubuntu (WSL):

ARP: Mapeamento de IP para MAC na rede virtual.

DNS (Porta 53): Resolução de nomes durante o uso do curl.

TCP/TLS (Porta 443): Handshake de segurança em conexões HTTPS.

⚡ Filtros Úteis no TShark
Ver apenas HTTP: tshark -i eth0 -Y http

Filtrar por IP: tshark -i eth0 -Y "ip.addr == 8.8.8.8"

Requisições GET: tshark -i eth0 -Y "http.request.method == GET"

Insight: Erros de libEGL ao abrir o Wireshark gráfico no WSLg são apenas conflitos de renderização da GPU e não afetam a captura.

---

## 📖 Laboratório: Resolução de Nomes (DNS)

O entendimento de DNS é crítico no dia a dia DevOps para configurar Service Discovery e Ingress.

### 1. Investigando o Servidor Local
* **Arquivo:** `/etc/resolv.conf`
* **Comando:** `cat /etc/resolv.conf`

### 2. Troubleshooting com `dig`
Alvo: `amandareis.vercel.app`

* **Consulta Padrão:** `dig amandareis.vercel.app`
* **Saída Simplificada:** `dig amandareis.vercel.app +short`

### 3. Principais Registros (Records)
* **A:** IPv4 do domínio.
* **CNAME:** Apelido/Alias (muito usado na Vercel).
* **NS:** Servidores de autoridade.
* **TXT:** Validação e segurança (SPF/DKIM).