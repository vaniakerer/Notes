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


```
    interface User {
        val nickname: String
        val email: String
    }
    
    class ParticularUser(override val nickname) : User {
        override val nickname : String
              get() = 
              
        private fun longOperation(){
             
        }
    
    }
 ```
    
Классы, реализующие интерфейс User, должны предоставить способ получить значение свойства nickname.

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
  
  
  ## Inner classes
```
class Outer {
      inner class Inner {
          fun getOuterReference(): Outer = this@Outer
      }
  }
  ```
  Щоб звернутися до зовнішнього класу потрібно явно вказат його ім’я
  
 
  ## Fields
  
  ```
  class MyClass {
    public var asf = "asf"
        private set
  }
  
  ```
  Таким чином можна забрати дрступ до set - методу публічного поля
 
  == - equals(). === - hashCode
  
  
  ## Delegate
  
  by - можна делегувати метод та поля класу
  
  
  ## object
   
   
   1. #### Singleton.
     Не можна задат конструктори.
     Моженаслідувати інші класи
     
   2. #### Companion
     Має доступ до приватних полів класу / конструкторів
     Не перевизначаються в підкласах
     
   3. #### Aonymous class
     Може реалізовувати декілька інтерфейсів
     Може мати доступ до не filan змінних влажуємого класу
     
     
   ## Lambda
   
   1. Можна зберігати в змінну:
   ```
   val sum = { х: In t, у: In t -> х + у }
   println(sum(l, 2))
   ```
   
   ###### Output:
   3
   
   2. Можна викликати напряму:
   
   ```
   { println(42) }()
   
   or
   
   run{ pringln(42) }
   ```
   ###### Output:
   42
   
   3. Може ’захватувати’ не фінальні змінні.
   
   ```
   fun tryToCountButtonClicks(button: Button): In t {
      var clicks = 0
      button.onClick { clicks++ }
      return clicks
   }
```

   Якщо лямбда вкористовується для заміни функціонального інтерфейсу (тільки із одним методом) і не захватує змінні - то створиться тільки один екземпляр того інтерфейсу і буде перевикористовуватись (в межах вклику).
   

   ###### Output:
   0
   
   final змінні (var) просто проокидуються в лямбду
   не фінальні (val) компілятором (можливо) вставляються в клас обгортку (Ref.kt); екземпляр класу Ref є фінальним, але      змінна, яка помістилась в нього залишається не фінальною
   
   ```
   val counter = 0
   val inc = { counter++ }
   ```
   counter буде поміщений в Ref.ct
   
   4. Ссилка на функцію / конструктор
   
   через :: можна ссилатись на метод класу:
   
   ```
   data class Person(val name: String, val age: Int)

   val getAge = Person::age
   println(getAge(Person("Ivan", 22)))
   ```
   ###### Output:
   22


   або конструктор:
   
   ```   
   val createPerson = ::Person
   val p = createPerson("Alice", 29)
   println(p)
   ```
   ###### Output:
   Person(name=Alice, age=29)  
   
   Можна ссилатись на фунцію верхнього рівня (::hightLevelFunction) без імені класую
   Можна ссилатись на функцію розширення


   ## Collections
   
   #### filter
    ```
    val a = arrayListOf(1, 2, 3, 4)
    val b = a.filter { it > 2 }
    println(b.joinToString())
    ```
   ###### Output:
   3, 4
   
   filter створює нову колекцію. Змінна a залшеться без змін (1, 2, 3, 4)
   
   #### map
   Аналогічний Rx
   
   #### mapKey / mapValue / filterKeys
   ```
    val a = mapOf(1 to "Ivan", 2 to "Kerer")
    println(a.mapKeys { it.key * 2 })
    println(a.mapValues { it.value + it.key })
   ```
   
   ###### Output:
   {2=Ivan, 4=Kerer}
   {1=Ivan1, 2=Kerer2}
   
   mapKeys, mapValues - змінюють ключі/значення відповідно
   
   #### all / any / count
   ```
    val a = listOf(1, 2, 3, 4, 5, 6, 7, "asfasf", 8, 9, 10)
    println(a.all { it is Int && it > 2 })
    println(a.any { it is String })
    println(a.count { it is String })
   ```
   
   ###### Output: 
   false
   true
   1
   
   #### Difference between size and count
   
   ```
   val a = listOf(1, 2, 3, 4, 5)
   a.filter{it > 2}.size
   a.count{it > 2}
   ```
   
   із size - за рахунок оператора filter створиться проміжна колекція. 
   із count - просто порахується кількість елементів
   
   
   #### find / firstOrNull
   
   Знаходять перший елемент, який підходить
   
   #### groupBy
   
   ```
   val people = listOf(Person("Alice", 31), Person("Bob, 29), Person("Carol", 31))
   println(people.groupBy { it.age })
   ```
   ###### Output
   {29=[Person(name=Bob, age=29)], 31=[Person(name=Alice, age=31), Person(name=Carol, age=31)]}
   
   Групує в мапу, де, ключем буде результат дямбди. people.groupy{} is Map<Int,List<Person>>
 
   one more example
   ```
    val a = listOf("Ivan", "Kerer", "September", "iOS", "Izotop")
    val map = a.groupBy { it.length }
    println(map)
   ```
   
   ###### Output
   {4=[Ivan, iOSs], 5=[Kerer], 9=[September], 6=[Izotop]}
   
   #### flatMap / flatten
   ```
   val books = listOf(Book("Thursday Next", listOf("Dasper Fforde")), Book("Mort", listOf("Terry Pratchett")), Book("Good Omens", listOf("Terry Pratchett","Neil Gaiman")))
   println(books.flatMap { it.authors }.toSet())
   ```
   
   ###### Output
   [Dasper Fforde, Terry Pratchett, Neil Gaiman]
   
   flatten - використовувати, якщо потрібно просто об’єднати колекції
   

   #### Sequence
   При використанні sequenses map не вконається лишній раз, а зупинеться на 2-му елементі
   ```
   println(listOf(l, 2, 3, 4).asSequence().map { it * it }.find{it > 3})
   ```
   
   #### with/apply
   with (просто бібліотечні функція) - повертає значення із лямбди
   apply (функція-розширення) - повертає самий об’єкт, до якого була виконана функція apply
   
   
   ## Generics
  
   ```
   class A<T>(val value : T) {
       fun test(value : T) {
           value?.toString();
       }
   }
   ```
   Generic type може бути з підтримкою null (Any?). Тому потрібно додавати null check (?.)
   Щоб заборонити використання null потрібно T зробити не доступним із null (T : Any instead of T : Any?)
   
   ## Any
   Compiles to Object in byte code.
   
   Any has only 3 methods equals(), hasCode() and toString(). If you whant to use wait()/notify() you have to cast your instance to Object
   
   ## Unit
   Compiles to void.
   Always has only one instance of this class.
   Medhod with Unit as a return parametr does not have to has a return call
   
   ## Nothing
   Has no instances.
   Means that a function with this return type won\`t return something (throw an exception or infinit cycle)
   
   ## Arrays
   Array<Int> -> Integer[]
   IntArray -> int[]
   
   ## Мультидекларации
   
   val point = Point(2, 6)
   val (x, y) = point // x = 2, y = 6
   
   Виклкаються методи componentN() для кожного із аргументів АБО якщо клас є data-класом - для кожного із полів, які є аргументами основного конструктора будуть згенеровані такі методи
   
  
   Може використовуватись для повернення декількох значеннь із функції
   
   # READ MORE ABOUT PROPERTIE DELEGATES
