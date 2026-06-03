# ⚽ Football Live — GitHub Pages

Painel web 100% estático para monitorar jogos ao vivo e exportar para o Google Sheets.
Sem servidor, sem custos, sem configuração de infraestrutura.

---

## Arquitetura

```
Browser (GitHub Pages) — gratuito
    ├── fetch() ──────────────► API-Football    (dados de jogos)
    └── fetch() ──────────────► Apps Script     (escreve no Sheets)
                                    └──────────► Google Sheets
```

---

## Deploy em 3 passos

### 1. Publicar no GitHub Pages

```bash
git init
git add index.html
git commit -m "first commit"
git remote add origin https://github.com/seu-usuario/football-live.git
git push -u origin main
```

No repositório → **Settings → Pages → Source: Deploy from branch → main → / (root)**

Seu painel estará em: `https://seu-usuario.github.io/football-live`

---

### 2. Configurar o Google Apps Script (backend gratuito para o Sheets)

1. Acesse [script.google.com](https://script.google.com) → **Novo projeto**
2. Apague o conteúdo padrão e cole o conteúdo de `apps-script.gs`
3. Substitua `SEU_SHEET_ID_AQUI` pelo ID da sua planilha
4. Clique em **Implantar → Nova implantação**
   - Tipo: **Aplicativo da Web**
   - Executar como: **Eu**
   - Quem pode acessar: **Qualquer pessoa**
5. Autorize o acesso quando solicitado
6. Copie a **URL do aplicativo da Web** gerada

---

### 3. Configurar o painel

Abra o painel no navegador → clique em **⚙️ Configurações** → preencha:

| Campo | Valor |
|---|---|
| API-Football Key | Sua chave de [dashboard.api-football.com](https://dashboard.api-football.com) |
| Google Apps Script URL | URL copiada no passo anterior |

Clique em **Salvar configurações** — as credenciais ficam salvas no navegador (localStorage).

---

## Como usar

| Ação | O que faz |
|---|---|
| **Buscar Jogos** | Lista jogos ao vivo + próximas 4h |
| Clicar no jogo | Carrega placar, eventos e escalação |
| **📊 Carregar Planilha** | Envia dados para o Google Sheets (3 abas) |
| **🔄 Atualizar** | Rebusca dados e atualiza a planilha já carregada |

### Abas geradas no Sheets

| Aba | Conteúdo |
|---|---|
| 📋 Resumo | Placar, liga, status, árbitro, horário |
| ⚽ Eventos | Gols, cartões e substituições com minuto |
| 👥 Escalação | Titulares e reservas dos dois times |

---

## Custo

| Serviço | Custo |
|---|---|
| GitHub Pages | Gratuito |
| API-Football (free) | Gratuito · 100 req/dia |
| Google Apps Script | Gratuito |
| Google Sheets | Gratuito |
| **Total** | **R$ 0,00** |

---

## Arquivos

```
football-pages/
├── index.html        ← Painel completo (HTML + CSS + JS em um único arquivo)
└── apps-script.gs    ← Código para colar no Google Apps Script
```
