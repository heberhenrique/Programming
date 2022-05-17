# Desafios

## **01 - Calculando impostos**

Escreva um programa que armazene uma empresa e consiga calcular impostos do simples nacional dadas as seguintes regras e premissas:

### **Regras de negócio**

- O programa deve começar exibindo a mensagem: `Digite seu CNPJ`
- O programa deve verificar se a empresa já foi cadastrada.
- Se a empresa não foi cadastrada, o programa deve a mensagem: `Digite o nome da Empresa`
- A seguir o programa deve armnazenar a empresa e seu nome.
- Caso o CNPJ já esteja cadastrado, exibir as opções:
  - `1 - Emitir nova nota fiscal`
  - `2 - Cadastrar notas anteriores`
  - `3 - Consultar notas anteriores`
- Caso a opção seja 1, exibir a mensagem: `Digite o valor da nota fiscal`
- Em seguida o programa exibe a mensagem: `Digite o CNPJ do cliente`
- Em seguida o programa exibe a mensagem: `Digite o nome do cliente`
- O programa deve exibir a mensagem: `Deseja emitir a nota? Sim/Nao`
- Caso o usuario digite sim o programa deve armazenar o `valor da nota`, `mes da emissao` e o `CNPJ` do cliente.
- Em seguida o programa deve exibir o valor do imposto a ser pago e suas divisões como no **exemplo**:

> IRPJ: R$ 6,97 <br>
> CSLL: R$ 6,10 <br>
> COFINS: R$ 22,33 <br>
> PIS: R$ 4,84 <br>
> INSS: R$ 75,58 <br>
> ISS: R$ 58,34 <br>
> VALOR TOTAL: R$ 174,16

- Caso o usuario digite qualquer tecla o programa exibe o menu novamente
- Caso o usuario escolha a opcao sair exibe a mensagem novamente: `Digite seu CNPJ`
- Caso o usuario digite `encerrar` o programa é finalizado;
- Caso o usuario escolha a opção `2 - Cadastrar notas anteriores` o programa segue o mesmo fluxo para cadastrar uma nova nota porem adiciona a informação do mes exibindo a mensagem: `Digite o mes da emissao`. Nesse caso nao é necessario apresentar os valores dos impostos.
- Caso o usuario escolha a opção `3 - Consultar notas anteriores`, Exibir o seguinte menu:
  - `1 - Consultar por Cliente`
  - `2 - Consultar por Mes`
- Caso a opção escolhida for a `1 - Consultar por Cliente`, exiba a mensagem: `Digite o CNPJ do cliente`
- Caso o Cliente não seja encontrado o sistema exibe a mensagem: `Cliente não encontrado`
- Caso o cliente esteja armazenado, exibe o resultado de todas as notas emitidas:

| Mês de Emissao  | Valor       |
| :---            |        ---: |
| 08/2019         | R$ 5.500,00 |
| 09/2019         | R$ 5.000,00 |

- Caso o usuario selecione a opção `2 - Consultar por Mes` o sistema deve exibir todas as notas emitidas naquele mês:

| Cliente                | Mês de Emissão  | Valor        |
| :---                   | :---:           |         ---: |
| Padaria Nova São Paulo | 08/2019         | R$ 5.500,00  |
| Posto Rudge Ramos      | 08/2019         | R$ 15.000,00 |

### **Calculando os impostos**

Para calcular os impostos vamos observar as tabelas abaixo:

#### _Alíquotas para o calculo_

| Receita Bruta em 12 Meses (em R$) | Alíquota        | Valor a Deduzir (em R$) |
| :---                              | :---:           | :---:                   |
| Até 180.000,00                    | 6,00%           | -                       |
| De 180.000,01 a 360.000,00        | 11,20%          | R$ 9.360,00             |

#### _Percentual de Repartição dos Tributos_

| Faixas                            | IRPJ            | CSLL          | Cofins | PIS   | INSS (CPP) | ISS    |
| :---                              | :---:           | :---:         | :---:  | :---: | :---:      | :---:  |
| Até 180.000,00                    | 4,00%           | 3,50%         | 12,82% | 2,78% | 43,40%     | 33,50% |
| De 180.000,01 a 360.000,00        | 4,00%           | 3,50%         | 14,05% | 3,05% | 43,40%     | 33,50% |

Se uma empresa faturou até 180 mil nos ultimos 12 meses, o calculo do imposto no mês pode ser feito de forma simples, vamos ver um exemplo de uma nota de R$ 2.902,50:

> 2.902,50 * 0,06 = ~174,15

Desses 174,15 cada imposto tem sua parcela como vimos na tabela de repartição. O `IRPJ` por exemplo fica com 4% desse valor, ou seja, R$ 6,97.

Caso a empresa tenha faturado entre `180.000,01 a 360.000,00` o calculo fica diferente pois temos que calcular a aliquota efetiva. Vejamos uma exemplo com um faturamento bruto nos ultimos 12 meses de `R$ 340.500,00` e tem uma nota de R$ 5.000,00 para ser emitida.

***Variáveis***

> RBT12 = `Receita bruta em 12 meses` <br>
> ALIQ  = `Aliquota nominal (que está na tabela)` <br>
> VB    = `Valor base. VB = RBT12 * ALIQ` <br>
> VAD   = `Valor a deduzir` <br>
> VD    = `Valor deduzido. VD = VB - VAD` <br>
> ALIQF = `Alíquota Efetiva ou Final. ALIQF = VD / RBT12` <br>
> VAL   = `Valor a pagar. VAL = VALOR DA NOTA * ALIQF` <br>

1. Calcular o valor base.
2. Calcular o valor deduzido.
3. Calcular a aliquota final.
4. Calcular o imposto.

Então teremos:

> RBT12 => `R$ 340.500,00` <br>
> ALIQ => `11,20%` <br>
> VB => `340.500,00 * 0.112 = R$ 38.136,00` <br>
> VAD => `R$ 9.360,00` <br>
> VD => `R$ 38.136,00 - R$ 9.360,00 = R$ 28.776` <br>
> ALIQF => `28.776,00 / 340.500,00 = 0,08`
> VAL => `5.000 * 0,08 = R$ 400,00`

### **Premissas**

- O programa só deve aceitar CNPJs válidos
- O programa só deve aceitar datas válidas
- O Nome da empresa deve possuir no minimo 10 caracteres
- Todas as empresas cadastradas são consideradas do Anexo III do Simples Nacional
- Toda nova nota fiscal emitida é considerado o mês de emissão o mês atual
- Não podem ser cadastradas notas fiscais com data futura
- Em todas as entradas o usuário pode digitar `cancelar` que volta para o menu anterior ou `voltar` que volta apenas um passo. Exemplo:

***voltar***

```csharp
Console.WriteLine("Digite o CNPJ do cliente");

// usuário digita 'voltar'
Console.WriteLine("Digite o valor da nota fiscal");
```

***cancelar***

```csharp
Console.WriteLine("Digite o CNPJ do cliente");

// usuário digita 'cancelar'
Console.WriteLine("1 - Emitir nova nota fiscal");
Console.WriteLine("2 - Cadastrar notas anteriores");
Console.WriteLine("3 - Consultar notas anteriores");
```

- As opções cancelar e voltar não estarão disponíveis quando os impostos estirem na tela pois qualquer tecla retorna para o menu principal.
- Caso o usuário digite sair o programa pede novamente o CNPJ da empresa para identificar a empresa que o mesmo estará genrando as notas.

### **Referências**

[Calcular Simples Nacional](https://www.dicionariofinanceiro.com/calcular-simples-nacional/)
[Tabela Anexo III Simples Nacional](http://www.planalto.gov.br/ccivil_03/leis/LCP/Lcp123.htm#anexoiii)

