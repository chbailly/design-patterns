
Au lieu d'appeller  
BankAccount.deposit(value)

On va enregistrer les commandes

```
CompositeBankAccountCommand commands {
  BankAccountCommand{ba, BankAccountCommand::deposit, 100},
  BankAccountCommand{ba, BankAccountCommand::withdraw, 200}
};
```

Avantage:
* on record la liste des commandes
* on peut faire un undo

```c++
struct Command
{
  virtual ~Command() = default;
  virtual void call() const = 0;
  virtual void undo() const = 0;
};

// should really be BankAccountCommand
struct BankAccountCommand : Command
{
  BankAccount& account;
  enum Action { deposit, withdraw } action;
  int amount;

  BankAccountCommand(BankAccount& account, 
    const Action action, const int amount)
    : account(account), action(action), amount(amount) {}

  void call() const override
  {
    switch (action)
    {
    case deposit:
      account.deposit(amount);
      break;
    case withdraw: 
      account.withdraw(amount);
      break;
    default: break;
    }
  }
  ```
