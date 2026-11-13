# Sandbox

Bem-vindo(a) ao repositório `sandbox`.

Este projeto é um conjunto de experimentos, protótipos e pequenos programas em C++ focados em áreas como:

- computação gráfica
- física real-time
- detecção de colisão
- geometria 3D
- simulação de tecido/roupa
- algoritmos de matemática aplicada
- visão computacional e aprendizado de máquina experimental

Em outras palavras, este repositório funciona como um laboratório pessoal para testar ideias, algoritmos e técnicas em programação e simulação 3D.

## Quem é este repositório para?

Ele é especialmente útil para:

- estudantes de programação iniciando em C++
- pessoas que querem aprender por exemplo prático
- desenvolvedores interessados em gráficos, física e matemática computacional
- quem gosta de estudar algoritmos pequenos em um ambiente experimental

Este não é um projeto de aplicação grande ou pronto para produção. Ele é mais parecido com um "caderno de experimentos".

## Estrutura do repositório

```text
sandbox/
├── .gitignore
├── LICENSE
├── README.md
├── sandbox.sln               # solução do Visual Studio
├── remove_temp_files.sh      # script auxiliar
├── include/                  # bibliotecas/headers compartilhados
├── bunnylod/                 # experimento relacionado a modelos 3D / bunny
├── clothsimd/                # simulação de tecido em SIMD
├── derp/                     # experimento de teste/variação
├── jointdrive/               # simulação de juntas/rigs
├── ploidfit/                 # experimentos de ajuste/fit
├── test_reflect/              # testes de reflexão
├── testbool/                 # testes booleanos / operações geométricas
├── testbsp/                  # testes de BSP (Binary Space Partitioning)
├── testcloth/                # testes de simulação de tecido
├── testcnn/                  # experimentos com CNN / redes neurais
├── testcov/                  # cobertura / cálculo de covariância 
├── testdx/                   # testes com DirectX
├── testgjk/                  # teste de algoritmo GJK
├── testhull/                 # convex hull / envoltória convexa
├── testicp/                  # ICP (Iterative Closest Point)
├── testphys/                 # testes de física
├── testrig/                  # testes de rig / esqueletos
├── testsubdiv/               # subdivisão de superfícies
├── testtrack/                # rastreamento / tracking
├── voxblob/                  # blobs / voxels / volume
└── ...
```

## O que você pode aprender aqui

Este repositório costuma incluir exemplos de:

- estruturas de dados 3D
- matrizes e transformações geométricas
- colisões entre objetos
- otimização de desempenho
- simulação de roupa e corpos deformáveis
- algoritmos de física para jogos e simulação
- processamento geométrico e análise de malhas
- aprendizado de máquina e visão computacional em esquema experimental

## Pré-requisitos

Como o repositório é feito em C++, você precisará de:

- um compilador C++ moderno
- o Visual Studio (recomendado, considerando o `sandbox.sln`)
- conhecimento básico em:
  - variáveis
  - funções
  - classes e objetos
  - ponteiros e referências
  - vetores e matrizes

Em alguns diretórios, pode haver dependências específicas de DirectX ou bibliotecas de renderização.

## Como compilar e rodar

### Opção 1: Visual Studio (recomendado)

1. Abra o arquivo `sandbox.sln`.
2. Escolha a configuração desejada (Debug/Release).
3. Compile a solução.
4. Execute um dos projetos de teste dentro da solução.

### Opção 2: compilação manual

Se você estiver usando outra IDE ou linha de comando, pode ser necessário compilar cada projeto separadamente, dependendo do diretório que você quiser testar.

Exemplo geral:

```bash
g++ -std=c++17 main.cpp -o programa
./programa
```

Mas vale lembrar: muitos destes exemplos podem depender de configurações específicas e bibliotecas extras, então o Visual Studio costuma ser a maneira mais simples de testar o repositório.

## Como estudar este projeto

Se você é iniciante ou está em nível intermediário, a melhor forma de usar este repositório é:

### 1. Comece por um exemplo simples

Escolha um diretório pequeno, como `testbool`, `testhull` ou outro que tenha menos dependências visuais.

### 2. Entenda a ideia do problema

Pergunte:

- o que esse programa está tentando simular?
- quais dados ele usa?
- como a entrada é representada?
- qual é o resultado final?

### 3. Leia o código em etapas

Em vez de ler tudo de uma vez, tente:

- identificar funções
- entender estruturas e classes
- rastrear o fluxo principal
- localizar o ponto de entrada do programa

### 4. Modifique aos poucos

Experimente:

- trocar constantes
- alterar parâmetros de simulação
- mudar a geometria
- adicionar logs para acompanhar o comportamento

Isso ajuda a aprender melhor do que apenas copiar código.

## Dicas para aprender mais rápido

- entenda matemáticas básicas: vetores, matrizes, transformações, ângulos
- compreenda o papel de coordenadas e escala em gráficos 3D
- pratique debug em C++ com prints e testes simples
- compare exemplos de diferentes diretórios para ver padrões semelhantes
- tente reescrever partes pequenas do código em um projeto seu

## Diretórios importantes

### `include/`

Normalmente contém cabeçalhos e utilitários compartilhados entre os testes.

### `testphys/`

Geralmente contém experimentos focados em física e simulação.

### `testcloth/`

Indica implementações de simulação de tecido e deformação.

### `testbsp/`

Está relacionado a BSP (Binary Space Partitioning), usado em colisão e particionamento espacial.

### `testdx/`

Contém testes envolvendo DirectX, comum em aplicações gráficas Windows.

### `testcnn/`

Área voltada a redes neurais e experimentos de visão computacional.

## Observações importantes

- Este repositório é experimental.
- Nem todos os projetos precisam ser executados ao mesmo tempo.
- Alguns diretórios podem depender de bibliotecas específicas e de um ambiente Windows.
- O código pode ser antigo, acadêmico ou parcialmente não documentado.

Essas características são comuns em repositórios de experimentação e não devem assustar — na verdade, são parte do aprendizado.

## Como começar de forma simples

Se você é estudante e quer aprender a partir deste projeto, a sequência recomendada é:

1. conhecer o básico de C++
2. abrir um diretório simples
3. entender as funções principais
4. compilar e rodar
5. alterar parâmetros
6. repetir com outro exemplo

## Licença

Este repositório inclui um arquivo `LICENSE`, então é recomendável lê-lo antes de reutilizar o código em projetos próprios.

## Resumo

`Sandbox` é um repositório de experimentos em C++ para quem quer aprender programação aplicada a gráficos, física, geometria e inteligência computacional de forma prática. Ele é mais um espaço de estudo do que uma aplicação finalizada.

Se você estiver começando, o melhor caminho é explorar poucos diretórios por vez, tentar entender o propósito de cada programa e, aos poucos, experimentar modificações.

## Próximos passos recomendados

- ler o arquivo `LICENSE`
- abrir um diretório pequeno
- localizar a função `main`
- compilar o projeto
- alterar um valor e observar o resultado

Com isso, você começará a entender melhor como esses exemplos funcionam na prática.

---

Se quiser, posso também criar uma versão mais curta, mais visual ou mais orientada para usuários totalmente iniciantes em C++. 
