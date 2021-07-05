Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2021-05-19T21:37:57+02:00

# 10- Single Responsibility Principle
Créée le mercredi 19 mai 2021

A personal journal ! just stores the entry. **Not another responsibility (persistence)** 

For persistense , instead of having a method:

```cpp
public void Save(string filename, bool overwrite = false)
{
  File.WriteAllText(filename, ToString());
}
```

To change persistence in all classes (journal, person, ..) you have to change code everywhere. 

Instead create a class for persistence:

```cpp
public class PersistenceManager
{
  public void SaveToFile(Journal journal, string filename,
                         bool overwrite = false)
  {
  if (overwrite || !File.Exists(filename))
    File.WriteAllText(filename, journal.ToString());
  }
}
```
