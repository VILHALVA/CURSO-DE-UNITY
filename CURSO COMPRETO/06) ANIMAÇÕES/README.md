# COMO CRIAR ANIMAÇÕES EM QUALQUER OBJETO?
Para criar animações em objetos na Unity, você pode usar o sistema de animação integrado da engine, que permite criar transições suaves entre diferentes estados de animação. Aqui estão os passos básicos para criar animações em qualquer objeto na Unity:

**Passo 1: Preparar o Objeto e Cena**

Antes de criar animações, certifique-se de que seu objeto e cena estejam prontos:

1. Selecione o objeto ao qual você deseja adicionar animações na hierarquia da Unity.

2. Certifique-se de que o objeto tenha um componente "Animator" (Animator Controller) associado. Se não tiver, adicione um criando um novo Animator Controller e atribuindo-o ao objeto.

**Passo 2: Criar o Animator Controller**

1. No painel "Animator" (janela de animação) da Unity, você pode criar um novo "Animator Controller" clicando com o botão direito e selecionando "Create Animator Controller". Dê um nome para o controller.

**Passo 3: Criar Estados de Animação**

1. No painel "Animator", você verá o Animator Controller vazio. Clique duas vezes nele para abrir a janela de animação.

2. No Animator Controller, você pode criar "estados de animação". Estes estados representarão as diferentes animações do objeto.

3. Crie um estado de animação para cada animação que deseja criar, como "Idle", "Run", "Jump", etc. Para fazer isso, clique com o botão direito no espaço vazio do Animator Controller e escolha "Create State" -> "Empty".

4. Você pode renomear os estados clicando duas vezes sobre eles.

**Passo 4: Criar Transições entre Estados**

1. Conecte os estados no Animator Controller criando "transições" entre eles. Para fazer isso, clique com o botão direito no estado de origem, escolha "Make Transition" e conecte-o ao estado de destino.

2. Configurar as condições de transição. Por exemplo, você pode definir uma condição para a transição de "Idle" para "Run" com base na velocidade do objeto.

**Passo 5: Criar Animações**

1. Crie as animações para cada estado. Para isso, selecione um estado no Animator Controller e abra a janela de animação.

2. No painel de animação, você pode criar e editar animações. Você pode usar o Animation Window para animar as propriedades do objeto, como posição, rotação e escala.

**Passo 6: Atribuir Animador ao Objeto**

1. No Inspector do objeto, você deve atribuir o Animator Controller ao componente "Animator" no objeto.

**Passo 7: Controlar as Animações por Script (Opcional)**

Se você deseja controlar as animações por meio de scripts, pode usar funções como `SetTrigger`, `SetBool`, `SetFloat`, etc., no script associado ao objeto para ativar transições entre estados.

Agora, o objeto deve ser capaz de reproduzir animações com base em transições e estados configurados no Animator Controller. Certifique-se de testar as animações na Unity para verificar se tudo está funcionando conforme o esperado.
