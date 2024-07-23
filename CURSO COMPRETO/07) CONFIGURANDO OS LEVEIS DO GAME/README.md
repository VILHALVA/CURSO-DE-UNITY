# CONFIGURANDO OS LEVEIS DO GAME
Configurar níveis no seu jogo do dinossauro envolve a criação de diferentes níveis de dificuldade ou ambientes que mudam conforme o jogador avança. Vamos adicionar uma mecânica de níveis que aumenta a dificuldade ao longo do tempo e pode incluir diferentes tipos de obstáculos ou mudanças no ambiente.

## Passo 1: Configurar o Sistema de Níveis
1. **Criar uma Classe `LevelManager`:**
   - Crie um novo script chamado `LevelManager` na pasta "Scripts".
   - Adicione o seguinte código:

```csharp
using UnityEngine;

public class LevelManager : MonoBehaviour
{
    public float levelDuration = 30f; // Duração de cada nível em segundos
    public float speedIncrease = 1f; // Aumento de velocidade a cada nível
    public ObstacleSpawner obstacleSpawner; // Referência ao script do Spawner de obstáculos
    private float levelTimer = 0f;
    private int currentLevel = 1;

    void Start()
    {
        levelTimer = levelDuration;
    }

    void Update()
    {
        levelTimer -= Time.deltaTime;
        if (levelTimer <= 0f)
        {
            AdvanceLevel();
        }
    }

    void AdvanceLevel()
    {
        currentLevel++;
        obstacleSpawner.IncreaseDifficulty(speedIncrease);
        levelTimer = levelDuration;
        Debug.Log("Level Up! Current Level: " + currentLevel);
    }
}
```

2. **Modificar o Script `ObstacleSpawner`:**
   - Adicione um método para aumentar a dificuldade ao script de geração de obstáculos (supondo que o nome do script seja `ObstacleSpawner`):

```csharp
using UnityEngine;
using System.Collections;

public class ObstacleSpawner : MonoBehaviour
{
    public GameObject[] obstaclePrefabs;
    public float spawnDelayMin = 1f;
    public float spawnDelayMax = 3f;
    public Transform spawnPoint;
    public float difficultyIncreaseRate = 0.1f;
    public float minSpawnDelay = 0.5f;
    private float currentSpawnDelayMin;
    private float currentSpawnDelayMax;

    void Start()
    {
        currentSpawnDelayMin = spawnDelayMin;
        currentSpawnDelayMax = spawnDelayMax;
        StartCoroutine(SpawnObstacles());
    }

    public void IncreaseDifficulty(float increaseAmount)
    {
        currentSpawnDelayMin = Mathf.Max(minSpawnDelay, currentSpawnDelayMin - increaseAmount);
        currentSpawnDelayMax = Mathf.Max(minSpawnDelay, currentSpawnDelayMax - increaseAmount);
    }

    private IEnumerator SpawnObstacles()
    {
        while (true)
        {
            float spawnDelay = Random.Range(currentSpawnDelayMin, currentSpawnDelayMax);
            yield return new WaitForSeconds(spawnDelay);
            SpawnObstacle();
        }
    }

    private void SpawnObstacle()
    {
        int obstacleIndex = Random.Range(0, obstaclePrefabs.Length);
        Instantiate(obstaclePrefabs[obstacleIndex], spawnPoint.position, Quaternion.identity);
    }
}
```

## Passo 2: Configurar o Ambiente de Nível
1. **Adicionar Variáveis para o Ambiente:**
   - No script `LevelManager`, você pode adicionar variáveis para controlar mudanças no ambiente (como a cor do fundo ou o tipo de terreno):

```csharp
using UnityEngine;

public class LevelManager : MonoBehaviour
{
    public float levelDuration = 30f;
    public float speedIncrease = 1f;
    public ObstacleSpawner obstacleSpawner;
    public Color[] backgroundColors;
    public SpriteRenderer background;
    private float levelTimer = 0f;
    private int currentLevel = 1;

    void Start()
    {
        levelTimer = levelDuration;
        UpdateBackgroundColor();
    }

    void Update()
    {
        levelTimer -= Time.deltaTime;
        if (levelTimer <= 0f)
        {
            AdvanceLevel();
        }
    }

    void AdvanceLevel()
    {
        currentLevel++;
        obstacleSpawner.IncreaseDifficulty(speedIncrease);
        levelTimer = levelDuration;
        UpdateBackgroundColor();
        Debug.Log("Level Up! Current Level: " + currentLevel);
    }

    void UpdateBackgroundColor()
    {
        if (backgroundColors.Length > 0)
        {
            int colorIndex = currentLevel % backgroundColors.Length;
            background.color = backgroundColors[colorIndex];
        }
    }
}
```

2. **Configurar o Background:**
   - Crie um `GameObject` com um `SpriteRenderer` para servir como o fundo do jogo.
   - Arraste o `SpriteRenderer` para o campo `background` no `Inspector` do `LevelManager`.
   - Adicione diferentes cores ao array `backgroundColors` no `Inspector` do `LevelManager`.

## Passo 3: Configurar e Testar na Cena
1. **Adicionar o `LevelManager` à Cena:**
   - Crie um `GameObject` vazio na cena e nomeie-o como "LevelManager".
   - Adicione o script `LevelManager` ao `GameObject`.

2. **Configurar Referências:**
   - Arraste o `ObstacleSpawner` para o campo correspondente no `LevelManager`.
   - Arraste o `SpriteRenderer` do fundo para o campo `background` no `LevelManager`.

3. **Testar o Jogo:**
   - Salve a cena.
   - Clique em "Play" no Unity Editor para testar o jogo.

