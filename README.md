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
System.out.println(FellowshipOfTheRing.toString().equals("Fellowship of The Ring"));
System.out.println(EvilFellowship.toString().equals("Fellowship of Evil"));
System.out.println(EvilFellowship.count() == 0);
System.out.println(FellowshipOfTheRing.count() == 0);
System.out.println(FellowshipOfTheRing.hasNoMembers() == true);
System.out.println(FellowshipOfTheRing.hasMembers() == false);

// 0.3pts -> Members count from 1 (not 0)
System.out.println(FellowshipOfTheRing.member(1) == null);
System.out.println(FellowshipOfTheRing.lastMember() == null);

// 0.3pts -> There is two members (order matters)
FellowshipOfTheRing.signUp(Gandalf); // member 1
FellowshipOfTheRing.signUp(Aragorn); // member 2
System.out.println(FellowshipOfTheRing.count() == 2);
System.out.println(FellowshipOfTheRing.hasNoMembers() == false);
System.out.println(FellowshipOfTheRing.hasMembers() == true);

// 0.4pts -> Member is a intermediary class between Fellowship and Person
System.out.println(FellowshipOfTheRing.member(1) instanceof Member);
System.out.println(FellowshipOfTheRing.member(2) instanceof Member);

// 0.4pts -> Through Member we can access the people
System.out.println(FellowshipOfTheRing.member(1).person().name().equals("Gandalf"));
System.out.println(FellowshipOfTheRing.member(1).person().equals(Gandalf));
System.out.println(FellowshipOfTheRing.member(1).person().equals(new Wizard("Gandalf")));
System.out.println(!FellowshipOfTheRing.member(1).person().equals(Aragorn));
System.out.println(FellowshipOfTheRing.member(2).person().equals(Aragorn));

// 0.4pts -> Out of Range should not throw an exception
System.out.println(FellowshipOfTheRing.member(-1) == null);
System.out.println(FellowshipOfTheRing.member(3) == null);

// 0.4pts -> The relationship is bidirectional
System.out.println(Aragorn.fellowship() == FellowshipOfTheRing);
System.out.println(Aragorn.fellowship() != EvilFellowship);
System.out.println(Aragorn.fellowship() == Gandalf.fellowship());
System.out.println(Gimli.fellowship() == null);

System.out.println(Aragorn.isMemberOfAFellowship() == true);
System.out.println(Aragorn.isMemberOfTheFellowship(FellowshipOfTheRing) == true);
System.out.println(Aragorn.isMemberOfTheFellowship(EvilFellowship) == false);
System.out.println(Gimli.isMemberOfAFellowship() == false);
System.out.println(Gimli.isMemberOfTheFellowship(FellowshipOfTheRing) == false);
System.out.println(Gimli.isMemberOfTheFellowship(EvilFellowship) == false);

// 0.5pts -> However, a person can be member of only one fellowship
EvilFellowship.signUp(Aragorn); // Aragorn has not been included
System.out.println(EvilFellowship.count() == 0);
System.out.println(EvilFellowship.hasNoMembers() == true);
System.out.println(Aragorn.fellowship() == FellowshipOfTheRing);
System.out.println(Aragorn.isMemberOfTheFellowship(FellowshipOfTheRing) == true);
System.out.println(Aragorn.isMemberOfTheFellowship(EvilFellowship) == false);

// 0.5pts -> There is another way to join the fellowships
Gimli.join(FellowshipOfTheRing);
Gimli.join(EvilFellowship); // has no effect (already in a fellowship)
System.out.println(FellowshipOfTheRing.count() == 3);
System.out.println(FellowshipOfTheRing.member(3).person().equals(Gimli));

// 0.5pts -> Even indirect way
Legolas.join(Gimli.fellowship());
System.out.println(FellowshipOfTheRing.count() == 4);
System.out.println(FellowshipOfTheRing.lastMember().person().equals(Legolas));

// 0.5pts -> More queries
System.out.println(FellowshipOfTheRing.count("Human") == 1);
System.out.println(FellowshipOfTheRing.count("Elf") == 1);
System.out.println(FellowshipOfTheRing.count("Hobbit") == 0);
System.out.println(FellowshipOfTheRing.has("Human") == true);
System.out.println(FellowshipOfTheRing.has("Hobbit") == false);

// 0.6pts -> Get the fellowship complete (adding various members at one time)
System.out.println(FellowshipOfTheRing.count() == 4);
FellowshipOfTheRing.signUp(Boromir, Frodo);
FellowshipOfTheRing.signUp(Sam, Meriadoc, Peregrin);
System.out.println(FellowshipOfTheRing.count() == 9);
System.out.println(FellowshipOfTheRing.count("Hobbit") == 4);

// 0.6pts -> Left the FellowshipOfTheRing
System.out.println(FellowshipOfTheRing.count() == 9);
System.out.println(FellowshipOfTheRing.count("Human") == 2);
System.out.println(Boromir.fellowship() == FellowshipOfTheRing);
System.out.println(FellowshipOfTheRing.member(5).person() == Boromir);

FellowshipOfTheRing.cancel(Boromir);

System.out.println(FellowshipOfTheRing.count() == 8);
System.out.println(FellowshipOfTheRing.count("Human") == 1);
System.out.println(Boromir.fellowship() == null);
System.out.println(FellowshipOfTheRing.member(5).person() == Frodo);

// 0.6pts -> Other way to unsubscribe
Frodo.left(); // leave current fellowship if any
System.out.println(FellowshipOfTheRing.count() == 7);
System.out.println(Frodo.fellowship() == null);

Gandalf.die();
System.out.println(FellowshipOfTheRing.count() == 6);
System.out.println(Gandalf.fellowship() == null);

// 0.6pts -> People can't join fellowships after die
System.out.println(FellowshipOfTheRing.count() == 6);
Gandalf.join(FellowshipOfTheRing);
System.out.println(Gandalf.fellowship() == null);
System.out.println(FellowshipOfTheRing.count() == 6);

// 0.7pts -> Asking if people are sharing a fellowship
System.out.println(Meriadoc.isFellowOf(Peregrin) == true);
System.out.println(Meriadoc.isFellowOf(Gandalf) == false);
System.out.println(Meriadoc.isFellowOf(Boromir) == false);
System.out.println(Meriadoc.isFellowOf(Meriadoc) == true);
System.out.println(Gandalf.isFellowOf(Gandalf) == true);

// 0.7pts -> Should be reflexive
System.out.println(Meriadoc.isFellowOf(Peregrin) == Peregrin.isFellowOf(Meriadoc));
System.out.println(Meriadoc.isFellowOf(Boromir) == Boromir.isFellowOf(Meriadoc));

// 0.7pts -> Yet another way to join a fellowship
System.out.println(Boromir.fellowship() == null);
Boromir.fellow(Meriadoc);
System.out.println(Boromir.fellowship() == Meriadoc.fellowship());
System.out.println(Meriadoc.isFellowOf(Boromir) == true);
Boromir.left();
System.out.println(Boromir.fellowship() == null);
Meriadoc.fellow(Boromir);
System.out.println(Boromir.fellowship() == Meriadoc.fellowship());

// 0.7pts -> Dissolve the fellowship :(
FellowshipOfTheRing.dissolve();
System.out.println(FellowshipOfTheRing.count() == 0);
System.out.println(FellowshipOfTheRing.hasNoMembers() == true);
System.out.println(FellowshipOfTheRing.member(1) == null);
System.out.println(FellowshipOfTheRing.lastMember() == null);
```

**Somar os pontos, dividir por 10 e multiplicar por 2.2**
