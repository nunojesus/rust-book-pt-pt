## Apêndice B: Operadores e símbolos

### Operadores

A seguinte lista dos operadores em Rust, é um exemplo de como o operador
irá aparecer no contexto, uma breve explicação e se este operador é
sobrecarregável. Se um operador é sobrecarregável, o traço relevante a ser utilizado para
sobrecarregar este operador que está listado.

* `!` (`ident!(…)`, `ident!{…}`, `ident![…]`): indica expansão de macro.
* `!` (`!expr`): complemento binário ou lógico. Sobrecarregável (`Not`).
* `!=` (`var != expr`): comparação de não-qualidade. Sobrecarregável (`PartialEq`).
* `%` (`expr % expr`): restante aritmética. Sobrecarregável (`Rem`).
* `%=` (`var %= expr`): restrição aritmética e atribuição. Sobrecarregável (`RemAssign`).
* `&` (`&expr`, `&mut expr`): pedir emprestado.
* `&` (`&type`, `&mut type`, `&'a type`, `&'a mut type`): tipo de ponteiro emprestado.
* `&` (`expr & expr`): lógica binária E. Sobrecarregável (`BitAnd`).
* `&=` (`var &= expr`): lógica binária E e tarefa. Sobrecarregável (`BitAndAssign`).
* `&&` (`expr && expr`): lógico E.
* `*` (`expr * expr`): multiplicação aritmética. Sobrecarregável (`Mul`).
* `*` (`*expr`): desreferência.
* `*` (`*const type`, `*mut type`): ponteiro bruto.
* `*=` (`var *= expr`): multiplicação aritmética e atribuição. Sobrecarregável (`MulAssign`).
* `+` (`trait + trait`, `'a + trait`): restrição de tipo composto.
* `+` (`expr + expr`): adição aritmética. Sobrecarregável (`Add`).
* `+=` (`var += expr`): adição e atribuição aritmética. Sobrecarregável (`AddAssign`).
* `,`: argumento e separador de elementos.
* `-` (`- expr`): negação aritmética. Sobrecarregável (`Neg`).
* `-` (`expr - expr`): subtração aritmetica. Sobrecarregável (`Sub`).
* `-=` (`var -= expr`): subtração aritmética e atribuição. Sobrecarregável (`SubAssign`).
* `->` (`fn(…) -> type`, `|…| -> type`): função e tipo de retorno de encerramento.
* `.` (`expr.ident`): acesso de membro.
* `..` (`..`, `expr..`, `..expr`, `expr..expr`): direito-exclusivo literal de alcance.
* `..` (`..expr`): estrutura de sintaxe de atualização literal.
* `..` (`variant(x, ..)`, `struct_type { x, .. }`): "e o restante" padrão de ligação.
* `...` (`...expr`, `expr...expr`) *numa expressão*: expressão de intervalo inclusiva.
* `...` (`expr...expr`) *num padrão*: padrão de alcance inclusivo.
* `/` (`expr / expr`): divisão aritmética. Sobrecarregável (`Div`).
* `/=` (`var /= expr`): divisão e atribuição aritmética. Sobrecarregável (`DivAssign`).
* `:` (`pat: type`, `ident: type`): restrições.
* `:` (`ident: expr`): inicialização do campo struct.
* `:` (`'a: loop {…}`): rótulo de loop.
* `;`: declaração e terminador de itens.
* `;` (`[…; len]`): parte da sintaxe da matriz de tamanho fixo
* `<<` (`expr << expr`): desvio à esquerda. Sobrecarregável (`Shl`).
* `<<=` (`var <<= expr`): shift esquerdo e atribuição. Sobrecarregável (`ShlAssign`).
* `<` (`expr < expr`): menos do que comparação. Sobrecarregável (`PartialOrd`).
* `<=` (`var <= expr`): menor ou igual à comparação. Sobrecarregável (`PartialOrd`).
* `=` (`var = expr`, `ident = type`): atribuição/equivalência.
* `==` (`var == expr`): comparação de igualdade. Sobrecarregável (`PartialEq`).
* `=>` (`pat => expr`): parte da sintaxe do braço de combinação.
* `>` (`expr > expr`): maior que a comparação. Sobrecarregável (`PartialOrd`).
* `>=` (`var >= expr`): maior ou igual a comparação. Sobrecarregável (`PartialOrd`).
* `>>` (`expr >> expr`):  shift direita. Sobrecarregável (`Shr`).
* `>>=` (`var >>= expr`): shift direita e atribuição. Sobrecarregável (`ShrAssign`).
* `@` (`ident @ pat`): vinculação do padrão.
* `^` (`expr ^ expr`): lógica binária exclusiva OU. Sobrecarregável (`BitXor`).
* `^=` (`var ^= expr`): lógica binária exclusiva OU e atribuição. Sobrecarregável (`BitXorAssign`).
* `|` (`pat | pat`): alternativas de padrão.
* `|` (`|…| expr`): encerramentos.
* `|` (`expr | expr`): lógica binária OU. Sobrecarregável (`BitOr`).
* `|=` (`var |= expr`): lógica binária OU e atribuição. Sobrecarregável (`BitOrAssign`).
* `||` (`expr || expr`): lógica OU.
* `_`: “ignorado” vinculação do padrão. Também usado para tornar literais inteiros legíveis.
* `?` (`expr?`):Propagação de erros.

### Símbolos não operacionais

#### Sintaxe Autónoma

* `'ident`: nomeado etiqueta de vida ou loop
* `…u8`, `…i32`, `…f64`, `…usize`, *etc.*: literal numérico de tipo específico.
* `"…"`: string literal.
* `r"…"`, `r#"…"#`, `r##"…"##`, *etc.*: literal de string crua, os caracteres de escape não são processados.
* `b"…"`: byte string literal, constrói um `[u8]` em vez de uma string.
* `br"…"`, `br#"…"#`, `br##"…"##`, *etc.*: literal de byte string raw, combinação de raw e byte string literal.
* `'…'`: carater literal.
* `b'…'`: ASCII byte literal.
* `|…| expr`: encerramento.
* `!`: sempre do tipo de fundo vazio para funções divergentes.

#### Sintaxe relacionada ao caminho

* `ident::ident`: caminho do namespace.
* `::path`: caminho relativo à raiz de caixas (*isto é* um caminho explicitamente absoluto).
* `self::path`: caminho relativo ao módulo atual (*isto é* um caminho explicitamente relativo).
* `super::path`: caminho relativo ao pai do módulo atual.
* `type::ident`, `<type as trait>::ident`: constantes, funções e tipos associados.
* `<type>::…`: item associado para um tipo que não pode ser nomeado diretamente (*por exemplo.* `<&T>::…`, `<[T]>::…`, *etc.*).
* `trait::method(…)`: desambiguando uma chamada de método ao nomear a característica que a define.
* `type::method(…)`: desambiguando uma chamada de método, nomeando o tipo para o qual está definido.
* `<type as trait>::method(…)`: desambiguando uma chamada de método, nomeando a característica *e* tipo.

#### Genéricos

* `path<…>` (*por exemplo.* `Vec<u8>`): especifica parâmetros para o tipo genérico *num tipo*.
* `path::<…>`, `method::<…>` (*por exemplo.* `"42".parse::<i32>()`): especifica parâmetros para tipo genérico, função ou método *numa expressão*. Muitas vezes referido como *turbofish*.
* `fn ident<…> …`: definir a função genérica.
* `struct ident<…> …`: definir estrutura genérica.
* `enum ident<…> …`: definir enumeração genérica.
* `impl<…> …`: definir a implementação genérica.
* `for<…> type`: limites de vida mais elevados.
* `type<ident=type>` (*por exemplo.* `Iterator<Item=T>`): um tipo genérico onde um ou mais tipos associados têm atribuições específicas.

#### Traço de Limite de Restrições

* `T: U`: parâmetro genérico `T` constrangido para os tipos que implementam `U`.
* `T: 'a`: tipo genérico `T` deve sobreviver à vida `'a`. Quando dizemos que um tipo expõe ‘o tempo de vida’, queremos dizer que não pode conter transitivamente qualquer referência com vidas mais curtas do que `'a`.
* `T : 'static`: O tipo genérico `T`não contém referências emprestadas além de `'static` uns.
* `'b: 'a`: vida genérica `'b` deve sobreviver à vida `'a`.
* `T: ?Sized`: permitir que o tipo de tipo genérico seja de tamanho dinâmico.
* `'a + trait`, `trait + trait`: restrição de tipo composto.

#### Macros e Atributos

* `#[meta]`: atributo externo.
* `#![meta]`: atributo interno.
* `$ident`: substituição de macro.
* `$ident:kind`: captura de macro.
* `$(…)…`: repetição macro.

#### Comentários

* `//`: comentário de linha.
* `//!`: linha interna comentário do doc.
* `///`: linha externa comentário do doc.
* `/*…*/`: comentário de bloco.
* `/*!…*/`: bloco interno comentário do doc.
* `/**…*/`: bloco externo comentário do doc.

#### Tuplas

* `()`: tupla vazia (unidade *a.k.a.*), tanto literal quanto ao tipo.
* `(expr)`: expressão entre parênteses.
* `(expr,)`: expressão de uma tupla de elemento único.
* `(type,)`: tipo de tupla de elemento único.
* `(expr, …)`: expressão de tupla.
* `(type, …)`: tipo de tupla.
* `expr(expr, …)`: expressão de chamada de função. Também usado para inicializar a tupla `struct`s e tupla `enum` variantes.
* `ident!(…)`, `ident!{…}`, `ident![…]`: invocação de macro.
* `expr.0`, `expr.1`, …: indexação de tupla.

#### Parênteses Encaracolados

* `{…}`: expressão de bloco.
* `Type {…}`: `struct` literal.

#### Parênteses Quadrados

* `[…]`: matriz literal.
* `[expr; len]`: matriz literal contendo `len` copias de `expr`.
* `[type; len]`: tipo de matriz contendo `len` instâncias de `type`.
* `expr[expr]`: indexação de coleta. Sobrecarregável (`Index`, `IndexMut`).
* `expr[..]`, `expr[a..]`, `expr[..b]`, `expr[a..b]`: indexação de cobrança que pretende ser o corte de coleta, usando `Range`, `RangeFrom`, `RangeTo`, `RangeFull` como o “índice”.
