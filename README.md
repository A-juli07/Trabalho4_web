# Projeto MVC - Defesas Arquiteturais

**Aluna:** Ana Julia Vieira Pereira Andrade da Costa
**Disciplina:** DCC 704 – Arquitetura e Tecnologias de Sistemas WEB
**Professor:** Jean Bertrand
**Trabalho:** Trabalho 4 - Implementando Defesas Arquiteturais

## Sobre o Projeto

Sistema CRUD de usuários desenvolvido em Node.js com Express, EJS e MongoDB, implementando defesas contra vulnerabilidades críticas: XSS, CSRF, SQL Injection e Força Bruta.

## Defesas Implementadas

### 1. Proteção HTTP Headers (Helmet)
- Configurado em `server.js`
- Headers de segurança: CSP, X-Frame-Options, X-Content-Type-Options

### 2. Proteção CSRF
- Tokens em todos os formulários
- Middleware `csurf` configurado
- Exceção: rota de login

### 3. Rate Limiting
- Limite de 5 tentativas por minuto no login
- Proteção contra força bruta

### 4. Prevenção SQL Injection
- Mongoose com queries parametrizadas
- Sem concatenação de strings

### 5. Prevenção XSS
- EJS com escape automático (`<%= %>`)
- Todas as views protegidas

### 6. Proteção de Credenciais
- Variáveis de ambiente (`.env`)
- Senhas com hash bcrypt
- `.gitignore` configurado

## Tecnologias

- Node.js / Express
- MongoDB / Mongoose
- EJS (templates)
- bcryptjs (hash de senhas)
- helmet (HTTP headers)
- csurf (proteção CSRF)
- express-rate-limit (rate limiting)
- express-session (sessões)

## Instalação

1. Instale as dependências:
```bash
npm install
```

2. Configure o arquivo `.env`:
```bash
cp .env.example .env
```

3. Edite o `.env` com suas configurações:
```
MONGODB_URI=mongodb://localhost:27017/projeto_mvc
PORT=3030
SESSION_SECRET=sua_chave_secreta_aqui
NODE_ENV=development
```

## Como Executar

1. Inicie o MongoDB:
```bash
net start MongoDB
```

2. Execute o servidor:
```bash
node server.js
```

3. Acesse: `http://localhost:3030`

## Estrutura do Projeto

```
├── controllers/
│   ├── authController.js    # Login/Logout
│   └── userController.js    # CRUD de usuários
├── middleware/
│   └── auth.js              # Proteção de rotas
├── models/
│   └── User.js              # Schema Mongoose
├── views/
│   ├── login.ejs
│   ├── perfil.ejs
│   ├── usersList.ejs
│   ├── formUsuario.ejs
│   └── editUsuario.ejs
├── public/
│   └── css/
│       └── style.css
└── server.js                # Configuração principal
```

## Rotas Principais

- `GET /login` - Página de login
- `POST /login` - Autenticação
- `POST /logout` - Encerrar sessão
- `GET /users` - Lista de usuários
- `GET /users/new` - Cadastro
- `POST /users` - Criar usuário
- `GET /users/:id/edit` - Editar usuário
- `POST /users/:id/update` - Atualizar usuário
- `POST /users/:id/delete` - Excluir usuário
- `GET /perfil` - Perfil do usuário
