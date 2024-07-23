# CRIANDO SEU PRÓPRIO ALGORITMO PARA GERAR INIMIGOS
Criar seu próprio algoritmo para gerar inimigos no jogo do dinossauro do Google envolve alguns passos. A ideia principal é criar inimigos de forma aleatória e em intervalos de tempo variados, para manter o jogo desafiador. Vamos construir um script que faz isso.

## Passo 1: Criar um Prefab para o Inimigo
1. **Criar um Prefab do Cacto:**
   - Arraste o sprite do cacto para a cena.
   - Adicione um componente `Box Collider 2D` ao cacto.
   - Adicione um componente `Rigidbody 2D` ao cacto e marque `Gravity Scale` como 0, pois não queremos que o cacto caia.
   - Clique com o botão direito no cacto no Hierarchy e selecione "Prefab" > "Create Prefab". Salve-o na pasta "Assets/Prefabs".
   - Exclua o cacto da cena depois de criar o prefab.

## Passo 2: Criar o Script para Gerar Inimigos
Vamos criar um script para gerar inimigos em intervalos de tempo aleatórios.

1. **Criar o Script `EnemySpawner`:**
   - Crie uma pasta "Scripts" na pasta "Assets" se ainda não tiver uma.
   - Clique com o botão direito na pasta "Scripts" e selecione "Create > C# Script". Nomeie o script como "EnemySpawner".
   - Abra o script e adicione o seguinte código:

```csharp
using System.Collections;
using UnityEngine;

public class EnemySpawner : MonoBehaviour
{
    public GameObject enemyPrefab;
    public float spawnDelayMin = 1f;
    public float spawnDelayMax = 3f;
    public Transform spawnPoint;

    private void Start()
    {
        StartCoroutine(SpawnEnemies());
    }

    private IEnumerator SpawnEnemies()
    {
        while (true)
        {
            float spawnDelay = Random.Range(spawnDelayMin, spawnDelayMax);
            yield return new WaitForSeconds(spawnDelay);
            SpawnEnemy();
        }
    }

    private void SpawnEnemy()
    {
        Instantiate(enemyPrefab, spawnPoint.position, Quaternion.identity);
    }
}
```

## Passo 3: Configurar o Spawner na Cena
1. **Adicionar o Spawner à Cena:**
   - Crie um GameObject vazio na cena e nomeie-o como "EnemySpawner".
   - Posicione o `EnemySpawner` à direita da tela, fora da visão da câmera (por exemplo, `x = 10`).

2. **Adicionar o Script ao Spawner:**
   - Selecione o `EnemySpawner` no Hierarchy.
   - Arraste o script `EnemySpawner` para o `Inspector`.
   - Arraste o prefab do cacto (que você criou anteriormente) para o campo `Enemy Prefab` no `Inspector`.
   - Arraste o próprio `EnemySpawner` para o campo `Spawn Point` no `Inspector`.

## Passo 4: Testar o Algoritmo de Geração
1. **Salvar e Executar:**
   - Salve a cena.
   - Clique em "Play" no Unity Editor para testar o jogo.

Se tudo estiver configurado corretamente, os cactos começarão a aparecer à direita da tela em intervalos de tempo aleatórios, se movendo para a esquerda.

## Passo 5: Ajustes Finais e Melhorias
- **Ajustar Velocidade do Inimigo:**
  - Se os inimigos estão se movendo muito devagar ou muito rápido, ajuste a velocidade deles no script de movimento (Obstacle).

- **Variar Tipos de Inimigos:**
  - Para adicionar mais variedade, você pode criar diferentes tipos de inimigos e usar um array ou lista para armazená-los. No método `SpawnEnemy`, você pode escolher aleatoriamente um inimigo da lista para instanciar.

- **Adicionar Dificuldade Progressiva:**
  - Para aumentar a dificuldade ao longo do tempo, você pode diminuir os intervalos de tempo entre os spawns ou aumentar a velocidade dos inimigos conforme o jogo avança.

Aqui está uma versão aprimorada do script `EnemySpawner` que inclui dificuldade progressiva:

```csharp
using System.Collections;
using UnityEngine;

public class EnemySpawner : MonoBehaviour
{
    public GameObject[] enemyPrefabs;
    public float spawnDelayMin = 1f;
    public float spawnDelayMax = 3f;
    public Transform spawnPoint;
    public float difficultyIncreaseRate = 0.1f;
    public float minSpawnDelay = 0.5f;

    private void Start()
    {
        StartCoroutine(SpawnEnemies());
    }

    private IEnumerator SpawnEnemies()
    {
        float currentSpawnDelayMin = spawnDelayMin;
        float currentSpawnDelayMax = spawnDelayMax;

        while (true)
        {
            float spawnDelay = Random.Range(currentSpawnDelayMin, currentSpawnDelayMax);
            yield return new WaitForSeconds(spawnDelay);
            SpawnEnemy();

            // Aumentar a dificuldade
            currentSpawnDelayMin = Mathf.Max(minSpawnDelay, currentSpawnDelayMin - difficultyIncreaseRate * Time.deltaTime);
            currentSpawnDelayMax = Mathf.Max(minSpawnDelay, currentSpawnDelayMax - difficultyIncreaseRate * Time.deltaTime);
        }
    }

    private void SpawnEnemy()
    {
        int enemyIndex = Random.Range(0, enemyPrefabs.Length);
        Instantiate(enemyPrefabs[enemyIndex], spawnPoint.position, Quaternion.identity);
    }
}
```

