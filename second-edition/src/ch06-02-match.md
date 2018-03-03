## O Operador de Fluxo de Controle `match`

A Rust possui um operador de fluxo de controle extremamente poderoso chamado de `match` que nos 
permite comparar um valor com uma série de padrões e em seguida, executar o código baseado
com qual o padrão corresponde. Os padrões podem ser constituídos por valores literais, variáveis
nomes, wildcards e muitas outras coisas; O capítulo 18 cobre todos os diferentes
tipos de padrões e o que eles fazem. O poder do `match` vem da
expressividade dos padrões e o compilador verifica que todos os
casos possíveis são tratados

Pensa num tipo de expressão `match` como uma máquina de classificação de moeda: as moedas delizam
para baixo ao lono de um caminho com furos com tamanhos diferentes ao longo dele, e cada moeda cai através
do primeiro buraco que encontra e que se encaixa. Da mesma forma, os valores vão
através de cada padrão num `match`, e no primeiro padrão o valor “encaixa-se”,
o valor irá cair no bloco do código associado para ser usado durante a execução.

Porque acabamos de mencionar as moedas, vamos usá-las como um exemplo usando `match`! Nós
podemos escrever uma função que pode levar uma moeda desconhecida dos Estados Unidos, e de uma
forma similar à da máquina de contagem, determinar qual é a moeda e devolver a tua
em centavos, como mostrado aqui na Listagem 6-3:

```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter,
}

fn value_in_cents(coin: Coin) -> u32 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}
```

<span class="caption">Listagem 6-3: Uma expressão de `match` e enum que tem
as variantes do enum como padrões.</span>
    
Vamos dividir o `match` na função `value_in_cents`. Primeiro, listamos
a palavra-chave `match` seguida de uma expressão, que neste caso é o valor da
`moeda'. Isto parece bastante semelhante com uma expressão usada com `if`, mas há uma
grande diferença: com `if`, a expressão precisa de devolver um valor booleano.
Aqui, pode ser qualquer tipo. O tipo de `moeda` neste exemplo é o `Moeda` enum
que definimos na Listagem 6-3.   

De seguida, estão os braços `match`. Um braço tem duas partes: um padrão e algum código. O
primeiro braço aqui tem um padrão que é o valor `Moeda::Centâvo` e de seguida, o `=>`
operador que separa o padrão e o código para executar. O código neste caso
é apenas o valor `1`. Cada braço é separado do próximo com uma vírgula.

Quando a expressão `match` é executada, ela compara o valor resultante contra
o padrão de cada braço, em ordem. Se um padrão corresponde ao valor, o código
associado a este padrão é executado. Se este padrão não corresponder ao
valor, a execução continua para o próximo braço, assim como uma máquina de classificação de moedas.
Podemos ter tantos braços quanto precisamos: na Listagem 6-3, o nosso `match` tem quatro braços.

O código associado a cada braço é uma expressão e o valor resultante da
expressão no braço correspondente é o valor que é devolvido para
toda a expressão `match`.

Os suportes encaracolados geralmente não são usados se o código do braço da partida for curto, como acontece
na Listagem 6-3, onde cada braço apenas devolve um valor. Se tu quiseres executar múltiplas
linhas de código num braço de correspondência, podes usar suportes encaracolado. Por exemplo, o
seguinte código iria imprimir “Centâvo da Sorte!” sempre que o método fosse chamado
com uma `Moeda::Centâvo`, mas ainda devolveria o último valor do bloco, `1`:

```rust
# enum Coin {
#    Penny,
#    Nickel,
#    Dime,
#    Quarter,
# }
#
fn value_in_cents(coin: Coin) -> u32 {
    match coin {
        Coin::Penny => {
            println!("Lucky penny!");
            1
        },
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}
```
### Padrões que Ligam-se aos Valores

Outra característica útil dos braços de combinação é que eles podem ligar-se a partes dos
valores que correspondem ao padrão. É assim que podemos extrair os valores das variantes
de enum.

Como exemplo, vamos mudar uma das nossas variantes de enum para armazenar dados dentro dela.
De 1999 a 2008, os Estados Unidos marcaram quartos com diferentes
projetos para cada um dos 50 estados de um lado. Nenhuma outra moeda obteve projetos
de estados, então apenas os alojamentos possuem este valor extra. Podemos adicionar esta informação para
o nosso `enum` mudando a variante `Quarto` para incluir um valor `UsState` armazenado
dentro disso, que foi o que fizemos aqui na Listagem 6-4:

```rust
#[derive(Debug)] // So we can inspect the state in a minute
enum UsState {
    Alabama,
    Alaska,
    // ... etc
}

enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}
```

<span class="caption">Listagem 6-4: A `Moeda` enum onde a variante 'Quarto`
também possui um valor `UsState`</span>

Imaginemos que um amigo nosso está a tentar recolher todos os 50 quartos do estado.
Enquanto classificamos a nossa mudança solta por tipo de moeda, também chamaremos o nome do
estado associado a cada quarto, então se for um do que o nosso amigo não possui,
eles podem adicioná-lo à sua coleção.

Na expressão da correspondência para este código, adicionamos uma variável chamada `state` para o
padrão que corresponde aos valores da variante `Moeda :: Quarto`. Quando uma
`Moeda::Quarto`, a variável `state` irá vincular ao valor desse
quarto do estado. Então podemos usar `state` no código para esse braço, desta forma:

```rust
# #[derive(Debug)]
# enum UsState {
#    Alabama,
#    Alaska,
# }
#
# enum Coin {
#    Penny,
#    Nickel,
#    Dime,
#    Quarter(UsState),
# }
#
fn value_in_cents(coin: Coin) -> u32 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter(state) => {
            println!("State quarter from {:?}!", state);
            25
        },
    }
}
```

Se chamássemos `valor_em_cêntavos(Moeda::Quarto(UsState::Alaska))`, `moeda`
seria `Moeda::Quarto(UsState::Alaska)`. Quando comparamos esse valor com cada um
dos braços, nenhum deles terá correspondência até atinguirmos `Moeda::Quarto(estado)`.
Nesse momento a liação para o `estado` será o valor `UsState :: Alaska`. Nós podemos
então usar essa ligação na expressão `println!`, obtendo assim o valor interior
de estado da variante enum `Moeda` para `Quarto`.

### Correspondência com `Opção<T>`

Na seção anterior, queríamos obter o valor interno `T` fora do `Alguns`
caso usarmos `Opção <T>`; também podemos lidar com `Opção <T> usando `match` como nós
fizemos com o enum `Moeda`! Em vez de comparar moedas, iremos conparar as
variantes de `Opção <T>`, mas a forma como a expressão `match` funciona permanece
a mesmo.

Digamos que queremos escrever uma função que tenha uma `Opção<i32>` e se
houver um valor no interior, adiciona um a esse valor. Se não houver um valor no interior,
a função deve devolver o valor `Nenhum` e não tenta executar qualquer
operações.

Esta função é muito fácil de escrever, graças ao `match`, e irá parecer-se com
Listagem 6-5:

```rust
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        None => None,
        Some(i) => Some(i + 1),
    }
}

let five = Some(5);
let six = plus_one(five);
let none = plus_one(None);
```

<span class="caption">Listagem 6-5: Uma função que usa uma expressão `match`
numa `Opção<i32>`</span>
    
#### Correspondência de `Alguns(T)`

Vamos examinar a primeira execução de `mais_um` com mais detalhe. Quando chamamos
`mais_um(cinco)`, a variável `x` no corpo de `mais_um` terá o
valor `Alguns(5)`. De seguida, comparamos isso com cada braço de correspondência. 

```rust,ignore
None => None,
```

O valor `Alguns(5)` não corresponde ao padrão `Nenhum`, então continuamos com o
próximo braço.

```rust,ignore
Some(i) => Some(i + 1),
```

O `Alguns(5)` corresponde `Alguns(i)`? Bem, claro que sim! Temos a mesma variante.
O `i` liga-se ao valor contido em `Alguns`, então `i` leva o valor `5`. O
código no braço de correspondência é então executado, então adicionamos um ao valor de `i` e
criamos um novo valor `Alguns` com o nosso total `6` dentro.

#### Correspondência de `Nenhum`

Agora vamos considerar a segunda chamada de `mais_um` na Listagem 6-5 onde `x` é
`Nenhum`. Nós entramos no `match` e comparamos com o primeiro braço.

```rust,ignore
None => None,
```

Corresponde! Não há valor a ser adicionado, então o programa pára e retorna o
`Nenhum` valor no lado direito de `=>`. Como o primeiro braço corresponde, nenhum outro
dos braços são comparados.

Combinar `match` e enums é útil em muitas situações. Vais ver este
padrão muitas vezes no código Rust: `match` contra um enum, vincula uma variável aos
dados internos e de seguida, executa o código com base nisso. É um pouco complicado no início, mas
uma vez que te acostumas, gostarias de o ter em todas as línguas. É
consistentemente um dos favoritos do utilizador.

### As Correspondências são Exaustivas

Há um outro aspecto do `match` que precisamos discutir. Considera esta versão
da nossa função `mais_um`:

```rust,ignore
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        Some(i) => Some(i + 1),
    }
}
```

Nós não lidamos com o caso `Nenhum`, então este código causará um erro. Felizmente é
um erro que o Rust sabe como apanhar. Se tentarmos compilar este código, obteremos iste
erro:

```text
error[E0004]: non-exhaustive patterns: `None` not covered
 -->
  |
6 |         match x {
  |               ^ pattern `None` not covered
```

Rust sabe que não cobrimos todos os casos possíveis e até mesmo sabemos qual
o padrão que nós esquecemos! As correpondências no Rust são *exaustivas*: devemos exaustar todas as últimas
possibilidade para que o código seja válido. Especialmente no caso de
`Opção<T>`, quando o Rust nos impede de esquecer de manipular explicitamente o
caso `Nenhum`, isto protege-nos de assumir que temos um valor quando podemos
ter nulo, fazendo com que o erro de biliões de dólares tenha sido discutido mais cedo.

### O `_` Marcador de posição

Rust também tem um padrão que podemos usar em situações quando não queremos listar todos
valores possíveis. Por exemplo, um `u8` pode ter valores válidos de 0 a 255. Se
só nos preocupamos com os valores 1, 3, 5 e 7, não queremos ter que listar o
0, 2, 4, 6, 8, 9 até 255. Felizmente, não precisamos: podemos
usar o padrão especial `_` em vez disso:

```rust
let some_u8_value = 0u8;
match some_u8_value {
    1 => println!("one"),
    3 => println!("three"),
    5 => println!("five"),
    7 => println!("seven"),
    _ => (),
}
```

O padrão `_` irá corresponder com qualquer valor. Ao colocá-lo depois dos nossos braços, o
`_` irá combinar todos os casos possíveis que não são especificados antes. O `()`
é apenas o valor da unidade, então nada vai acontecer no caso de `_`. Como resultado,
podemos dizer que não queremos fazer nada por todos os possivéis valores que não
listamos antes do espaço reservado `_`.

No entanto, a expressão `match` pode ser um pouco palavroso numa situação em que só
nos preocupamos com *um* dos casos. Para esta situação, Rust fornece `if let`.
