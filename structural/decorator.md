
A la python
===

```c++
// return type and argument list
template <typename R, typename... Args> 
struct Logger3<R(Args...)>
{
  Logger3(function<R(Args...)> func, const string& name)
    : func{func},
      name{name}
  {
  }

  R operator() (Args ...args)
  {
    cout << "Entering " << name << endl;
    R result = func(args...);
    cout << "Exiting " << name << endl;
    return result;
  }

  function<R(Args ...)> func;
  string name;
};

template <typename R, typename... Args>
auto make_logger3(R (*func)(Args...), const string& name)
{
  return Logger3<R(Args...)>(
    std::function<R(Args...)>(func), 
    name);
}
```

Classes enrichissent la clase encapsulée
====

```c++
struct TransparentShape : Shape
{
  Shape& shape;
  uint8_t transparency;


  TransparentShape(Shape& shape, const uint8_t transparency)
    : shape{shape},
      transparency{transparency}
  {
  }
```
