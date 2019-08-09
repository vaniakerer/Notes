# Notes

## Kotlin

1. You should unpack an array to provide it in a function with #vararg

`val args: Array<String>.....
 val lis t = listO f( "args: ", *args)`
 
 2. String.toRegex()
 
 ## Interfaces.
 
Должны явно реализовать метод, если
наследуется несколько его реализаций
Ключевое слово «super» с именем супертипа в угловых
скобках определяет родителя, чей метод будет вызван

Якщо тільки один інтерфейс має реалізацію метода із одинаковими назвами - можна викликати як super.method()
Якщо мають декілька - super<InterfaceName>.method()
 
 ```
 interface Clickable {
    fun a()
    fun b() = "Clickable b"
    fun c() = "Focusable c"
 }

 interface Focusable {
    fun a()
    fun b() = "Focusable b"
    fun c(): String
    fun d()
 }
 
 class Implementation : Clickable, Focusable {
    override fun a() {}
    override fun b() = super<Clickable>.b()
    override fun c() = super.c()
    override fun d() {}
 }

    println(implementation.b())
    println(implementation.c())
```

###### Output:
    
 Clickable b
 Focusable c
 
  ## Astract classes.
  
 ``` 
 abstract class Animated {
   
       abstract fun animate() // by default opened
   
       open fun stopAnimating() {
          // just opened
       }

       fun animateTwice() {
          // final (not opened)
          //it does not metter, that class is abstract. 
        }
   }
   ```
  
 
 ## Modifiers.
```
  Модификатор                   Член класса                  Объявление верхнего уровня
  public (по умолчанию)       Доступен повсюду               Доступно повсюду
  internal                    Доступен только в модуле       Доступно в модуле
  protected                   Доступен в подклассах          —
  private                     Доступен в классе              Доступно в файле
```

  Клас із модифікатором internal не може мати пеблічних extention functions

  Клас із модифікатором private буде скомпілений в клас із модифікатором package default
  internal -> public. 
  Із java-коду можна обійти модифікатор internal
