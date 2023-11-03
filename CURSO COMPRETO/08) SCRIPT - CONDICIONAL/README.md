# SCRIPT - CONDICIONAL
O uso de estruturas condicionais como "if" e "else" é fundamental para controlar o fluxo do seu programa em C#. Além disso, para trocar animações por script na Unity, você precisará acessar o componente Animator associado ao seu objeto. Vou explicar o básico de como usar "if" e "else" e como trocar animações por script:

**Estruturas Condicionais (if e else):**

No C#, "if" e "else" são usados para tomar decisões com base em condições. Aqui está uma estrutura de exemplo:

```csharp
int idade = 20;

if (idade < 18)
{
    // Executado se a condição for verdadeira (idade < 18)
    Debug.Log("Você é menor de idade.");
}
else
{
    // Executado se a condição for falsa (idade >= 18)
    Debug.Log("Você é maior de idade.");
}
```

**Trocar Animações por Script:**

Para trocar animações por script na Unity, você precisará do componente "Animator" associado ao objeto. Aqui estão os passos básicos:

**1. Acesso ao Componente Animator:**

Certifique-se de que o objeto tenha um componente "Animator" associado. Você pode adicioná-lo ao objeto na hierarquia da Unity.

**2. Referência ao Componente Animator:**

Dentro do seu script, você deve criar uma referência ao componente Animator. Normalmente, isso é feito declarando uma variável pública do tipo "Animator":

```csharp
public Animator meuAnimator;
```

**3. Trocar a Animação:**

Você pode usar o método "SetTrigger" para acionar uma transição de animação com base em um parâmetro definido no Animator:

```csharp
if (algumaCondicao)
{
    meuAnimator.SetTrigger("NomeDoGatilho");
}
```

Aqui, "NomeDoGatilho" é o nome do gatilho que você definiu no Animator. A transição de animação associada a esse gatilho será acionada quando a condição for verdadeira.

**Exemplo de Troca de Animação por Script:**

Suponha que você tenha um Animator com uma transição de "Idle" para "Run" e um gatilho chamado "ComeceACorrer". Você pode usar o script a seguir para iniciar a animação de corrida quando alguma condição for atendida:

```csharp
using UnityEngine;

public class TrocaDeAnimacao : MonoBehaviour
{
    public Animator meuAnimator;

    void Start()
    {
        // Inicialmente, o objeto está no estado "Idle"
        // Inicie a animação de corrida quando a condição for verdadeira
        if (algumaCondicao)
        {
            meuAnimator.SetTrigger("ComeceACorrer");
        }
    }
}
```

Lembre-se de que você deve atribuir o componente Animator ao campo "meuAnimator" no Inspector do objeto para que o script funcione corretamente.

Este é um exemplo simples de como usar "if", "else" e trocar animações por script na Unity. Com esses conceitos, você pode criar lógica de animação mais complexa e interativa para seus jogos.