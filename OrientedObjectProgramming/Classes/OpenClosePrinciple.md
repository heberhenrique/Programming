# Princípio Abert-Fechado

**Aviso! Este texto abaixo é uma tradução do artigo de Robert C. Martin feito em seu blog [Clean Coder](https://blog.cleancoder.com/uncle-bob/2014/05/12/TheOpenClosedPrinciple.html)**

O texto abaixo pode conter modificações feitas por mim a fim de melhorar os exemplos apresentados. Para conferir o artigo original basta clicar no [link](https://blog.cleancoder.com/uncle-bob/2014/05/12/TheOpenClosedPrinciple.html)

<hr>

## Sobre o conceito

Em 1988 Bertrand Meyer definiu um dos princípios mais importantes da engenharia de software. O Princípio Aberto Fechado (OCP). Em seu livro [Object Oriented Software Construction](https://www.amazon.com/Object-Oriented-Software-Construction-Prentice-Hall-International/dp/0136290493)¹, ele disse:

> - Um módulo será dito **`aberto`** se estiver disponível para extensão.
> Por exemplo, deve ser possível adicionar campos às estruturas de dados que contém ou novos elementos ao conjunto de  funções que executa.
> - Um módulo será dito **`fechado`** se estiver disponível para uso por outros módulos.
> Isso pressupõe que o módulo recebeu uma descrição bem definida e estável (a interface no sentido de ocultar informações).
> No caso de um módulo de linguagem de programação, um módulo fechado é aquele que pode ser compilado e armazenado em uma biblioteca, para  uso de outros.
> No caso de um módulo de design ou especificação, fechar um módulo significa simplesmente tê-lo aprovado pela gerência,
> adicioná-lo ao repositório oficial do projeto de itens de software aceitos (geralmente chamado de projeto _baseline_) e publicar sua interface para benefício de outros projetistas.

Esta definição é obviamente antiga. Hoje em dia muitas linguagens não exigem que os módulos sejam compilados. E obter as especificações do módulo aprovadas pela gerência cheira a uma mentalidade em [cascata](https://www.fm2s.com.br/modelo-cascata/). Ainda assim, a essência de um grande princípio ainda brilha através dessas velhas palavras. A saber:

> Você deve ser capaz de estender o comportamento de um sistema _`sem ter que modificá-lo`_.

Pense nisso com muito cuidado. Se os comportamentos de todos os módulos em seu sistema puderem ser estendidos, sem modificá-los, você poderá adicionar novos recursos a esse sistema sem modificar nenhum código antigo. Os recursos seriam adicionados apenas escrevendo um novo código.

Além disso, como nenhum código antigo foi alterado, ele não precisaria ser recompilado e, portanto, não precisaria ser reimplantado. Adicionar um novo recurso envolveria deixar o código antigo no lugar e apenas implantar o novo código, talvez em um novo jar, dll ou gem.

E isso deve lhe dar uma dica sobre o que um jar, dll ou gem realmente deve ser. Eles devem ser recursos isoláveis!

## Isso é um absurdo?

À primeira leitura, o princípio aberto e fechado pode parecer absurdo. Nossas linguagens e nossos designs geralmente não permitem que novos recursos sejam escritos, compilados e implantados separadamente do resto do sistema. Raramente nos encontramos em um lugar onde o sistema atual está fechado para modificação e ainda pode ser estendido com novos recursos.

De fato, geralmente adicionamos novos recursos fazendo um grande número de alterações em todo o corpo do código existente. Sabíamos que isso era ruim muito antes de Martin Fowler escrever o livro² que o rotulou de [`Cirurgia de espingarda`](https://en.wikipedia.org/wiki/Shotgun_surgery), mas ainda o fazemos.

Ah, mas há Eclipse, ou IntelliJ, ou Visual Studio, ou Vim, ou Text Mate, ou Minecraft ou… Bem, você entendeu. Há uma grande quantidade de ferramentas que podem ser facilmente estendidas sem modificá-las ou reimplantá-las. Nós os estendemos escrevendo plugins.

Os sistemas de plug-in são a consumação final, a apoteose, do Princípio Aberto-Fechado. Eles são uma prova positiva de que sistemas abertos-fechados são possíveis, úteis e imensamente poderosos.

Como esses sistemas conseguiram fechar suas regras de negócios primárias para modificação e ainda deixar todo o aplicativo aberto para ser estendido? Simples. Eles acreditavam no OCP e usavam as ferramentas do projeto orientado a objetos para separar a política de alto nível dos detalhes de baixo nível. Eles gerenciaram cuidadosamente suas dependências, invertendo aquelas que cruzavam os limites arquitetonicamente significativos na direção errada.

Afinal, a maneira de obter uma arquitetura de plugin é garantir que todas as dependências dentro do plugin apontem para o sistema; e que nada no sistema aponta para os plugins. O sistema não conhece os plugins. Os plugins conhecem o sistema.

## Arquitetura de Plugin

E se o design de seus sistemas fosse baseado em plugins, como Vim, Emacs, Minecraft ou Eclipse? E se você pudesse conectar o Banco de Dados ou a GUI. E se você pudesse conectar novos recursos e desconectar os antigos. E se o comportamento do seu sistema fosse amplamente controlado pela configuração de seus plugins? Que poder isso lhe daria? Quão fácil seria adicionar novos recursos ou novas interfaces de usuário ou novas interfaces de máquina/máquina? Quão fácil seria adicionar ou remover SOA. Quão fácil seria adicionar ou remover REST? Quão fácil seria adicionar ou remover Spring, Rails, Hibernate, Oracle ou…

Bem, acho que você entendeu meu significado. Quando suas regras de negócios fundamentais são o núcleo de uma arquitetura de plug-in, você nunca está vinculado a um determinado conjunto de recursos, interface, banco de dados, estrutura ou qualquer outra coisa.

## Conclusão

Ouvi dizer que o OCP é errado, impraticável, inviável e não é para programadores reais com trabalho real a fazer. A ascensão das arquiteturas de plugins deixa claro que essas visões são um completo absurdo. Pelo contrário, uma arquitetura de plug-in forte provavelmente será o aspecto mais importante dos futuros sistemas de software.

<hr>

¹ Object Oriented Software Construction, 1st. ed. Bertrand Meyer, Prentice Hall, 1988 <br>
² Refactoring, Martin Fowler, Addison Wesley, 1999