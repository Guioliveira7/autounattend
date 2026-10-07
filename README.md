# 🖥️ Windows 11 Pro — Instalação Automática (pt-BR)

Arquivo `autounattend.xml` para instalar o **Windows 11 Pro (x64)** de forma praticamente automática, já em português do Brasil, com o sistema limpo, rápido e pronto para uso assim que chegar na área de trabalho.

Ideal para **TI, laboratórios, escolas, empresas** e para quem formata PC com frequência e quer sempre o mesmo resultado.

> Gerado com o [Unattend Generator](https://schneegans.de/windows/unattend-generator/) de Christoph Schneegans e ajustado para a minha rotina.

---

## ✨ O que ele faz

### 🌎 Região e idioma
- Idioma de instalação e sistema: **Português (Brasil)**
- Teclado: **ABNT2**
- Localização: **Brasil**
- Fuso horário: **Brasília**

### 👤 Conta e acesso
- Cria a conta local **`User`**, no grupo **Administradores**
- **Sem senha** e com login automático no primeiro boot
- Senha configurada para **nunca expirar**
- Nome do computador **aleatório**
- Sem tela de Wi-Fi e sem as telas de configuração expressa da Microsoft no OOBE

### ⚡ Desempenho
- Ativa o plano de energia **Desempenho Máximo** (Ultimate Performance)
- Efeitos visuais ajustados para **desempenho**
- Desativa o registro de último acesso a arquivos (`DisableLastAccess`)
- Remove a pasta **Windows.old** após a instalação
- Desativa o *Startup Boost* do Edge

### 🧹 Bloatware removido
Copilot, Recall, Cortana, Teams, Clipchamp, Bing Search, Dev Home, Feedback Hub, Obter Ajuda, Introdução, Família, Mapas, Notícias, Mail e Calendário, Outlook, OneNote, Pessoas, To Do, Carteira, Seu Telefone, Skype, Paint 3D, Visualizador 3D, Mixed Reality, Solitaire, Zune Música/Vídeo, Assistência Rápida, Gravador de Passos, Painel de Entrada Matemática, Windows Hello, entre outros.

### 🎨 Interface
- Menu de contexto **clássico** (estilo Windows 10)
- Barra de tarefas **alinhada à esquerda**
- Pesquisa em formato de **caixa** e botão de Visão de Tarefas oculto
- **Widgets** desativados
- Menu Iniciar sem fixados
- Explorador abre em **Este Computador**
- **Extensões de arquivo visíveis**
- Opção **Finalizar tarefa** ao clicar com o botão direito na barra de tarefas
- Sugestões de apps e resultados do Bing desativados
- Teclas de Aderência (Sticky Keys) desativadas
- Tela de boas-vindas do Edge desativada

### 🔧 Recursos e ajustes de sistema
- **Caminhos longos** habilitados (acima de 260 caracteres)
- **Área de Trabalho Remota** habilitada
- ACL da unidade do sistema reforçada
- Execução de **scripts PowerShell** permitida
- Auditoria de processos ativada
- Isolamento de Núcleo (**Core Isolation**) ativado
- Reinício automático com login desativado

### 📦 Instalado no primeiro login
| Item | Como |
|---|---|
| **Mozilla Firefox** | via `winget` (exige Windows 11 24H2 ou superior) |
| **Visual C++ Redistributable x64** | download direto da Microsoft |
| **.NET Framework 3.5** | a partir da pasta `sources\sxs` da mídia de instalação |
| **Visualizador de Fotos clássico** | chaves de registro restauradas |

---

## 🚀 Como usar

1. Baixe a **ISO oficial** do Windows 11 no site da Microsoft.
2. Grave a ISO em um **pendrive** com [Rufus](https://rufus.ie/) ou similar.
3. Copie o arquivo **`autounattend.xml`** para a **raiz do pendrive**, ao lado das pastas `sources` e `boot`.
4. Dê boot pelo pendrive e inicie a instalação.
5. Escolha o disco/partição onde o Windows será instalado.
6. Aguarde. O resto é automático. ☕

> 💡 O nome do arquivo precisa ser exatamente `autounattend.xml`.

---

## ⚠️ Antes de usar

- **A seleção do disco continua manual.** O arquivo não contém configuração de particionamento, então você escolhe onde instalar. Mesmo assim, **faça backup** dos seus dados antes.
- **Conta sem senha:** por padrão, o Windows **não permite login remoto** em contas sem senha. Como a Área de Trabalho Remota está habilitada, **defina uma senha** depois da instalação se quiser usar o acesso remoto.
- **Segurança:** uma conta de administrador sem senha é indicada para laboratórios e uso controlado. Em ambientes expostos, defina uma senha.
- **Ativação:** o arquivo usa apenas a chave genérica de instalação do Windows 11 Pro, que **não ativa** o sistema. É necessário ter uma licença válida.
- **Versão do Windows:** a instalação do Firefox via `winget` só roda no **Windows 11 24H2 (build 26100) ou superior**. Em versões anteriores, essa etapa é ignorada com um aviso.
- **.NET 3.5:** depende de a mídia de instalação estar disponível no primeiro login (o script procura a pasta `sources\sxs` nas unidades). Sem ela, o recurso não é instalado.
- **Internet:** o Visual C++ Redistributable e o Firefox são baixados no primeiro login.
