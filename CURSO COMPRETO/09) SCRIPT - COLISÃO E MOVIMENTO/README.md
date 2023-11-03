# SCRIPT - COLISÃO E MOVIMENTO
Aqui está um exemplo simples de script em C# para lidar com detecção de colisões e movimento em um objeto na Unity. Este script assume que você deseja mover um objeto usando as teclas de seta e detectar colisões com outros objetos. Você pode personalizar e expandir este script de acordo com suas necessidades específicas.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class MovimentoEColisao : MonoBehaviour
{
    public float velocidade = 5.0f; // Velocidade de movimento
    private Rigidbody rb;

    void Start()
    {
        // Obtém uma referência ao componente Rigidbody do objeto
        rb = GetComponent<Rigidbody>();
    }

    void Update()
    {
        // Obtém entrada do jogador para movimento
        float movimentoHorizontal = Input.GetAxis("Horizontal");
        float movimentoVertical = Input.GetAxis("Vertical");

        // Calcula a direção de movimento
        Vector3 direcao = new Vector3(movimentoHorizontal, 0.0f, movimentoVertical);

        // Aplica força ao objeto para movê-lo
        rb.AddForce(direcao * velocidade);
    }

    void OnCollisionEnter(Collision colisao)
    {
        // Se houver uma colisão com outro objeto
        if (colisao.gameObject.CompareTag("Inimigo"))
        {
            // Faça alguma ação, como destruir o inimigo ou perder o jogo
            Debug.Log("Colisão com inimigo!");
        }
    }
}
```

Neste script:

- `velocidade` é a velocidade de movimento do objeto.
- `rb` é uma referência ao componente Rigidbody do objeto para aplicar forças de movimento.
- No método `Start()`, obtemos uma referência ao componente Rigidbody.
- No método `Update()`, obtemos entrada do jogador usando `Input.GetAxis()` para controlar o movimento do objeto. Em seguida, aplicamos uma força ao objeto usando `rb.AddForce()` para movê-lo.
- O método `OnCollisionEnter()` é chamado quando há uma colisão com outro objeto. Você pode adicionar lógica específica para colisões aqui. Neste exemplo, verificamos se a colisão é com um objeto com a tag "Inimigo" e realizamos alguma ação em resposta à colisão.

Lembre-se de que este é um exemplo básico e pode ser expandido para atender às necessidades específicas do seu jogo. Certifique-se de ajustar o script e os valores de acordo com o seu cenário.