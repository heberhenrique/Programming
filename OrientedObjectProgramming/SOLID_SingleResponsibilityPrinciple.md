# Princípio de Responsabilidade Única

**Aviso! Este texto abaixo é uma tradução do artigo de Robert C. Martin feito em seu blog [Clean Coder](https://blog.cleancoder.com/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html)**

O texto abaixo pode conter modificações feitas por mim a fim de melhorar os exemplos apresentados. Para conferir o artigo original basta clicar no [link](https://blog.cleancoder.com/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html)

<hr>

## **Nascimento do conceito**

Em 1972, David L. Parnas publicou um artigo clássico intitulado ["Sobre os critérios a serem usados ​​na decomposição de sistemas em módulos"](https://www.cs.umd.edu/class/spring2003/cmsc838p/Design/criteria.pdf). Apareceu na edição de dezembro das Comunicações da ACM, Volume 15, Número 12.

Neste artigo, Parnas comparou duas estratégias diferentes para decompor e separar a lógica em um algoritmo simples. O artigo é uma leitura fascinante, e eu recomendo fortemente que você o estude. Sua conclusão, em parte, é a seguinte:

> _“Tentamos demonstrar com esses exemplos que quase sempre é incorreto iniciar a decomposição de um sistema em módulos com base em um fluxograma._ <br>
> _Em vez disso, propomos que se comece com uma lista de decisões de projeto difíceis ou decisões de projeto que provavelmente mudarão._ <br>
> _Cada módulo é então projetado para esconder tal decisão dos outros.”_

Eu adicionei a ênfase na penúltima frase. A conclusão de Parnas foi que os módulos deveriam ser separados com base, pelo menos em parte, na forma como podem mudar.

Dois anos depois, Edsger Dijkstra escreveu outro artigo clássico intitulado ["Sobre o papel do pensamento científico"](https://www.cs.utexas.edu/users/EWD/ewd04xx/EWD447.PDF), em que introduziu o termo: **A Separação de Preocupações**.

As décadas de 1970 e 1980 foram um período fértil para os princípios da arquitetura de software. **Programação estruturada** e design estavam na moda. Durante esse tempo, as noções de Acoplamento e Coesão foram introduzidas por Larry Constantine e ampliadas por Tom DeMarco, Meilir Page-Jones e muitos outros.

No final da década de 1990, tentei consolidar essas noções em um princípio, que chamei de: Princípio da Responsabilidade Única. (Tenho a vaga sensação de que roubei o nome desse princípio de Bertrand Meyer, mas não pude confirmar isso.)

O Princípio de Responsabilidade Única (SRP) afirma que cada módulo de software deve ter um e apenas um motivo para mudar. Isso soa bem e parece se alinhar com a formulação de Parnas. No entanto, levanta a questão: o que define uma razão para mudar?

Algumas pessoas se perguntam se uma correção de bug se qualifica como motivo para mudar. Outros se perguntam se as refatorações são razões para mudar. Essas questões podem ser respondidas apontando o acoplamento entre o termo “motivo para mudar” e “responsabilidade”.

Certamente o código não é responsável por correções de bugs ou refatoração. Essas coisas são de responsabilidade do programador, não do programa. Mas se for esse o caso, pelo que o programa é responsável? Ou, talvez, uma pergunta melhor seja: a quem o programa é responsável? Melhor ainda: a quem o desenho do programa deve responder?

Imagine uma organização empresarial típica. Há um CEO no topo. Reportando-se a esse CEO estão os executivos de nível C: o CFO, COO e CTO, entre outros. O CFO é responsável por controlar as finanças da empresa. O COO é responsável por gerenciar as operações da empresa. E o CTO é responsável pela infraestrutura e desenvolvimento de tecnologia dentro da empresa.

## **No código**

Agora considere este pedaço de código:

```csharp
public class Employee {
  public double CalculatePay();
  public bool Save();
  public string ReportHours();
}
```

- O método `CalculatePay` implementa os algoritmos que determinam quanto um determinado funcionário deve ser pago, com base no contrato desse funcionário, status, horas trabalhadas etc.
- O método `Save` armazena os dados gerenciados pelo objeto `Employee` no banco de dados corporativo.
- O método `ReportHours` retorna uma string que é anexada a um relatório que os auditores usam para garantir que os funcionários estejam trabalhando o número apropriado de horas e estejam recebendo a remuneração apropriada.

Agora, qual desses executivos C-Level subordinados ao CEO é responsável por especificar o comportamento do método `CalculatePay`? Qual deles seria demitido¹ pelo CEO se esse método fosse catastroficamente mal especificado? Claramente a resposta é o CFO. Especificar o pagamento dos funcionários é uma responsabilidade financeira. Se todos os funcionários fossem pagos em dobro por um ano porque alguém na organização do CFO especificou incorretamente as regras de cálculo do pagamento, o CFO provavelmente seria demitido.

Um executivo de nível C diferente é responsável por especificar o formato e o conteúdo da string retornada do método `ReportHours`. Esse executivo gerencia os auditores e revisores, e isso é uma responsabilidade de operações. Portanto, se houvesse uma especificação incorreta catastrófica desse relatório, o COO seria demitido.

Finalmente, deve ser óbvio qual dos executivos de nível C seria demitido se houvesse uma especificação incorreta catastrófica do método de salvamento. Se o banco de dados corporativo fosse corrompido por uma especificação errada tão horrível, o CTO provavelmente seria demitido.

Portanto, é lógico que, quando forem feitas alterações no algoritmo dentro do método `CalculatePay`, a solicitação dessas alterações se originará da organização liderada pelo CFO. Da mesma forma, será a organização do COO que solicitará alterações no método `ReportHours` e a organização dos CTOs que solicitará alterações no método `Save`.

E isso chega ao cerne do Princípio da Responsabilidade Única. _**Este princípio é sobre as pessoas**_.

Ao escrever um módulo de software, você quer ter certeza de que, quando as alterações forem solicitadas, essas alterações só possam se originar de uma única pessoa, ou melhor, de um único grupo de pessoas fortemente acopladas representando uma única função de negócios estreitamente definida. Você deseja isolar seus módulos das complexidades da organização como um todo e projetar seus sistemas de forma que cada módulo seja responsável (responda) às necessidades de apenas uma função de negócios.

Por quê? Porque não queremos que o COO seja demitido porque fizemos uma alteração solicitada pelo CTO. Nada aterroriza mais nossos clientes e gerentes do que descobrir que um programa funcionou mal de uma maneira que, do ponto de vista deles, não tinha relação com as alterações solicitadas. Se você alterar o método `CalculatePay` e inadvertidamente quebrar o método `ReportHours`, então o COO começará a exigir que você _nunca mais altere o método `CalculatePay` novamente_.

Imagine que você levou seu carro a um mecânico para consertar um vidro elétrico quebrado. Ele liga para você no dia seguinte dizendo que está tudo resolvido. Quando você pega seu carro, descobre que a janela funciona bem; mas o carro não pega. Não é provável que você retorne a esse mecânico porque ele é claramente um idiota.

É assim que clientes e gerentes se sentem quando quebramos coisas com as quais eles se importam e que _não_ nos pediram para mudar.

Esta é a razão pela qual não colocamos `SQL` em páginas web. Esta é a razão pela qual não geramos `HTML` nos módulos que computam os resultados. Esta é a razão pela qual as regras de negócios não devem conhecer o esquema do banco de dados. Esta é a razão pela qual _nós separamos as preocupações_.

Outra formulação para o Princípio da Responsabilidade Única é:

> _Reúna as coisas que mudam pelas mesmas razões_. <br>
> Separe as coisas que mudam por diferentes razões.

Se você pensar sobre isso, perceberá que essa é apenas outra maneira de definir **coesão** e **acoplamento**. Queremos **aumentar a coesão** entre as coisas que mudam pelas mesmas razões e queremos **diminuir o acoplamento entre as coisas** que mudam por diferentes razões.

No entanto, ao refletir sobre esse princípio, lembre-se de que as razões da mudança são as _**pessoas**_. São as _**pessoas**_ que pedem mudanças. E você não quer confundir essas pessoas, ou você mesmo, misturando o código que muitas pessoas diferentes se importam por diferentes razões.

<hr>

¹Estou usando um pouco de hipérbole aqui. Executivos de nível C geralmente não são demitidos por pequenas especificações incorretas. Ainda assim, não está fora do campo de possibilidades e enfatiza que as organizações que se reportam a esses executivos se preocupam com diferentes preocupações.