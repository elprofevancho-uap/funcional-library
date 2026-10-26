<img width="1524" height="650" alt="image" src="https://github.com/user-attachments/assets/bf447451-850d-4d02-9ee9-47f9bb3caf33" />

# Ejercicio de Programación Funcional en Scala: Sistema de Biblioteca

Este repositorio contiene un ejercicio práctico diseñado para afianzar conceptos clave de la **Programación Funcional en Scala**, tales como inmutabilidad, funciones de orden superior (`filter`, `map`, `groupBy`), manejo seguro de datos ausentes (`Option`) y composición de funciones.

---

## 🎯 Objetivos de Aprendizaje

1. Modelar un dominio mediante **Estructuras de Datos Inmutables** (`case class`).
2. Aplicar **Funciones Puras** sin efectos secundarios ni mutación de estado.
3. Utilizar **Combinadores de Colecciones** estándar de Scala.
4. Manejar ausencia de valores de forma segura mediante el tipo `Option`.

---

## 📚 Dominio del Problema

El sistema maneja tres entidades principales representadas mediante `case class`:

```scala
case class Book(id: String, title: String, author: String, year: Int, genres: List[String])
case class Member(id: String, name: String, active: Boolean)
case class Loan(bookId: String, memberId: String, loanDate: String, returned: Boolean)
```

---

## 📝 Consignas del Ejercicio

Implementa las siguientes funciones dentro de un objeto `LibrarySystem`:

### Reto 1: Búsqueda por Género (Filtrado Básico)
Crea la función `booksByGenre`:
- **Firma:** `def booksByGenre(books: List[Book], genre: String): List[Book]`
- **Descripción:** Devuelve todos los libros que incluyan el género especificado en su lista de géneros.

### Reto 2: Transformación de Títulos (Mapeo)
Crea la función `uppercaseTitles`:
- **Firma:** `def uppercaseTitles(books: List[Book]): List[String]`
- **Descripción:** Toma la lista de libros y devuelve una lista únicamente con los títulos de los libros transformados a mayúsculas.

### Reto 3: Búsqueda Segura por ID (`Option`)
Crea la función `findBookById`:
- **Firma:** `def findBookById(books: List[Book], id: String): Option[Book]`
- **Descripción:** Busca un libro por su `id`. En lugar de retornar `null` o lanzar una excepción si el libro no existe, debe devolver un `Option[Book]` (`Some(book)` si existe, `None` si no).

### Reto 4: Estadísticas de Libros por Año (Agrupación)
Crea la función `countBooksByYear`:
- **Firma:** `def countBooksByYear(books: List[Book]): Map[Int, Int]`
- **Descripción:** Agrupa los libros por su año de publicación y calcula cuántos libros fueron publicados en cada año. La clave del mapa resultante es el año y el valor es la cantidad de libros.

### Reto 5: Libros Prestados a un Socio (Composición)
Crea la función `booksLoanedToMember`:
- **Firma:** `def booksLoanedToMember(books: List[Book], loans: List[Loan], memberId: String): List[Book]`
- **Descripción:** Devuelve la lista de libros que actualmente tiene prestados un socio determinado (es decir, préstamos asociados al `memberId` que tengan `returned == false`).

---

## 💻 Esqueleto de Código

Puedes utilizar este esqueleto para comenzar tu implementación:

```scala
object LibrarySystem {

  case class Book(id: String, title: String, author: String, year: Int, genres: List[String])
  case class Member(id: String, name: String, active: Boolean)
  case class Loan(bookId: String, memberId: String, loanDate: String, returned: Boolean)

  def booksByGenre(books: List[Book], genre: String): List[Book] = ???

  def uppercaseTitles(books: List[Book]): List[String] = ???

  def findBookById(books: List[Book], id: String): Option[Book] = ???

  def countBooksByYear(books: List[Book]): Map[Int, Int] = ???

  def booksLoanedToMember(books: List[Book], loans: List[Loan], memberId: String): List[Book] = ???
}
```

---

## 🧪 Datos de Prueba para Ejecución

Puedes probar tus soluciones con el siguiente conjunto de datos:

```scala
val sampleBooks = List(
  Book("b1", "1984", "George Orwell", 1949, List("Dystopian", "Fiction")),
  Book("b2", "Brave New World", "Aldous Huxley", 1932, List("Dystopian", "Sci-Fi")),
  Book("b3", "Fahrenheit 451", "Ray Bradbury", 1953, List("Dystopian", "Sci-Fi")),
  Book("b4", "The Hobbit", "J.R.R. Tolkien", 1937, List("Fantasy"))
)

val sampleLoans = List(
  Loan("b1", "m1", "2023-10-01", returned = false),
  Loan("b2", "m1", "2023-09-15", returned = true),
  Loan("b3", "m2", "2023-10-05", returned = false)
)

// Ejemplo de prueba
println(LibrarySystem.booksByGenre(sampleBooks, "Sci-Fi"))
println(LibrarySystem.booksLoanedToMember(sampleBooks, sampleLoans, "m1"))
```
