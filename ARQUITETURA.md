# Arquitetura e Relacionamentos - CICLODADOS

## 🏗️ Arquitetura Geral do Sistema

O CICLODADOS é estruturado como uma plataforma distribuída e modular, composta por cinco camadas principais:

### 1. **Frontend (Remix - React.js)**
- **Repositório**: [ameciclo.org](https://github.com/Ameciclo/ameciclo)
- **Função**: Interface pública e plataforma de dados
- **Tecnologias**: Remix, TypeScript, Tailwind CSS, Mapbox GL
- **Hospedagem**: Vercel

### 2. **Backend APIs (Express.js/Hono)**
- **Repositório**: [Atlas](https://github.com/Ameciclo/atlas)
- **Função**: APIs RESTful e microserviços
- **Tecnologias**: Node.js, TypeScript, Hono, PostgreSQL + PostGIS
- **Hospedagem**: DigitalOcean

### 3. **CMS (Strapi v5)**
- **Repositório**: [Strapi](https://github.com/Ameciclo/strapi)
- **Função**: Gerenciamento de conteúdo e metadados
- **Tecnologias**: Strapi v5, PostgreSQL
- **Acesso**: [do.strapi.ameciclo.org](https://do.strapi.ameciclo.org)

### 4. **Sistema de Gestão (Ameciclistas)**
- **Repositório**: [Ameciclistas](https://github.com/Ameciclo/ameciclistas)
- **Função**: Gestão interna da organização
- **Tecnologias**: Remix, Firebase, Telegram Web App
- **Acesso**: [ameciclistas.ameciclo.org](https://ameciclistas.ameciclo.org)

### 5. **Automação e IoT**
- **Repositórios**: [Ameciclobot](https://github.com/Ameciclo/ameciclobot), [BPR Sistema](https://github.com/Ameciclo/bpr-sistema)
- **Função**: Automação de processos e coleta de dados IoT
- **Tecnologias**: Node.js, ESP32, Firebase, Azure AI

## 🔄 Fluxo de Dados e Integrações

### Diagrama de Fluxo Principal
```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   BPR Sistema   │───▶│    Firebase     │───▶│     Atlas       │
│   (IoT/ESP32)   │    │  (Realtime DB)  │    │   (APIs/DB)     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                                                        │
┌─────────────────┐    ┌─────────────────┐             │
│  Ameciclobot    │───▶│     Strapi      │◀────────────┘
│  (Automação)    │    │     (CMS)       │
└─────────────────┘    └─────────────────┘
                                │
┌─────────────────┐             │
│ Ameciclistas    │◀────────────┘
│ (Gestão Interna)│
└─────────────────┘
                │
                ▼
┌─────────────────┐
│  Ameciclo.org   │
│   (Frontend)    │
└─────────────────┘
```

### Integrações Específicas

#### **Atlas ↔ Ameciclo.org**
- APIs RESTful fornecem dados para visualizações
- Endpoints especializados por domínio (contagens, sinistros, etc.)
- Documentação OpenAPI automática

#### **Firebase ↔ Ameciclistas**
- Autenticação de usuários
- Dados em tempo real para gestão interna
- Sincronização com Telegram Web App

#### **Ameciclobot ↔ Google Workspace**
- Criação automática de documentos
- Processamento de planilhas financeiras
- Gestão de calendário e eventos

#### **BPR Sistema ↔ Firebase**
- Dados IoT das bicicletas comunitárias
- Monitoramento em tempo real
- Notificações via Telegram

## 📋 Dependências e Relacionamentos

### Dependências Críticas
```
Ameciclo.org
├── Atlas (APIs de dados)
├── Strapi (Conteúdo e metadados)
└── Mapbox (Visualizações geográficas)

Atlas
├── PostgreSQL + PostGIS (Banco principal)
├── APIs externas (DATASUS, CTTU, IBGE)
└── Docker (Containerização)

Ameciclistas
├── Firebase (Autenticação e dados)
├── Telegram Web App SDK
└── Google APIs (integração)

Ameciclobot
├── Firebase (dados organizacionais)
├── Google Workspace APIs
├── Azure AI (GPT, Whisper)
└── Telegram Bot API

BPR Sistema
├── Firebase Realtime Database
├── ESP32 (hardware)
└── Google Geolocation API
```

### Fluxos de Autenticação
- **Público**: Acesso livre aos dados abertos
- **Interno**: JWT + Firebase para Ameciclistas
- **Bot**: Telegram authentication
- **APIs**: Token-based authentication

## 🛠️ Configuração do Ambiente Completo

### 1. Configuração do Backend (Atlas)
```bash
cd atlas
docker-compose up -d  # PostgreSQL + PostGIS
pnpm install
pnpm db:migrate
pnpm dev  # Inicia todos os microserviços
```

### 2. Configuração do CMS (Strapi)
```bash
cd strapi
npm install
npm run develop
```

### 3. Configuração do Frontend (Ameciclo.org)
```bash
cd ameciclo
npm install
npm run dev
```

### 4. Configuração do Sistema Interno (Ameciclistas)
```bash
cd ameciclistas
npm install
# Configurar Firebase
npm run dev
```

### 5. Configuração da Automação (Ameciclobot)
```bash
cd ameciclobot/functions
npm install
# Configurar credenciais (Google, Azure, Telegram)
npm run serve
```

## 🔧 Ferramentas de Desenvolvimento

### Padrões de Código
- **TypeScript**: Linguagem principal
- **ESLint**: Linting padronizado
- **Prettier**: Formatação de código
- **Conventional Commits**: Padrão de commits

### CI/CD
- **GitHub Actions**: Pipelines automatizados
- **Vercel**: Deploy automático do frontend
- **DigitalOcean**: Hospedagem de APIs
- **Firebase**: Deploy de funções

### Monitoramento
- **Portainer**: Monitoramento de containers
- **Metabase**: Dashboards de dados
- **Firebase Console**: Logs e métricas

## 📈 Métricas e Indicadores

### Dados Disponíveis
- **320.320+ registros** de mortalidade no trânsito (2015-2023)
- **Múltiplas bases** de contagens de ciclistas
- **Dados completos** de infraestrutura cicloviária
- **Orçamento público** municipal e estadual
- **Dados IoT** das bicicletas comunitárias

### Cobertura Técnica
- **20 comandos** ativos no Ameciclobot
- **12+ microserviços** no Atlas
- **15+ hooks** customizados no frontend
- **99%+ uptime** em produção

## 🔮 Roadmap e Evolução

### Próximos Passos
- **API Pública**: Abertura completa das APIs
- **Expansão Geográfica**: Outras cidades brasileiras
- **Novas Integrações**: Mais fontes de dados públicos
- **Melhorias UX**: Interface mais acessível
- **Formação**: Mais oficinas comunitárias

### Tecnologias Futuras
- **Machine Learning**: Análise preditiva de dados
- **Real-time Analytics**: Dashboards em tempo real
- **Mobile Apps**: Aplicativos nativos
- **Blockchain**: Transparência de dados

## 📚 Documentação Adicional

### Por Repositório
- [Atlas - Documentação de APIs](https://github.com/Ameciclo/atlas/blob/main/README.md)
- [Ameciclo.org - Guia de Desenvolvimento](https://github.com/Ameciclo/ameciclo/blob/main/README.md)
- [Ameciclistas - Manual do Sistema](https://github.com/Ameciclo/ameciclistas/blob/main/README.md)
- [Ameciclobot - Comandos e Funcionalidades](https://github.com/Ameciclo/ameciclobot/blob/main/README.md)
- [BPR Sistema - Hardware e IoT](https://github.com/Ameciclo/bpr-sistema/blob/main/README.md)

### Recursos Técnicos
- [Protótipo Figma](https://www.figma.com/proto/4pVXpZveDOgcXNK0bib4Tj/Ciclodados)
- [Documentação Técnica](https://ameciclo.org/documentacao)
- [Visualizações Metabase](https://do.metabase.ameciclo.org)

---

*Esta documentação é mantida pela equipe técnica da Ameciclo e atualizada conforme a evolução do projeto.*