# SCRIPT - VARIAVEIS E OBJETOS
Programação em C# é uma habilidade fundamental para criar jogos na Unity. Vou explicar o básico de scripts em C# na Unity para ajudá-lo a começar:

**1. Criar um Script:**

1. No Unity, vá para a pasta "Assets" no Project no Unity e clique com o botão direito do mouse.
2. Selecione "Create" -> "C# Script" para criar um novo script. Dê um nome apropriado ao seu script, como "PlayerController".

**2. Editar um Script:**

1. Clique duas vezes no script para abri-lo em um editor de código, como o Visual Studio ou o Visual Studio Code. Você também pode usar editores de texto, como o Notepad++, se preferir.

**3. Estrutura Básica de um Script em C#:**

Aqui está uma estrutura de script C# simples na Unity:

```csharp
using UnityEngine;

public class NomeDoScript : MonoBehaviour
{
    // Variáveis para armazenar informações
    public int minhaVariavelInteira = 5;
    public float minhaVariavelFlutuante = 2.5f;
    public string minhaVariavelString = "Hello, Unity!";
    
    // Método de inicialização
    void Start()
    {
        // Código a ser executado quando o objeto é criado
    }

    // Método de atualização
    void Update()
    {
        // Código a ser executado a cada quadro (frame)
    }
}
```

**4. Variáveis:**

- Variáveis são usadas para armazenar informações. Elas podem ser de diferentes tipos, como inteiros, números de ponto flutuante, strings, etc.

**5. Métodos:**

- Métodos são blocos de código que realizam ações específicas. Os métodos "Start()" e "Update()" são comuns na Unity. "Start()" é chamado uma vez quando o objeto é criado, e "Update()" é chamado a cada quadro (frame) do jogo.

**6. Eventos de Colisão (Exemplo):**

```csharp
void OnCollisionEnter(Collision collision)
{
    // Código a ser executado quando o objeto colide com outro objeto
}
```

**7. Referenciar Componentes da Unity:**

Você pode referenciar componentes da Unity, como Transform, Rigidbody, Collider, etc., dentro do seu script. Por exemplo:

```csharp
public Transform minhaTransform;
public Rigidbody meuRigidbody;

void Start()
{
    minhaTransform = GetComponent<Transform>();
    meuRigidbody = GetComponent<Rigidbody>();
}
```

**8. Depuração (Debugging):**

Você pode usar a função "Debug.Log()" para imprimir informações no console da Unity para depuração:

```csharp
void Start()
{
    Debug.Log("O jogo começou!");
}

void Update()
{
    Debug.Log("Tempo decorrido: " + Time.time);
}
```

**9. Anexar um Script a um Objeto:**

Para usar seu script, anexe-o a um objeto na hierarquia da Unity. Selecione o objeto, vá para o componente "Add Component", pesquise o nome do script e adicione-o.

Essas são noções básicas para começar com scripts em C# na Unity. À medida que você se aprofunda, aprenderá conceitos mais avançados, como eventos, classes personalizadas, funções de colisão, animações e muito mais. A prática constante e a exploração de recursos de aprendizado, como tutoriais e documentação, ajudarão você a se tornar um programador de jogos mais habilidoso.