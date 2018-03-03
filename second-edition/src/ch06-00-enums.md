# Enums e Correspondência de Padrões

Neste capítulo, vamos analisar *enumerações*, também referidas como *enums*.
Enums permite que tu definas um tipo, enumerando os seus possíveis valores. Primeiro,
vamos definir e usar um enum para mostrar como um enum pode codificar o significado junto com
os dados. De seguida, exploraremos um enum particularmente útil, chamado `Opção`, que
expressa que um valor pode ser algo ou nada. Então, olharemos para
o padrão de correspondência na expressão `match` torna mais fácil executar diferentes
códigos para diferentes valores de um enum. Finalmente, abordaremos como a `if let`
construção é outro idioma conveniente e conciso disponível para tu lidares con os
enums no teu código.

Enums são uma característica em muitos idiomas, mas as suas capacidades diferem em cada um dos
idiomas. Os enums de Rust são mais semelhantes aos *tipos de dados algébricos* idiomas funcionais
como F#, OCaml e Haskell.
