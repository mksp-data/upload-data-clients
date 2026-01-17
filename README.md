# 🚀 Upload de Arquivos para Clientes — Azure Blob Storage + GitHub Pages

Este repositório contém uma página web simples e escalável para que clientes enviem arquivos diretamente para containers individuais no **Azure Blob Storage**, utilizando **SAS Tokens**.  
A página é hospedada gratuitamente via **GitHub Pages** e não requer backend.

---

## 📌 Objetivo

Permitir que cada cliente envie arquivos para seu próprio container no Azure, de forma:

- ✔ Segura  
- ✔ Simples  
- ✔ Escalável  
- ✔ Sem necessidade de login  
- ✔ Sem backend  
- ✔ Sem instalar nada  

Cada cliente acessa a mesma página, mas com um parâmetro na URL que define para qual container o arquivo será enviado.

Exemplo:

```
https://SEU_USUARIO.github.io/upload-data-clients/?cliente=terranordeste
```

---

## 🧠 Como funciona

1. O cliente acessa a página com `?cliente=nome`.
2. O JavaScript identifica o cliente.
3. O código seleciona o SAS Token correspondente no objeto `clientes`.
4. O arquivo é enviado diretamente para o Azure Blob Storage via requisição `PUT`.

Nenhum arquivo passa pelo GitHub Pages ou por servidores intermediários.

---

## 🗂 Estrutura do Projeto

```
upload-data-clients/
│
├── index.html   # Página principal de upload
└── README.md    # Este arquivo
```

---

## 🔧 Configuração dos Clientes

No arquivo `index.html`, existe um objeto chamado `clientes`:

```js
const clientes = {
    terranordeste: "URL_SAS_DO_CONTAINER_TERRANORDESTE",
    cliente2: "URL_SAS_DO_CONTAINER_CLIENTE2",
    cliente3: "URL_SAS_DO_CONTAINER_CLIENTE3"
};
```

### ➕ Adicionando um novo cliente

1. Crie um container no Azure Storage:
   ```
   entrada-novocliente
   ```

2. Gere um SAS Token **somente para esse container**, com permissões:
   - Write (w)
   - Create (c)
   - List (l) — opcional, mas útil para testes

3. Adicione no objeto:

```js
clientes.novocliente = "URL_SAS_DO_CONTAINER_NOVOCLIENTE";
```

4. Envie o link para o cliente:

```
https://SEU_USUARIO.github.io/upload-data-clients/?cliente=novocliente
```

---

## 🌐 Publicação no GitHub Pages

1. Vá em **Settings** do repositório  
2. Acesse **Pages**  
3. Em *Build and deployment*, selecione:
   - **Source:** Deploy from a branch  
   - **Branch:** main  
   - **Folder:** / (root)

4. O GitHub irá gerar um link como:

```
https://SEU_USUARIO.github.io/upload-data-clients/
```

---

## 🖥 Como o cliente usa

1. Acesse o link enviado (exemplo):
   ```
   https://SEU_USUARIO.github.io/upload-data-clients/?cliente=terranordeste
   ```
2. Escolha o arquivo  
3. Clique em **Enviar**  
4. O arquivo é enviado diretamente para o Azure

Simples e sem complicação.

---

## 🎨 Personalização

A página utiliza **Bootstrap 5**, permitindo:

- Temas personalizados  
- Logos  
- Cores da sua empresa  
- Layout responsivo  
- Barra de progresso (opcional)  

Se quiser melhorar o visual, basta editar o `index.html`.

---

## 🔒 Segurança

- Cada cliente recebe um SAS exclusivo  
- O SAS só dá acesso ao container dele  
- Não há backend para vazar dados  
- O cliente nunca vê arquivos de outros clientes  
- O SAS pode ter validade longa ou curta

---

## 📈 Escalabilidade

Este modelo permite:

- Adicionar novos clientes em segundos  
- Criar quantos containers forem necessários  
- Manter tudo organizado e isolado  
- Reutilizar a mesma página para todos

---

## 🧩 Tecnologias Utilizadas

- **Azure Blob Storage**  
- **SAS Tokens**  
- **JavaScript (Fetch API)**  
- **Bootstrap 5**  
- **GitHub Pages**  

---

## 🤝 Contribuições

Sinta-se à vontade para abrir issues ou enviar PRs com melhorias, como:

- Barra de progresso  
- Validação de tipos de arquivo  
- Tema escuro  
- Layout mais moderno  

---

## 📬 Suporte

Se precisar de ajuda para adicionar novos clientes, melhorar o layout ou automatizar a geração de SAS, estou por aqui.
