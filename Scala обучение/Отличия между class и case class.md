
#Scala 

Scala, `class` и `case class` - это два разных вида классов с различными свойствами и предназначением. Вот основные отличия между ними с примерами:

1. **Сравнение по содержимому (`equals`, `hashCode`, `toString`):**
    - `case class` автоматически генерирует методы `equals`, `hashCode` и `toString`, которые сравнивают объекты по содержимому и позволяют удобно выводить их на печать.
    - В `class` эти методы по умолчанию не генерируются и должны быть определены вручную, если требуется сравнивать объекты по содержимому.

Пример:

scalaCopy code

case class Person(name: String, age: Int) val person1 = Person("Alice", 30) val person2 = Person("Alice", 30) 

println(person1 == person2)     println(person1.hashCode == person2.hashCode) 
println(person1.toString)         

class Car(val brand: String, val model: String) val car1 = new Car("Toyota", "Camry") 
val car2 = new Car("Toyota", "Camry")  println(car1 == car2)
// Вывод: false (по умолчанию сравниваются ссылки)`

2. **Сопоставление с образцом (Pattern Matching):**
    - `case class` поддерживает сопоставление с образцом (pattern matching) из коробки, что упрощает работу с образцами данных.
    - `class` не поддерживает сопоставление с образцом из коробки.

Пример:

scalaCopy code

def matchPerson(person: Person): String = person match {
case Person("Alice", _) => "Hello, Alice!"     case _ => "Hello, stranger!"
} 

val person = Person("Alice", 30) println(matchPerson(person)) 

3. **Иммутабельность (неизменяемость) по умолчанию:**
    - Поля `case class` по умолчанию объявляются как неизменяемые (val).
    - В `class` поля по умолчанию могут быть изменяемыми (var) или неизменяемыми (val), в зависимости от объявления.

Пример:

scalaCopy code

case class Address(city: String, country: String) 
val address = Address("New York", "USA") 

// address.city = "London" - это вызовет ошибку, так как поля неизменяемые

class Product(val name: String, var price: Double) 

val product = new Product("Phone", 500.0) product.price = 550.0 

// Это допустимо для изменяемого поля`

В целом, `case class` предназначены для хранения данных и имеют много удобных функциональностей, таких как автоматическое сравнение и сопоставление с образцом. В то время как `class` предоставляют более широкие возможности для создания классов с пользовательской логикой и поведением.