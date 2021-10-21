import java.util.*
 
open class Person(var name : String, var birthYear : Int)
{
	var age : Int = Calendar.getInstance().get(Calendar.YEAR) - birthYear
}
 
class Student(name : String, birthYear : Int, var averageGrade : Double, var extramural : Boolean = false ):Person(name, birthYear)
{
 override fun toString(): String = "Имя: $name, Год рождения: $birthYear, Средняя оценка: $averageGrade, Заочный студент: $extramural "
 
}
 
class Lecturer(name : String, birthYear : Int, var degree : String, var experienceFrom : Int):Person(name, birthYear){
	
   override fun toString(): String = "Имя: $name, Год рождения: $birthYear, Ученая стпень: $degree, Год начала учебного стажа: $experienceFrom " 
  
}
 
fun sortByAge(persons:List<Person>):List<Person> { 
   	
 	val sortedList1 = persons.sortedWith(compareBy(Person::age)).reversed()
 	println(sortedList1.joinToString( separator = "\n"))
 	return sortedList1
}
 
fun MutableList<Person>.sortByNameStudents():List<Student>
{
	return this.filter{ it is Student }.sortedByDescending{ it.name } as List<Student>
}
 
fun MutableList<Person>.sortByAverageGrade(exceptExtramural : Boolean):List<Student>
{
	// если false - выводить всех студентов
	if (exceptExtramural == false) return (this.filter{ it is Student } as List<Student>).sortedByDescending{ it.averageGrade }
	//  иначе не выводить заочников
	else return (this.filter{ it is Student } as List<Student>).filter{ !it.extramural }.sortedByDescending{ it.averageGrade }
}
 
fun main() {
   	
	val persons = mutableListOf<Person>(Student("Ушаков Дмитрий", 2000,4.4,false),
                     	Student("Берсенев Кирилл", 2000,5.0,false),
                     	Student("Нырков Александр", 2000,4.9,false),
                     	Student("Куликов Денис", 2001,3.5,true),
                     	Student("Потапов Даниил", 2001,4.1,false),
                     	Lecturer("Сыромясов Алексей Олегович",1983,"Кандидат физико-математических наук",2010),
                         Lecturer("Мещерякова Светлана Ивановна",1967,"Кандидат педагогических наук",1992),
                         Lecturer("Фирсова Светлана Анатольевна",1972,"Кандидат физико-математических наук",1998),
                         Lecturer("Мадонов Анатолий Николаевич",1973,"Кандидат физико-математических наук",1998),
                         Lecturer("Белов Владимир Федорович",1952,"Доктор технических наук",1980))
 	println("Список всех:")
 	println(persons.joinToString( separator = "\n"))
 	println()
     println("Cписок, отсортированный по возрасту")
     sortByAge(persons)
 	println()
     println("Cписок студентов, отсортированный по имени")
 	println(persons.sortByNameStudents().joinToString( separator = "\n"))
 	println()
     println("Cписок студентов, отсортированный по средней оценке")
 	println(persons.sortByAverageGrade(false).joinToString( separator = "\n"))
 
}
