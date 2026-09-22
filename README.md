# -projetos_cdt
Aqui está uma versão completa, rica e estruturada do arquivo README.md para o seu repositório no GitHub. Ela inclui snippets do seu próprio código, badges, instruções passo a passo e tabelas organizadas.
Basta copiar o conteúdo abaixo e salvar como README.md no seu projeto:
🚀 IA SKY: Assistente Pessoal, Automação Local e Google Calendar
Bem-vindo ao repositório da IA SKY! Este projeto é uma assistente virtual unificada desenvolvida em Python que une o processamento de linguagem natural local (Ollama / Llama 3.1) com automação do sistema operacional, pesquisas na web e gestão da agenda do Google.
O sistema possui interface gráfica (Tkinter) com suporte a abas de conversa, múltiplos usuários com autenticação criptografada, memória de longo prazo e Function Calling nativo.
📅 Estrutura e Módulos do Sistema
O projeto é dividido em blocos bem definidos de funcionalidade e integração:
⚙️ Bloco 1: Automação e Ferramentas Locais
A assistente consegue interagir diretamente com o sistema operacional para executar tarefas e buscar informações externas:
 * Abertura de Aplicativos: Suporte a Windows, macOS e Linux para abrir softwares nativos ou instalados.
 * Comandos de Terminal: Execução remota via cmd/shell com timeout de segurança de 15 segundos.
 * Pesquisa Web: Módulo de busca dinâmica utilizando a biblioteca googlesearch-python.
def abrir_aplicativo(nome_app: str) -> str:
    """Abre um aplicativo local no sistema operacional (Windows/Linux/Mac)."""
    nome_clean = nome_app.lower().strip()
    sistema = sys.platform
    # ... executa comandos via subprocess ...

📅 Bloco 2: Integração Google Calendar API
Integração com a API REST do Google Calendar para agendamento automático de compromissos:
 * OAuth2 Authentication: Gerenciamento seguro de credentials.json e geração do token local token.json.
 * Conversão de Datas: Aceita strings no formato ISO e ajusta a duração do evento e fuso horário (America/Sao_Paulo).
def agendar_compromisso_google(titulo: str, data_inicio_iso: str, duracao_minutos: int = 60) -> str:
    """Cria um evento no Google Calendar no formato 'YYYY-MM-DDTHH:MM:SS'."""
    service, msg = obter_servico_google_calendar()
    # ... constrói o evento e envia para a API ...

🗃️ Bloco 3: Banco de Dados & Persistência SQLite
Persistência local segura utilizando o banco de dados historico_sky.db:
 * Autenticação: Tabela de usuários com armazenamento de senhas utilizando hash SHA-256.
 * Histórico de Sessões: Mapeamento completo das conversas agrupadas por sessões e usuários.
 * Memória Resumida: Extração contínua e aprendizado de fatos sobre o usuário para personalização dos prompts.
| Tabela | Função Principais |
|---|---|
| usuarios | Armazena id, nome e senha_hash. |
| conversas | Registro de mensagens, ID da sessão e timestamp. |
| memoria_resumida | Guarda preferências e fatos extraídos das conversas. |
🧠 Bloco 4: Agente IA com Function Calling
O coração da assistente é movido pelo modelo Llama 3.1 (8b) via biblioteca oficial do Ollama:
 * Orquestração de Ferramentas: A IA analisa a mensagem do usuário e decide autonomamente se deve disparar uma função Python local ou apenas responder.
 * Injeção de Contexto Temporal: Informa continuamente a data, hora e dia da semana exatos para facilitar interpretações como "agende para amanhã às 15h".
resposta = ollama.chat(
    model=self.modelo,
    messages=lista_mensagens,
    tools=[abrir_aplicativo, agendar_compromisso_google, pesquisar_na_web, executar_comando_cmd],
    options={"temperature": 0.3}
)

🖥️ Bloco 5: Interface Gráfica Tkinter (GUI)
 * Gerenciamento de Sessões: Suporte a abas dinâmicas de bate-papo.
 * Temas Customizáveis: Suporte a modos Claro e Escuro com paletas de cores configuráveis via JSON.
🛠️ Pré-requisitos e Instalação
1. Clonar o repositório
git clone https://github.com/seu-usuario/ia-sky.git
cd ia-sky

2. Instalar as dependências do Python
pip install ollama google-api-python-client google-auth-httplib2 google-auth-oauthlib googlesearch-python

3. Configurar o Ollama
Certifique-se de ter o Ollama instalado na sua máquina e baixe o modelo padrão:
ollama run llama3.1:8b

4. Configurar a API do Google Calendar (Opcional)
 * Acesse o Google Cloud Console.
 * Ative a Google Calendar API e crie uma credencial do tipo OAuth 2.0 Client ID (Desktop App).
 * Faça o download do arquivo .json, renomeie para credentials.json e coloque-o na raiz do projeto.
💡 Como Executar
Execute o script principal via terminal:
python sky.py

 * Tela de Login: Digite seu usuário e senha. Se for o seu primeiro acesso, uma nova conta será criada automaticamente.
 * Interação por Chat: Faça solicitações diretas como:
   * "Abre o Bloco de Notas para mim."
   * "Pesquise sobre as principais notícias de IA na web."
   * "Agende uma reunião com o time para amanhã às 14:00."
   * "Eu gosto de torcer para o Santos." (A SKY guardará essa informação na memória)
