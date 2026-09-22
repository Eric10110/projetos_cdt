# -projetos_cdt
Aqui está o README.md adaptado no estilo dinâmico e estruturado da sua Jornada de Transformação Tecnológica, cobrindo toda a arquitetura, módulos e requisitos do projeto da IA SKY:
🚀 IA SKY: Assistente Pessoal e Automação Local
Bem-vindo ao repositório da IA SKY! Este é o projeto unificado de uma assistente virtual inteligente capaz de unir o poder dos modelos de linguagem locais com a automação do sistema operacional, pesquisas em tempo real e gestão de agenda.
Aqui você encontrará uma arquitetura robusta baseada em Python, que combina privacidade (execução de IA offline via Ollama), persistência de dados e automação avançada com Function Calling.
📅 Estrutura e Módulos do Sistema
O projeto está organizado em blocos funcionais e modulares:
⚙️ Bloco 1: Automação e Ferramentas Locais
 * Controle do Sistema Operacional: Abertura e inicialização de aplicações locais no Windows, macOS e Linux.
 * Execução de Comandos: Integração direta com o terminal/CMD de forma segura, com suporte a tempo limite (timeout).
 * Pesquisa Web: Busca e extração de links atualizados em tempo real via googlesearch-python.
📅 Bloco 2: Integração Google Calendar
 * Autenticação OAuth2: Conexão segura com a API do Google Calendar utilizando escopos de autorização.
 * Agendamento Inteligente: Conversão de datas e criação de compromissos diretamente no calendário principal do usuário.
🗃️ Bloco 3: Banco de Dados & Persistência
Armazenamento local utilizando SQLite3 com três pilares fundamentais:
 * Usuários: Autenticação e proteção de dados com hash criptográfico (SHA-256).
 * Conversas: Histórico de sessões para navegação fluida entre múltiplos chats.
 * Memória Resumida: Extração e armazenamento contínuo de preferências e fatos sobre o usuário.
🧠 Bloco 4: Agente IA & Function Calling
 * Integração Ollama: Comunicação direta com o modelo local (llama3.1:8b).
 * Invocação de Ferramentas: A IA decide de forma autônoma quando acionar comandos de sistema, pesquisas ou o calendário com base na necessidade do usuário.
 * Contexto Temporal: Injeção dinâmica de data, hora e dia da semana para agendamentos precisos.
🖥️ Bloco 5: Interface Gráfica (GUI)
 * Interface Tkinter: Painel visual dinâmico com suporte a múltiplas abas de conversas.
 * Customização de Temas: Alternância nativa entre modo Claro e Escuro.
🛠️ Requisitos e Dependências
Para executar a IA SKY, você precisará dos seguintes elementos instalados:
 * Python 3.10+
 * Ollama (rodando localmente com o modelo llama3.1:8b)
Bibliotecas Python:
pip install ollama google-api-python-client google-auth-httplib2 google-auth-oauthlib googlesearch-python

💡 Como Executar
 * Inicie o Ollama e garanta que o modelo padrão está baixado:
   ollama run llama3.1:8b

 * Configure o Google Calendar (Opcional):
   * Baixe seu arquivo de credenciais da Google Cloud Console e salve no diretório raiz do projeto como credentials.json.
 * Execute a aplicação:
   python sky.py
   !
