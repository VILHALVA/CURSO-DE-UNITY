# CURSO DE UNITY
👨‍⚖️UNITY É UMA ENGINE DE DESENVOLVIMENTO DE JOGOS E APLICATIVOS MULTIPLATAFORMA. É AMPLAMENTE UTILIZADA NA INDÚSTRIA DE JOGOS PARA CRIAR JOGOS INTERATIVOS EM 2D E 3D. ALÉM DISSO, TAMBÉM PODE SER USADA PARA DESENVOLVER APLICATIVOS PARA DISPOSITIVOS MÓVEIS, REALIDADE VIRTUAL E REALIDADE AUMENTADA.

[![GitHub Repo stars](https://img.shields.io/badge/VILHALVA-GITHUB-03A9F4?logo=github)](https://github.com/VILHALVA) 
[![GitHub Repo stars](https://img.shields.io/badge/VEJA%20OS-VIDEOS-03A9F4?logo=youtube)](https://www.youtube.com/@vilhalva100/search?query=Unity)

[![GitHub Repo stars](https://img.shields.io/badge/VEJA-DOCUMENTAÇÃO-03A9F4?logo=google)](https://docs.unity.com/) 
[![GitHub Repo stars](https://img.shields.io/badge/LINGUAGEM%20DE-PROGRAMAÇÃO-03A9F4?logo=google)](https://github.com/VILHALVA/CURSO-DE-C-SHARP)
<br>

[![GitHub Repo stars](https://img.shields.io/badge/-PLAYLIST%20DO%20YOUTUBE-blueviolet)](https://youtube.com/playlist?list=PL4nQezgDb6K402DAybKB9ZR5NfWGtH445&si=4DJLFMuwh6gl3R3h)

<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQmOXKgyGaKd1MKhA7Ny_HveUuB5g4zuQ-RtQ&usqp=CAU" align="center" width="280"> <br>

![](https://i.imgur.com/waxVImv.png)

# CONCEITO:
A Unity é uma poderosa plataforma de desenvolvimento de jogos e aplicativos 3D/2D. Vou citar alguns conceitos básicos para que você possa se familiarizar com a plataforma:

1. **GameObject (Objeto de Jogo)**:
   - Um GameObject é a unidade fundamental em Unity. Pode ser qualquer objeto no seu jogo, como personagens, inimigos, câmeras, luzes, etc. Eles são a base para a criação de elementos no seu mundo de jogo.

2. **Component (Componente)**:
   - Componentes são partes que você pode adicionar a um GameObject para dar a ele funcionalidades específicas. Por exemplo, um componente de "Rigidbody" pode ser adicionado a um GameObject para torná-lo físico e interagir com a física do mundo do jogo.

3. **Script (Roteiro)**:
   - Os scripts em Unity são escritos em C# (ou outra linguagem de script suportada) e são usados para programar comportamentos de GameObjects. Você pode adicionar scripts aos GameObjects para controlar movimento, interações, lógica do jogo, etc.

Aqui está um exemplo simples de um script C# que faz um GameObject mover-se na direção do eixo X quando pressionamos uma tecla:

```csharp
using UnityEngine;

public class MovimentoSimples : MonoBehaviour
{
    public float velocidade = 5.0f;

    void Update()
    {
        float movimentoHorizontal = Input.GetAxis("Horizontal");
        Vector3 direcao = new Vector3(movimentoHorizontal, 0, 0);
        transform.Translate(direcao * velocidade * Time.deltaTime);
    }
}
```

Neste exemplo:

- `Update()` é um método que é chamado a cada quadro.
- `Input.GetAxis("Horizontal")` obtém a entrada do teclado no eixo horizontal.
- `transform.Translate()` move o GameObject na direção especificada.

# CARACTERISTICAS:
## Características Positivas:
1. **Ampla Comunidade e Suporte**: Unity tem uma grande comunidade de desenvolvedores, fóruns, tutoriais e documentação disponíveis. Isso torna mais fácil encontrar ajuda e recursos on-line quando você está enfrentando desafios.

2. **Multiplataforma**: A Unity suporta a exportação de jogos para várias plataformas, incluindo Windows, macOS, iOS, Android, consoles, Web e VR. Isso permite que os desenvolvedores alcancem uma ampla base de usuários.

3. **Gráficos de Alta Qualidade**: A Unity oferece um sistema gráfico poderoso que permite criar jogos com gráficos impressionantes e realistas. Ela suporta efeitos visuais avançados, shaders personalizados e renderização de alta qualidade.

4. **Facilidade de Aprendizado**: A Unity é conhecida por sua interface amigável e intuitiva, o que a torna uma escolha sólida para desenvolvedores iniciantes. Há também uma curva de aprendizado suave para programadores que já estão familiarizados com C#.

5. **Asset Store**: A Asset Store da Unity oferece uma ampla gama de ativos, como modelos 3D, texturas, scripts e plugins prontos para uso. Isso pode economizar muito tempo no desenvolvimento de jogos.

6. **Ferramentas de Colaboração**: A Unity oferece ferramentas de colaboração que facilitam o trabalho em equipe. Várias pessoas podem trabalhar no mesmo projeto simultaneamente, o que é útil para estúdios de desenvolvimento maiores.

## Características Negativas:
1. **Desempenho**: Em projetos complexos ou mal otimizados, a Unity pode enfrentar problemas de desempenho. O desenvolvedor precisa ser cuidadoso ao otimizar o código e os ativos para garantir um desempenho suave.

2. **Licenciamento**: A Unity tem diferentes tipos de licenças, e a versão gratuita possui algumas restrições. Os desenvolvedores podem precisar pagar taxas de licença, dependendo das necessidades do projeto.

3. **Tamanho dos Builds**: Os builds de jogos Unity tendem a ser maiores do que os de algumas outras engines. Isso pode ser um problema, especialmente para jogos móveis, onde o espaço é limitado.

4. **Atualizações Frequentes**: A Unity lança atualizações frequentes, o que pode ser positivo para manter a engine atualizada, mas também pode causar problemas de compatibilidade e exigir adaptação constante dos projetos.

5. **Recursos Pagos**: Alguns recursos avançados e serviços, como o Unity Pro, exigem pagamento adicional. Isso pode aumentar os custos de desenvolvimento.

6. **Curva de Aprendizado para Recursos Avançados**: Embora a Unity seja amigável para iniciantes, o uso eficaz de recursos avançados, como shaders personalizados e física complexa, pode ser desafiador e requer mais experiência.

