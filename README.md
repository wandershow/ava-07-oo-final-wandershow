# AVA 07: projeto final de orientação a objetos

> Minha solução em Java para o trabalho da disciplina de Programação Orientada a Objetos (IFRS, 2018). Tema: projeto final de orientação a objetos. O enunciado original está logo abaixo.

---

# OO-final

_Classroom link:_ <https://classroom.github.com/a/2Z78n1lA>

#### Prazo: 2018-12-06 Peso: 2.2 pt

<http://youtu.be/NUIZvAe3RBg>

#### Regras

- A biblioteca padrão (API) do Java não pode ser usada (`ArrayList`, `Math`, etc), incluindo os métodos de `Integer` (`parseInt`, etc) e `String`, exceto `length`, `charAt` e `equals`;
- Pode-se introduzir novas classes, atributos e métodos desde que não impacte nos Casos de Teste;
- Os Casos de Teste não podem ser alterados (se um erro no teste for encontrado, informe o professor);
- Os Casos de Teste estão agrupados por funcionalidades, sendo que o objetivo não é simplesmente passar nos testes, mas cumprir a funcionalidade!
- Outros casos de teste semelhantes, que testam a mesma funcionalidade, podem ser incluídos para a correção, evitando que algum método seja implementado como constante apenas para passar no teste e não para cumprir a funcionalidade, ex: `int count() { return 0; }`.

### Fellowship of The Ring

Implementar a _Sociedade do Anel_, usando relacionamentos, herança, sobrecarga, comandos, consultas, etc, conforme os casos de teste a seguir. A pontuação de cada seção está anotada com comentários no formato `// --> ...`

**IMPORTANTE: observar as restrições acima antes de implementar**

**Implemente as funcionalidades segundo os seguintes Casos de Teste:**

```java
// Initializing People
Person Gandalf  = new Wizard("Gandalf");
Person Aragorn  = new Human("Aragorn");
Person Gimli    = new Dwarf("Gimli");
Person Legolas  = new Elf("Legolas");
Person Boromir  = new Human("Boromir");
Person Frodo    = new Hobbit("Frodo");
Person Sam      = new Hobbit("Sam");
Person Meriadoc = new Hobbit("Meriadoc");
Person Peregrin = new Hobbit("Peregrin");

// Initializing Fellowships
Fellowship FellowshipOfTheRing = new Fellowship("of The Ring");
Fellowship EvilFellowship      = new Fellowship("of Evil");

// 0.3pts -> Every person has a name
System.out.println(Gandalf.name().equals("Gandalf"));
System.out.println(Gandalf.toString().equals("Gandalf"));

// 0.3pts -> There is no members yet
