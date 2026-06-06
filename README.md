# Vitrine-Digital
Repositório para a documentação do projeto Vitrine Digital - PUC Minas
# 🏷️ Vitrine Digital 👨‍💻

> Plataforma interativa de e-commerce e catálogo digital projetada para conectar consumidores a produtos de forma ágil, segura e altamente intuitiva.

Este README.md apresenta um template organizado, ideal para servir como referência acadêmica e profissional. Ele reúne as seções essenciais recomendadas pelo Prof. Dr. João Paulo Aramuni na disciplina de Projeto de Software da PUC Minas, permitindo organização clara, documentação eficiente e padronização. O objetivo deste documento é facilitar a compreensão da arquitetura, instruções de execução e tecnologias da plataforma **Vitrine Digital**.

---

## 🚧 Status do Projeto

![Build Status](https://img.shields.io/badge/Build-Passing-success?style=for-the-badge&logo=github)
![Spring Boot](https://img.shields.io/badge/Backend-Spring%20Boot%203.x-brightgreen?style=for-the-badge&logo=springboot)
![React](https://img.shields.io/badge/Frontend-React%2018-blue?style=for-the-badge&logo=react)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL%2016-blue?style=for-the-badge&logo=postgresql)

---
## 📚 Índice

- [Links Úteis](#-links-úteis)
- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades Principais](#-funcionalidades-principais)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Arquitetura](#-arquitetura)
- [Instalação e Execução](#-instalação-e-execução)
- [Deploy](#-deploy)
- [Estrutura de Pastas](#-estrutura-de-pastas)
- [Demonstração](#-demonstração)
- [Testes](#-testes)
- [Documentações Utilizadas](#-documentações-utilizadas)
- [Autores](#-autores)
- [Contribuição](#-contribuição)
- [Agradecimentos](#-agradecimentos)
- [Licença](#-licença)

---

## 🔗 Links Úteis

- **🌐 Demo Online:** [Acesse a Aplicação Web](https://vitrine-digital.vercel.app) 
- **💻 Descrição:** Link para a aplicação em ambiente de produção distribuída globalmente.
- **📖 Documentação da API:** [Swagger UI OpenAPI Docs](http://localhost:8080/swagger-ui.html)
- **📚 Descrição:** Documentação interativa dos endpoints REST gerada via SpringDoc.

---

## 📝 Sobre o Projeto

O **Vitrine Digital** é uma plataforma robusta de comércio eletrônico criada com o objetivo de facilitar a digitalização de pequenos varejistas. A plataforma oferece uma experiência ágil onde o cliente final navega por um catálogo dinâmico de produtos, gerencia seu carrinho de compras e realiza checkouts fluidos com integrações externas simuladas.

No contexto acadêmico, o projeto atua como laboratório prático para a aplicação de conceitos cruciais de engenharia de software: desenvolvimento orientado a objetos, arquitetura distribuída desacoplada (cliente-servidor), segurança baseada em tokens (JWT) e integridade referencial utilizando bancos de dados relacionais.

---
## ✨ Funcionalidades Principais

- **🔐 Autenticação Segura (JWT):** Controle de acessos restritos por perfil (Cliente e Administrador).
- **⚙️ Gerenciamento de CRUD Completo:** Módulo administrativo para cadastro, edição, listagem e exclusão de Produtos.
- **🛒 Carrinho de Compras Interativo:** Gestão em tempo real de itens selecionados e recálculo automático de subtotais.
- **📦 Dedução Automática de Estoque:** Validação e baixa automatizada do inventário físico após o checkout.
- **🔄 Integração Externa:** Simulação síncrona com gateways de pagamento externos e APIs de cotação de frete.

---

## 🛠 Tecnologias Utilizadas

### 💻 Front-end
- **Framework Core:** React v18
- **Build Tool:** Vite
- **Estilização:** Tailwind CSS
- **Comunicação HTTP:** Axios

### 🖥️ Back-end
- **Linguagem / Runtime:** Java 17 (JDK)
- **Framework:** Spring Boot 3.x
- **Banco de Dados:** PostgreSQL 16
- **ORM / Mapeamento:** Hibernate / JPA
- **Segurança:** Spring Security + JWT

### ⚙️ Infraestrutura & DevOps
- **Containerização:** Docker e Docker Compose
- **Deploy:** Vercel (Front-end) e Railway/AWS (Back-end)
- **Modelagem Visual:** PlantUML

---

## 🏗 Arquitetura

O sistema adota o padrão de **Arquitetura Cliente-Servidor Desacoplada**, segmentada nas seguintes camadas principais:

1. **Camada de Apresentação (Front-end):** Aplicação React (Single Page Application) que consome os serviços JSON expostos pelo servidor.
2. **Camada de Controle (REST Controllers):** Endpoints HTTP responsáveis por interceptar requisições, rotear chamadas e validar os dados de transferência (DTOs).
3. **Camada de Negócio (Service Layer):** Encapsula todas as regras de negócio pesadas, validações de estoque, fluxo de checkout e integração com serviços externos.
4. **Camada de Persistência (Repository Layer):** Abstração gerada pelo ecossistema Spring Data JPA para comunicação segura, fluida e parametrizada com o banco PostgreSQL.

---
## 🔧 Instalação e Execução

### Pré-requisitos
Certifique-se de que o seu ambiente de desenvolvimento possui as seguintes ferramentas configuradas:
- **Java JDK:** Versão 17 ou superior (Necessário para o Back-end)
- **Node.js:** Versão LTS (v18.x ou superior) (Necessário para o Front-end)
- **Gerenciador de Pacotes:** npm ou yarn
- **Docker:** (Recomendado para execução orquestrada do Banco de Dados)

### 🔑 Variáveis de Ambiente

#### 1. Back-end (Spring Boot)
Configure estas variáveis no arquivo `application.yml` ou exporte no seu sistema operacional:
| Variável | Descrição | Exemplo |
| :--- | :--- | :--- |
| `SERVER_PORT` | Porta onde o Back-end será executado. | `8080` |
| `SPRING_DATASOURCE_URL` | URL de conexão JDBC (PostgreSQL). | `jdbc:postgresql://localhost:5432/vitrinedb` |
| `SPRING_DATASOURCE_USERNAME`| Usuário do banco de dados. | `postgres` |
| `SPRING_DATASOURCE_PASSWORD`| Senha do banco de dados. | `senha-segura-123` |
| `JWT_SECRET` | Chave secreta para assinatura de tokens. | `chave_super_segura_base64_aqui` |

#### 2. Front-end (React, Vite)
Crie um arquivo `.env.local` na raiz da pasta `/frontend`:
```env
VITE_API_URL=http://localhost:8080/api
## 📂 Estrutura de Pastas

A organização do repositório reflete a arquitetura separada (monorepo com front-end e back-end isolados), facilitando a manutenção e a localização dos módulos e componentes.

```text
.
├── docker-compose.yml           # 🐳 Orquestração dos containers
├── README.md                    # 📘 Documentação principal
├── /docs                        # 📚 Artefatos técnicos e diagramas PlantUML
│
├── /frontend                    # 📁 Aplicação React (SPA)
│   ├── .env.example             # 🧩 Modelo de variáveis de ambiente
│   ├── package.json             # 📦 Dependências do Node.js
│   └── /src
│       ├── /components          # 🧱 Componentes de interface reutilizáveis
│       ├── /pages               # 📄 Telas principais da plataforma
│       ├── /services            # 🔌 Conexões com a API REST (Axios)
│       └── /utils               # 🛠️ Funções utilitárias auxiliares
│
└── /backend                     # 📁 API REST Spring Boot
    ├── pom.xml                  # 🛠️ Dependências Maven
    └── /src/main/java/com/pucminas/vitrinedigital
        ├── /controller          # 🎮 Endpoints REST expostos
        ├── /service             # ⚙️ Regras e lógicas de negócio
        ├── /repository          # 🗄️ Acesso a dados (Spring Data JPA)
        ├── /model               # 🧬 Entidades relativas ao Banco de Dados
        └── /dto                 # ✉️ Objetos de transferência de dados
## 🎥 Demonstração

### 🌐 Aplicação Web
Abaixo estão as interfaces principais projetadas para a experiência do usuário final e do administrador.

| Tela | Captura de Tela / Fluxo |
| :--- | :--- |
| **Página Inicial (Catálogo)** | *(Substitua por um print da sua tela inicial)* |
| **Autenticação Segura** | *(Substitua por um print da tela de Login)* |
| **Carrinho de Compras** | *(Substitua por um print da gestão do carrinho)* |

---

## 💻 Exemplo de Saída no Terminal (Back-end)

Abaixo um exemplo de resposta JSON padronizada pela API ao consultar o catálogo de produtos:

```json
// GET /api/v1/produtos
{
  "total": 2,
  "produtos": [
    {
      "id": 1,
      "nome": "Smartphone Galaxy S24",
      "preco": 4500.00,
      "quantidadeEstoque": 15
    },
    {
      "id": 2,
      "nome": "Monitor Ultrawide 34\"",
      "preco": 2300.00,
      "quantidadeEstoque": 8
    }
  ]
}
## 🧪 Testes

A qualidade do software é garantida através de testes em ambas as extremidades do ecossistema.

**Testes Unitários e de Integração (Back-end):**
Para rodar a suíte de testes com JUnit 5 e Mockito na API:
```bash
cd backend
./mvnw test
Testes de Interface (Front-end):
Para rodar os testes de componentes e renderização no React:
cd frontend
npm run test

🔗 Documentações utilizadas
As referências abaixo foram fundamentais para a definição arquitetural e resolução de desafios técnicos durante o desenvolvimento da plataforma:
📖 Front-end: Documentação Oficial do React
📖 Ferramenta de Build: Guia de Configuração do Vite
📖 Back-end: Documentação Oficial do Spring Boot
📖 Infraestrutura: Documentação de Referência do Docker
📖 Padronização: Conventional Commits (Padrão de Mensagens)

👥 Autores
👤 Nome	💼 LinkedIn	📤 GitHub	🎓 Instituição
Davi Vinicius Barbosa de Oliveira	Seu LinkedIn	Seu GitHub	Engenharia de Software - PUC Minas

🤝 Contribuição
Contribuições são o que tornam a comunidade de código aberto um lugar incrível para aprender, inspirar e criar. Qualquer contribuição que você fizer será muito apreciada.
1 Faça um Fork do projeto.
2 Crie uma branch para sua feature (git checkout -b feature/MinhaFeature).
3 Faça o commit das suas alterações (git commit -m 'feat: Adiciona funcionalidade X'). Recomendamos o uso de Conventional Commits.
4 Faça o push para a branch (git push origin feature/MinhaFeature).
5 Abra um Pull Request (PR).

🙏 Agradecimentos
Gostaria de registrar meus agradecimentos às instituições e profissionais que guiaram a excelência técnica na construção deste projeto:
Engenharia de Software PUC Minas - Pelo apoio institucional, infraestrutura acadêmica e fomento contínuo à inovação e boas práticas de engenharia.
Prof. Dr. João Paulo Aramuni - Pelos valiosos ensinamentos sobre Arquitetura de Software e Padrões de Projeto.
Fernanda Kipper - Pelos conteúdos excepcionais de Desenvolvimento Web, DevOps e melhores práticas em Front-end.
Rodrigo Branas - Pela didática ímpar na aplicação de Clean Architecture e Clean Code.
Código Fonte TV - Pelo vasto conteúdo, tutoriais e apoio incondicional à comunidade de Desenvolvimento.

📄 Licença
Este projeto é distribuído e protegido sob os termos da Licença MIT. Consulte o arquivo LICENSE para mais detalhes.
