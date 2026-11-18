<div align="center">

# 📡 Sigma Backup Manager (.bd)

**Gerenciador 100% Client-Side para backup e transporte rápido de clientes IPTV da plataforma Sigma.**

[![Acessar Aplicação](https://img.shields.io/badge/🌐_ACESSAR_ONLINE-0dcaf0?style=for-the-badge)](https://rubenbruno89.github.io/sigma-backup/)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Bootstrap](https://img.shields.io/badge/Bootstrap-6610F2?style=for-the-badge&logo=bootstrap&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)

</div>

---

## 🌐 Acesso Online

Você pode usar a aplicação diretamente pelo navegador sem precisar baixar nada:

👉 **[https://rubenbruno89.github.io/sigma-backup/](https://rubenbruno89.github.io/sigma-backup/)**

---

## 📋 Sobre o Projeto

O **Sigma Backup Manager** é uma aplicação web em arquivo único (`index.html`) criada para facilitar o gerenciamento dos seus clientes IPTV.

Você cadastra o cliente com **Nome, WhatsApp, Data de Vencimento e URL/Dados (M3U, Xtream, etc.)**, e a aplicação gera um arquivo de backup **`.bd`** que pode ser baixado localmente, importado novamente ou enviado para a nuvem para transporte rápido entre dispositivos.

**Nenhum servidor ou banco de dados é necessário.** Tudo roda direto no navegador, usando `localStorage` para persistência.

## ✨ Funcionalidades

- [x] Cadastro, edição e exclusão de clientes (CRUD completo)
- [x] Campos: **Nome, WhatsApp, Data de Vencimento e URL/Dados**
- [x] Status automático de vencimento: `Ativo`, `Vence em Xd`, `Vencido`
- [x] Busca em tempo real por nome, WhatsApp ou URL
- [x] Botão rápido para chamar o cliente no WhatsApp (`wa.me`)
- [x] Botão para copiar a URL do cliente com 1 clique
- [x] Persistência automática no navegador (`localStorage`)
- [x] **Download local do backup `.bd`**
- [x] **Importação/Restauração de arquivo `.bd`** (com opção de mesclar ou substituir)
- [x] **Transporte Rápido via `temp.sh`** - 100% em HTML puro, sem erro de CORS
- [x] **Alternativa automática via API** (`TmpFiles.org` com fallback para `File.io`)
- [x] Interface responsiva em Dark Mode com Bootstrap 5

## 🚀 Como Usar

### Opção 1: Online (GitHub Pages)
Basta acessar [https://rubenbruno89.github.io/sigma-backup/](https://rubenbruno89.github.io/sigma-backup/) diretamente pelo PC ou celular.

### Opção 2: Rodando Localmente (Offline)
Não precisa instalar dependências ou servidor. Basta clonar o repositório e abrir o `index.html`:

```bash
git clone https://github.com/rubenbruno89/sigma-backup.git
cd sigma-backup
# Abra o index.html com dois cliques no navegador
```

### Passo a Passo
1. Preencha o formulário à esquerda com os dados do cliente e clique em **Salvar na Lista**.
2. Na **Central de Backup & Transporte Rápido**, escolha como deseja exportar ou restaurar:

| Botão | Função |
| :--- | :--- |
| **Baixar .bd Local** | Baixa o arquivo `sigma_backup_AAAA-MM-DD.bd` para o seu dispositivo |
| **Enviar temp.sh** | Envia o `.bd` para o `temp.sh` e abre o link direto em uma nova janela |
| **Alt Rápido (API)** | Gera o link direto na tela via `TmpFiles.org` / `File.io` |
| **Importar .bd** | Restaura um backup salvo anteriormente (mesclando ou substituindo) |

## 📦 Formato do Arquivo `.bd`

O arquivo `.bd` é gerado em formato JSON estruturado, facilitando futuras integrações com outras linguagens ou sistemas.

```json
{
  "app": "SigmaBackupManager",
  "version": "1.1",
  "exportedAt": "2026-05-13T12:00:00.000Z",
  "totalClients": 1,
  "data": [
    {
      "id": "uuid-do-cliente",
      "nome": "João Silva",
      "whatsapp": "5511999999999",
      "vencimento": "2026-06-13",
      "urlDados": "http://servidor.com:80/get.php?username=...",
      "createdAt": "2026-05-13T12:00:00.000Z"
    }
  ]
}
```

## ☁️ Transporte Rápido - Como Funciona?

### Contorno de CORS no `temp.sh` (HTML Puro)
O `temp.sh` não envia o cabeçalho `Access-Control-Allow-Origin: *`, bloqueando requisições via `fetch()` no navegador. Para resolver isso 100% no front-end, a aplicação utiliza um **formulário HTML nativo oculto** combinado com a API `DataTransfer`, injetando o arquivo `.bd` gerado em memória e disparando um POST nativo direto para `https://temp.sh/upload`.

### Alternativa Automática (APIs com CORS liberado)
O botão **Alt Rápido (API)** gera o link direto dentro da própria página:
1. **TmpFiles.org** — Link direto de download (`/dl/`), expira em 60 minutos.
2. **File.io** — Fallback automático caso o TmpFiles esteja indisponível, expira após o 1º download.

> ⚠️ **Aviso de Segurança:** Os links gerados contêm as credenciais/URLs dos seus clientes. Não compartilhe publicamente e baixe o arquivo o mais rápido possível.

## 🛠️ Tecnologias Utilizadas

* **HTML5** — Estrutura
* **CSS3** — Estilização customizada
* **Bootstrap 5.3** — Layout responsivo em Dark Mode
* **Bootstrap Icons** — Ícones
* **JavaScript Vanilla (ES6+)** — Lógica da aplicação, sem frameworks externos

## 📁 Estrutura do Projeto

```
sigma-backup/
├── index.html    # Aplicação completa (HTML + CSS + JS)
├── README.md     # Documentação do projeto
└── LICENSE       # Licença MIT
```

## 🔒 Privacidade

* Nenhum dado é enviado para servidor próprio.
* Todos os registros ficam armazenados exclusivamente no `localStorage` do seu navegador.
* O envio para serviços temporários (`temp.sh` / `TmpFiles` / `File.io`) ocorre apenas mediante ação manual nos botões de upload.

## 🤝 Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma *Issue* ou enviar um *Pull Request*.

## 📄 Licença

Este projeto está licenciado sob a licença **MIT** — veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

<div align="center">
  Desenvolvido para gerenciamento de clientes IPTV • <a href="https://rubenbruno89.github.io/sigma-backup/">Sigma Backup Manager</a>
</div>
