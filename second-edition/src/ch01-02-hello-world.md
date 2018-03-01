## Olá Mundo!

Agora que ja tens o Rust instalado, vamos escrever o teu primeiro programa em Rust. É
tradição quando se aprende um novo idioma, para escrever um pequeno programa para imprimir o
texto "Olá, mundo!" para o ecrã, então vamos lá fazer o mesmo aqui!

> Nota: Este livro assume  uma familiaridade básica com a linha de comando. O próprio Rust
> não faz exigências específicas sobre a sua edição, ferramentas ou onde o teu código
> vive, então se preferires um IDE (Integrated Development Environment) para a
> linha de comando, fica à vontade para usares o teu IDE favorito. Muitos IDEs agora têm alguns
> graus de suporte de Rust; verifica a documentação do IDE para obteres detalhes. Possibilitar
> um excelente suporte IDE tem sido o foco recente da equipa Rust, e o progresso nesta frente
> foi feito rapidamente!

### Criar um Diretório de Projetos

Primeiro, faz um diretório para colocar o teu código Rust. O Rust não se importa com o teu
codigo de vidas, mas para os exercícios e projetos neste livro, sugerimos
criares um diretório *projects* no teu diretório pessoal e mantem todos os teus
projetos lá.

Abre um terminal e insire os seguintes comandos para criares um diretório *projects*
e dentro disto, um diretório para este projeto "Olá, mundo!":

Linux e Mac:

```text
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

Windows CMD:

```cmd
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

Windows PowerShell:

```powershell
> mkdir $env:USERPROFILE\projects
> cd $env:USERPROFILE\projects
> mkdir hello_world
> cd hello_world
```

### Escrever e Executar um Programa Rust

Em seguida, cria um novo arquivo de origem e chama-o *main.rs*---Os arquivos Rust terminam sempre com
a extensão *.rs*. Se estiver a usar mais de uma palavra no teu nome de arquivo, usa
o sublinhado para separá-los. Por exemplo, tu irias usar *hello_world.rs*
em vez de *helloworld.rs*.

Agora abre o arquivo *main.rs* que acabaste de criar e insere o código mostrado na
Listagem 1-1:

<span class="filename">Filename: main.rs</span>

```rust
fn main() {
    println!("Hello, world!");
}
```

<span class="caption">Listagem 1-1: Um programa que imprime “Olá, mundo!”</span>

Guarda o arquivo e volta para a janela do terminal. No Linux ou MacOS, coloca
os seguintes comandos para compilar e executar o arquivo:

```text
$ rustc main.rs
$ ./main
Hello, world!
```

No Windows, usa `.\main.exe` em vez de `./main`.

```powershell
> rustc main.rs
> .\main.exe
Hello, world!
```

Independentemente do teu sistema operacional, tu deverás ver a string `Hello, world!`
imprime para o terminal. Se não vires esta saída, consulta a seção “Solução de problemas”
a seção anterior para obteres formas para obteres ajuda.

Se tu viste impreso `Hello, world!`, então parabéns! Tu escreveste oficialmente
um programa Rust. Isto torna-te um programador de Rust! Bem vindo!

<!-- Quaisquer palavras rápidas de conselhos se não o fizeram? (Divulgação: eu tentei
seguir isto usando o Bash no Windows e não conseguiu o pôr a funcionar)-->
<!-- Adicionado um ponteiro para a seção anterior de solução de problemas que também se aplica
aqui/Carol-->

### Anatomia de um Programa de Rust

Agora, vamos ao ver ao detalhe o que aconteceu no teu programa “Olá, mundo!”.
Aqui está a primeira parte do puzzle:

```rust
fn main() {

}
```

Estas linhas definem uma *função* em Rust. A função `main` é especial: é
sempre o primeiro código que é executado para cada programa executável de Rust. A primeira
linha declara uma função chamada `main` que não tem parâmetros e não retorna
nada. Se houvesse parâmetros, os seus nomes iriam para dentro de parênteses,
`(` e `)`.

Observa também que o corpo da função está envolvido em chavetas arredondadas, `{` e `}`.
O Rust exige estas em torno de todos os corpos das funções. É considerado um bom estilo para
colocar as aberturas de chavetas arredondadas na mesma linha que a declaração da função,
com um espaço no meio

> No momento de escrever, um formatador automático, `rustfmt`, está abaixo
> desenvolvimento. Se tu quiseres manter um estilo padrão nos projetos Rust,
> `rustfmt` é uma ferramenta que irá formatar o teu código num estilo específico. O
> plano é eventualmente incluí-lo com a distribuição padrão do Rust, como
> `rustc`, então, dependendo de quando tu vais ler este livro, tu podes tê-lo já
> instalado! Verifica a documentação online para obteres mais detalhes.

Dentro da função `main`, temos este código:

```rust
    println!("Hello, world!");
```

Esta linha faz todo o trabalho neste pequeno programa: imprime texto para o
ecrã. Há uma série de detalhes a serem observados aqui. O primeiro é que o estilo
Rust é recuar com quatro espaços, e não uma aba.

O segundo detalhe importante é a chamada `println!`. Este código está a chamar o Rust
*macro*. Se chamasses uma função em vez disto, seria inserido como
`println` (sem o`!`). Vamos discutir as macros Rust em mais detalhe em
Apêndice D, mas, por enquanto tu precisas de saber que quando vês um `!`
significa que estás a chamar por uma macro ao invés de uma função normal.

<!-- Posso sugerir apenas cortar esta próxima seção de macro -- por causa da
introdução, nós realmente não precisamos desta informação, e eu sinto que este primeiro exercício
deve ser curto e doce e simples -->
<!-- Sinto-me bem com isto; é uma pergunta bastante comum que algumas pessoas
fazem neste ponto, mas sinto-me bem com aquelas pessoas que têm que fazer alguma pesquisa
on-line se são curiosos /Carol -->

A seguir vem `"Hello, world!"`, que é uma *string*. Nós passamos esta string como um
argumento para `println!` e o efeito total é que a string é impressa para
o ecrã. Bastante fácil!

Terminamos a linha com um ponto e vírgula `;`, o que indica que esta expressão é
sobre, e a próxima está pronta para começar. A maioria das linhas de código Rust termina com um
`;`.

### Compilar e Executar São Etapas Separadas

Acabaste de ver como executar um programa recém-criado, então agora vamos partir este
processo e examinar cada passo.

Antes de executar um programa Rust, precisas compilá-lo usando o compilador Rust
ao inserir o comando `rustc` e passar o nome do arquivo de origem,
como isto:

```text
$ rustc main.rs
```

Se tiveres conhecimentos de C ou C ++, notarás que isto é semelhante ao
`gcc` ou `clang`. Depois de compilares com sucesso, Rust produz um binário
executável.

No Linux, Mac e PowerShell no Windows, podes ver o executável
inserindo o comando `ls` no teu shell da seguinte forma:

```text
$ ls
main  main.rs
```

Com CMD no Windows, tu colocarias:

```cmd
> dir /B %= the /B option says to only show the file names =%
main.exe
main.pdb
main.rs
```

Isto mostra que temos dois arquivos: o código-fonte, com a extensão *.rs* e
o executável (*main.exe* no Windows, *main* em qualquer outro lugar). Tudo o que resta
para fazer a partir daqui é executar o arquivo *main* ou *main.exe*, desta forma:

```text
$ ./main  # or .\main.exe on Windows
```

Se *main.rs* fosse o teu programa “Olá, mundo!, isto imprimiria `Olá,
mundo!` para o teu terminal.

Se tiveres conhecimentos de um idioma dinâmico como o Ruby, Python ou JavaScript, não
o poderás usar para compilar e executar um programa como etapas separadas. Rust é uma
linguagem *compilada com antecedência*, o que significa que tu podes compilar um programa,
dar o executável a outras pessoas, e elas podem executá-lo, mesmo sem ter
o Rust instalado. Se forneceres a alguém um arquivo `.rb`, `.py` ou `.js`, por outro
lado, eles precisam ter uma implementação Ruby, Python ou JavaScript instalada
(respectivamente), mas tu só precisas de um comando para compilar e executar o teu
programa. Tudo é uma compensação no design do idioma.

Compilar apenas com `rustc` é bom para programas simples, mas como o teu projeto
cresce, tu vais querer gerir todas as opções e facilitar a
compartilha do teu código. De seguida, vamos apresentar-te uma ferramenta chamada Cargo, que
te vai ajudar a escrever programas Rust do mundo real.
