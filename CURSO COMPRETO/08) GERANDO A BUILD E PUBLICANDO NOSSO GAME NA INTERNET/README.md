# GERANDO A BUILD E PUBLICANDO NOSSO GAME NA INTERNET
Para gerar a build e publicar seu jogo do dinossauro na internet, você precisará seguir alguns passos para compilar o jogo em uma forma jogável e depois hospedar o jogo em um site ou plataforma de sua escolha. Vou te guiar por esse processo.

## Passo 1: Gerar a Build do Jogo
1. **Preparar o Projeto:**
   - Certifique-se de que o seu jogo está completo e testado.
   - Vá para `File` > `Build Settings`.

2. **Selecionar a Plataforma:**
   - No painel `Build Settings`, escolha a plataforma para a qual você deseja compilar o jogo. Para a web, você pode escolher `WebGL` ou `Windows`, `Mac`, `Linux` se quiser criar um aplicativo desktop.

3. **Adicionar a Cena ao Build:**
   - Certifique-se de que sua cena principal está listada na seção `Scenes In Build`. Se não estiver, clique em `Add Open Scenes` para adicioná-la.

4. **Configurar as Opções de Build:**
   - Clique em `Player Settings` e configure as opções de Player, como o nome do jogo, ícones e configurações de resolução, dependendo da plataforma selecionada.
   - Para WebGL, você pode ajustar configurações como qualidade gráfica e compactação.

5. **Gerar a Build:**
   - Volte para a janela `Build Settings`.
   - Clique em `Build` e escolha um diretório para salvar os arquivos gerados.
   - O Unity começará a compilar o jogo e gerar os arquivos necessários.

## Passo 2: Hospedar o Jogo na Internet
### **Publicar na Web com o Unity WebGL**
1. **Publicar em um Servidor Web:**
   - Após a compilação, você terá uma pasta com arquivos HTML, JavaScript e outros recursos. Você precisará fazer o upload desses arquivos para um servidor web.

2. **Usar um Serviço de Hospedagem Gratuita ou Paga:**
   - **GitHub Pages:** Ideal para projetos pequenos. Você pode criar um repositório no GitHub e usar o GitHub Pages para hospedar seu jogo.
     - Crie um repositório no GitHub.
     - Faça upload dos arquivos da build para o repositório.
     - Vá para as configurações do repositório e habilite o GitHub Pages. Selecione a branch onde você fez o upload dos arquivos.

   - **Itch.io:** Uma plataforma popular para jogos indie.
     - Crie uma conta no Itch.io.
     - No painel do usuário, clique em `Upload New Project`.
     - Selecione a opção `HTML` para jogos WebGL.
     - Faça upload dos arquivos da build do Unity.
     - Configure a página do seu jogo e publique.

   - **Netlify/Vercel:** Plataformas fáceis de usar para hospedar sites e jogos WebGL.
     - Crie uma conta no Netlify ou Vercel.
     - Use a opção de arrastar e soltar para fazer o upload da pasta da build, ou conecte seu repositório do GitHub.

### **Publicar para Desktop (Windows, Mac, Linux)**
1. **Escolher uma Plataforma de Distribuição:**
   - **Steam:** Uma plataforma popular para distribuição de jogos. Você precisará seguir o processo de publicação do Steamworks, que inclui configurar uma página de loja e passar pela revisão da Valve.
   - **itch.io:** Também suporta jogos de desktop. Você pode criar uma página de projeto e fazer o upload dos arquivos executáveis.
   - **Game Jolt:** Outra plataforma que permite a distribuição de jogos.

2. **Empacotar e Enviar o Jogo:**
   - Para Windows, crie um arquivo ZIP contendo o executável e os arquivos de dados.
   - Para Mac, crie um arquivo .app e compacte-o.
   - Para Linux, empacote o jogo em um arquivo .tar.gz ou .zip.

3. **Subir os Arquivos:**
   - Siga as instruções específicas de cada plataforma para fazer o upload e configurar seu jogo.

