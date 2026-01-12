# CICLODADOS - A Plataforma da Mobilidade por Bicicleta do Recife

> **Repositório de resumo de repositórios do Projeto CICLODADOS - A plataforma da mobilidade por bicicleta do Recife - Mover-se na Web.**

## 📋 Visão Geral do Projeto

O CICLODADOS é uma iniciativa da **Ameciclo** (Associação Metropolitana de Ciclistas do Recife) que visa democratizar o acesso aos dados sobre mobilidade urbana por bicicleta no Grande Recife. A plataforma integra dados públicos, comunitários e institucionais em uma infraestrutura digital moderna, combinando tecnologia de ponta com engajamento territorial.

### 🎯 Objetivos Principais

- **Democratizar dados**: Tornar acessíveis informações sobre mobilidade por bicicleta
- **Integrar fontes**: Unificar dados públicos, comunitários e institucionais
- **Promover transparência**: Facilitar o acesso a informações sobre orçamento público e políticas cicloviárias
- **Fortalecer comunidades**: Conectar desenvolvimento tecnológico com práticas territoriais
- **Apoiar pesquisas**: Fornecer base de dados para estudos e políticas públicas

## 🏗️ Arquitetura do Ecossistema

O projeto CICLODADOS é composto por múltiplos repositórios que trabalham de forma integrada:

```
CICLODADOS Ecosystem
├── Frontend (ameciclo.org)
├── Backend APIs (Atlas)
├── Sistema de Gestão (Ameciclistas)
├── Automação (Ameciclobot)
└── IoT/Hardware (BPR Sistema)
```

## 📦 Repositórios do Projeto

### 🌐 [Ameciclo.org](https://github.com/Ameciclo/ameciclo) - Site Institucional e Plataforma de Dados

**Tecnologias**: Remix, TypeScript, Tailwind CSS, Mapbox GL

**Responsabilidades**:
- Site institucional da Ameciclo
- Plataforma de dados abertos (dados.ameciclo.org)
- Interface para visualização de indicadores urbanos
- Sistema de mapas interativos
- Seções especializadas: contagens, perfil ciclista, sinistros, orçamento público

**Status**: ✅ Produção - Migração Next.js → Remix concluída

**Principais Funcionalidades**:
- **CicloDados**: Nova plataforma integrada de visualização
- **Observatório de Sinistros**: Dados de acidentes e vias inseguras
- **Contagens de Ciclistas**: Monitoramento de fluxo cicloviário
- **Perfil Ciclista**: Pesquisas e dados demográficos
- **Orçamento Público**: LOA e DOM para mobilidade

---

### 🔧 [Atlas](https://github.com/Ameciclo/atlas) - Backend e APIs

**Tecnologias**: Node.js, TypeScript, PostgreSQL, PostGIS, Hono, Drizzle ORM

**Responsabilidades**:
- APIs RESTful para dados de mobilidade urbana
- Banco de dados georreferenciado (PostgreSQL + PostGIS)
- Microserviços especializados por domínio
- Documentação automática com OpenAPI
- Integração com dados públicos (DATASUS, CTTU, IBGE)

**Status**: ✅ Produção - Monorepo com múltiplos serviços

**Serviços Principais**:
- **cyclist-profile**: Gestão de perfis de ciclistas
- **cyclist-counts**: Dados de contagens
- **traffic-violations**: Análise de infrações
- **traffic-deaths**: Dados de mortalidade no trânsito
- **emergency-calls**: Chamados SAMU
- **cycling-infra**: Infraestrutura cicloviária

---

### 👥 [Ameciclistas](https://github.com/Ameciclo/ameciclistas) - Sistema de Gestão Interno

**Tecnologias**: Remix, TypeScript, Firebase, Telegram Web App

**Responsabilidades**:
- Sistema interno de gestão da Ameciclo
- Controle de biblioteca e empréstimos
- Gestão do sistema Bota pra Rodar
- Controle de inventário e recursos
- Sistema financeiro e de fornecedores
- Interface híbrida (Web + Telegram)

**Status**: ✅ Produção - Sistema completo operacional

**Módulos Principais**:
- **Biblioteca**: Acervo público e sistema de empréstimos
- **Bota pra Rodar**: Gestão de bicicletas comunitárias
- **Inventário**: Controle de equipamentos e ferramentas
- **Recursos**: Vendas e doações
- **Financeiro**: Gestão de pagamentos e fornecedores

---

### 🤖 [Ameciclobot](https://github.com/Ameciclo/ameciclobot) - Automação e IA

**Tecnologias**: Node.js, TypeScript, Telegraf, Firebase, Azure AI, Google APIs

**Responsabilidades**:
- Automação de processos organizacionais
- Integração com Google Workspace
- Processamento de documentos com IA
- Sistema de notificações e lembretes
- Gestão de eventos e agenda
- Transcrição de áudios e vídeos

**Status**: ✅ Produção - 20 comandos ativos

**Funcionalidades Principais**:
- **Gestão Documental**: Criação automática de Google Docs, Sheets, Slides
- **Assistente Financeiro**: Processamento de extratos e comprovantes
- **Eventos**: Criação e gestão de agenda com IA
- **Pedidos de Informação**: Monitoramento de transparência pública
- **Transcrições**: Conversão de áudio em texto

---

### 🚴 [BPR Sistema](https://github.com/Ameciclo/bpr-sistema) - IoT e Hardware

**Tecnologias**: ESP32, C++, Node.js, Telegram Bot, Firebase, Remix

**Responsabilidades**:
- Sistema embarcado para monitoramento de bicicletas
- Coleta de dados IoT em tempo real
- Bot Telegram para notificações
- Dashboard web para visualização
- Integração com Firebase Realtime Database

**Status**: ✅ Produção - Sistema v2.0 operacional

**Componentes**:
- **Firmware Bicicleta**: Scanner WiFi com ESP32
- **Firmware Central**: Base coletora de dados
- **Bot Telegram**: Monitoramento em tempo real
- **Dashboard Web**: Interface de visualização

## 🔄 Integração entre Repositórios

### Fluxo de Dados
```
BPR Sistema → Firebase → Atlas → Ameciclo.org
     ↓           ↓        ↓         ↓
Ameciclistas ← Ameciclobot ← APIs ← Frontend
```

### Tecnologias Compartilhadas
- **TypeScript**: Linguagem principal em todo o ecossistema
- **Firebase**: Banco de dados em tempo real e autenticação
- **PostgreSQL + PostGIS**: Dados georreferenciados
- **Remix**: Framework frontend moderno
- **Docker**: Containerização e deploy

## 🚀 Como Começar

### Pré-requisitos
- Node.js 20+
- PostgreSQL 16 com PostGIS
- Firebase CLI
- Docker (opcional)

### Configuração Rápida

1. **Clone os repositórios principais**:
```bash
git clone https://github.com/Ameciclo/ameciclo.git
git clone https://github.com/Ameciclo/atlas.git
git clone https://github.com/Ameciclo/ameciclistas.git
```

2. **Configure o banco de dados**:
```bash
cd atlas
docker-compose up -d  # PostgreSQL + PostGIS
pnpm install
pnpm db:migrate
```

3. **Inicie o frontend**:
```bash
cd ameciclo
npm install
npm run dev
```

### Ambientes de Desenvolvimento

- **Frontend**: [ameciclodev.vercel.app](https://ameciclodev.vercel.app/)
- **APIs**: Documentação disponível em cada serviço
- **Sistema Interno**: [ameciclistas.ameciclo.org](https://ameciclistas.ameciclo.org)

## 📊 Dados e Fontes

### Fontes de Dados Integradas
- **DATASUS**: Dados de mortalidade no trânsito
- **CTTU**: Infrações e dados de trânsito
- **IBGE**: Dados demográficos e territoriais
- **Prefeitura do Recife**: Orçamento e políticas públicas
- **Pesquisas Ameciclo**: Contagens e perfil ciclista
- **Comunidades**: Dados participativos do Bota pra Rodar

### Cobertura Geográfica
- **Foco Principal**: Região Metropolitana do Recife (RMR)
- **Extensão**: Outras cidades brasileiras com dados disponíveis
- **Sistema de Coordenadas**: WGS84 com extensões PostGIS

## 🏆 Reconhecimentos

- **Selo Bicicleta Brasil** - Ministério das Cidades
- **Prêmio Promovendo a Mobilidade por Bicicleta** - Transporte Ativo
- **Apresentação no Rec'n'Play 2025** - Festival de Inovação do Recife

## 🤝 Como Contribuir

### Para Desenvolvedores
1. Escolha um repositório de interesse
2. Leia a documentação específica no README do projeto
3. Configure o ambiente de desenvolvimento
4. Siga os padrões de código (TypeScript, ESLint, Prettier)
5. Abra um Pull Request

### Para Pesquisadores
- Acesse os dados através da API pública
- Consulte a documentação em [ameciclo.org/documentacao](https://ameciclo.org/documentacao)
- Entre em contato para colaborações

### Para Comunidades
- Participe das oficinas de formação
- Contribua com dados territoriais
- Use as ferramentas para advocacy local

## 📞 Contato e Suporte

- **Site**: [ameciclo.org](https://ameciclo.org)
- **Email**: contato@ameciclo.org
- **Telegram**: @ameciclo_info
- **GitHub**: [github.com/Ameciclo](https://github.com/Ameciclo)

## 📄 Licença

Todos os projetos do ecossistema CICLODADOS são licenciados sob a **GNU Affero General Public License v3.0 (AGPL-3.0)**.

### O que isso significa?
- ✅ **Uso livre**: Você pode usar este software para qualquer propósito
- ✅ **Modificação**: Você pode modificar o código fonte
- ✅ **Distribuição**: Você pode distribuir o software original ou modificado
- ✅ **Uso comercial**: Permitido uso comercial
- ⚠️ **Copyleft**: Modificações devem ser disponibilizadas sob a mesma licença
- ⚠️ **Código aberto**: Se você executar uma versão modificada em um servidor, deve disponibilizar o código fonte

**Copyright (C) 2024 Ameciclo - Associação Metropolitana de Ciclistas do Recife**

Para mais detalhes, consulte o arquivo LICENSE em cada repositório ou visite: https://www.gnu.org/licenses/agpl-3.0.html

---

## 🔗 Links Úteis

### Repositórios Ativos
- [Ameciclo.org](https://github.com/Ameciclo/ameciclo) - Site e plataforma de dados
- [Atlas](https://github.com/Ameciclo/atlas) - Backend e APIs
- [Ameciclistas](https://github.com/Ameciclo/ameciclistas) - Sistema de gestão
- [Ameciclobot](https://github.com/Ameciclo/ameciclobot) - Automação e IA
- [BPR Sistema](https://github.com/Ameciclo/bpr-sistema) - IoT e hardware

### Plataformas em Produção
- [Site Institucional](https://ameciclo.org)
- [Plataforma de Dados](https://dados.ameciclo.org)
- [Sistema Interno](https://ameciclistas.ameciclo.org)
- [Bot Telegram](https://t.me/ameciclobot)

### Documentação e Recursos
- [Documentação Técnica](https://ameciclo.org/documentacao)
- [Protótipo Figma](https://www.figma.com/proto/4pVXpZveDOgcXNK0bib4Tj/Ciclodados)
- [Metabase (Visualizações)](https://do.metabase.ameciclo.org)
- [CMS Strapi](https://do.strapi.ameciclo.org)

---

**Desenvolvido com ❤️ pela Ameciclo** - Promovendo a mobilidade sustentável no Grande Recife

*Este é um projeto de tecnologia social que articula ciência, mobilidade e cidadania para construir uma cidade mais justa e sustentável.*