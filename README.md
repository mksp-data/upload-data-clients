# 🚀 Upload de Arquivos — Azure Blob Storage + GitHub Pages

Página web para clientes enviarem arquivos diretamente para **Azure Blob Storage** usando **SAS Tokens**.

---

## ✨ Características

- ✔ Sem backend  
- ✔ Sem login  
- ✔ Tema escuro moderno  
- ✔ Suporta múltiplos clientes  
- ✔ Validação de tipos e tamanho (600MB max)  
- ✔ Barra de progresso por arquivo  
- ✔ Drag & drop

---

## 🔧 Como usar

### 1. Adicionar um novo cliente

Edite o arquivo `clientes.json`:

```json
{
  "terranordeste": "URL_SAS_AQUI",
  "novoCliente": "URL_SAS_DO_NOVO_CLIENTE"
}
```

### 2. Gerar o SAS Token

No Azure:
1. Crie um container (ex: `entrada-seuclient`)
2. Gere SAS com permissões: **Write, Create, List**
3. Copie a URL completa do blob

### 3. Compartilhe o link

```
https://seu-usuario.github.io/upload-data-clients/?cliente=novoCliente
```

---

## 📂 Estrutura

```
├── index.html      # Página principal
├── clientes.json   # Configuração de clientes
└── README.md       # Este arquivo
```

---

## 🔒 Segurança

- Cada cliente tem SAS exclusivo
- SAS acessa apenas seu container
- Nenhum arquivo passa por servidor intermediário
- SAS pode ter data de expiração

---

## 🌐 Publicação

GitHub Pages → Settings → Pages → Deploy from branch (main, /)

---

## 📝 Tipos de arquivo permitidos

`.xlsx`, `.xls`, `.csv`, `.txt`, `.parquet`, `.json`, `.xml`, `.tsv`

