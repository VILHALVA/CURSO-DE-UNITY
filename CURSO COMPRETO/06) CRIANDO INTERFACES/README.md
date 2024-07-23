# CRIANDO INTERFACES
Criar interfaces de usuário (UI) é um passo essencial para tornar o jogo mais envolvente e interativo. No contexto do jogo do dinossauro, podemos criar interfaces para exibir a pontuação, um botão de "Reiniciar" e uma mensagem de "Game Over".

## Passo 1: Criar a Interface de Usuário
1. **Adicionar um Canvas:**
   - Vá para `GameObject` > `UI` > `Canvas` para criar um canvas na cena.
   - O Canvas será a raiz para todos os elementos da interface de usuário.

2. **Adicionar um Texto para Pontuação:**
   - No Canvas, vá para `GameObject` > `UI` > `Text` para adicionar um texto.
   - Nomeie este texto como "ScoreText".
   - Posicione o texto no canto superior direito da tela.
   - Ajuste o tamanho da fonte, a cor e o alinhamento conforme necessário.

3. **Adicionar um Texto para "Game Over":**
   - No Canvas, adicione outro texto (`GameObject` > `UI` > `Text`).
   - Nomeie este texto como "GameOverText".
   - Posicione-o no centro da tela.
   - Defina o texto como "Game Over" e ajuste o tamanho da fonte e a cor.
   - Desative este texto no `Inspector` (desmarque a caixa ao lado do nome do objeto para desativá-lo).

4. **Adicionar um Botão de "Reiniciar":**
   - No Canvas, vá para `GameObject` > `UI` > `Button` para adicionar um botão.
   - Nomeie este botão como "RestartButton".
   - Posicione-o abaixo do texto "Game Over".
   - Edite o texto do botão para "Reiniciar".
   - Desative este botão no `Inspector`.

## Passo 2: Criar o Script `GameManager`
Vamos melhorar o script `GameManager` para controlar a interface de usuário.

1. **Atualizar o Script `GameManager`:**

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;
using UnityEngine.UI;

public class GameManager : MonoBehaviour
{
    public GameObject gameOverText;
    public GameObject restartButton;
    public Text scoreText;
    private bool isGameOver = false;
    private float score = 0f;

    void Start()
    {
        gameOverText.SetActive(false);
        restartButton.SetActive(false);
        score = 0f;
    }

    void Update()
    {
        if (!isGameOver)
        {
            score += Time.deltaTime;
            scoreText.text = "Score: " + Mathf.FloorToInt(score).ToString();
        }
    }

    public void GameOver()
    {
        isGameOver = true;
        gameOverText.SetActive(true);
        restartButton.SetActive(true);
    }

    public void RestartGame()
    {
        SceneManager.LoadScene(SceneManager.GetActiveScene().name);
    }
}
```

## Passo 3: Configurar os Botões
1. **Adicionar Listener ao Botão de "Reiniciar":**
   - Selecione o botão "RestartButton" no `Inspector`.
   - No componente `Button`, clique em `+` para adicionar um novo evento ao `OnClick`.
   - Arraste o objeto `GameManager` para o campo `Object` no evento `OnClick`.
   - No menu suspenso, selecione `GameManager` > `RestartGame`.

## Passo 4: Conectar Tudo
1. **Ajustar o Script `DinoController`:**

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

## Passo 5: Testar o Jogo
1. **Salvar e Executar:**
   - Salve a cena.
   - Clique em "Play" no Unity Editor para testar o jogo.

