# TEXTURAS E NORMAL MAP
## CONCEITO:
Texturas e normal maps são elementos importantes no desenvolvimento de jogos em 3D, pois contribuem para a aparência visual e realista de objetos e superfícies. Vou explicar o que são e como você pode usá-los na Unity:

1. **Texturas**:
   - **O que são**: Texturas são imagens 2D que são aplicadas a superfícies 3D para dar detalhes visuais, como cor, padrões, rugosidades, etc. Elas são essenciais para criar aparências realistas em modelos 3D.
   - **Uso na Unity**: Para aplicar uma textura a um objeto na Unity, siga estes passos:
     1. Importe sua textura (uma imagem) para o projeto Unity.
     2. Crie um material e atribua a textura a esse material.
     3. Aplique o material ao objeto na hierarquia Unity ou no componente Renderer no Inspector.
     4. Ajuste as propriedades do material, como a escala da textura e a transparência, conforme necessário.

2. **Normal Maps**:
   - **O que são**: Normal maps são usados para criar a ilusão de detalhes 3D em superfícies planas. Eles alteram a forma como a luz interage com um objeto, criando sombras e realces que não existem fisicamente.
   - **Uso na Unity**: Para aplicar um normal map a um material na Unity:
     1. Importe o normal map como uma textura.
     2. Crie ou edite um material.
     3. Na seção "Normal Map" do material, atribua a textura normal map.
     4. Ajuste a intensidade e escala do normal map conforme necessário. Valores negativos podem inverter a direção das normais.

Normal maps são particularmente úteis para adicionar detalhes de superfície, como relevos, rugosidades e arranhões, sem aumentar significativamente a complexidade do modelo 3D.

Ao usar texturas e normal maps na Unity, você pode melhorar a qualidade visual dos seus jogos, tornando-os mais imersivos e realistas. É importante lembrar que o desempenho do jogo também é afetado pelo uso excessivo de texturas e normal maps de alta resolução, então é importante otimizar seus ativos para garantir que o jogo funcione bem em diferentes plataformas.

## TUTORIAL:
Configurar texturas e criar normal maps no Photoshop é uma parte importante do processo de desenvolvimento de jogos em 3D. Vou explicar como configurar texturas e criar normal maps usando o Photoshop:

**Configuração de Textura:**

1. **Crie ou Abra uma Textura**:
   - Abra o Photoshop e crie um novo documento com as dimensões desejadas para a textura.
   - Ou abra uma imagem existente que servirá como base para a textura.

2. **Edite a Textura**:
   - Use as ferramentas do Photoshop para editar e criar a textura desejada. Você pode pintar, adicionar detalhes, ajustar cores, aplicar filtros, etc.

3. **Salve a Textura**:
   - Após editar a textura, vá em "Arquivo" -> "Salvar Como" e escolha o formato de imagem adequado (por exemplo, PNG ou TGA) para preservar a qualidade e a transparência, se necessário.

**Criação de Normal Maps:**

Para criar um normal map a partir de uma textura no Photoshop, você pode seguir os seguintes passos:

1. **Duplique a Textura**:
   - Duplique a camada da textura para manter uma cópia original.

2. **Converta a Textura em Escala de Cinza**:
   - Vá em "Imagem" -> "Modo" -> "Escala de Cinza" para converter a camada em tons de cinza.

3. **Ajuste o Contraste**:
   - Aumente o contraste para realçar os detalhes de altura. Você pode fazer isso em "Imagem" -> "Ajustes" -> "Brilho/Contraste" ou usando outras ferramentas de ajuste.

4. **Desfoque Gaussiano**:
   - Aplique um leve desfoque gaussiano à camada para suavizar os detalhes e criar uma textura mais suave. Vá em "Filtro" -> "Desfoque" -> "Desfoque Gaussiano".

5. **Aplicação de Normalização Azul**:
   - Normalmente, o canal azul da textura em escala de cinza é usado para a direção da normal map. Copie o canal azul da camada e cole-o como uma nova camada.

6. **Inversão do Canal Azul**:
   - Inverta as cores do canal azul para que as áreas mais claras representem alturas positivas e as áreas mais escuras representem alturas negativas.

7. **Aplicação do Normal Map**:
   - Com a camada do canal azul invertido selecionada, vá em "Editar" -> "Definir como Normal Map" para converter a camada em um normal map.

8. **Salve o Normal Map**:
   - Vá em "Arquivo" -> "Salvar Como" e escolha o formato de imagem necessário para o normal map.

Agora você tem um normal map criado a partir da textura original no Photoshop. Esse normal map pode ser aplicado a modelos 3D na Unity para dar a ilusão de detalhes de superfície tridimensionais. Certifique-se de ajustar a intensidade do normal map conforme necessário na Unity para obter o efeito desejado.