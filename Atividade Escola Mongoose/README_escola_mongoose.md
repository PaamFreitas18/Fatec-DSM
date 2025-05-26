# 🏫 Atividade - Escola Mongoose

**Disciplina:** Técnicas de Programação II  
**Professor:** Henrique Louro  
**Aluno:** [Seu Nome Aqui]

## 🔗 Repositório da Atividade
Este é o repositório público da atividade prática com Express, TypeScript e Mongoose:  
📁 [https://github.com/PaamFreitas18](https://github.com/PaamFreitas18)

---

## 🚀 Instalação

```bash
npm install
npm run dev
```

Crie um arquivo `.env`:

```
PORT=3001
```

---

## 🧪 Testes com `curl` e Respostas

### 1. ➕ Cadastro de Professor
```bash
curl -X POST http://localhost:3001/professor \
  -H "Content-Type: application/json" \
  -d '{"nome": "Henrique Louro", "email": "henrique.louro@fatec.sp.gov.br", "cpf": "07494812857"}'
```
**Resposta:**
```json
{
  "nome": "Henrique Louro",
  "email": "henrique.louro@fatec.sp.gov.br",
  "cpf": "07494812857",
  "_id": "682f6384f4bd0fb518a18a28",
  "__v": 0
}
```

### 2. ❌ Validação de CPF Inválido
```bash
curl -X POST http://localhost:3001/professor \
  -H "Content-Type: application/json" \
  -d '{"nome": "Fulano", "email": "fulano@teste.com", "cpf": "12345678910"}'
```
**Resposta:**
```json
{
  "message": "12345678910 não é um CPF válido"
}
```

### 3. ❌ Validação de E-mail Inválido
```bash
curl -X POST http://localhost:3001/professor \
  -H "Content-Type: application/json" \
  -d '{"nome": "Fulano", "email": "fulano@teste", "cpf": "07494812857"}'
```
**Resposta:**
```json
{
  "message": "fulano@teste não é um formato de e-mail válido"
}
```

### 4. 🔍 Listar Professores
```bash
curl -X GET http://localhost:3001/professor
```
**Resposta:**
```json
[
  {
    "_id": "682f6384f4bd0fb518a18a28",
    "nome": "Henrique Louro",
    "email": "henrique.louro@fatec.sp.gov.br",
    "cpf": "07494812857",
    "__v": 0
  }
]
```

### 5. 📝 Atualizar Professor
```bash
curl -X PUT http://localhost:3001/professor \
  -H "Content-Type: application/json" \
  -d '{"id":"682f6384f4bd0fb518a18a28", "nome":"Henrique Atualizado", "email":"henrique@fatec.sp.gov.br", "cpf":"07494812857"}'
```
**Resposta:**
```json
{
  "_id": "682f6384f4bd0fb518a18a28",
  "nome": "Henrique Atualizado",
  "email": "henrique@fatec.sp.gov.br",
  "cpf": "07494812857",
  "__v": 0
}
```

### 6. 🗑️ Excluir Professor
```bash
curl -X DELETE http://localhost:3001/professor \
  -H "Content-Type: application/json" \
  -d '{"id":"682f6384f4bd0fb518a18a28"}'
```
**Resposta:**
```json
{
  "message": "Professor excluído com sucesso"
}
```

### 7. ➕ Cadastro de Disciplina
```bash
curl -X POST http://localhost:3001/disciplina \
  -H "Content-Type: application/json" \
  -d '{"descricao": "Lógica de Programação"}'
```
**Resposta:**
```json
{
  "descricao": "Lógica de Programação",
  "_id": "682f6dbdf4bd0fb518a18a3e",
  "__v": 0
}
```

### 8. 🔗 Associação Professor–Disciplina
```bash
curl -X POST http://localhost:3001/professor_has_disciplina \
  -H "Content-Type: application/json" \
  -d '{"professor": "682f6384f4bd0fb518a18a28", "disciplina": "682f6dbdf4bd0fb518a18a3e"}'
```
**Resposta:**
```json
{
  "professor": "682f6384f4bd0fb518a18a28",
  "disciplina": "682f6dbdf4bd0fb518a18a3e",
  "_id": "682f78b5f4bd0fb518a18a43",
  "__v": 0
}
```

---

## 📚 Referências

- [Documentação do Mongoose](https://mongoosejs.com/)
- [Express.js](https://expressjs.com/)
- [Validador de CPF](https://www.geradorcpf.com/algoritmo_do_cpf.htm)
- [Repositório do professor](https://github.com/hdblouro/escola)
