# Princípio de segregação em Interfaces

**`Aviso! Este texto abaixo é uma tradução do artigo de Robert C. Martin feito em 1996 para a revista` [_C++ Report_](https://drive.google.com/file/d/0BwhCYaYDn8EgOTViYjJhYzMtMzYxMC00MzFjLWJjMzYtOGJiMDc5N2JkYmJi/view?resourcekey=0-3H2Ld4l-dIZZVRmHSpNLcA). O texto pode conter alterações para o melhor entendimento dos leitores**

Esta é a quarta coluna do meu _caderno de engenharia_ para a _C++ Report_. Os artigos que aparecem nesta coluna se concentram no uso de C++ e OOD (Oriented Object Design - Design Orientado a Objetos) e abordam questões de software engenharia.

Eu almejo artigos que são pragmáticos e diretamente úteis para o engenheiro de software em seu dia-a-dia. Nesses artigos eu procuro fazer uso da nova Linguagem de Modelagem unificada definida for Booch e Rumbaugh (UML Versão 0.8) para documentar projetos orientados a objetos.

## Introdução

Na minha última coluna (maio de 96), discuti o princípio da `Inversão de Dependência (DIP)`. Este princípio afirma que os módulos que encapsulam a política de alto nível não devem depender de módulos que implementam detalhes.

Em vez disso, ambos os tipos de módulos devem depender abstrações. Para ser mais sucinto e simplista, as classes abstratas não devem depender de
aulas concretas, pelo contrário, `classes concretas devem depender de classes abstratas`. Um bom exemplo de
este princípio é o padrão [TEMPLATE METHOD](https://refactoring.guru/pt-br/design-patterns/template-method) do livro [Design Patterns](https://www.amazon.com.br/Padr%C3%B5es-Projetos-Solu%C3%A7%C3%B5es-Reutiliz%C3%A1veis-Orientados/dp/8573076100/ref=asc_df_8573076100/?tag=googleshopp00-20&linkCode=df0&hvadid=379748659420&hvpos=&hvnetw=g&hvrand=12796718980143394616&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=1001767&hvtargid=pla-812887614857&psc=1) do GOF([Gang of Four](http://wiki.c2.com/?GangOfFour)).

Nesse padrão, um algoritmo de alto nível é codificado em uma classe base abstrata e faz uso de puro de funções virtuais para implementar seus detalhes. As classes derivadas implementam essas funções virtuais detalhadas.
ções. Assim, a classe que contém os detalhes depende da classe que contém as abstrações.

