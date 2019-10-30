# Site do Grupo de Estudos Em Programação Funcional

Site do grupo de estudos de programação funcional da UFFS campus chapecó, orientado pelo professor Emílio Wuerges. Desenvolvido pelos próprios alunos, para a comunidade em geral.

## Introdução

O site foi construído sob a plataforma [Hakyll](https://jaspervdj.be/hakyll/index.html), um gerador de páginas estáticas em haskell. Nele propõe a divulgar relatórios dos encontros dos grupos, discussões e artigos sobre o tema de programação funcional. No futuro também é provável que contenha um tutorial de haskell a partir de materias recolhidos por todos do grupo. Também haverá referências de links para aprender programação funcional.

## Instalação do projeto

Para instalar o projeto é necessário ter instalado na máquina a plataforma [Stack](https://docs.haskellstack.org/en/stable/README/). Recomendável o uso do ghc dentro do mesmo ambiente. Para instalar a dependência do projeto, rode o seguinte comando:

```
$ stack install hakyll --resolver lts-12.26
```

Após isto baixe o zip do projeto ou clone-o
```
$ git clone https://github.com/ChaosAmd/grupo-funcional-site.git
````
Doravante à nova pasta, execute o stack init para gerar o yaml. Importante notar que a versão é lts-12.26, para não dar conflito com outros ambientes stack.

```
$ cd instaled_path/grupo-funcional-site
$ stack init stack init --resolver lts-12.26
```

Caso ocorra erro na instalação, comunique na aba Issues do página deste github.

## Colaboração

Para contribuir, dê um fork no projetok, crie um branch com a feature desejada e seja feliz. A versão do stack utilizada é 12.4, mas pretende ser atualizada.
