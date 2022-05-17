# **Lógica de Programação**

## **Um pouco de história**

Antes de pensar em sair desenvolvendo um programa de computador, primeiro é preciso entender porque os computadores foram criados. Falando de forma bem breve os computadores foram criados para resolverem problemas matemáticos desde seus primeiros 'rascunhos' como a máquina analítica de **Charles Babbage (1791-1871)**. Desde então muitos nomes passaram a aprimorar o computador de forma que ele fosse mais eficiente até chegar na forma que temos hoje.
Então de uma forma geral os computadores são facilitadores do nosso dia-a-dia.

## **Por trás dos programas de computador - Algorítimos**

Os programas de computadores são construídos através de códigos que chamados de algoritimos. Mas o que são algoritimos? Vejamos o que o dicinário tem como definição:

> ## **algoritmo** ## 
> *substantivo masculino*
>
> 1. **`MATEMÁTICA`** <br>
> sequência finita de regras, raciocínios ou operações que, aplicada a um número finito de dados, permite solucionar classes semelhantes de problemas.
> 2. **`INFORMÁTICA`** <br>
> conjunto das regras e procedimentos lógicos perfeitamente definidos que levam à solução de um problema em um número finito de etapas.
>

Ambas as definições acima nos dão uma ideia bem paracida do que é um algorítimo. Fazendo um paralelo com o mundo real podemos definir algorítimo como uma receita ou uma fórmula para resolver algo. Uma receita de bolo é de fato um algorítimo, pois ela nos dá o passo-a-passo de como transformar nossos ingredientes em um bolo, assim como a formula de um produto de beleza também pode ser considerado um algorítimo pois através dela é que chegamos ao produto final. Mas atenção, nem toda sequencia de procedimentos é um algoritimo, pois se eles não estiverem organizados de forma lógica não poderemos resolver nosso problema.

E o que é lógica? Mais um pouco de dicionário pra vocês:

> ## **lógica** ##
> *substantivo feminino*
>
> 1. **`FILOSOFIA`** <br>
> parte da filosofia que trata das formas do pensamento em geral (dedução, indução, hipótese, inferência etc.) e das operações intelectuais que visam à
> ***determinação do que é verdadeiro ou não**.
> 2. **`POR METONÍMIA`** <br>
> tratado, compêndio de lógica.
> 3. **`POR EXTENSÃO`** <br>
> *(da acp. 1)* maneira rigorosa de raciocinar. <br>
> "l. implacável"
> 4. **`POR EXTENSÃO`** <br>
> forma por que costuma raciocinar uma pessoa ou um grupo de pessoas ligadas por um fato de ordem social, psíquica, geográfica etc. <br>
> "a l. do louco"
> 5. **`POR EXTENSÃO`** <br>
> maneira por que necessariamente se encadeiam os acontecimentos, as coisas ou os elementos de natureza efetiva. <br>
> "a l. das paixões"
> 6. **`POR EXTENSÃO`** <br>
> encadeamento ***coerente** de alguma coisa que obedece a certas convenções ou regras. <br>
> "a l. do discurso musical"
> 7. **`INFORMÁTICA`** <br>
> organização e planejamento das instruções, **assertivas** etc. em um algoritmo, a fim de viabilizar a implantação de um programa.

A conclusão que podemos chegar é que a lógica é um conjunto de passos a serem dados que se estiverem organizados da maneira correta vão de fato resolver nosso problema. Voltemos a pensar no bolo que estávamos a fazer. Se eu misturar a farinha e a água e levar a geladeira eu vou ter qualquer coisa menos um bolo, da mesma forma que se eu misturar corretamente todos os tipos de ingredientes necessários mas não usar as porções corretas, certamente a receita não dará certo, logo não temos um algorítimo.

É igualmente importante perceber que lógica, matemática e filosofia estão intimamente ligadas. Os maiores matemáticos foram também as maiores referências no campo da filosofia a exemplo de Pitágoras que foi referência nas duas áreas.

## **Pensado de maneira lógica**

Para começar a escrever programas de computador é preciso então pensar de forma detalhista porque o computador não entende ou não deduz os passos que seu programa vai dar. Tudo bem eu sei que alguém pode ter pensado que hoje tem sugestões pra tudo até mesmo na hora de escrever código mas sendo mais preciso, o coração do seu programa não vai ser entendido pelo computador se não explicar exatamente como devemos fazer para que aquele programa seja executado.

Vamos a um exemplo a mais um exemplo da vida real antes de entrar na lógica de fato. Imagine que você vai atravessar uma rua. Na sua cabeça já estão ocorrendo milhares de operações e calculos sem que você saiba e o que realmente vocie se atenta é se o semáfaro está aberto para pedestres ou não. Mas sabemos que nem sempre os motoristas vão respeitar o sinal de trânsito pois os mesmos podem estar desatentos a acabar passando o farol mesmo que ele esteja aberto para que os pedestres passem. Nesse caso você também olha para os lados para verificar se tem algum carro vindo e não está atento a velocidade da via por exemplo. Mas tudo isso você já faz de forma implícita porque você já conhece o procedimento para atravessar a rua. Quando você vai ensinar uma criança a atravessar a rua, todos esses mínimos detalhes são passados para que ela entenda exatamente o que tem que ser feito. Quantos vídeos já vimos de crianças correndo até a rua sem olhar pros lados? Isso é porque elas ainda não tem a mesma percepção qie nós, ou seja ainda não conseguem processar essas instruções lógicas.

## **Escrevendo nossas instruções**

Para descrever nossos programas usamos operadores condicionais e operadores aritiméticos para que o programa entenda o passo-a-passo. Vamos começar vendos operadores condicionais que são as principais estruturas dentro do programa.

### **Operadores condicionais**

Ainda pensado na instrução de como atravessar a rua, vamos começar a listar os passos necessários para concluir essa tarefa.

- Andar até o semáforo de pesdestres
- Apertar o botão
- Aguardar o semáforo abrir

Até aqui podemos executar esses passos sem que comprometa a execução da nossa tarefa que é atravessar a rua em segurança mas para executar outros passo precisamos verficar se determinadas condições são verdadeiras, como por exemplo verificar se o sinal está aberto para os pedestres. O quando a luz verde está acesa significa que podemos passar, caso contrário deveremos aguardar. Então vamos adicionar um passo que verifica essa condição.

- Andar até o semáforo de pesdestres
- Apertar o botão
- Aguardar o semáforo abrir
- Luz do semáforo está verde?
  - `Se` sim, Atravessar a rua.
  - `Senão` aguardar o semáforo abrir

A representação dos operadores condicionais acontece pelo `SE` e pelo `SENÃO`onde o `SE` onde o `SE` representa uma condição que é verificada e caso for verdadeira o comando a seguir é executado e o `SENÃO` representa o que acontece caso a primeira condição não seja verdadeira.

## Referências

[Tecnoblog - Quem inventou o computador?](https://tecnoblog.net/responde/quem-inventou-o-computador/) <br>
[Tecnoblog - ENIAC completa 65 anos](https://tecnoblog.net/especiais/eniac-primeiro-computador-do-mundo-completa-65-anos/) <br>