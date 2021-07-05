
L'object Personne a une liste de listeners. Il appelle alors notify pour notifier changement de propriété (âge).

````c++
struct ConsoleListener : PersonListener
  {
    void person_changed(Person& p, const string& property_name, const any new_value) override
    {
      cout << "person's " << property_name << " has been changed to ";
      if (property_name == "age")
      {
        cout << any_cast<int>(new_value);
      }
      else if (property_name == "can_vote")
      {
        cout << any_cast<bool>(new_value);
      }
      cout << "\n";
    }
  };

void Person::set_age(const int age)
  {
    if (this->age == age) return;

    auto old_c_v = get_can_vote();

    this->age = age;
    notify("age", this->age);
}

  void Person::subscribe(PersonListener* pl)
  {
    listeners.push_back(pl);
  }

  void Person::notify(const string& property_name, const any new_value)
  {
    for (const auto listener : listeners)
      listener->person_changed(*this, property_name, new_value);
  }
  
````
