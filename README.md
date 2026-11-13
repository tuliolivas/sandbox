# Sandbox — laboratório de C++ e gráficos 3D

Este repositório reúne pequenos programas e experimentos em C++ sobre computação gráfica, geometria, colisões, física e simulação 3D. Ele é um laboratório para estudar ideias por meio de código executável — não uma única aplicação pronta para produção.

O guia foi escrito para quem está começando ou já conhece o básico de programação e quer aprender como conceitos de C++ e matemática aparecem em demonstrações visuais. Muitos exemplos foram feitos para Windows e para ferramentas gráficas mais antigas; pode ser necessário ajustar o ambiente para executá-los hoje.

## Por onde começar

Se você nunca programou em C++, siga primeiro um curso ou material básico sobre variáveis, condicionais, repetições, funções, vetores (`std::vector`) e compilação. Depois, use este repositório como material de exploração: abra um exemplo, procure a função `main` ou `WinMain`, acompanhe os dados e altere uma coisa por vez.

Uma sequência possível para estudar os conceitos do repositório:

1. `testhull/` — pontos 3D e envoltória convexa;
2. `testgjk/` — colisão/separação entre formas convexas;
3. `testphys/` — corpos rígidos, gravidade e colisões;
4. `testcloth/` — tecido aproximado por pontos e molas;
5. `testsubdiv/` — malhas poligonais e subdivisão;
6. `testbsp/` — estruturas espaciais e operações booleanas em sólidos.

Essa ordem é uma sugestão didática, não uma dependência de compilação. Cada diretório é um projeto ou experimento separado.

## O que significam alguns termos?

- **Vértice:** ponto usado para descrever uma forma 3D.
- **Aresta:** segmento que liga dois vértices.
- **Triângulo/polígono:** face que forma a superfície de uma malha.
- **Malha (mesh):** conjunto de vértices e faces que representa um objeto.
- **Vetor 3D:** três valores, normalmente chamados `x`, `y` e `z`, para representar posição, direção ou velocidade.
- **Transformação:** operação que move, gira ou redimensiona um objeto.
- **Colisão:** teste para descobrir se formas se tocam ou se sobrepõem.
- **Simulação:** atualização da posição e do estado dos objetos ao longo do tempo.
- **Visualização:** desenho da geometria na janela para que seja possível observar o resultado.

Os arquivos `include/linalg.h`, `include/geometric.h`, `include/mesh.h` e `include/wingmesh.h` são bons lugares para encontrar tipos e operações reutilizados pelos exemplos. Por exemplo, `float3` representa um vetor com três componentes, e `int3` é usado em vários lugares para índices de triângulos.

## Estrutura do repositório

```text
sandbox/
├── README.md
├── LICENSE
├── .gitignore
├── sandbox.sln
├── remove_temp_files.sh
├── include/
├── bunnylod/
├── clothsimd/
├── derp/
├── jointdrive/
├── ploidfit/
├── test_reflect/
├── testbool/
├── testbsp/
├── testcloth/
├── testcnn/
├── testcov/
├── testdx/
├── testgjk/
├── testhull/
├── testicp/
├── testphys/
├── testrig/
├── testsubdiv/
├── testtrack/
└── voxblob/
```

### Arquivos na raiz

- **`sandbox.sln`** — solução do Visual Studio. Ela reúne projetos independentes, como `testhull`, `testcloth`, `testphys` e `testbsp`; não é um único programa com uma só função de entrada.
- **`.gitignore`** — lista arquivos temporários de compilação do Visual Studio que não devem ser versionados.
- **`remove_temp_files.sh`** — script de limpeza de arquivos temporários. Leia o conteúdo antes de executá-lo: ele remove diretórios e arquivos que correspondem aos caminhos e padrões escritos no script.
- **`LICENSE`** — licença MIT na raiz. Alguns arquivos também incluem avisos próprios de autoria ou licença; verifique os avisos do código e dos dados que pretende reutilizar.

### Pastas de código compartilhado

- **`include/`** — cabeçalhos reutilizados pelos projetos. Entre eles estão `linalg.h` (vetores, matrizes e operações matemáticas), `geometric.h` (operações geométricas), `mesh.h` (dados de malhas), `wingmesh.h` (malhas com conectividade de faces/arestas), `physics.h` (corpos rígidos e restrições) e `glwin.h`/`dxwin.h` (auxiliares de janela e desenho). Outros cabeçalhos cobrem, por exemplo, hull, GJK, imagens, JSON, XML e reflexão.

### Demonstrações e experimentos

- **`bunnylod/`** — demonstração de *progressive mesh*: simplifica uma malha de coelho removendo vértices e permite visualizar níveis de detalhe. `progmesh.cpp` implementa o algoritmo de redução; `bunnygut.cpp` prepara e desenha o modelo.
- **`clothsimd/`** — simulação de tecido em lote com operações SIMD (instruções que processam vários valores de uma vez). `clothsimd.cpp` compara caminhos de simulação e apresenta uma cena gráfica. O próprio código registra limitações e dependências de hardware/instruções; não é o primeiro exemplo recomendado para iniciantes.
- **`derp/`** — demonstra interpolação de poses usando quatérnios duais. Uma pose combina posição e orientação; a demonstração anima objetos entre duas poses.
- **`jointdrive/`** — exemplo de personagem articulado tipo *ragdoll*. Corpos rígidos conectados por juntas tentam acompanhar uma animação, limitados pelo torque configurado.
- **`ploidfit/`** — gera uma nuvem de pontos parabólica e ajusta uma superfície quadrática aos pontos. Também demonstra alinhamento por eixos principais e curvaturas.
- **`test_reflect/`** — demonstra reflexão de dados para exibir e alterar parâmetros do programa em um formulário HTML no navegador. O exemplo inicia um servidor local na porta `12345`; use-o apenas em ambiente controlado e não exponha o serviço publicamente sem revisar sua segurança.
- **`testbool/`** — demonstra operações booleanas em sólidos (por exemplo, subtrair formas) usando estruturas BSP; reutiliza código de `testbsp/`.
- **`testbsp/`** — compila malhas em árvores BSP (*Binary Space Partitioning*, ou particionamento binário do espaço) e demonstra operações CSG, como união e interseção, além de modos de visualização das células e planos.
- **`testcloth/`** — demonstra um tecido feito de pontos conectados por molas. `testcloth.cpp` cria a cena, chama a simulação de `springnet.h` e desenha o resultado; é possível alternar o modo de arame com `w` e mover pontos com o mouse.
- **`testcnn/`** — testa uma rede neural convolucional com XOR e com o conjunto MNIST de dígitos manuscritos. Os arquivos de dados MNIST não estão incluídos: o código espera que sejam obtidos separadamente e colocados nesta pasta. Consulte os comentários no início de `testcnn.cpp` para os nomes esperados.
- **`testcov/`** — demonstra covariância e eixos principais de uma nuvem de pontos, desenhando um elipsoide alinhado a esses eixos. Barra de espaço cria outra nuvem; o mouse permite interagir com os pontos.
- **`testdx/`** — exemplo pequeno de renderização de malhas usando a camada DirectX do projeto (`dxwin.h`/`dxshaders.h`). É específico do ambiente Windows e da configuração DirectX disponível.
- **`testgjk/`** — visualiza o algoritmo GJK, usado para testar separação/contato entre objetos convexos. A demonstração gera duas nuvens de pontos, calcula seus cascos convexos e desenha informações de separação.
- **`testhull/`** — gera pontos aleatórios e mostra a envoltória convexa (*convex hull*) que os contém. Permite alterar o limite de vértices e observar a geometria.
- **`testicp/`** — demonstra ICP (*Iterative Closest Point*), um método que procura alinhar dados geométricos por correspondências entre pontos e planos.
- **`testphys/`** — demonstra física de corpos rígidos: caixas e outras formas caem, colidem e recebem restrições. A barra de espaço inicia/pausa a simulação; `r` reinicia os objetos.
- **`testrig/`** — carrega e simula um modelo articulado usando um arquivo `.chr`. A pasta inclui `default_hand.chr` e um `readme.txt` que identifica a origem pública do modelo.
- **`testsubdiv/`** — carrega `EntireBody.obj` e demonstra subdivisão de malha (o código chama `WingMeshSubDiv` repetidamente), além de permitir selecionar e editar vértices.
- **`testtrack/`** — exemplo experimental de rastreamento de um objeto a partir de pontos de profundidade. Gera amostras, compara-as com um modelo rígido e atualiza a pose física.
- **`voxblob/`** — demonstra uma superfície editável armazenada em uma grade de voxels e convertida em malha por uma técnica relacionada a *marching cubes*. No exemplo, as teclas `b` e `r` removem e restauram partes da superfície.

Os nomes de algumas pastas começam com `test`, mas isso não significa necessariamente que sejam testes automatizados. Em muitos casos, são aplicações de demonstração interativas com janela gráfica.

## Ferramentas e compatibilidade

Os projetos são majoritariamente C++ e a solução `sandbox.sln` foi criada para Visual Studio. A solução declara Visual Studio 2015 (versão 14) e vários projetos usam o toolset `v140`; isso indica uma base antiga. Uma versão atual do Visual Studio pode precisar dos componentes de compatibilidade correspondentes, ou de ajustes nos arquivos de projeto.

Os exemplos usam APIs gráficas legadas do Windows, incluindo OpenGL e DirectX em diferentes projetos. Portanto:

- comece por um computador Windows com Visual Studio e os componentes C++ instalados;
- use a solução para selecionar e compilar um projeto específico;
- espere que alguns projetos precisem de configuração adicional ou não compilem sem atualização;
- não presuma que um comando genérico `g++` funcione: vários exemplos dependem de cabeçalhos e APIs do Windows e não possuem um sistema de build multiplataforma.

## Compilar um exemplo pelo Visual Studio

1. Instale o Visual Studio com a carga de trabalho **Desenvolvimento para desktop com C++**.
2. Clone o repositório e abra `sandbox.sln`.
3. No Gerenciador de Soluções, escolha um projeto de demonstração, por exemplo `testhull` ou `testphys`.
4. Selecione a configuração `Debug` para investigar o código ou `Release` para execução mais rápida.
5. Selecione a plataforma disponível (`Win32` ou `x64`) e compile o projeto escolhido.
6. Execute o programa e observe os controles exibidos na janela ou no código-fonte.

A solução tem configurações Win32 e x64, mas nem todos os projetos necessariamente oferecem ou suportam ambas. Para encontrar os controles, procure as atribuições a `keyboardfunc` e as mensagens `PrintString` no arquivo principal do projeto.

### Pré-requisitos específicos

- **`testcnn/`:** requer os quatro arquivos de dados MNIST indicados nos comentários de `testcnn.cpp`; eles não vêm neste repositório.
- **`testrig/`:** o modelo `default_hand.chr` está incluído.
- **Projetos gráficos:** podem exigir componentes Windows/DirectX/OpenGL compatíveis com o código legado.

## Como ler uma demonstração

Ao abrir um projeto, tente esta ordem:

1. **Ache o ponto de entrada.** Procure `main(...)` ou `WinMain(...)`. É onde o programa começa.
2. **Identifique os dados.** Procure `std::vector<float3>`, `Mesh`, `WingMesh`, `RigidBody` ou estruturas semelhantes.
3. **Localize o ciclo principal.** Em aplicações interativas, procure `while (glwin.WindowUp())` ou `while (dxwin.WindowUp())`. Esse ciclo lê interação, atualiza a simulação e desenha a cena repetidamente.
4. **Siga uma função de cada vez.** Por exemplo, em `testphys/testphys.cpp`, `PhysicsUpdate(...)` atualiza a física e as funções de desenho mostram os corpos.
5. **Faça uma alteração pequena.** Mude uma dimensão, posição ou parâmetro, compile novamente e compare o resultado.

Se algo não compilar, leia a primeira mensagem de erro e verifique qual cabeçalho, biblioteca, plataforma ou arquivo de dados está faltando. Evite mudar vários parâmetros ao mesmo tempo: assim fica mais fácil descobrir a causa.

## Conceitos de C++ úteis para este código

- **`.h` e `#include`:** arquivos de cabeçalho declaram ou implementam tipos e funções reutilizados. Por exemplo, `#include "physics.h"` permite usar as estruturas e funções da simulação física.
- **`std::vector<T>`:** lista que pode crescer; é usada para guardar pontos, vértices, triângulos e corpos.
- **`struct` e `class`:** agrupam dados e funções. `RigidBody`, em `include/physics.h`, representa um corpo rígido.
- **Referência (`T&`):** permite acessar um objeto existente sem copiá-lo. Ponteiros (`T*`) também aparecem para representar objetos opcionais ou ligações entre corpos.
- **Laço de atualização:** o programa altera posições e velocidades em pequenos passos de tempo; depois atualiza a imagem para mostrar o estado novo.

## Matemática 3D que ajuda

Não é necessário dominar toda a matemática antes de abrir o código. Estes tópicos ajudam a entender gradualmente:

1. coordenadas cartesianas e vetores 2D/3D;
2. comprimento de um vetor e normalização;
3. produto escalar (`dot`) e produto vetorial (`cross`);
4. matrizes e transformações de posição;
5. rotações e quatérnios (`float4` usado como quatérnio em vários exemplos);
6. triângulos, normais, malhas e planos;
7. colisões, restrições e integração no tempo.

Tente encontrar essas operações em exemplos concretos. `testgjk/testgjk.cpp`, por exemplo, usa pontos e cascos convexos; `testphys/testphys.cpp` cria corpos e chama o solucionador físico; `testcov/testcov.cpp` calcula e desenha eixos principais.

## Limitações e cuidados

- O repositório é uma coleção de experimentos independentes, com diferentes idades e estilos; não há garantia de que todos compilem sem ajustes em ferramentas atuais.
- A solução organiza vários projetos do Visual Studio, mas não há um build genérico para compilar tudo em qualquer sistema operacional.
- Alguns exemplos precisam de dados externos, como o MNIST usado em `testcnn/`.
- A raiz inclui uma licença MIT, mas também existem avisos particulares em arquivos de terceiros ou em demonstrações específicas. Leia os avisos aplicáveis antes de redistribuir código ou dados.
- `test_reflect` abre um serviço HTTP local para controle do exemplo. Não o publique na internet sem uma revisão de segurança.
- `remove_temp_files.sh` executa comandos de remoção. Inspecione o script e confirme o diretório antes de usá-lo.

## Licença

A raiz do repositório contém uma licença MIT. Consulte também os cabeçalhos e avisos dos arquivos específicos, especialmente ao reutilizar trechos, demonstrações ou dados que possam ter termos próprios.

## Resumo

Use este repositório como um laboratório visual: comece por uma demonstração pequena, encontre seu ponto de entrada, descubra que dados ela manipula e acompanhe o ciclo de atualização e desenho. Depois, conecte o que observou aos conceitos de C++, vetores, malhas, transformações, colisão e física 3D.
