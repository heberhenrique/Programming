# Princípio de Substituição de Liskov

**Aviso! Este texto abaixo é uma tradução de vários artigos. No final temos as referências dos textos usados para compor esse documento.**

## Introdução

O princípio de substituição de Liskov (LSP) é uma definição particular de uma relação de `subtipagem`, chamada de [`subtipagem comportamental forte`](https://en.wikipedia.org/wiki/Behavioral_subtyping), que foi inicialmente introduzida por [Barbara Liskov](https://en.wikipedia.org/wiki/Barbara_Liskov) em um discurso de conferência de 1988 intitulado _`Abstração e hierarquia de dados`_. Ele é baseado no conceito de "substituibilidade" - um princípio na programação orientada a objetos que afirma que um objeto (assim como uma classe) e um subobjeto (como uma classe que estende/herda a primeira classe) devem ser intercambiáveis sem quebrar o programa. É uma relação semântica e não meramente sintática, porque pretende garantir a interoperabilidade semântica de tipos em uma hierarquia, tipos de objetos em particular. Barbara Liskov e [Jeannette Wing](https://en.wikipedia.org/wiki/Jeannette_Wing) descreveram o princípio sucintamente em um artigo de 1994 da seguinte forma¹:

> _Se q(x) é uma propriedade demonstrável dos objetos x de tipo T, então q(y) deve ser verdadeiro para objetos y de tipo S onde S é subtipo de T.

No mesmo artigo, Liskov e Wing detalharam sua noção de `subtipagem comportamental` em uma extensão da [`lógica de Hoare`](https://en.wikipedia.org/wiki/Hoare_logic), que guarda certa semelhança com o `projeto por contrato` de Bertrand Meyer na medida em que considera a interação da subtipagem com pré-condições, pós-condições e invariantes.

## Princípio

A noção de Liskov de um subtipo comportamental define uma noção de substituibilidade para objetos; isto é, se S é um subtipo de T, então objetos do tipo T em um programa podem ser substituídos por objetos do tipo S sem alterar nenhuma das propriedades desejáveis ​​desse programa (por exemplo, [corretude](https://en.wikipedia.org/wiki/Correctness_(computer_science))).

A subtipagem comportamental é uma noção mais forte do que a subtipagem típica de funções definidas na teoria de tipos, que se baseia apenas na `contravariância` dos tipos de parâmetro e na covariância do tipo de retorno. A subtipagem comportamental é indecidível em geral: se q é a propriedade "método para x sempre termina", então é impossível para um programa (por exemplo, um compilador) verificar se ela é verdadeira para algum subtipo S de T, mesmo que q seja válido para T. No entanto, o princípio é útil para pensar como definir hierarquias de classes.

O princípio de substituição de Liskov impõe alguns requisitos padrão em assinaturas que foram adotadas em linguagens de programação orientadas a objetos mais recentes (geralmente no nível de classes em vez de tipos; veja [`subtipagem nominal vs. estrutural`](https://en.wikipedia.org/wiki/Subtyping#Subtyping_schemes) para a distinção):

- Contravariância de tipos de parâmetro de método no subtipo.
- Covariância de tipos de retorno de método no subtipo.
- `Novas exceções não podem ser lançadas pelos métodos no subtipo`, exceto se forem subtipos de exceções lançadas pelos métodos do supertipo (classe pai).

Além dos requisitos de assinatura, o subtipo deve atender a várias condições comportamentais. Eles são detalhados em uma terminologia semelhante à da metodologia de design por contrato, levando a algumas restrições sobre como os contratos podem interagir com a herança:

- As pré-condições não podem ser reforçadas no subtipo.
- As pós-condições não podem ser enfraquecidas no subtipo.
- As invariantes ​​devem ser preservadas no subtipo.
- Restrição do histórico (a "regra do histórico"). Os objetos são considerados modificáveis ​​apenas por meio de seus métodos (encapsulamento). Como os subtipos podem introduzir métodos que não estão presentes no supertipo, a introdução desses métodos pode permitir mudanças de estado no subtipo que não são permitidas no supertipo. A restrição de histórico proíbe isso. Foi o novo elemento introduzido por Liskov e Wing. Uma violação dessa restrição pode ser exemplificada definindo um ponto mutável como um subtipo de um ponto imutável. Isso é uma violação da restrição de histórico, porque na história do ponto imutável, o estado é sempre o mesmo após a criação, portanto, não pode incluir a história de um ponto mutável em geral. Os campos adicionados ao subtipo podem, no entanto, ser modificados com segurança porque não são observáveis ​​pelos métodos do supertipo. Assim, pode-se definir um círculo com centro imutável e raio mutável como um subtipo de um ponto imutável sem violar a restrição histórica.