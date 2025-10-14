# TreeCount API

API desenvolvida em Java 21 com Maven, para gerenciamento de contagem de árvores. Este projeto inclui testes automatizados, build com Docker e CI/CD configurado via GitHub Actions.

---

## 📦 Pré-requisitos

- Java 21
- Maven
- Docker
- GitHub account (para CI/CD e secrets)
- Git (para clonar o projeto)

---

## 🚀 Como executar localmente

1. Clone o repositório:
   ```bash
   git clone https://github.com/arthursidor/treecount-api.git
   cd treecount-api
Build e teste o projeto com Maven:

`Copiar código`

./mvnw clean package -DskipTests=false
./mvnw test
Build da imagem Docker:

`Copiar código`

docker build -t treecount-api:latest .
Executar a aplicação com Docker:

`Copiar código`

docker run -d -p 8080:8080 --name treecount-api treecount-api:latest
A API estará disponível em http://localhost:8080.

🧪 Testes Automatizados
O projeto já inclui testes existentes em src/test/java. Eles são executados automaticamente:

Durante a build com:

`Copiar código`

./mvnw clean package -DskipTests=false
E na etapa de testes explicitamente:

`Copiar código`

./mvnw test
No pipeline CI/CD, estes testes garantem que o código está correto antes do deploy.

⚙️ CI/CD com GitHub Actions
O workflow do CI/CD está configurado em .github/workflows/ci-cd.yml.

Ele executa:

Checkout do código

Configuração do Java 21

Build do projeto

Execução de testes automatizados

Login no Docker Hub

Build e push da imagem Docker

Deploy em ambiente de staging

🔑 Secrets necessários no GitHub
DOCKER_USERNAME → arthursidor

DOCKER_PASSWORD → arthur321

Para adicionar: GitHub → Settings → Secrets and variables → Actions → New repository secret

🐳 Docker
Build da imagem:

`Copiar código`

docker build -t arthursidor/treecount-api:latest .
Rodar o container:

`Copiar código`

docker run -d -p 8080:8080 --name treecount-api arthursidor/treecount-api:latest
Parar e remover o container:


`Copiar código`

docker stop treecount-api
docker rm treecount-api

📁 Estrutura do Projeto

treecount-api/
│
├─ src/main/java/      # Código fonte
├─ src/test/java/      # Testes automatizados
├─ Dockerfile          # Configuração do container
├─ .github/workflows/  # CI/CD
├─ mvnw, mvnw.cmd      # Wrapper Maven
└─ pom.xml             # Configuração Maven