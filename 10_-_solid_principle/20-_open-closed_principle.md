Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2021-05-19T21:45:04+02:00

#  20- open-closed principle 
Créée le mercredi 19 mai 2021


exemple ! Filtrage sur un/plusieurs critère


open for extension, closed for modificaiton.

Basé sur **interfaces (qui ne changent pas), et non sur des superclasses**

Extension: on implémente ces interface (les combine aussi)


Interface pour tester si filtre accèpte l'entrée;

```cpp
public abstract class ISpecification<T>
{
  public abstract bool IsSatisfied(T p);
```


On peyt implémenter ColorSpecification, SizeSpecification, AndSpecification(combine specifications)

Par ailleurs, on aura un IFilter, qui ne changera pas

```cpp
public interface IFilter<T>
{
  IEnumerable<T> Filter(IEnumerable<T> items,
                        ISpecification<T> spec);
}
```

