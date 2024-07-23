# GAME OVER 💥 CONFIGURANDO OS ESTADOS DO JOGO
Configurar um sistema de "Game Over" envolve várias etapas, incluindo a detecção de colisões fatais, a exibição de uma tela de "Game Over" e a capacidade de reiniciar o jogo. Vamos implementar isso passo a passo.

## Passo 1: Detectar Colisões Fatais
Já temos um script `DinoController` que detecta colisões. Vamos expandi-lo para lidar com o estado de "Game Over".

1. **Atualizar o Script `DinoController`:**

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

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
    private bool isGameOver = false;

    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
        boxCollider = GetComponent<BoxCollider2D>();
        animator = GetComponent<Animator>();
        originalSize = boxCollider.size;
    }

    void Update()
    {
        if (!isGameOver)
        {
            HandleJump();
            HandleCrouch();
            UpdateAnimations();
        }
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
            GameOver();
        }
    }

    private void GameOver()
    {
        isGameOver = true;
        animator.SetTrigger("GameOver");
        // Adicione mais lógica de game over aqui, como desativar movimentos e mostrar a tela de Game Over
    }
}
```

## Passo 2: Criar a Tela de "Game Over"
1. **Criar a UI de "Game Over":**
   - Vá para `GameObject` > `UI` > `Text` para adicionar um texto à sua cena. Nomeie-o como "GameOverText".
   - Posicione o texto no centro da tela e ajuste suas propriedades (fonte, tamanho, cor, etc.) para que ele diga "Game Over".
   - Desative o `GameOverText` no `Inspector` (desmarque a caixa ao lado do nome do objeto para desativá-lo).

2. **Criar um Script `GameManager`:**
   - Crie um novo script chamado "GameManager" na pasta "Scripts".
   - Adicione o seguinte código:

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;
using UnityEngine.UI;

public class GameManager : MonoBehaviour
{
    public GameObject gameOverText;
    public Text scoreText;
    private bool isGameOver = false;
    private float score = 0f;

    void Start()
    {
        gameOverText.SetActive(false);
        score = 0f;
    }

    void Update()
    {
        if (!isGameOver)
        {
            score += Time.deltaTime;
            scoreText.text = "Score: " + Mathf.FloorToInt(score).ToString();
        }

        if (isGameOver && Input.GetKeyDown(KeyCode.R))
        {
            RestartGame();
        }
    }

    public void GameOver()
    {
        isGameOver = true;
        gameOverText.SetActive(true);
    }

    private void RestartGame()
    {
        SceneManager.LoadScene(SceneManager.GetActiveScene().name);
    }
}
```

3. **Adicionar o `GameManager` à Cena:**
   - Crie um GameObject vazio na cena e nomeie-o como "GameManager".
   - Arraste o script `GameManager` para o `GameManager` no `Inspector`.
   - Arraste o objeto `GameOverText` para o campo `GameOverText` no `GameManager`.
   - Adicione um texto de pontuação (`UI` > `Text`), nomeie-o como "ScoreText" e arraste-o para o campo `ScoreText` no `GameManager`.

## Passo 3: Conectar Tudo
1. **Modificar o Script `DinoController` para Interagir com o `GameManager`:**

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

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
    private bool isGameOver = false;
    private GameManager gameManager;

    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
        boxCollider = GetComponent<BoxCollider2D>();
        animator = GetComponent<Animator>();
        originalSize = boxCollider.size;
        gameManager = FindObjectOfType<GameManager>();
    }

    void Update()
    {
        if (!isGameOver)
        {
            HandleJump();
            HandleCrouch();
            UpdateAnimations();
        }
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
            GameOver();
        }
    }

    private void GameOver()
    {
        isGameOver = true;
        animator.SetTrigger("GameOver");
        gameManager.GameOver();
    }
}
```

## Passo 4: Testar o Jogo
1. **Salvar e Executar:**
   - Salve a cena.
   - Clique em "Play" no Unity Editor para testar o jogo.

Agora, quando o dinossauro colidir com um obstáculo, o jogo deve exibir "Game Over" e parar de gerar inimigos e atualizar a pontuação. O jogador pode pressionar "R" para reiniciar o jogo.

