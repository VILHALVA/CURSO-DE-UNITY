# CODIFICANDO
## Passo 1: Configurar o Projeto
1. **Criar um Novo Projeto:**
   - Abra o Unity Hub, clique em "New" e selecione um template 2D.
   - Dê um nome ao seu projeto, como "DinoGame" e clique em "Create".

2. **Configurar a Cena:**
   - A cena padrão ("SampleScene") será carregada. Renomeie-a para "MainScene" se desejar.

## Passo 2: Importar Recursos
Você precisará de alguns recursos gráficos para o dinossauro, o solo e os obstáculos. Você pode criar gráficos simples ou encontrar sprites online. Para este exemplo, usaremos gráficos básicos.

1. **Criar Sprites:**
   - Crie ou baixe sprites para o dinossauro, o solo e os cactos.
   - Importe esses sprites para o Unity arrastando-os para a pasta "Assets" no Project Explorer.

## Passo 3: Configurar a Cena
1. **Adicionar o Solo:**
   - Arraste o sprite do solo para a cena.
   - Posicione o solo na parte inferior da tela.
   - Adicione um componente `Box Collider 2D` para detectar colisões.
   - Marque a opção "Is Trigger" se não quiser que o solo bloqueie os objetos.

2. **Adicionar o Dinossauro:**
   - Arraste o sprite do dinossauro para a cena.
   - Adicione um componente `Rigidbody 2D` para permitir que ele seja afetado pela física.
   - Adicione um componente `Box Collider 2D` para detectar colisões.

3. **Adicionar o Script de Movimento do Dinossauro:**
   - Crie uma pasta "Scripts" na pasta "Assets".
   - Clique com o botão direito na pasta "Scripts" e selecione "Create > C# Script". Nomeie o script como "DinoController".
   - Abra o script e adicione o seguinte código:

```csharp
using UnityEngine;

public class DinoController : MonoBehaviour
{
    public float jumpForce = 10f;
    private Rigidbody2D rb;
    private bool isGrounded = true;

    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space) && isGrounded)
        {
            rb.velocity = Vector2.up * jumpForce;
            isGrounded = false;
        }
    }

    private void OnCollisionEnter2D(Collision2D collision)
    {
        if (collision.gameObject.CompareTag("Ground"))
        {
            isGrounded = true;
        }
    }
}
```

4. **Adicionar o Script ao Dinossauro:**
   - Arraste o script "DinoController" para o dinossauro na cena.

5. **Adicionar o Solo como Ground:**
   - Selecione o objeto do solo na cena e adicione a tag "Ground" ao objeto.

## Passo 4: Adicionar Obstáculos
1. **Adicionar o Cacto:**
   - Arraste o sprite do cacto para a cena.
   - Adicione um componente `Box Collider 2D`.
   - Adicione um script para mover os obstáculos:

```csharp
using UnityEngine;

public class Obstacle : MonoBehaviour
{
    public float speed = 5f;

    void Update()
    {
        transform.Translate(Vector2.left * speed * Time.deltaTime);

        if (transform.position.x < -10)
        {
            Destroy(gameObject);
        }
    }
}
```

2. **Adicionar o Script ao Cacto:**
   - Arraste o script "Obstacle" para o cacto na cena.

3. **Criar um Spawner de Obstáculos:**
   - Crie um GameObject vazio chamado "Spawner" na cena.
   - Posicione o Spawner à direita da tela.
   - Crie um script "Spawner" e adicione o seguinte código:

```csharp
using UnityEngine;

public class Spawner : MonoBehaviour
{
    public GameObject obstaclePrefab;
    public float spawnRate = 2f;
    private float nextSpawn = 0f;

    void Update()
    {
        if (Time.time > nextSpawn)
        {
            Instantiate(obstaclePrefab, transform.position, Quaternion.identity);
            nextSpawn = Time.time + spawnRate;
        }
    }
}
```

4. **Adicionar o Script ao Spawner:**
   - Arraste o script "Spawner" para o GameObject "Spawner".
   - No Inspector do Spawner, arraste o prefab do cacto para o campo "Obstacle Prefab".

## Passo 5: Testar o Jogo
1. **Salvar e Executar:**
   - Salve a cena.
   - Clique em "Play" no Unity Editor para testar o jogo.

