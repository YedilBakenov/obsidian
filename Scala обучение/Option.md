#Scala 
`Option` в Scala представляет собой контейнер, который может содержать либо некоторое значение (Some), либо отсутствие значения (None). Он используется для более безопасной и более функциональной обработки возможных отсутствующих значений, избегая ошибок времени выполнения, таких как NullPointerException.

Синтаксис создания `Option`:
val someValue: Option[T] = Some(value) // создание Option с ненулевым значением
val noneValue: Option[T] = None       // создание Option без значения (None)


Где `T` - это тип значения, которое будет содержаться в `Option`.

Пример использования `Option`:
// Пример функции, возвращающей Option
def findPerson(id: Int): Option[String] = {
  val database = Map(1 -> "Alice", 2 -> "Bob", 3 -> "Charlie")
  database.get(id) // Возвращает Some(value) если значение существует, и None, если значения нет
}

// Вызов функции с различными аргументами
val person1 = findPerson(1) // Some("Alice")
val person2 = findPerson(4) // None

// Обработка Option с помощью match
person1 match {
  case Some(name) => println(s"Person found: $name")
  case None => println("Person not found")
}

person2 match {
  case Some(name) => println(s"Person found: $name") // Этот блок не выполнится, так как person2 содержит None
  case None => println("Person not found")
}

// Получение значения из Option с помощью метода getOrElse
val personName1 = person1.getOrElse("Unknown") // "Alice"
val personName2 = person2.getOrElse("Unknown") // "Unknown", так как person2 содержит None

// Использование метода map для преобразования Option
val upperCaseName = person1.map(_.toUpperCase) // Some("ALICE")
val upperCaseName2 = person2.map(_.toUpperCase) // None


Где `T` - это тип значения, которое будет содержаться в `Option`.

Пример использования `Option`:

// Пример функции, возвращающей Option
def findPerson(id: Int): Option[String] = {
  val database = Map(1 -> "Alice", 2 -> "Bob", 3 -> "Charlie")
  database.get(id) // Возвращает Some(value) если значение существует, и None, если значения нет
}

// Вызов функции с различными аргументами
val person1 = findPerson(1) // Some("Alice")
val person2 = findPerson(4) // None

// Обработка Option с помощью match
person1 match {
  case Some(name) => println(s"Person found: $name")
  case None => println("Person not found")
}

person2 match {
  case Some(name) => println(s"Person found: $name") // Этот блок не выполнится, так как person2 содержит None
  case None => println("Person not found")
}

// Получение значения из Option с помощью метода getOrElse
val personName1 = person1.getOrElse("Unknown") // "Alice"
val personName2 = person2.getOrElse("Unknown") // "Unknown", так как person2 содержит None

// Использование метода map для преобразования Option
val upperCaseName = person1.map(_.toUpperCase) // Some("ALICE")
val upperCaseName2 = person2.map(_.toUpperCase) // None

Использование `Option` позволяет улучшить читаемость кода и избежать ошибок, связанных с отсутствующими значениями. Вы можете использовать различные методы Option, такие как `getOrElse`, `map`, `flatMap`, `filter` и т.д., чтобы управлять содержимым и преобразовывать значения, не вызывая исключений при работе с возможно отсутствующими данными.

object Main2 {
  def main(args: Array[String]): Unit = {
      
    // Использование Some для оборачивания значения
    val someValue: Option[Int] = Some(42)

    // Использование метода Option() для оборачивания значения
    val anotherValue: Option[String] = Option("Hello")

    // Использование Some напрямую
    val yetAnotherValue: Some[Double] = Some(3.14)
  }
}
