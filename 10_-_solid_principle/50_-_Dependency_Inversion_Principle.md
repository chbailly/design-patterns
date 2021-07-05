Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2021-05-20T00:03:19+02:00

#  50 - Dependency Inversion Principle 
Créée le jeudi 20 mai 2021

Ne pas confondre avec Dependency Injection

High-level modules should not depend on low-level modules. Both should depend on abstractions.

##  bad 


Research: high level
RelasionSgios: low level

```cpp
public class Research
{
  public Research(Relationships relationships)
  {
    // high-level: find all of John's children
    var relations = relationships.Relations;
    foreach (var r in relations
      .Where(x => x.Item1.Name == "John"
               && x.Item2 == Relationship.Parent))
    {
      WriteLine($"John has a child called {r.Item3.Name}");
    }
  }
}
```

## good

Faire une interface 


```cpp
public interface IRelationshipBrowser
{
  IEnumerable<Person> FindAllChildrenOf(string name);
}
```

Que Relationships va implémenter

et se baser sur cette interface

```cpp
public Research(IRelationshipBrowser browser)
{
  foreach (var p in browser.FindAllChildrenOf("John"))
  {
    WriteLine($"John has a child called {p.Name}");
  }
}
```






