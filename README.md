BERSERKER Network Scanner 

Este script é uma interface simplificada para o Nmap com menu interativo, desenvolvido para automatizar varreduras de rede complexas. Organizado em categorias temáticas, oferece acesso rápido às principais funcionalidades do Nmap através de uma interface intuitiva.

Instalação

    git clone https://github.com/Caio-Campolino/BERSERKER.git

    cd BERSERKER

    chmod +x berserk.sh

    sudo ./berserker.sh

1. Verificação Inicial
   
       if! command -v nmap &> /dev/null; then
    Função: Verifica a instalação do Nmap

    Flags:

   command -v: Localiza o executável

   &>/dev/null: Redireciona erros/saída para nulidade

2. Banner Artístico

          echo -e "\e[1;31m"

    Efeito: Ativa cor vermelha brilhante

    Códigos ANSI:
\e[1;31m: Vermelho bold
\e[0m: Reset de formatação

3. Sistema de Menu
Menu Principal

        case $main_choice in
        1) basic_scans ;;

    Lógica: Usa case para direcionar para submenus

    Cores:

   Verde: Títulos
   Branco: Opções



4. Varredunas Básicas (basic_scans)

| Opção | Comando Nmap       | Descrição                                |
|-------|--------------------|------------------------------------------|
| 1     | nmap -sn           | Ping sweep para hosts ativos            |
| 2     | nmap -sS -T4       | SYN scan em portas comuns (1000)         |
| 3     | nmap -p- -T4       | Varredura completa TCP (1-65535)         |
| 4     | nmap -sU -T4       | Varredura UDP básica                     |


# Flags Especiais

- **-T4**: Timing agressivo (6 níveis)
- **-p-**: Todas portas TCP
- **-sU**: Modo UDP



5. # Varreduras Avançadas (advanced_scans)

| Técnica        | Comando | Uso Típico               |
|----------------|---------|--------------------------|
| Stealth(SYN)   | -sS     | Evasão básica            |
| ACK Scan       | -sA     | Mapear regras firewall   |
| FIN Scan       | -sF     | Bypass stateless FW      |
| XMAS Tree      | -sX     | Envio de flags múltiplas |
| NULL Scan      | -sN     | Pacotes sem flags        |


# 6. Técnicas de Evasão (firewall_evasion)

| Técnica         | Implementação                     | Exemplo                                   |
|-----------------|-----------------------------------|-------------------------------------------|
| Fragmentação    | `-f`                              | Divide pacotes em 8 bytes                 |
| Decoys          | `-D decoy1,decoy2,ME`             | Ofusca IP real                            |
| Spoofing        | `-S IP_FALSO -e INTERF`           | Falsificação de origem                    |
| Porta Source    | `-g 53`                           | Usa porta 53 como origem                  |
| MTU Customizado | `--mtu 24`                        | Pacotes de 24 bytes                       |

# 7. Detecção de OS/Serviços (os_services)

| Opção               | Comando                     | Detalhe                          |
|---------------------|-----------------------------|----------------------------------|
| 1                   | `nmap -O`                   | Fingerprinting de OS            |
| 2                   | `nmap -sV`                  | Versões de serviços             |
| 3                   | `--version-intensity 5`     | Análise máxima (0-9)            |
| 4                   | `--traceroute`              | Mapeamento de rotas             |


# 8. Scripts NSE (nse_scans)

| Script       | Função                                | Exemplo de Uso                     |
|--------------|---------------------------------------|------------------------------------|
| `vuln`       | Verifica vulnerabilidades comuns      | `--script vuln`                   |
| `http-enum`  | Enumeração de diretórios web          | `-p 80,443 --script http-enum`    |
| `dns-brute`  | Força bruta de subdomínios            | `--script dns-brute`              |
| `malware`    | Detecção de backdoors                 | `--script malware`                |


# 9. Output de Resultados (output_options)

| Formato      | Extensão   | Característica                          |
|--------------|------------|-----------------------------------------|
| Normal       | `.nmap`    | Legível para humanos                    |
| XML          | `.xml`     | Estruturado para parsing                |
| Grepable     | `.gnmap`   | Formatado para grep/awk                 |
| Todos        | Múltiplo   | Gera os 3 formatos simultaneamente      |

10. Modo Agressivo

        nmap -A -T4

Inclui:

   Detecção de OS (-O)

   Versão de serviços (-sV)

   Scripts básicos (-sC)

  Traceroute (--traceroute)

Fluxo de Execução

    graph TD
      A[Início] --> B{Verifica Nmap}
      B -->|Instalado| C[Exibe Banner]
      C --> D[Menu Principal]
      D --> |1-7| E[Submenu Específico]
      E --> F[Executa Nmap]
      F --> G[Retorna ao Menu]
      D --> |8| H[Sai]

Customização

    Cores: Modifique os códigos ANSI no cabeçalho

    Novas Opções: Adicione cases no menu correspondente

    Parâmetros: Ajuste timing (-T) e verbosidade (-v)

Boas Práticas

    Execute como root para funcionalidades completas

    Use em redes autorizadas

    Combine técnicas para varreduras stealth

    Armazene logs com -oA scan_results

Aviso Legal: Use apenas em redes que você tem autorização explícita para scanear. O desenvolvedor não se responsabiliza pelo uso indevido.
