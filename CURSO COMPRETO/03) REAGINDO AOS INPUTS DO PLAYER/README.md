# REAGINDO AOS INPUTS DO PLAYER
Para fazer o jogo reagir aos inputs do jogador, precisamos lidar com eventos como pular, abaixar e detectar colisões. Vamos melhorar o script do dinossauro para reagir a mais inputs e adicionar algumas funcionalidades adicionais.

## Passo 1: Melhorar o Script do Dinossauro
Vamos aprimorar o script `DinoController` para lidar com mais ações do jogador.

1. **Script `DinoController` Atualizado:**

```csharp
using UnityEngine;

public class DinoController : MonoBehaviour
{
    public float jumpForce = 10f;
    public float crouchSpeed = 2f;
    private Rigidbody2D rb;
    private BoxCollider2D boxCollider;
    private Vector2 originalSize;
    private bool isGrounded = true;
    private bool isCrouching = false;

    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
        boxCollider = GetComponent<BoxCollider2D>();
        originalSize = boxCollider.size;
    }

    void Update()
    {
        HandleJump();
        HandleCrouch();
    }

    void HandleJump()
    {
        if (Input.GetKeyDown(KeyCode.Space) && isGrounded && !isCrouching)
        {
            rb.velocity = Vector2.up * jumpForce;
            isGrounded = false;
        }
    }

    void HandleCrouch()
    {
        if (Input.GetKeyDown(KeyCode.DownArrow))
        {
            boxCollider.size = new Vector2(boxCollider.size.x, boxCollider.size.y / 2);
            isCrouching = true;
        }
        else if (Input.GetKeyUp(KeyCode.DownArrow))
        {
            boxCollider.size = originalSize;
            isCrouching = false;
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

## Passo 2: Configurar Animações (Opcional)
Para uma experiência mais completa, você pode adicionar animações para o dinossauro. Vamos supor que você tenha sprites para diferentes estados (correr, pular, abaixar).

1. **Adicionar Componentes de Animação:**
   - Adicione um `Animator` ao dinossauro.
   - Crie uma `Animator Controller` na pasta "Assets" e configure os diferentes estados de animação (Run, Jump, Crouch).

2. **Atualizar o Script para Lidar com Animações:**

```csharp
using UnityEngine;

public class DinoController : MonoBehaviour
{
    public float jumpForce = 10f;
    public float crouchSpeed = 2f;
    private Rigidbody2D rb;
    private BoxCollider2D boxCollider;
    private Animator animator;
    private Vector2 originalSize;
    private bool isGrounded = true;
    private bool isCrouching = false;

    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
        boxCollider = GetComponent<BoxCollider2D>();
        animator = GetComponent<Animator>();
        originalSize = boxCollider.size;
    }

    void Update()
    {
        HandleJump();
        HandleCrouch();
        UpdateAnimations();
    }

    void HandleJump()
    {
        if (Input.GetKeyDown(KeyCode.Space) && isGrounded && !isCrouching)
        {
            rb.velocity = Vector2.up * jumpForce;
            isGrounded = false;
        }
    }

    void HandleCrouch()
    {
        if (Input.GetKeyDown(KeyCode.DownArrow))
        {
            boxCollider.size = new Vector2(boxCollider.size.x, boxCollider.size.y / 2);
            isCrouching = true;
        }
        else if (Input.GetKeyUp(KeyCode.DownArrow))
        {
            boxCollider.size = originalSize;
            isCrouching = false;
        }
    }

    void UpdateAnimations()
    {
        animator.SetBool("isGrounded", isGrounded);
        animator.SetBool("isCrouching", isCrouching);
        animator.SetFloat("yVelocity", rb.velocity.y);
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

## Passo 3: Melhorar a Detecção de Colisões
Para uma detecção de colisões mais precisa e ações subsequentes, como terminar o jogo ou reduzir pontos de vida, você pode adicionar mais lógica ao seu script.

1. **Atualizar o Script para Tratar Colisões com Obstáculos:**

```csharp
using UnityEngine;

public class DinoController : MonoBehaviour
{
    public float jumpForce = 10f;
    public float crouchSpeed = 2f;
    private Rigidbody2D rb;
    private BoxCollider2D boxCollider;
    private Animator animator;
    private Vector2 originalSize;
    private bool isGrounded = true;
    private bool isCrouching = false;

    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
        boxCollider = GetComponent<BoxCollider2D>();
        animator = GetComponent<Animator>();
        originalSize = boxCollider.size;
    }

    void Update()
    {
        HandleJump();
        HandleCrouch();
        UpdateAnimations();
    }

    void HandleJump()
    {
        if (Input.GetKeyDown(KeyCode.Space) && isGrounded && !isCrouching)
        {
            rb.velocity = Vector2.up * jumpForce;
            isGrounded = false;
        }
    }

    void HandleCrouch()
    {
        if (Input.GetKeyDown(KeyCode.DownArrow))
        {
            boxCollider.size = new Vector2(boxCollider.size.x, boxCollider.size.y / 2);
            isCrouching = true;
        }
        else if (Input.GetKeyUp(KeyCode.DownArrow))
        {
            boxCollider.size = originalSize;
            isCrouching = false;
        }
    }

    void UpdateAnimations()
    {
        animator.SetBool("isGrounded", isGrounded);
        animator.SetBool("isCrouching", isCrouching);
        animator.SetFloat("yVelocity", rb.velocity.y);
    }

    private void OnCollisionEnter2D(Collision2D collision)
    {
        if (collision.gameObject.CompareTag("Ground"))
        {
            isGrounded = true;
        }
        else if (collision.gameObject.CompareTag("Obstacle"))
        {
            // Handle collision with obstacle (e.g., end game, reduce health)
            Debug.Log("Collided with an obstacle!");
            // Add your game over logic here
        }
    }
}
```

## Passo 4: Ajustar os Obstáculos
Certifique-se de que os obstáculos tenham a tag "Obstacle" e ajustem seus `Box Collider 2D` para detecção de colisões precisa.

## Passo 5: Testar e Refinar
Teste o jogo frequentemente para garantir que todos os inputs e reações estejam funcionando conforme o esperado. Ajuste os valores de `jumpForce`, `crouchSpeed`, e a configuração dos colliders conforme necessário para melhorar a jogabilidade.

