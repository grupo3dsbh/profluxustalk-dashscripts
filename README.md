# Chatwoot Dashboard Scripts - ProFluxus

Scripts personalizados para integração do ProFluxus com o dashboard do Chatwoot.

## 📋 Scripts Disponíveis

### 1. ProFluxus Config (`profluxus-config.html`)

Gerenciador completo de configurações ProFluxus integrado ao Chatwoot.

#### Funcionalidades

**Configurações por Conta:**
- WhatsApp (número para notificações)
- Tipo de uso:
  - Receber Leads
  - Notificações ProFluxus

**Configurações Globais:**
- API de Atualização de Consultor
  - URL do endpoint
  - Método HTTP (POST/GET)
  - Chave de API (Access Token)
  - Dados adicionais (Prompt)
- Documento (CPF/CNPJ)

#### Integrações

**API ProFluxus (Única):**
- Endpoint: `/platform/api/v1/users/{id}`
- Métodos: `GET` (buscar) + `PATCH` (atualizar)
- Header: `api_access_token: oT4hMJhLrpeVmqZdHpcsY9Nr`
- Sem dependência da API Chatwoot padrão
- Busca dados sob demanda ao clicar no botão

#### Interface

**Lista de Agentes (somente `/settings/agents`):**
- Detecta agentes automaticamente pelos links de perfil
- Botão 📱 ao lado do nome de cada agente
- Modal completo com todos os campos
- Busca dados via API ProFluxus ao clicar
- Permite configurar qualquer agente da conta

#### Como Usar

1. **Inserir no Chatwoot:**
   - Copie o conteúdo de `profluxus-config.html`
   - Cole no console do navegador ou adicione como script customizado

2. **Configurar Agentes:**
   - Acesse: `/accounts/{id}/settings/agents`
   - Aguarde os botões 📱 aparecerem ao lado de cada agente
   - Clique no botão do agente que deseja configurar
   - Configure todos os campos no modal
   - Salve as configurações

#### Estrutura de Dados

```javascript
// Custom Attributes por conta
{
  "account_123": {
    "whatsapp": "+55 31 99999-9999",
    "uso_profluxus": "receber_leads"
  },
  // Dados globais
  "chave_openai": "token_aqui",
  "prompt_openai": "informações adicionais",
  "documento": "12345678900",
  "api_openai": {
    "url": "https://api.exemplo.com/consultor",
    "method": "POST"
  }
}
```

---

### 2. Toggle Contatos (`toggle-contatos.html`)

Script que transforma o botão de contatos (👤) em um toggle verdadeiro.

#### Funcionalidades

- **Primeiro clique:** Abre o painel de contatos
- **Segundo clique:** Fecha o painel de contatos
- Detecção automática do painel aberto
- Compatível com diferentes frameworks de ícones (Lucide, Heroicons, etc.)

#### Como Funciona

1. Detecta o botão de contatos pelo ícone `.i-ph-user-bold`
2. Intercepta cliques com `useCapture=true`
3. Verifica se o painel está aberto
4. Se aberto, previne propagação e clica no botão X
5. Se fechado, permite abertura normal

#### Como Usar

1. **Inserir no Chatwoot:**
   - Copie o conteúdo de `toggle-contatos.html`
   - Cole no console do navegador ou adicione como script customizado

2. **Testar:**
   - Clique no botão de contatos (👤)
   - Painel abre
   - Clique novamente no botão (👤)
   - Painel fecha

## 🚀 Instalação

### Método 1: Console do Navegador (Temporário)

```bash
# Copie o conteúdo do script desejado
# Abra o console (F12)
# Cole e pressione Enter
```

### Método 2: Userscript (Permanente)

Use extensões como Tampermonkey ou Greasemonkey:

1. Instale a extensão
2. Crie novo script
3. Cole o conteúdo
4. Configure para rodar no domínio do Chatwoot

### Método 3: Injeção no Backend

Adicione os scripts ao template do Chatwoot para carregar automaticamente.

## 🔧 Desenvolvimento

### Estrutura do Projeto

```
profluxustalk-dashscripts/
├── profluxus-config.html    # Gerenciador de configurações
├── toggle-contatos.html      # Toggle do painel de contatos
└── README.md                 # Esta documentação
```

### Branch de Desenvolvimento

- Branch: `claude/chatwoot-dashboard-scripts-YOxo5`
- Commits com mensagens descritivas em português
- Versionamento semântico

### Tecnologias

- JavaScript vanilla (ES6+)
- IIFE (Immediately Invoked Function Expression)
- Modo estrito (`'use strict'`)
- Mutation Observer para SPAs
- Fetch API para requisições

## 📝 Changelog

### 2026-01-06

- ✅ Remove completamente dependência da API Chatwoot
- ✅ Usa APENAS API ProFluxus para todas as operações
- ✅ Simplifica detecção de agentes (via links de perfil)
- ✅ Remove cache de agentes e seção de perfil
- ✅ Busca dados sob demanda ao clicar no botão
- ✅ Script reduzido de 1048 para 720 linhas
- ✅ Elimina erros 401 de autenticação

### 2026-01-05

- ✅ Implementa integração completa com API ProFluxus
- ✅ Adiciona modal de configuração completo
- ✅ Suporta configurações por conta e globais
- ✅ Interface na página de perfil
- ✅ Botões na lista de agentes (admin)
- ✅ Toggle de contatos funcional
- ✅ Corrige campos do gerenciador ProFluxus
- ✅ Adiciona script de toggle para painel de contatos
- ✅ Primeira versão do gerenciador de configurações

## 🐛 Debug

Ambos os scripts incluem logs detalhados no console:

```javascript
// ProFluxus Config
console.log('📱 ProFluxus Config carregado!');
console.log('✅ Agentes carregados no cache');
console.log('✅ Configurações salvas');

// Toggle Contatos
console.log('👥 Toggle Contatos carregado!');
console.log('🖱️ CLIQUE NO BOTÃO DE CONTATOS');
console.log('🔴 Painel está ABERTO → FECHANDO');
```

Abra o console do navegador (F12) para acompanhar a execução.

## 📄 Licença

Scripts desenvolvidos para uso interno do ProFluxus.

## 👤 Autor

Desenvolvido por Claude para ProFluxus
