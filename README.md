# 🚀 Upload de Arquivos — Azure Blob Storage + GitHub Pages

Página web para clientes enviarem arquivos diretamente para **Azure Blob Storage** usando **SAS Tokens**.

---

## ✨ Características

- ✔ Sem backend  
- ✔ Sem login  
- ✔ Tema escuro moderno  
- ✔ Suporta múltiplos clientes  
- ✔ Validação de tipos de arquivo personalizados
- ✔ Renomeação automática (cliente_tipo_timestamp)
- ✔ Limite 600MB por arquivo  
- ✔ Barra de progresso por arquivo  
- ✔ Drag & drop

---

## 🔧 Como usar

### 1. Estrutura do clientes.json

```json
{
  "terranordeste": {
    "nome": "Terra Nordeste",
    "sas": "URL_SAS_AQUI",
    "tiposArquivos": {
      "pedidos": ["pedidos", "pedido"],
      "clientes": ["clientes", "cliente"]
    }
  },
  "novoCliente": {
    "nome": "Novo Cliente",
    "sas": "URL_SAS_AQUI",
    "tiposArquivos": {
      "vendas": ["vendas", "venda"],
      "estoque": ["estoque"]
    }
  }
}
```

### 2. Gerar SAS Token

No Azure:
1. Crie container (ex: `entrada-seuclient`)
2. Gere SAS com permissões: **Write, Create, List**
3. Copie a URL completa

### 3. Configurar tipos de arquivo

Defina no JSON quais nomes os arquivos podem ter:
- `"pedidos": ["pedidos", "pedido"]` → aceita: `pedidos.xlsx`, `pedido_nov.xlsx`, `pedidos-tn.csv`
- Rejeita tudo que não contém essas palavras

### 4. Compartilhe o link

```
https://seu-usuario.github.io/upload-data-clients/?cliente=terranordeste
```

---

## 📂 Estrutura

```
├── index.html      # Página principal
├── clientes.json   # Configuração de clientes e tipos
└── README.md       # Este arquivo
```

---

## 🔒 Segurança

- Cada cliente tem SAS exclusivo
- SAS acessa apenas seu container
- Validação de tipos no navegador
- Nenhum arquivo passa por servidor intermediário
- Renomeação automática padroniza nomes

---

## 📝 Renomeação automática

Arquivos são renomeados para: **cliente_tipo_timestamp.extensao**

Exemplo:
- `pedidos_nov_2025.xlsx` → `terranordeste_pedidos_1705679400000.xlsx`
- `clientes-tn.csv` → `terranordeste_clientes_1705679401000.csv`

---

## 🌐 Publicação

GitHub Pages → Settings → Pages → Deploy from branch (main, /)

