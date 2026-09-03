
# Subindo-e-Protegendo-um-Servidor-Web-Linux-De-VM-Local-para-AWS-Cloud
# 🐧 linux webserver to aws cloud
Status: 🟢 Etapa local concluída | ☁️ AWS em desenvolvimento

Implantação, configuração e troubleshooting de um servidor Web Linux, com evolução planejada para infraestrutura em AWS.

Parte concluída:

Ubuntu Linux em VM
Configuração e análise de rede IPv4
Nginx
Validação da configuração
Testes HTTP com curl
Análise de access.log
Identificação de códigos HTTP 200, 301, 304 e 404
Troubleshooting de endereço IP

Próxima etapa:

AWS EC2
Security Groups
Nginx na AWS
Controle de acesso
HTTPS
Hardening básico
Monitoramento/logs

                INTERNET
                    |
                    v
              AWS Security Group
                    |
                    v
                EC2 Ubuntu
                    |
              +-----+-----+
              |           |
             UFW         Nginx
              |           |
              +-----+-----+
                    |
                 Fail2ban
                    |
                  Logs
                  
# 🐧 Linux Web Server Security
<img width="1276" height="797" alt="Captura de tela 2026-09-01 124442" src="https://github.com/user-attachments/assets/81669c54-cbae-4b02-bace-b39f8c48d961" />
> Implantação e troubleshooting de um servidor Web Linux em máquina virtual, utilizando Nginx, HTTP e análise de logs.


## Arquitetura

Windows
   |
   | HTTP
   v
Ubuntu VM
   |
   +-- Nginx
   |
   +-- UFW Firewall
   |
   +-- Fail2ban
   |
   +-- Logs

## Tecnologias

- Ubuntu Server
- Nginx
- UFW
- Fail2ban
- Linux
- VirtualBox

## Implementação

1. Nginx

Servidor web configurado para responder requisições HTTP.

2. UFW

Firewall configurado para permitir somente
as portas necessárias.

3. Fail2ban

Monitoramento dos logs do Nginx para detectar
tentativas repetidas de autenticação inválida.

4. Teste

Foram realizadas tentativas de autenticação inválidas
a partir de uma máquina Windows.
<img width="1871" height="1017" alt="Captura de tela 2026-09-03 103053" src="https://github.com/user-attachments/assets/56f7f2c0-8b84-4259-8fa9-cb27f3d06181" />
Após atingir o limite configurado, o Fail2ban
bloqueou o endereço IP de origem.


## Resultado

O IP de teste foi identificado e bloqueado pelo Fail2ban.


## Próximos passos

- Hardening adicional do servidor
- HTTPS/TLS
- Monitoramento
- Migração para AWS EC2
- Configuração de Security Groups
## 🎯 Finalidade

Configurar um servidor Web em ambiente Linux, validar seu funcionamento, realizar testes HTTP e analisar os registros de acesso do servidor.

O projeto também teve como objetivo praticar troubleshooting de rede e serviços Linux.

## 🖥️ ferramentas/laboratorio

- Ubuntu Linux
- Máquina virtual (VM)
- Nginx
- HTTP
- Bash
- curl

  🧠 Competências praticadas
Linux
Administração básica de serviços
Nginx
IPv4
HTTP
curl
Análise de logs
Troubleshooting
Linha de comando

## 🏗️ Arquitetura

```text
Cliente
   │
   │ HTTP
   ▼
Rede local
   │
   ▼
Ubuntu VM
   │
   ▼
Nginx
   │
   ▼
Servidor Web

## 1. Configuração de rede


A interface de rede da máquina virtual foi identificada utilizando:

ip -4 addr show enp0s3

A interface enp0s3 apresentou o endereço IPv4: 192.168.0.16/24



## 2. Configuração e validação do Nginx

O estado do serviço foi verificado com o comando:

sudo systemctl status nginx --no-pager

O serviço apresentou o estado: Active (running)

A configuração também foi validada utilizando:

sudo nginx -t

Após a validação, o serviço foi recarregado:

sudo systemctl reload nginx



## 3. Teste HTTP

O servidor foi testado utilizando curl:

curl -I http://192.168.0.16

Também foi realizado um teste através do endereço local:

curl -I http://localhost

A opção -I permite visualizar os cabeçalhos da resposta HTTP.

Uma resposta 200 OK indica que a requisição foi processada com sucesso.




## 4. Análise dos logs

Os registros de acesso do Nginx foram acompanhados através de:

sudo tail -f /var/log/nginx/access.log

Durante os testes foram observados diferentes códigos HTTP:

Código	Significado
200	Requisição processada com sucesso
301	Redirecionamento permanente
304	Recurso não modificado
404	Recurso não encontrado

Também foram observadas requisições provenientes de dispositivos da rede local.

🛠️ 5. Troubleshooting

Durante o laboratório, inicialmente foi utilizado o endereço IP:

192.168.0.5

O teste de conexão não foi bem-sucedido.

A investigação da interface de rede mostrou que o endereço IP atual da máquina era: 192.168.0.16

Após utilizar o endereço correto, o teste HTTP foi realizado novamente com sucesso.

Processo de diagnóstico
Falha de conexão
       ↓
Verificação do Nginx
       ↓
Nginx ativo
       ↓
Verificação da interface de rede
       ↓
IP atual identificado
       ↓
Novo teste HTTP

📸 6. Evidências
Configuração de rede
Nginx em execução
Teste HTTP
Logs de acesso


🚧 Próxima etapa
Migração para AWS Cloud

A próxima etapa do projeto será reproduzir a infraestrutura em uma máquina virtual EC2 na AWS, adicionando conceitos de:

EC2
Security Groups
Controle de acesso
Hardening básico
HTTPS
Monitoramento e logs

A etapa AWS ainda não foi implementada neste projeto.
