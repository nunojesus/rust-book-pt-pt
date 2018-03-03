## Funções Avançadas & Encerramentos

Finalmente, vamos discutir alguns recursos avançados relacionados com as funções e
encerramentos: ponteiros de funções, funções divergentes e enceramentos de retorno.


### Ponteiros de Funções

<!-- Talvez dê um exemplo de quando gostaríamos de usar isto? -->
<!-- Adicionar uma breve frase, mas nós discutimos a interface com idiomas que
não tenham encerramentos abaixo, o que eu acho que não faz sentido até que nós definirmos como
os ponteiros de função são diferentes dos encerramentos... /Carol -->

Nós conversamos sobre como passar os encerramentos para funções; tu também podes passar
funções reulares para funções! Isto é útil quando queremos passar uma função que temos
já definida em vez de definir um novo encerramento. Fazemos isto usando a função
ponteiros para nos permitir usar funções como argumentos para outras funções.
Funções forçem para o tipo `fn`, com uma minúscula ‘f’ para não confundir
com o traço de enceramento `Fn`. O tipo `fn` é chamado de *ponteiro de função*. A
sintaxe para especificar que um parâmetro é um ponteiro de função é semelhante à
de encerramentos, como mostrado na Listagem 19-35:

<span class="filename">Filename: src/main.rs</span>

```rust
fn add_one(x: i32) -> i32 {
    x + 1
}

fn do_twice(f: fn(i32) -> i32, arg: i32) -> i32 {
    f(arg) + f(arg)
}

fn main() {
    let answer = do_twice(add_one, 5);

    println!("The answer is: {}", answer);
}
```

<span class="caption">Listagem 19-35: Usando o tipo `fn` para aceitar uma função
ponteiro como argumento</span>

Isto imprime `A resposta é: 12`. Especificamos que o parâmetro `f` no
`do_twice` é um `fn` que leva um parâmetro do tipo `i32` e retorna um
`i32'. Podemos chamar `f` no corpo de `do_twice`. Em `main`, podemos passar
o nome da função `add_one` como o primeiro argumento para `do_twice`.

Ao contrário dos fechos, `fn` é um tipo e não uma característica, então especificamos `fn` como o
tipo de parâmetro diretamente, em vez de declarar um parâmetro de tipo genérico com
um dos traços `Fn` como um atalho de traço.

Os ponteiros de função implementam os três traços de fecho (`Fn`,` FnMut` e
`FnOnce`), para que possamos sempre passar um ponteiro de função como um argumento para uma
função que espera um encerramento. Prefere escrever funções usando um tipo genérico
e um dos traços do encerramento, para que as suas funções possam aceitar
funções ou encerramentos.

Um exemplo de um caso em que tu queres aceitar apenas `fn` e não encerramentos é
quando interagindo com o código externo que não possui encerramentos: funções C podem
aceitar funções como argumentos, mas C não possui encerramentos.

Para um exemplo em que podemos usar um encerramento definido em linha ou uma função
nomeada, vejamos um uso de `map`. Para usar a função `map` para transformar um
vetor de números num vetor de cordas, poderíamos usar um encerramento:

```rust
let list_of_numbers = vec![1, 2, 3];
let list_of_strings: Vec<String> = list_of_numbers
    .iter()
    .map(|i| i.to_string())
    .collect();
```

Ou podemos nomear uma função como o argumento para `map` em vez do encerramento:

```rust
let list_of_numbers = vec![1, 2, 3];
let list_of_strings: Vec<String> = list_of_numbers
    .iter()
    .map(ToString::to_string)
    .collect();
```

Observa que precisamos de usar a sintaxe totalmente qualificada que falamos na
seção “Traços Avançados” porque existem várias funções disponíveis
chamado `to_string`; aqui, estamos a usar a função `to_string` definida na
tração `ToString`, que a biblioteca padrão implementou para qualquer tipo que
implementa o `Display`.

Algumas pessoas preferem este estilo, algumas pessoas preferem usar encerramentos. Acabam
com o mesmo código, então usa o que achas mais claro para ti.

### Encerramentos de Retorno

Os encerramentos são representados por traços, o que significa que não podemos retornar encerramentos
diretamente. Na maioria dos casos em que podemos querer retornar uma característica, podemos usar
o tipo de concreto que implementa o traço como o valor de retorno da
função. Nós não podemos fazer isto com encerramentos, no entanto, como eles não têm um
tipo de concreto que é retornável; não podemos usar o ponteiro da função
`fn` como um tipo de retorno, por exemplo.

Este código que tenta retornar um encerramento diretamente não compilará:

```rust,ignore
fn returns_closure() -> Fn(i32) -> i32 {
    |x| x + 1
}
```

O erro do compilador é:

```text
error[E0277]: the trait bound `std::ops::Fn(i32) -> i32 + 'static:
std::marker::Sized` is not satisfied
 -->
  |
1 | fn returns_closure() -> Fn(i32) -> i32 {
  |                         ^^^^^^^^^^^^^^ `std::ops::Fn(i32) -> i32 + 'static`
  does not have a constant size known at compile-time
  |
  = help: the trait `std::marker::Sized` is not implemented for
  `std::ops::Fn(i32) -> i32 + 'static`
  = note: the return type of a function must have a statically known size
```

O nosso erro faz referência ao traço `Sized` novamente! O Rust não sabe quanto espaço
ele precisará para armazenar o encerramento. Nós vimos uma solução para isto na seção
anterior: podemos usar um objeto de traço:

```rust
fn returns_closure() -> Box<Fn(i32) -> i32> {
    Box::new(|x| x + 1)
}
```

Este código irá compilar muito bem. Para mais informações sobre objetos de traços, consulta
a seção “Objetos de Traço” no Capítulo 17.

## Resumo

Whew! Agora, examinamos as características do Rust que não são usadas com freqüência, mas estão
disponíveis se tu precisares delas em circunstâncias muito específicas. Introduzimos
muitos tópicos complexos para que, quando tu os encontrares em mensagem de erro,
sugestões ou em outros códigos, pelo menos terás visto estes conceitos e
sintaxe anteriormente. Tu podes usar este capítulo como uma referência para te orientar para
as tuas soluções.

Agora, vamos colcar tudo o que aprendemos ao longo do livro com
mais um projeto!
