# Tipos Dependentes

Na programação funcional, as funções são cidadãos de primeira classe, isto é,
podem ser passadas como parâmetros em funções e serem retornadas.

De forma análoga em linguagens com tipos dependentes, os tipos são cidadãos
de primeira classe, podem ser passados como argumentos em funções e serem retonados por elas.
Não só os tipos podem ser manipulados como se fossem valores, mas os valores podem ser parte
integrante dos próprios tipos.

Observe o exemplo abaixo, que mostra uma função que retorna tipos como se fossem valores:
(Todos os exemplos neste texto serão em Idris, uma linguagem semelhante a Haskell mas com tipos dependentes.)

```
numOrChar : Bool -> Type
numOrChar True = Nat
numOrChar False = Char
```

Com tipos dependentes, o tipo de retorno de uma função pode depender não apenas do tipo da entrada, como neste exemplo em Haskell:

```
first :: [a] -> a
first (x:_) = x
```

mas também do **valor** da entrada. Veja um exemplo em Idris:

```
letterOrInteger : (x : Bool) -> numOrChar x
letterOrInteger True = 2
letterOrInteger False = 'b'
```

Um exemplo clássico é a definição de vetor em Idris. Perceba que o tamanho do vetor já é parte do próprio tipo do vetor --- 
um vetor com tamanho 2 possui um tipo diferente de um vetor com tamanho 3, e uma função que recebe vetores de qualquer tamanho
deve ser polimórfica:

```
data Vect : Nat -> Type -> Type where
   Nil  : Vect Z a
   (::) : a -> Vect k a -> Vect (S k) a
```

A função de concatenação faz ótimo uso dessa propriedade em seu cabeçalho. (++) recebe um vetor de tamanho *n*, outro de tamanho *m*, e retorna
um de tamanho *n + m*. O próprio cabeçalho garante que o vetor resultante sempre terá tamanho igual à soma dos dois originais. Qualquer implementação
que não garanta essa propriedade em todos os possíveis casos resultará em um erro de compilação.

```
(++) : Vect n a -> Vect m a -> Vect (n + m) a
(++) Nil       ys = ys
(++) (x :: xs) ys = x :: xs ++ ys
```

Essa é uma das principais vantagens de usar tipos dependentes, delegar *ainda mais* para o 
compilador a resposabilidade de verificar a corretude da implementação.
