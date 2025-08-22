
#Scala 

`object` и `case object` - это специальные конструкции в Scala, которые создают одиночные экземпляры (синглтоны). Однако есть небольшие различия в их использовании.


**`object` в Scala:**

- `object` создает синглтон-объект, который может иметь методы, поля и поведение.
- Экземпляр `object` создается автоматически, и он всегда единственный.
- Может быть использован для создания утилитарных функций, реализации шаблонов одиночек (singleton pattern), создания фабрик и других служебных задач.

Пример:

scalaCopy code

`object MathUtils {   
def add(a: Int, b: Int): Int = a + b    
def subtract(a: Int, b: Int): Int = a - b 
}
val sum = MathUtils.add(5, 3) 
println(sum) // Вывод: 8`


**`case object` в Scala:**

- `case object` создает синглтон-объект, но обычно используется для создания экземпляров для сопоставления с образцом (pattern matching).
- Экземпляр `case object` создается автоматически, и он всегда единственный.
- Полезен при работе с сопоставлением с образцом, так как объекты `case object` автоматически участвуют в этом процессе.

Пример:

scalaCopy code

`sealed trait Day
case object Monday extends Day 
case object Tuesday extends Day 

def isWeekend(day: Day): Boolean = day match { 
case Saturday | Sunday => true    
case _ => false
}

println(isWeekend(Monday))  // Вывод: false println(isWeekend(Saturday)) // Вывод: true`

В этом примере `case object` используется для создания экземпляров `Monday` и `Tuesday`, которые затем используются в сопоставлении с образцом в функции `isWeekend`.

Вкратце, `object` используется для создания обычных синглтон-объектов с методами и полями, а `case object` - для создания синглтонов, которые легко поддаются сопоставлению с образцом.