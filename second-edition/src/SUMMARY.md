# A Linguagem de Programação Rust

[Prefácio](foreword.md)
[Introdução](ch00-00-introduction.md)

## Começando

- [Começando](ch01-00-getting-started.md)
    - [Instalação](ch01-01-installation.md)
    - [Olá, Mundo!](ch01-02-hello-world.md)
    - [Olá, Cargo!](ch01-03-hello-cargo.md)

- [Tutorial Jogo da Advinha](ch02-00-guessing-game-tutorial.md)

- [Conceitos Comuns de Programação](ch03-00-common-programming-concepts.md)
    - [Variáveis e Mutabilidade](ch03-01-variables-and-mutability.md)
    - [Tipos de Dados](ch03-02-data-types.md)
    - [Como as Funções Funcionam](ch03-03-how-functions-work.md)
    - [Comentários](ch03-04-comments.md)
    - [Estruturas de Controlo](ch03-05-control-flow.md)

- [Entender "Ownership"](ch04-00-understanding-ownership.md)
    - [O que é "Ownership"?](ch04-01-what-is-ownership.md)
    - [Referencias e "Borrowing"](ch04-02-references-and-borrowing.md)
    - ["Slices"](ch04-03-slices.md)

- [Usar Estruturas para Estruturar Dados Relacionados](ch05-00-structs.md)
    - [Definir e Inicializar Estruturas](ch05-01-defining-structs.md)
    - [Um Exemplo de Programa Usando Estruturas](ch05-02-example-structs.md)
    - [Sintaxe de Métodos](ch05-03-method-syntax.md)

- [Enumerados e Correspôndencia de Padrões](ch06-00-enums.md)
    - [Definir um Enumerado](ch06-01-defining-an-enum.md)
    - [Usar o Operador de Estruturas de Controlo `match`](ch06-02-match.md)
    - [Estruturas de Controlo Resumidas com `if let`](ch06-03-if-let.md)

## Literacia Básica do Rust

- [Módulos](ch07-00-modules.md)
    - [`mod` e o Sistema de Arquivos](ch07-01-mod-and-the-filesystem.md)
    - [Controlar a Visibilade com `pub`](ch07-02-controlling-visibility-with-pub.md)
    - [Referir Nomes em Módulos Diferentes](ch07-03-importing-names-with-use.md)

- [Coleções Comuns](ch08-00-common-collections.md)
    - [Vetores](ch08-01-vectors.md)
    - [Strings](ch08-02-strings.md)
    - [Hash Maps](ch08-03-hash-maps.md)

- [Tratamento de Erros](ch09-00-error-handling.md)
    - [Erros Inrecuperáveis com `panic!`](ch09-01-unrecoverable-errors-with-panic.md)
    - [Erros Recuperáveis com `Result`](ch09-02-recoverable-errors-with-result.md)
    - [To `panic!` or Not To `panic!`](ch09-03-to-panic-or-not-to-panic.md)

- [Tipos Genéricos, Traits, e Lifetimes](ch10-00-generics.md)
    - [Tipos de Dados Genéricos](ch10-01-syntax.md)
    - [Traits: Definir Comportamento Partilhado](ch10-02-traits.md)
    - [Validar Referências com Lifetimes](ch10-03-lifetime-syntax.md)

- [Testar](ch11-00-testing.md)
    - [Escrever testes](ch11-01-writing-tests.md)
    - [Correr testes](ch11-02-running-tests.md)
    - [Organização dos Testes](ch11-03-test-organization.md)

- [Um projeto I/O: Construir um Programa de Linha de Comandos](ch12-00-an-io-project.md)
    - [Aceitar Argumentos da Linha de Comandos](ch12-01-accepting-command-line-arguments.md)
    - [Ler um Ficheiro](ch12-02-reading-a-file.md)
    - [Restruturar para Melhorar a Modularidade e Tratamento de Erros](ch12-03-improving-error-handling-and-modularity.md)
    - [Desenvolver a Funcionalidade da Biblioteca com Desenvolvimento Orientado a Testes](ch12-04-testing-the-librarys-functionality.md)
    - [Trabalhar com Variáveis de Ambiente](ch12-05-working-with-environment-variables.md)
    - [Escrever Messagens de Erros para Standard Error invés de Standard Output](ch12-06-writing-to-stderr-instead-of-stdout.md)

## Pensar em Rust

- [Caracteristícas de Linguagem Funcional: Iteradors e "Closures"](ch13-00-functional-features.md)
    - [Closures: Funções Anónimas que Conseguem Capturar o Seu Ambiente](ch13-01-closures.md)
    - [Processar uma Série de Itens com Iteradores](ch13-02-iterators.md)
    - [Melhorar o Nosso Projeto I/O](ch13-03-improving-our-io-project.md)
    - [Comparar o Performance: Ciclos vs. Iteradores](ch13-04-performance.md)

- [Mais sobre Cargo e Crates.io](ch14-00-more-about-cargo.md)
    - [Customizar Builds com Perfis de Lançamento](ch14-01-release-profiles.md)
    - [Publicar uma Crate para Crates.io](ch14-02-publishing-to-crates-io.md)
    - [Espaçoes de Trabalho do Cargo](ch14-03-cargo-workspaces.md)
    - [Instalar Binários do Crates.io com `cargo install`](ch14-04-installing-binaries.md)
    - [Extender Cargo com Comandos Personalizados](ch14-05-extending-cargo.md)

- [Ponteiros Inteligentes](ch15-00-smart-pointers.md)
    - [`Box<T>` Aponta para Dados Localizados no Heap e têm um Tamanho Conhecido](ch15-01-box.md)
    - [O Trait `Deref` Permite Acesso aos Dados a Partir de uma Referência](ch15-02-deref.md)
    - [O Trait `Drop` Corre Código na Limpeza](ch15-03-drop.md)
    - [`Rc<T>`, o Ponteiro Inteligente que Conta Referências](ch15-04-rc.md)
    - [`RefCell<T>` e o Padrão de Mutabilidade Interna](ch15-05-interior-mutability.md)
    - [Criar Ciclos de Referência e Escoar Memória é Seguro](ch15-06-reference-cycles.md)

- [Concorrência sem Medo](ch16-00-concurrency.md)
    - [Threads](ch16-01-threads.md)
    - [Envio de Mensagens](ch16-02-message-passing.md)
    - [Estado Partilhado](ch16-03-shared-state.md)
    - [Concorrência Extensível: `Sync` e `Send`](ch16-04-extensible-concurrency-sync-and-send.md)

- [Rust é uma Linguagem de Programação Orientada a Objetos?](ch17-00-oop.md)
    - [O Que Significa Orientado a Objetos?](ch17-01-what-is-oo.md)
    - [Objetos Trait para Usar Valores de Tipos Diferentes](ch17-02-trait-objects.md)
    - [Implementações do Padrão de Design Orientado aos Objetos](ch17-03-oo-design-patterns.md)

## Tópicos Avançados

- [Padrões Correspôndem à Estrutura de Valores](ch18-00-patterns.md)
    - [Todos os Lugares onde Padrões Podem ser Usados](ch18-01-all-the-places-for-patterns.md)
    - [Refutibilidade: Se um Padrão pode Falhar a Corresponder](ch18-02-refutability.md)
    - [Todos os Sintaxes de Padrões](ch18-03-pattern-syntax.md)

- [Características Avançadas](ch19-00-advanced-features.md)
    - [Rust Inseguro](ch19-01-unsafe-rust.md)
    - [Lifetimes Avançadas](ch19-02-advanced-lifetimes.md)
    - [Traits Avançadas](ch19-03-advanced-traits.md)
    - [Tipos Avançados](ch19-04-advanced-types.md)
    - [Funções e Closures Avançadas](ch19-05-advanced-functions-and-closures.md)

- [Projeto Final: Construir um Servidor Web com Múltiplas Threads](ch20-00-final-project-a-web-server.md)
    - [Servidor Web com uma Única Thread](ch20-01-single-threaded.md)
    - [Transformar o Nosso Servidor de Thread Única para um Servidor de Múltiplas Threads](ch20-02-multithreaded.md)
    - [Encerramento e Limpesa Graciosa](ch20-03-graceful-shutdown-and-cleanup.md)

- [Apêndice](appendix-00.md)
    - [A - Palavras Chave](appendix-01-keywords.md)
    - [B - Operadores e Símbolos](appendix-02-operators.md)
    - [C - Traits Deriváveis](appendix-03-derivable-traits.md)
    - [D - Macros](appendix-04-macros.md)
    - [E - Traduções](appendix-05-translation.md)
    - [F - Características Mais Modernas](appendix-06-newest-features.md)
    - [G - Como o Rust é Feito e “Nightly Rust”](appendix-07-nightly-rust.md)
