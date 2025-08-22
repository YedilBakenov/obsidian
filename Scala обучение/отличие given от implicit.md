#Scala 

`given` и `implicit` - это два ключевых слова в Scala, которые используются для работы с неявными значениями. В Scala 3, `given` заменяет использование `implicit`, но с некоторыми улучшениями и явной видимостью. Вот основные различия между ними:

1. **Явная видимость:**
    
    - `given`: Неявное значение, объявленное с помощью `given`, должно быть явно указано, чтобы быть использованным.
    - `implicit`: Неявные значения, объявленные с помощью `implicit`, могут быть неявно найдены и использованы, что может привести к сложностям в понимании кода.
2. **Локальная видимость:**
    
    - `given`: Значения, объявленные с помощью `given`, могут иметь локальную видимость, что делает их применение более контролируемым.
    - `implicit`: Значения, объявленные с помощью `implicit`, имеют глобальную видимость, что может привести к неожиданным взаимодействиям и сложностям.
3. **Явные преобразования:**
    
    - `given`: При использовании `given` можно объявлять неявные преобразования с явными именами.
    - `implicit`: В `implicit` значениях преобразования неявно находятся и могут быть сложноуправляемыми.

Пример:

scalaCopy code

  given defaultName: String = "Гость" 
  
  def greet(name: String)(given default: String): String = {  
     s"Привет, $name! Добро пожаловать к нам!" } 
     
implicit val defaultName: String = "Гость" 

def greet(name: String)(implicit default: String): String = {    
s"Привет, $name! Добро пожаловать к нам!"
}`

Здесь `given` и `implicit` выполняют аналогичные задачи, но `given` предоставляет более явную и контролируемую видимость неявных значений. В целом, `given` представляет собой более современный и предсказуемый способ работы с неявными значениями в Scala 3.



Вот примеры явно указанных и неявно указанных значений с использованием `given` и `implicit`.

**Явно указанное значение (Using `given`):**

scalaCopy code

`object GivenExplicitExample { 
given defaultName: String = "Гость"

def greet(name: String)(given default: String): String = {       
s"Привет, $name! Добро пожаловать к нам!"  
}     

def main(args: Array[String]): Unit = {     
val specificName = "Иван"         println(greet(specificName)(using defaultName)) 
	}
}`

В этом примере значение `defaultName` передается явно в функцию `greet` с использованием `using defaultName`.

**Неявно указанное значение (Using `implicit`):**

scalaCopy code

`object ImplicitExplicitExample {     implicit val defaultName: String = "Гость"   

def greet(name: String)(implicit default: String): String = {        
s"Привет, $name! Добро пожаловать к нам!" 
}      

def main(args: Array[String]): Unit = {     
val specificName = "Иван"         println(greet(specificName)) 
	}
 }`

В этом примере значение `defaultName` передается неявно в функцию `greet`, так как оно объявлено как неявное значение.

**Обратите внимание:**

- С помощью `given` и `using`, значения передаются явно и четко.
- С помощью `implicit`, значения могут быть найдены неявно, что может затруднить отслеживание, особенно в более сложных программах.

Оба подхода позволяют использовать значения по умолчанию, но `given` и `using` делают процесс более видимым и понятным.