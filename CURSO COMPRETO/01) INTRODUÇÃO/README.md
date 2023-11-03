# INTRODUÇÃO, INSTALAÇÃO E CONFIGURAÇÃO
## Introdução à Unity:
A Unity é uma das engines de desenvolvimento de jogos mais populares e amplamente utilizadas no mundo. Ela é conhecida por sua versatilidade, permitindo criar jogos e aplicativos interativos para uma variedade de plataformas, desde PC e dispositivos móveis até consoles e realidade virtual.

Principais características da Unity:
- Ambiente de desenvolvimento unificado.
- Suporte a linguagem de programação C#.
- Gráficos de alta qualidade e ferramentas de animação.
- Física integrada e simulação.
- Exportação para várias plataformas, incluindo Windows, macOS, iOS, Android, consoles, Web e VR.
- Asset Store para recursos prontos para uso.
- Amplas comunidades e recursos de aprendizado.

## Instalação e Configuração:
Aqui estão as etapas básicas para instalar e configurar o Unity:

1. **Download do Unity Hub**:

   O Unity Hub é um aplicativo que ajuda a gerenciar várias versões do Unity e projetos. Você pode baixá-lo no site [oficial da Unity](https://unity.com/pt/download)

2. **Instalação do Unity Hub**:

   Após o download, execute o instalador do Unity Hub. Siga as instruções na tela para concluir a instalação.

3. **Iniciar o Unity Hub**:

   Após a instalação, inicie o Unity Hub. Você verá a tela de login. Você pode criar uma conta Unity ou fazer login em uma existente.

4. **Adicionar ou Instalar o Unity**:

   - No Unity Hub, vá para a guia "Instalar" para adicionar ou instalar uma versão do Unity.
   - Clique no botão "Adicionar" ou "Instalar".
   - Escolha a versão do Unity que deseja usar. Você também pode adicionar módulos adicionais, como suporte a Android ou iOS.
   - Siga as instruções para concluir a instalação.

5. **Configuração de Licença**:

   Durante a instalação ou ao adicionar uma versão do Unity, você será solicitado a escolher uma licença. Existem opções gratuitas e pagas, dependendo das suas necessidades. Você precisará aceitar os termos da licença para continuar.

6. **Iniciar um Novo Projeto**:

   Após instalar o Unity, você pode criar um novo projeto. No Unity Hub, vá para a guia "Projetos" e clique em "Novo". Escolha um modelo de projeto (por exemplo, "3D" ou "2D") e configure as opções do projeto.

7. **Interface da Unity**:

   Quando você cria ou abre um projeto, a interface da Unity é aberta. Ela é composta por várias janelas e painéis, incluindo a cena, hierarquia, inspetor e o editor de código. Familiarize-se com a interface para começar a desenvolver seu jogo.

Agora você está pronto para começar a desenvolver seu jogo na Unity. Você pode criar GameObjects, adicionar scripts, criar cenas, importar ativos e muito mais. A Unity oferece uma ampla gama de recursos e documentação para ajudar no desenvolvimento do seu projeto.

## Primeiro Jogo:
Para criar um jogo simples em que um cubo cai no chão na Unity, você precisa seguir algumas etapas básicas. Aqui está um guia passo a passo:

**Passo 1: Iniciar um Novo Projeto**

1. Abra o Unity Hub e crie um novo projeto. Você pode escolher entre um projeto 2D ou 3D, dependendo de suas preferências. Para este exemplo, criaremos um projeto 3D.

**Passo 2: Criar o Ambiente do Jogo**

1. Na hierarquia do seu projeto, clique com o botão direito do mouse e selecione "3D Object" -> "Cube" para criar um cubo.
2. No painel "Inspector", você pode ajustar a posição do cubo para que ele fique acima do chão.

**Passo 3: Criar o Chão**

1. Novamente na hierarquia, clique com o botão direito do mouse e escolha "3D Object" -> "Cube" para criar um segundo cubo. Esse será o chão.
2. No painel "Inspector", ajuste a escala do cubo do chão para que ele seja uma superfície plana que cubra a área onde o cubo cairá.

**Passo 4: Adicionar Física aos Objetos**

1. Selecione o cubo que deve cair (o primeiro cubo que você criou).
2. No painel "Inspector", clique em "Add Component" e procure por "Rigidbody". Adicione um componente Rigidbody ao cubo. Isso permitirá que ele seja afetado pela física e caia devido à gravidade.

**Passo 5: Configurar a Gravidade**

1. Na parte superior da janela do Unity, vá em "Edit" -> "Project Settings" -> "Physics" para acessar as configurações de física.
2. Certifique-se de que a "Gravity" (gravidade) esteja definida em um valor negativo adequado, como -9.8, para simular a gravidade da Terra.

**Passo 6: Testar o Jogo**

1. Salve seu projeto e pressione o botão "Play" no topo da janela Unity para testar o jogo.
2. O cubo deve cair devido à gravidade e pousar no chão.

Isso é uma versão muito básica de um jogo em que um cubo cai no chão. Você pode expandir esse conceito adicionando elementos como animações, interações do jogador, sons, efeitos visuais e muito mais para criar um jogo mais completo e envolvente. Lembre-se de que a Unity oferece uma ampla gama de recursos e documentação para ajudar no desenvolvimento de jogos mais complexos.