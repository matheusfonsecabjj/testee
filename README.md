# Sistema de Agenda Inteligente para Nutricionistas

Sistema completo de agendamento de consultas com lembretes automáticos via email e WhatsApp.

## Funcionalidades

### Para Nutricionistas
- Cadastro e autenticação segura
- Painel de gerenciamento de consultas
- Link único para compartilhar com pacientes
- Visualização de consultas próximas e passadas
- Atualização de status das consultas
- Gerenciamento de horários disponíveis

### Para Pacientes
- Agendamento online simples
- Escolha de data e horário disponível
- Confirmação automática por email
- Lembrete 24h antes da consulta

## Tecnologias Utilizadas

- **Frontend**: React, TypeScript, Tailwind CSS, Vite
- **Backend**: PHP
- **Banco de Dados**: Supabase (PostgreSQL)
- **Ícones**: Lucide React

## Estrutura do Banco de Dados

### Tabelas
- `nutritionists` - Dados dos nutricionistas
- `availability_slots` - Horários disponíveis
- `appointments` - Consultas agendadas
- `notifications_log` - Log de notificações enviadas

## Instalação

### Pré-requisitos
- Node.js 18+
- PHP 7.4+
- Conta Supabase configurada

### Configuração

1. Clone o repositório
2. Instale as dependências:
```bash
npm install
```

3. Configure as variáveis de ambiente no arquivo `.env`:
```
VITE_SUPABASE_URL=sua_url_supabase
VITE_SUPABASE_ANON_KEY=sua_chave_anon
```

4. Execute o projeto:
```bash
npm run dev
```

5. Para produção, faça o build:
```bash
npm run build
```

## Estrutura de Pastas

```
project/
├── public/
│   ├── api/                    # APIs PHP
│   │   ├── config.php         # Configuração e helpers
│   │   ├── appointments/      # Endpoints de consultas
│   │   ├── availability/      # Endpoints de disponibilidade
│   │   ├── nutritionist/      # Endpoints de nutricionistas
│   │   └── notifications/     # Endpoints de notificações
│   └── cron/                  # Scripts cron para lembretes
├── src/
│   ├── components/            # Componentes React
│   │   ├── BookingForm.tsx   # Formulário de agendamento
│   │   ├── BookingPage.tsx   # Página pública de agendamento
│   │   ├── Dashboard.tsx     # Painel do nutricionista
│   │   ├── LoginForm.tsx     # Formulário de login
│   │   └── RegisterForm.tsx  # Formulário de cadastro
│   ├── types/                # Tipos TypeScript
│   ├── App.tsx               # Componente principal
│   └── main.tsx              # Ponto de entrada
└── README.md
```

## Endpoints da API

### Nutricionistas
- `POST /api/nutritionist/register.php` - Cadastro
- `POST /api/nutritionist/login.php` - Login
- `GET /api/nutritionist/get-by-link.php` - Buscar por link único

### Consultas
- `POST /api/appointments/create.php` - Criar consulta
- `GET /api/appointments/list.php` - Listar consultas
- `PUT /api/appointments/update.php` - Atualizar status

### Disponibilidade
- `POST /api/availability/set.php` - Definir horários
- `GET /api/availability/get.php` - Buscar disponibilidade

### Notificações
- `GET /api/notifications/send-reminders.php` - Enviar lembretes

## Sistema de Notificações

### Configuração do Cron
Para enviar lembretes automáticos 24h antes das consultas, configure um cron job:

```bash
# Executar diariamente às 9h
0 9 * * * php /caminho/para/public/cron/daily-reminders.php
```

### Tipos de Notificações
1. **Confirmação** - Enviada imediatamente após o agendamento
2. **Lembrete** - Enviada 24h antes da consulta

## Como Usar

### Como Nutricionista

1. **Cadastro**
   - Acesse a página inicial
   - Clique em "Criar Conta"
   - Preencha seus dados
   - Após o cadastro, você receberá um link único

2. **Compartilhar Link**
   - No painel, copie seu link de agendamento
   - Compartilhe com seus pacientes via WhatsApp, email ou redes sociais

3. **Gerenciar Consultas**
   - Visualize todas as consultas no painel
   - Filtre por próximas ou passadas
   - Atualize o status das consultas
   - Veja informações dos pacientes

### Como Paciente

1. **Agendar Consulta**
   - Acesse o link único fornecido pelo nutricionista
   - Preencha seus dados pessoais
   - Escolha data e horário disponível
   - Confirme o agendamento

2. **Receber Notificações**
   - Receba confirmação por email imediatamente
   - Receba lembrete 24h antes da consulta

## Segurança

- Senhas criptografadas com bcrypt
- Row Level Security (RLS) habilitado no Supabase
- Validação de dados no backend
- Proteção contra SQL injection
- CORS configurado adequadamente

## Próximas Melhorias

- [ ] Integração real com API de WhatsApp
- [ ] Integração com Google Calendar
- [ ] Sistema de avaliações
- [ ] Relatórios e estatísticas
- [ ] Notificações push
- [ ] Reagendamento pelo paciente
- [ ] Múltiplos idiomas

## Suporte

Para dúvidas ou problemas, entre em contato através do repositório.

## Licença

Este projeto está sob a licença MIT.
