🌳 TreeCount API
🚀 Descrição

O TreeCount API é um projeto desenvolvido em Java 21 com Spring Boot, containerizado com Docker, e configurado com CI/CD via GitHub Actions.
O objetivo é disponibilizar uma API para registro e contagem de árvores plantadas, com deploy automatizado em ambientes de staging e produção.

🧩 Estrutura do Projeto
treecount-api/
├── src/
├── Dockerfile
├── docker-compose.yml
├── .github/workflows/ci-cd.yml
├── README.md
└── ...

⚙️ Configuração do CI/CD

O pipeline CI/CD usa GitHub Actions com as seguintes etapas:

🏗️ 1. Build e Teste

Ao realizar um push na branch main, o pipeline:

Faz checkout do código;

Configura o Java 21;

Executa o build e os testes automatizados;

Cria e publica uma imagem Docker no Docker Hub.

🌍 2. Deploy em Staging

Após o build, o deploy para staging é feito automaticamente.
O container é iniciado em um servidor remoto com:

docker pull arthursidor/treecount-api:latest
docker stop treecount-api || true
docker rm treecount-api || true
docker run -d -p 8080:8080 --name treecount-api arthursidor/treecount-api:latest

🚢 3. Deploy em Produção

O deploy em produção é manual, disparado pelo GitHub Actions usando o evento workflow_dispatch.

🔑 Configuração de Secrets no GitHub

Antes de executar o pipeline, crie os seguintes secrets no repositório:

Nome	Descrição
DOCKER_USERNAME	arthursidor
DOCKER_PASSWORD	arthur321

🧪 Como Executar Localmente
# Build da imagem
docker build -t treecount-api .

# Executar o container
docker run -p 8080:8080 treecount-api


A API estará disponível em:
👉 http://localhost:8080

🚀 Como Executar o Deploy Manual

Vá até Actions no GitHub;

Selecione o workflow CI/CD Pipeline;

Clique em Run workflow;

Escolha o ambiente desejado (production) e clique em Run.

📘 Tecnologias Utilizadas

Java 21

Spring Boot

Docker

Docker Compose

GitHub Actions