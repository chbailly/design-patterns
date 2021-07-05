Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2021-05-20T00:01:28+02:00

#  40- Interface segragation principle
Créée le jeudi 20 mai 2021

```cpp
class MyFavouritePrinter /* : IMachine */
{
  void Print(Document d) {}
  void Fax(Document d) {}
  void Scan(Document d) {}
};
```

Faire des interfaces séparés plutot que d'avoir à l'implémenter qu'une partie (et ensuite les composer en héraitant de plusieurs interfaces)
