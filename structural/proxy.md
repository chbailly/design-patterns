

Object which has the same interface as the original object (generally encapsulates it) but implements the operations differently

Here lazy bitmap will create a bitmap only when drawing (used)

```c++
struct Image
{
  virtual ~Image() = default;
  virtual void draw() = 0;
};

struct Bitmap : Image
{
  Bitmap(const string& filename)
  {
    cout << "Loading image from " << filename << endl;
  }

  void draw() override
  {
    cout << "Drawing image" << endl;
  }
};

struct LazyBitmap : Image
{
  LazyBitmap(const string& filename): filename(filename) {}
  ~LazyBitmap() { delete bmp; }
  void draw() override
  {
    if (!bmp)
      bmp = new Bitmap(filename);
    bmp->draw();
  }
  ```
