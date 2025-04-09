# 🛠️ Como Usar um Domínio Grátis .eu.org com Cloudflare para seu Servidor de Minecraft

Esse guia te ensina a configurar um domínio personalizado grátis (ex: `mc.seudominio.eu.org`) para seu servidor de Minecraft, usando o serviço gratuito do [eu.org](https://nic.eu.org) junto com o [Cloudflare](https://cloudflare.com). Tudo 100% gratuito, com suporte a conexão via domínio sem precisar usar porta!

---

## 📦 O que você vai precisar

- Um domínio gratuito no [eu.org](https://nic.eu.org)
- Conta no [Cloudflare](https://cloudflare.com)
- IP público da sua internet ([meuip.com.br](https://meuip.com.br))
- Servidor Minecraft rodando com a porta 25565 liberada

---

## 🔹 Passo 1 – Registrar domínio no eu.org

1. Acesse [https://nic.eu.org/arf/en/](https://nic.eu.org/arf/en/)
2. Preencha o campo **Requested domain name** com algo como:
sa0z.eu.org
3. Em **Name Servers**, insira os do Cloudflare:
Name1: xxx.ns.cloudflare.com Name2: xxx.ns.cloudflare.com
4. Marque:
server names + replies on SOA + replies on NS (recommended)
5. Envie e aguarde aprovação (pode levar algumas horas)

---

## 🔹 Passo 2 – Configurar no Cloudflare

1. Crie uma conta no [Cloudflare](https://dash.cloudflare.com/)
2. Clique em **"Adicionar site"** e insira seu domínio (ex: `sa0z.eu.org`)
3. Siga o processo até o painel de DNS
4. Certifique-se de que os **nameservers** combinam com os do eu.org

---

## 🔹 Passo 3 – Adicionar os registros DNS

### 🟢 Registro A (aponta para seu IP público)
| Tipo | Nome | Valor (IP)       | Proxy     |
|------|------|------------------|-----------|
| A    | mc   | Seu IP público   | DNS Only ✅ |

> Vai criar o domínio `mc.seudominio.eu.org`

---

### 🎯 Registro SRV (para esconder a porta)

| Tipo | Nome | Serviço     | Protocolo | Prioridade | Peso | Porta  | Destino              |
|------|------|-------------|-----------|------------|------|--------|-----------------------|
| SRV  | mc   | _minecraft  | _tcp      | 0          | 5    | 25565  | mc.seudominio.eu.org |

> No Cloudflare:
- **Service**: `_minecraft`
- **Name**: `mc`
- **Target**: `mc.seudominio.eu.org`
- **Port**: `25565`
- **Proxy**: DNS Only

---

## 🔹 Passo 4 – Libere a porta no roteador

1. Acesse seu roteador (normalmente `192.168.0.1`)
2. Vá em **Redirecionamento de Portas / Port Forwarding**
3. Libere a porta `25565` para o IP local da máquina onde o servidor roda

---

## 🔹 Passo 5 – Teste a conexão

1. Abra o Minecraft
2. Vá em **Multiplayer > Add Server**
3. No IP, digite:
mc.seudominio.eu.org

Se tudo estiver certo, seu server vai aparecer sem precisar digitar IP ou porta! 🥳

---

## 🧠 Dicas Finais

- Pode trocar `mc` por `play` ou qualquer subdomínio estiloso
- Use [DuckDNS](https://www.duckdns.org/) se seu IP for dinâmico
- O domínio `.eu.org` pode ser usado futuramente pra e-mail, site, loja, etc.

---

### 👋 Curtiu?

Esse guia foi feito por quem penou aprendendo tudo na marra 😅  
Se te ajudou, deixa uma estrela no repositório ⭐ e compartilha com os amigos!
