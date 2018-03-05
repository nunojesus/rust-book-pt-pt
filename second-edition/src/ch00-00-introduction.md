# Introdução

Bem-vindo ao "The Rust Programming Language", um livro introdução sobre o Rust.

Rust é uma linguagem de programação que ajuda-te a escrever mais rápido e software mais confiável.
A ergonomia de alto nível e o controle de baixo nível geralmente estão em desacordo um com o
outro no design da linguagem de programação; Rust representa este desafio.
Através do balanceamento da poderosa capacidade técnica e de uma grande experiência do desenvolvedor,
Rust dá-te a opção de controlar detalhes de baixo nível (como o uso da memória)
sem todos aqueles problemas tradicionalmente associados a este controle.

## Para Quem é o Rust

Rust é ótimo para muitas pessoas por várias razões. Vamos discutir alguns dos
grupos mais importantes.


### Equipas de Desenvolvedores

Rust está a provar que é uma ferramenta produtiva para colaborar entre grandes equipas de
desenvolvedores com diferentes níveis de conhecimento de programação de sistemas. O código de baixo nível
é propenso a uma variedade de erros subtis, que na maioria das outras línguas só podem ser
através de testes extensivos e revisão cuidadosa do código por desenvolvedores
experientes. Em Rust, o compilador desempenha um papel de guardião ao recusar-se o
código de compilação com estes tipos de erros--incluindo erros de concorrência. Pelo trabalho
ao lado do compilador, a equipa pode passar mais tempo focando-se na lógica do
programa em vez de perseguir os erros.

Rust também traz ferramentas contemporâneas de desenvolvedores para o mundo da programação de sistemas:

* Cargo, o gestor de dependência incluídas e a ferramenta de construção, faz a adição,
  compila e gere dependências indolores e consistentes em todo o ecossistema 
  Rust.
* Rustfmt garante um estilo de codificação consistente entre os desenvolvedores.
* O Servidor de Linguagem Rust alimenta a integração do IDE para a conclusão do código e
   mensagens de erro em linha.

Ao usares estas e outras ferramentas no ecossistema Rust, os desenvolvedores podem ser
produtivos ao escrever código de nível de sistema.

### Estudantes

Rust é para estudantes e pessoas interessadas em aprender sobre conceitos
de sistemas. Muitas pessoas aprenderam sobre os tópicos como sistemas operacionais
de desenvolvimento através do Rust. A comunidade fica feliz em responder às perguntas dos alunos.
Através de esforços como este livro, as equipas Rust querem criar conceitos de sistemas
mais acessíveis para mais pessoas, especialmente aquelas que começam com a
programação.

### Empresas

O Rust é usado na produção por centenas de empresas, grandes e pequenas, para uma
variedade de tarefas, como ferramentas de linha de comando, serviços web, ferramentas DevOps,
dispositivos embutidos, análise e transcodificação de áudio e vídeo, criptografia,
bioinformática, motores de pesquisa, internet de aplicativos de coisas, máquina
de aprendizagem e até mesmo grandes partes do navegador Firefox.

### Desenvolvedores de Código Aberto

Rust é para pessoas que querem construir a linguagem de programação Rust, comunidade,
ferramentas para desenvolvedores e bibliotecas. Adorariamos que contribuices para a linguagem
Rust.

### Pessoas que Valorizam Velocidade e Estabilidade

Por velocidade, queremos dizer tanto a velocidade dos programas que o Rust permite criar e
a velocidade na qual Rust permite que tu os escrevas. As verificações do compilador Rust garantem
estabilidade através de adições de características e refatoração, ao contrário do frágil
código legado em linguagens sem estas verificações que os desenvolvedores têm medo de
modificar. Ao lutar por abstrações de custo zero, recursos de nível superior que
compilam o código de nível inferior tão rápido quanto o código escrito manualmente, o Rust esforça-se para
fazer do código seguro, seja também um código rápido.

Esta não é uma lista completa de todos que a linguagem Rust pretende apoiar, mas
estes são alguns dos principais interessados. Em geral, a maior ambição do Rust
é de tomar compromissos aceites pelos programadores há décadas e
eliminar a dicotomia. Segurança *e* produtividade. Velocidade *e* ergonomia.
Experimenta o Rust e vê se as tuas opções funcionam para ti.

## Para Quem é Este Livro

Este livro assume que tu escreveste um código em alguma outra linguagem de programação,
mas não faz nenhum pressuposto sobre qual delas. Nós tentamos fazer que o
material seja amplamente acessível para aqueles que têm grandes conhecimentos
sobre programação. Nós não passamos muito tempo a falar sobre o que *é* a programação 
ou como pensar sobre isto; alguém que seja novo a programar inteiramente seria melhor
servido se lê-se um livro específico para introdução à programação.

## Como Usar o Livro

Este livro geralmente assume que tu estás a lêr isto da frente para trás, isto é,
capítulos posteriores desenvolvem os conceitos em capítulos anteriores e anteriores
capítulos podem não aprofundar detalhadamente sobre um tópico, revisitando o tópico num capítulo
mais à frente.

Existem dois tipos de capítulos neste livro: capítulos conceituais e projeto de
capítulos. Nos capítulos de conceito, tu aprenderás sobre um aspecto de Rust. Nos
capítulos de projetos, construiremos pequenos programas juntos, aplicando o que temos
aprendido até agora. Os capítulos 2, 12 e 20 são capítulos do projeto; o resto é
capítulos de conceito.

Além disto, o Capítulo 2 é uma introdução prática ao Rust como uma linguagem. Nós
iremos cobrir conceitos a  alto nível e os capítulos posteriores entrarão em detalhes.
Se és o tipo de pessoa que gosta de sujar as mãos de imediato,
o Capítulo 2 é ótimo para isto. Se tu fores *realmente* este tipo de pessoa, tu podes
até mesmo se quiseres ignorar o Capítulo 3, que fala sobre recursos que são muito parecidos
para outras linguagens de programação, e vai direto para o Capítulo 4 para aprenderes sobre
o sistema de propriedade do Rust. Em contraste, se tu és particularmente aprendiz meticuloso
que prefere aprender todos os detalhes antes de passar para o próximo, tu podes
se quiseres ignorar o Capítulo 2 e ir direto para o Capítulo 3.

O Capítulo 5 discute as estruturas e métodos, e o Capítulo 6 fala sobre enums, expressões
`match` e a construção do fluxo de controle `if let`. Estruturas e enums são as
maneiras de fazer tipos personalizados em Rust.

No Capítulo 7, tu podes aprender sobre o sistema de módulos de Rust e a privacidade para
organizares o teu código e a tua API pública. O capítulo 8 discute algumas coisas comuns
estruturas de dados de coleta fornecidas pela biblioteca padrão: vetores, strings,
e mapas de hash. O capítulo 9 trata da filosofia de tratamento dos erros do Rust e
técnicas.

O Capítulo 10 aprofunda sobre os genéricos, traços e vidas, o que te dá o poder
para definir o código que se aplica a vários tipos. O Capítulo 11 é todo sobre testes,
o que ainda é necessário, mesmo com as garantias de segurança do Rust para garantir que a tua
lógica do programa está correta. No Capítulo 12, vamos construir um subconjunto da
funcionalidade da ferramenta da linha de comando `grep` que procura texto dentro
dos arquivos e usaremos muitos dos conceitos que discutimos nos capítulos anteriores.

O Capítulo 13 explora os encerramentos e iteradores: características do Rust que vêm de
linguagens de programação funcional. No Capítulo 14, exploraremos mais sobre Carga
e fala sobre as melhores práticas para compartilhar as tuas bibliotecas com outras pessoas. Capítulo
15 discute os ponteiros inteligentes fornecidos pela biblioteca padrão e os traços
que permitem a sua funcionalidade.

No Capítulo 16, passaremos por diferentes modelos de programação simultânea e
como o Rust ajuda-te a programar sem medo usando múltiplos segmentos. O Capítulo 17
olha como as expressões Rust se comparam aos princípios de programação orientados a objetos que tu
podes estar familiarizado com.

O Capítulo 18 é uma referência em padrões e correspondência de padrões, que são poderosas
formas de expressar idéias em todos os programas Rust. Capítulo 19 é um smorgasbord
de tópicos avançados que poderás estar interessado, incluindo o inoperante Rust e
mais sobre vidas, traços, tipos, funções e fechamentos.

No Capítulo 20, terminaremos com um projeto onde implementaremos um nível baixo
de servidor web multithread!

Finalmente, existem alguns apêndices. Estes contêm informações úteis sobre a
linuaem num formato mais parecido com a referência.

No final, não existe uma maneira errada de ler um livro: se quiseres avançar, força!
Tu poderás ter que saltar de volta se achares as coisas confusas. Faz o que
funciona melhor para ti.

Uma parte importante do processo de aprender Rust é aprender a ler as
mensagens de erro que o compilador te dá. Como tal, vamos mostrar muito
código que não compila e a mensagem de erro que o compilador irá mostrar 
nesta situação. Como tal, se tu escolheres um exemplo aleatório, pode não compilar!
Lê o texto ao redor para garantir que não tenhas escolhido
um dos exemplos em andamento.

## Contribuir para o livro

Este livro é de código aberto. Se encontrares um erro, não hesites em indicar
um problema ou envia uma solicitação de tração [no GitHub]. Consulta [CONTRIBUTING.md] para
mais detalhes.


[on GitHub]: https://github.com/rust-lang/book
[CONTRIBUTING.md]: https://github.com/rust-lang/book/blob/master/CONTRIBUTING.md
