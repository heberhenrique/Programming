# Banco Imobiliário - Ultimate Edition São Paulo

Crie um jogo onde até 6 pessoas poderão jogar Banco Imobiliário.

## Objetivo do Jogo

Conquistar a maior fortuna possível e/ou levar os outros jogadores à falência.

## Sobre o jogo

Muitas pessoas já conhecem banco imobiliário entretanto nossa versão tem um tempero a mais para que vocês sejam desafiados tanto ao criar o jogo quanto na hora de usufruir dele.

## Regras do Jogo / Programa

### Iniciando o jogo

Ao iniciar o programa é perguntado a quantidade de jogadores e após isso o nome de cada jogador é informado.

### Definindo Sequência de Jogadores

- Cada jogador lançará os dados para definir qual será o primeiro jogador a começar a partida.
- O jogador que lançar os dados e obtiver o maior número começa, seguido por aqueles que tiverem numeração inferior.
- Caso haja empate  nos números sorteados o programa define a ordem de forma randomica.

### Preparação para o jogo

- Cada jogador terá uma conta corrente que terá saldo Inicial de $ 1.000.000,00 (um milhão).
- Cada jogador terá um cartão de crédito com saldo de $ 500.000 (quinhentos mil).

### Inicio do jogo

- O jogador começa a rodada jogando os dois dados e somar o resultado, então avançar com o peão a quantidade de casas e cumprir o que determina aquela casa.
- Caso o jogador tire nos dados dois números iguais, ele tem direito a novo lançamento.
- Caso tire dois números iguais três vezes, ele vai para a prisão.

### Movimentação no tabuleiro

- Caso seu peão caia em uma propriedade sem dono, você terá o direito de comprá-la pelo preço indicado no tabuleiro.
- Caso seu peão pare na casa Sorte ou Revés, você deve pegar a primeira carta do monte, cumprir o que ela indica e a devolver para o final do monte após concluir a tarefa.
- Caso seu peão caia na casa que indica “Vá para a prisão”, o peão do jogador é movido imediatamente para a prisão.

### Comprando propriedades e compahias

- Um jogador pode comprar uma propriedade com o saldo em conta ou utilizando o saldo cartão de crédito.
- Após comprar aquela propriedade o Titulo de Posse é transferido para o jogador.
- Para a compra da propriedade além do valor nominal são pagos os seguintes impostos:
  - ITBI: 3% sobre o valor nominal
  - Escritura: 1% sobre o valor nominal
  - Registro: $ 500,00
- Para comprar compahias(empresas) além do valor nominal é cobrado o imposto de 15% em cima do valor nominal.
- Caso o jogador não tenha como pagar os impostos a compra não é realizada.
- Os impostos só podem ser pagos em dinheiro, ou seja, com saldo em conta. Não é permitido fazer o pagamento de impostos usando o cartão.

### Usando o cartão de crédito

- Ao efetuar uma compra com cartão de crédito o jogador pode lançar um dado para verificar a quantidade de vezes em que a compra vai ser parcelada.
- A compra pode ser parcelada em no máximo 6 vezes.
- Cada parcela deve ser paga no inicio do turno daquele jogador.
- A dívida pode ser quitada por inteiro sempre no início do turno daquele jogador.
- Caso o jogador não tenha dinheiro para pagar a parcela ou a fatura (no caso de compra sem parcelamento), ele terá a opção de efetuar o pagamento mínimo e consequentemente o juros na próxima fatura conforme a seguir:
  - O pagamento mínimo equivale a 17% do valor da fatura.
  - Ex: Fatura $ 1000,00. Valor do mínimo 170.
  - O os Juros aplicados são referente ao valor que ficou pendente, ou seja, o valor do pagamento efetuado - o valor total da fatura. Os juros são 12% sobre a diferença entre o valor pago e o valor da fatura original.
  - Ex: Valor pago $ 170,00. Valor do rotativo 830. Valor de juros a ser pagos na proxima fatura: 99,60
- `Caso o jogador utilize o crédito rotativo ele fica impedido de fazer novas aquisições enquanto sua dívida não for quitada`.
- Caso a dívida seja quitada o jogador só poderá comprar propriedades em posse do banco na próxima rodada.

### Faturando

Para ganhar dinheiro no jogo o jogador precisa ter propriedades pois é através delas que o mesmo poderá cobrar aluguel de outro jogador.

- Quando outro jogador parar em uma propriedade que possui um dono o mesmo deverá pagar o aluguel devido de acordo com a descrição no titulo de posse.
- O mesmo acontece quando um jogador parar em uma casa do tabuleiro que representa uma compahia que possui dono.

### Valorizando o terreno

- Quando conseguir comprar todas as propriedades de um mesmo grupo de cores, você poderá acrescentar casas, hotéis nos seus terrenos, aumentando assim o valor de seus aluguéis.
- Você só poderá construir uma segunda casa em uma propriedade, se todas as outras daquele grupo de cores já tiver pelo menos uma casa. Para construir a terceira, todas deverão ter pelo menos duas casas, e assim sucessivamente.
- Para construir um hotel o jogador deverá ter 4 casas em cada terreno. Antes de colocar o hotel o jogador vende suas casas para o banco pela metade do preço e coloca um hotel em seu lugar.

### Valorizando Empresas

Um jogador recebe dinheiro através de do valor indicado no titulo de posse que basicamente é o valor que o jogador obteve nos dados antes de chegar até aquela casa do tabuleiro multiplicado pelo valor indicado na carta.

- Se um jogador tiver posse de todas as compahias do jogo, o valor a receber indicado na carta é multiplicado por 2.
- Cada jogador pode colocar até duas franquias em cada compahia para funcionar como as casas em propriedades. A cada franquia o valor a ser multiplicado aumenta conforme a indicação na carta.

### Impostos

- A cada quatro rodadas no tabuleiro um jogador deve pagar os seguintes impostos:
  - IPTU
  - Imposto de Renda

#### IPTU

As seguintes tabelas serão usadas para o calculo do IPTU:

- `Propriedades com casas`:

| Faixas de Valor ($)                   | Multiplicar por   | Subtrair      |
| :---                                  | :----             | :---          |
| Até 150.000,00                        | 0,007             | 0,00          |
| De  150.001,00 a 300.000,00           | 0,009             | 300,00        |
| De R$ 300.001,00 a R$ 600.000,00      | 0,011             | 900,00        |
| De R$ 600.001,00 a R$ 1.200.000,00    | 0,013             | 2.100,00      |
| Acima de R$ 1.200.000,00              | 0,015             | 4.500,00      |

- `Propriedades com Hotéis`

| Faixas de Valor ($)                   | Multiplicar por   | Subtrair      |
| :---                                  | :----             | :---          |
| Até 150.000,00                        | 0,011             | 0,00          |
| De  150.001,00 a 300.000,00           | 0,013             | 300,00        |
| De R$ 300.001,00 a R$ 600.000,00      | 0,015             | 900,00        |
| De R$ 600.001,00 a R$ 1.200.000,00    | 0,017             | 2.100,00      |
| Acima de R$ 1.200.000,00              | 0,019             | 4.500,00      |

#### Imposto de Renda

O Imposto de Renda é calculado