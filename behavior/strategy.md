Motivation
===

High level algorithm (making hot beverage) et low level algorithm (specific for tea, hot chocolate)

Dynamic
=====

``` c++

num class OutputFormat
{
  Markdown,
  Html
};

struct ListStrategy
{
  virtual ~ListStrategy() = default;
  virtual void add_list_item(ostringstream& oss, const string& item) {};
  virtual void start(ostringstream& oss) {};
  virtual void end(ostringstream& oss) {};
};

struct MarkdownListStrategy : ListStrategy
{
  void add_list_item(ostringstream& oss, const string& item) override
  {
    oss << " * " << item << endl;
  }
};

struct HtmlListStrategy : ListStrategy
{
  void start(ostringstream& oss) override
  {
    oss << "<ul>" << endl;
  }
  
  struct TextProcessor
{
 ........
private:
  ostringstream oss;
  unique_ptr<ListStrategy> list_strategy;
};
```

Static (policy)
=======

```c++
template <typename LS>
struct TextProcessor {
private:
  ostringstream oss;
  LS list_strategy;
};
```
