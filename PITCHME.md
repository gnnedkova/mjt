## Въведение в Java

_14.10.2020_

---

#### Какво е Java?

@ul

- Език за програмиране
- Java компилатор
- Java виртуална машина (JVM)
- Java Development Kit (JDK)
  - Java Runtime Environment (JRE)
- Java платформа

@ulend

---

#### Java Editions

@ul

- Java Edition е вариация на Java платформата (JDK-то), асемблирана за различна цел
  - Java Platform Standard Edition (Java SE)
  - Java Platform Enterprise Edition (Java EE)
  - Java Platform Micro Edition (Java ME)
    - Android SDK
  - Java Card

@ulend

---

#### JDK инструменти

@ul

- Основни
  - javac
  - java
- Допълнителни
  - jshell 
  - javadoc
  - jar
  - ...

@ulend

---

#### Java: най-популярните IDE-та

@ul

- IntelliJ IDEA
- Eclipse
- NetBeans

@ulend

---

#### Езикът Java

- Създаден през 1995 от James Gosling (Sun Microsystems)
- Актуална версия: Java 15 (released 15.09.2020)

![Java logo and mascot](images/01.1-java-logo-mascot.png)

---

#### Езикът Java

@ul

- Обектно-ориентиран
- Със C/C++ синтаксис
- "Write once, run anywhere"

@ulend

---

#### Hello world!

<br/>

```java
public class HelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello world!");
    }
}
```

<br/>

```bash
$ javac HelloWorldApp.java
$ java HelloWorldApp
Hello world!
```

---

#### Стандартно Java приложение

![Java app diagram](images/01.2-java-app.jpg)

---

#### Java виртуалната машина (JVM)

@ul

- Интерпретира и изпълнява byte код инструкции
- Компилира по време на изпълнението byte кода до машинен код
- Заделя памет за оперативните данни
- Автоматично изчиства паметта
- Зарежда класове
- Стартира нишки
- Взаимодейства с операционната система

@ulend

---

#### Ще започнем с езика Java от...

@ul

- Tиповете данни
- Оператори, изрази, statements
- Условия и разклонения
- Итерация / Цикли
- Низове и операции с тях
- Масиви
- Функции

@ulend

---

#### Tипове данни и променливи

@ul

- Тип данни == множество стойности + операции върху тях
- Java е статично типизиран език => всички променливи трябва да бъдат декларирани, преди да бъдат използвани, и типът на дадена променлива се фиксира в декларацията ѝ и не може да се променя
- Декларацията включва името и типа, и може да е съчетана (или не) с инициализация

@ulend

---

#### Tипове данни и променливи

![Variables](images/01.3-variables.jpg)

---

#### Tипове данни

@ul

- Примитивни типове
  - Булев (boolean) тип
  - Числени (numeric) типове
    - Целочислени (integral) типове
    - Типове за числа с плаваща запетая (floating-point)
- Reference типове

@ulend

---

#### Примитивни типове данни

<table>
  <tr>
    <th style="font-size:0.9em">Тип данни</th>
    <th style="font-size:0.9em">Размер</th>
    <th style="font-size:0.9em">Минимум</th>
    <th style="font-size:0.9em">Максимум</th>
  </tr>
  <tr style="font-size:0.7em">
    <td>boolean</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>byte</td>
    <td>8 бита</td>
    <td>-128</td>
    <td>+127</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>char</td>
    <td>16 бита</td>
    <td>Unicode 0</td>
    <td>Unicode 2<sup>16</sup> - 1</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>short</td>
    <td>16 бита</td>
    <td>-2<sup>15</sup></td>
    <td>+2<sup>15</sup> - 1</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>int</td>
    <td>32 бита</td>
    <td>-2<sup>31</sup></td>
    <td>+2<sup>31</sup> - 1</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>long</td>
    <td>64 бита</td>
    <td>-2<sup>63</sup></td>
    <td>+2<sup>63</sup> - 1</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>float</td>
    <td>32 бита</td>
    <td>IEEE754</td>
    <td>IEEE754</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>double</td>
    <td>64 бита</td>
    <td>IEEE754</td>
    <td>IEEE754</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>void</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
  </tr>
</table>

---

#### Минимална и максимална стойност на примитивните типове

```java
Byte.MIN_VALUE // -128
Byte.MAX_VALUE // 127
Short.MIN_VALUE // -32768
Short.MAX_VALUE // 32767
Integer.MIN_VALUE // -2147483648
Integer.MAX_VALUE // 2147483647
Long.MIN_VALUE // -9223372036854775808
Long.MAX_VALUE // 9223372036854775807
(int) Character.MIN_VALUE // 0
(int) Character.MAX_VALUE // 65535
```
---

#### Типът char

@ul

- цяло число без знак
- стойност (*code point*) от 0 до 65535 включително
- представя Unicode символ
- може да участва в аритметични операции (със своя code point)

@ulend

---

#### Типът char

<table>
  <tr>
    <th style="font-size:0.9em">Code point</th>
    <th style="font-size:0.9em">Unicode escape</th>
    <th style="font-size:0.9em">Печатна репрезентация</th>
    <th style="font-size:0.9em">Описание</th>
  </tr>
  <tr style="font-size:0.7em">
    <td>33</td>
    <td>\u0021</td>
    <td>!</td>
    <td>Символ за удивителна</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>50</td>
    <td>\u0032</td>
    <td>2</td>
    <td>Цифра 2</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>65</td>
    <td>\u0041</td>
    <td>A</td>
    <td>Главна латинска буква 'A'</td>
  </tr>
</table>

---

#### Литерали на примитивните типове

```java
int i = 1;           // int by default
long l = 1L;         // L or l
double d = 0.1;      // d or D is optional
double d2 = 1e-1;    // same, in scientific
float f = 0.1;       // will not compile, why?
char c = 'A';
char c2 = '\u0041';  // again, 'A'
```

---

#### Целочислени литерали

```java
// The number 26, in decimal
int decVal = 26;

// The number 26, in hexadecimal
int hexVal = 0x1a;

// The number 26, in binary
int binVal = 0b11010;

// The number 26, in octal
int octVal = 032;
```

---

#### Литерали с подчертавка: syntactic sugar

```java
int thousand = 1_000;
int million = 1_000_000;
long magic = 0xCAFE_BABE;
int one = 0b1;
int mask = 0b1010_1010_1010;
```

---

#### Стойности по подразбиране

- Компилаторът **не** присвоява стойности по подразбиране на неинициализираните локални променливи!

---

<table>
  <tr>
    <th>Тип данни</th>
    <th>Стойност по подразбиране</th>
  </tr>
  <tr style="font-size:0.8em">
    <td>boolean</td>
    <td>false</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>short</td>
    <td>0</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>int</td>
    <td>0</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>long</td>
    <td>0L</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>float</td>
    <td>0.0f</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>double</td>
    <td>0.0d</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>char</td>
    <td>'\u0000'</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>Reference типове</td>
    <td>null</td>
  </tr>
</table>

---

#### Конвертиране на типовете

- Имплицитно - без загуба на точност
- Експлицитно - чрез cast

<table style="width:100%">
  <tr>
    <th style="width:50%">Израз</th>
    <th style="width:25%">Тип на израза</th>
    <th style="width:25%">Стойност на израза</th>
  </tr>
  <tr style="font-size:0.8em">
    <td>"1234" + 99</td>
    <td>String</td>
    <td>"123499"</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>(int) 2.71828</td>
    <td>int</td>
    <td>2</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>11 \* 0.3</td>
    <td>double</td>
    <td>3.3</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>(int) 11 \* 0.3</td>
    <td>double</td>
    <td>3.3</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>11 \* (int) 0.3</td>
    <td>int</td>
    <td>0</td>
  </tr>
  <tr style="font-size:0.8em">
    <td>(int) (11 \* 0.3)</td>
    <td>int</td>
    <td>3</td>
  </tr>
<table>

---

#### Защо ни трябват типове?

- За да ни помага компилаторът в откриването на грешки

<br />

![Java app diagram](images/01.4-rocket.jpg)

<p style="font-size:0.5em">През 1996, ракетата Ариана 5 експлодира след излитане поради софтуерна грешка в конвертирането на типове (опит да „набута“ 64-битово число в 16 бита).</p>

---

#### Оператори

<table style="width:100%">
  <tr>
    <th style="width:50%; font-size:0.8em">Operators</th>
    <th style="width:50%; font-size:0.8em">Precedence</th>
  </tr>
  <tr style="font-size:0.5em">
    <td>postfix</td>
    <td>expr++ expr--</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>unary</td>
    <td>++expr --expr +expr -expr ~ !</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>multiplicative</td>
    <td>\* / %</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>additive</td>
    <td>+ -</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>shift</td>
    <td><< >> >>></td>
  </tr>
  <tr style="font-size:0.5em">
    <td>relational</td>
    <td>< > <= >= instanceof</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>equality</td>
    <td>== !=</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>bitwise AND</td>
    <td>&</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>bitwise exclusive OR</td>
    <td>^</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>bitwise inclusive OR</td>
    <td>|</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>logical AND</td>
    <td>&&</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>logical OR</td>
    <td>||</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>ternary</td>
    <td>? :</td>
  </tr>
  <tr style="font-size:0.5em">
    <td>assignment</td>
    <td>= += -= *= /= %= &= ^= |= <<= >>= >>>=</td>
  </tr>
</table>

---

#### Scoping

```java
{
    int x = 12;
    // Only x available
    {
        int q = 96;
        // Both x & q available
    }
    // Only x available
    // q is "out of scope" 
}

```

---

### Wrapper types

@ul

- Представляват референтни аналози на примитивните типове
- Използват се
    - където синтаксисът на езика изисква обект, а не примитивен тип
    - когато ни трябват константи или помощни функции, които са имплементирани в съответния wrapper клас
- имплицитно се конвертират към съответния си примитивен тип, и обратно

@ulend

---

#### Примитивни типове и wrapper типове

<table>
  <tr>
    <th style="font-size:0.8em">Тип данни</th>
    <th style="font-size:0.8em">Размер</th>
    <th style="font-size:0.8em">Минимум</th>
    <th style="font-size:0.8em">Максимум</th>
    <th style="font-size:0.8em">Wrapper</th>
  </tr>
  <tr style="font-size:0.6em">
    <td>boolean</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>Boolean</td>
  </tr>
  <tr style="font-size:0.6em">
    <td>char</td>
    <td>16 бита</td>
    <td>Unicode 0</td>
    <td>Unicode 2<sup>16</sup> - 1</td>
    <td>Character</td>
  </tr>
  <tr style="font-size:0.6em">
    <td>byte</td>
    <td>8 бита</td>
    <td>-128</td>
    <td>+127</td>
    <td>Byte</td>
  </tr>
  <tr style="font-size:0.6em">
    <td>short</td>
    <td>16 бита</td>
    <td>-2<sup>15</sup></td>
    <td>+2<sup>15</sup> - 1</td>
    <td>Short</td>
  </tr>
  <tr style="font-size:0.6em">
    <td>int</td>
    <td>32 бита</td>
    <td>-2<sup>31</sup></td>
    <td>+2<sup>31</sup> - 1</td>
    <td>Integer</td>
  </tr>
  <tr style="font-size:0.6em">
    <td>long</td>
    <td>64 бита</td>
    <td>-2<sup>63</sup></td>
    <td>+2<sup>63</sup> - 1</td>
    <td>Long</td>
  </tr>
  <tr style="font-size:0.6em">
    <td>float</td>
    <td>32 бита</td>
    <td>IEEE754</td>
    <td>IEEE754</td>
    <td>Float</td>
  </tr>
  <tr style="font-size:0.6em">
    <td>double</td>
    <td>64 бита</td>
    <td>IEEE754</td>
    <td>IEEE754</td>
    <td>Double</td>
  </tr>
  <tr style="font-size:0.6em">
    <td>void</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>Void</td>
  </tr>
</table>

---

#### Константи и utility методи във wrapper типовете

```java
Integer.MAX_VALUE
Integer.MIN_VALUE
new Integer(25).intValue()
Integer.parseInt(String)
```

@snap[south span-100]
@[1-1](максималната стойност на типа)
@[2-2](минималната стойност на типа)
@[3-3](връща int стойността, "опакована" в дадената инстанция)
@[4-4](конвертира низ с текстово представяне на цяло число към int)
@snapend

---

#### Autoboxing

```java
// primitive type
char c = 'a';

// wrapper class
Character ch1 = new Character('a');

// autoboxing: char implicitly converted to Character
Character ch2 = 'x';

// Character instance implicitly converted to char
char c2 = ch1;
```

@snap[south span-100]
@[1-2](инициализиране на променлива от тип char с литерал)
@[4-5](инициализирне на Character обект с литерал)
@[7-8](autoboxing)
@[10-11](wrapper to primitive conversion)
@snapend

---

#### Низове в Java

@ul

- Низовете са reference тип, а не примитивен
- Инстанции са на `String` класа
- Immutable са: всяка промяна води до създаване на нов `String` обект, а старият остава непроменен

@ulend

---

#### Низовете в паметта: string pool vs heap

@ul

- String литералите се създават в специална област на паметта на JVM-a, наречена *string pool*
- При опит за добавяне на низ в string pool-a, ако там вече съществува низ със същото съдържание, не се създава нов обект, а се връща референция към съществуващия (-> пести се памет)

@ulend

---

#### Низовете в паметта: string pool vs heap

@ul

- String обектите, създадени с оператора `new`, се създават в динамичната памет (heap-a). Всеки низ в heap-a е отделна инстанция, дори съдържанието на два и повече низа да е идентично
- String обект може да се прехвърли от heap-a в string pool-a чрез извикване на метода му `intern()`

@ulend

---

#### Сравняване на низове

@ul

- Сравняването на низове с `==` е сравнение на съответните референции
- Сравняването на низове за идентичност като съдържание се прави с метода `equals()` на String класа

@ulend

---

#### Низовете в паметта: string pool vs heap

```java
String literalOne = "FMI"; // goes to the string pool
String literalTwo = "FMI"; // "FMI" is present in the String pool ->
                           // literalTwo will refer to the same object

System.out.println(literalOne == literalTwo); // true

String newString = new String("FMI"); // new object in the heap

System.out.println(literalOne == newString); // false
System.out.println(literalOne.equals(newString)); // true

String intern = newString.intern(); // adds the string to the pool
                                    // and returns a reference to it
System.out.println(literalOne == newString); // false, newString
                                             // is not reassigned
System.out.println(literalOne == intern); // true
```

---

#### Низове - литерали, конкатениране

```java
String language = "Java";
String tbd = null;
String message = "I <3 " + language;
String year = "The current year is " + 2020;
```

---

#### Многоредови низови литерали

```java
// multi-line string literals before
String html = "<html>\n" +
              "    <body>\n" +
              "        <p>Hello world!</p>\n" +
              "    <body>\n" +
              "</html>\n";

// new in Java 15: text blocks for multi-line string literals
String html = """
                       <html>
                           <body>
                               <p>Hello world!</p>
                           </body>
                       </html>
              """;
```

---

#### Низове - обхождане

```java
String s = "Firebird";
char ic = s.charAt(i);
char[] ca = s.toCharArray();

for (int i = 0; i < ca.size(); i++) {...}
for (char c : ca) {...} // enhanced for-loop, a.k.a. for-each

Arrays.sort(ca);
String sorted = String.valueOf(ca); // "Fbdeiirr"
```

---

#### String.split()

```java
String str1 = "Current year is 2020";

String[] tokens = str1.split(" "); // разделител – интервал

// tokens = ["Current", "year", "is", "2020"]

int year = Integer.parseInt(tokens[3]); 
// year == 2020
```

---

#### Други операции с низове

<small>
Класът `String` има още много методи, реализиращи операции, които ще ни потрябват.
Разгледайте ги в [документацията](https://docs.oracle.com/en/java/javase/15/docs/api/java.base/java/lang/String.html) на класа.
</small>

---

#### Mutable низове

<small>
Когато имаме нужда от mutable низове, т.е. такива, промяната на които да не води до създаване на нова инстанция, вместо `String` трябва да използваме класовете `StringBuilder` или `StringBuffer`.
</small>

<table>
  <tr style="font-size:0.7em">
    <th>Class name</th>
    <th>Mutable</th>
    <th>Performant</th>
    <th>Thread-safe</th>
  </tr>
  <tr style="font-size:0.7em">
    <td>String</td>
    <td>no</td>
    <td>slow, if modified</td>
    <td>yes</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>StringBuilder</td>
    <td>yes</td>
    <td>fast</td>
    <td>no</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>StringBuffer</td>
    <td>yes</td>
    <td>slower</td>
    <td>yes</td>
  </tr>
</table>

---

#### Local variable type inference

```java
// since Java 10
var message = "FMI rulez!"; // local variable type inference

message = "Cool"; // variable can be reassigned

message = 1; // will not compile: type is fixed upon declaration
             // and cannot change

var mystery; // will not compile: type cannot be inferred
             // without initializer
```

---

#### Булеви константи

@ul

- `true` или `false`
- За разлика от С/С++, не може да се използва число вместо булев израз

@ulend

---

#### Булеви логически оператори

@ul[squares]

- | - the OR operator
- & - the AND operator
- ^ - the XOR operator
- ! - the NOT operator
- || - the short-circuit OR operator
- && - the short-circuit AND operator
- == - the EQUAL TO operator
- != - the NOT EQUAL TO operator

@ulend

---

#### Булеви логически оператори

<table>
  <tr>
    <th>A</th>
    <th>B</th>
    <th>A|B</th>
    <th>A&B</th>
    <th>A^B</th>
    <th>!A</th>
  </tr>
  <tr>
    <td>false</td>
    <td>false</td>
    <td>false</td>
    <td>false</td>
    <td>false</td>
    <td>true</td>
  </tr>
  <tr>
    <td>true</td>
    <td>false</td>
    <td>true</td>
    <td>false</td>
    <td>true</td>
    <td>false</td>
  </tr>
  <tr>
    <td>false</td>
    <td>true</td>
    <td>true</td>
    <td>false</td>
    <td>true</td>
    <td>true</td>
  </tr>
  <tr>
    <td>true</td>
    <td>true</td>
    <td>true</td>
    <td>true</td>
    <td>false</td>
    <td>false</td>
  </tr>
</table>

---

#### if-else

```java
if (booleanExpression) {
    // statements
}

if (booleanExpression) {
    // statements
} else {
    // statements
}
```

---

#### Операторът ? :

```java
// the only ternary (i.e. three-argument) operator in Java
condition ? statement1 : statement2

// the above is equivalent to
if (condition) {
    statement1
} else {
    statement2
}  
```

---

#### Итерация - while

```java
while (booleanExpression) {
    statement
}
```

---

#### Итерация - do-while

```java
do {
    statement
} while (booleanExpression);
```

---

#### Итерация - for

```java
for (initialization; booleanExpression; step) {
    statement
}
```

---

#### Безусловно разклонение на изпълнението

@ul

- `return [value]`
- `break [label]`
- `continue [label]`
- Няма `goto` (ключовата дума е запазена, но не е използвана)

@ulend

---

#### Switch

```java
switch (selector) {
    case value1 : statement; break; 
    case value2 : statement; break; 
    case value3 : statement; break; 
    // [... ]
    default: statement; 
}
```

---

#### Подобрен `switch` (от Java 15)

```java
char ch = 'a';
int t;

// before
switch (ch) {
    case 'a'      : t = 1; break;
    case 'b', 'c' : t = 12; break;
    default       : t = 27;
}

// since Java 15
switch (ch) {
    case 'a'      -> t = 1;
    case 'b', 'c' -> t = 12;
    default       -> t = 27;
}
```

---

#### Подобрен `switch` като израз (от Java 15)

```java
int z = switch (ch) {
    case 'a'      -> 1;
    case 'b', 'c' -> 12;
    default       -> 27;
};

int r = switch (ch) {
    case 'a' : yield 1;
    case 'b' : yield 12;
    default  : yield 27;
};
```

---

#### Масиви

![Array](images/01.5-array.jpg)

---

#### Масиви

```java
int[] a;     // preferred syntax
int a[];     // also valid

// explicit initialization
// can be done only during declaration
int[] a = {1, 2, 3, 4};

int[] b = new int[7];
b.length;
```

---

#### Масиви

@ul

- Декларация – не се заделя памет за елементите на масива
- Инициализация – заделя се памет за елементите на масива
- Масивите от примитивни типове се инициализират автоматично със стойността по подразбиране на съответния тип

@ulend

---

#### Многомерни масиви

```java
int[][] a;
a = new int[3][4];

int[][] b = {
    { 1, 0, 12, -1 },
    { 7, -3, 2, 5 },
    { -5, -2, 2, -9 },
};
```

@snap[east fragment]
![Matrix](images/01.6-matrix.jpg)
@snapend

---

#### Многомерни масиви

```java
double[][] matrix = new double[7][];
// rows have not yet been created

for (int i = 0; i < 7; i++) {
    // Create row i with i + 1 elements.
    matrix[i] = new double[i+1];
}
```

---

#### Операции с масиви

```java
System.arraycopy(src, srcPos, dest, destPos, length); // копиране

Arrays.equals(arr1, arr2); // проверка за еднаквост
Arrays.fill(arr, value); // запълване с дадена стойност
Arrays.toString(arr); // конвертиране в низ
```

---

#### Операции с масиви

```java
Arrays.sort(arr); // сортиране
Arrays.sort(a, Collections.reverseOrder()); // сортиране в обратен ред
```

---

#### Функции

![Functions](images/01.7-funcs.jpg)

---

Писане на стандартния изход

```java
System.out.println("Something printed on the console");
```

Четене от стандартния вход

```java
import java.util.Scanner;
// [...]

Scanner sc = new Scanner(System.in);
String lineRead = sc.nextLine();

// [...]
```

---

## Въпроси?

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@snapend

---

![Thinking in Java](images/01.8-thinking-in-java.jpg)

---

![Effective Java](images/01.9-effective-java.jpg)


## Обектно-ориентирано програмиране с Java

![Java OOP](images/02.1-oop.jpg)

_21.10.2020_

---

#### Предната лекция говорихме за:

@ul

- Tиповете данни
- Оператори, изрази, statements
- Условия и разклонения
- Итерация / Цикли
- Низове и операции с тях
- Масиви
- Функции

@ulend

---

#### Днес ще разгледаме:

@ul

- Класове и обекти
- Абстрактни класове и интерфейси
- Фундаменталните ООП принципи
  - Енкапсулация
  - Наследяване
  - Полиморфизъм
  - Абстракция

@ulend

---

#### Обектно-ориентирано програмиране

@ul

- Родено е от необходимостта за по-добър контрол над конкурентната модификация на споделени данни
- Основната идея е, да няма директен достъп до данните, а те да се достъпват през нарочен за целта слой код
- Понеже данните трябва да се предават и модифицират, се ражда концепцията за обект

@ulend

---

#### Обект

@ul

- Обект в най-общ смисъл е множество данни, които могат да се предават и достъпват само чрез множество методи, които се подават заедно с данните
- Данните съставляват *състоянието на обекта*, а методите съставляват *поведението на обекта*
- Състоянието на обекта е скрито (*енкапсулирано*) от директен достъп
- Обектът е инстанция (представител) на даден клас. Обекти се създават явно чрез оператора `new` или неявно, и живеят в heap паметта

@ulend

---

#### Създаване на обекти

```java
String message = new String("Operation completed."); // explicit
Integer studentsCount = Integer.valueOf(60); // implicit
int[] intArr = new int[100]; // explicit
String[] stringArr = {"Some", "example"}; // implicit
stringArr = new String[]{"Changed", "my", "mind"}; // explicit
```

---

#### Клас

@ul

- Клас – дефиниция на (клас от) обекти
  - описва състояние чрез член-данни (член-променливи)
  - описва поведение чрез методи 
- Конструктор(и)
- Метод(и)
- Възможно е даден клас да няма състояние или да няма поведение
- Всеки клас има определен *интерфейс* - формално описание на начина, по който други обекти могат да взаимодействат с него

@ulend

---

#### Методи на клас

@ul

– функция(и) за манипулиране на състоянието на класа
  - име и списък от параметри (*сигнатура*)
  - броят на параметрите се нарича *арност*
  - два метода имат еднаква сигнатура, ако имат еднакви имена, еднаква арност и еднаква последователност от типове в списъка от параметри

@ulend

---

#### Методи на клас

@ul

  - модификатори, тип на връщаната стойност, сигнатура и тяло, оградено с {}
  - тялото може да съдържа декларации на локални променливи и statements
  - може да има странични ефекти

@ulend

---

```java
public class HelloWorldApp {

    public static void main(String[] args) {
        System.out.println("Hello world!");
    }

}
```

---

#### Методи с променлив брой аргументи

@ul

- специален вид параметър на метод: редица от нула или повече аргументи от един и същи тип
- Нарича се *varargs*, от *variable arguments*
- Синтаксис: име на тип, следван от три точки (многоточие)
- Ако метод има varargs параметър, той трябва да е един и да е последен в списъка
- При достигане до varargs параметър, компилаторът създава масив от останалите аргументи и ги подава на метода като масив
- В тялото на метода се достъпва като масив

@ulend

---

```java
// A method that takes variable number of integer arguments
static void funWithVarargs(int... a) {
    System.out.println("Number of arguments: " + a.length); 

    // using for-each loop to display contents of a
    for (int i : a) {
        System.out.print(i + " "); 
    } 
}

public static void main(String[] args) {
    // standard syntax
}

public static void main(String... args) {
    // varargs syntax - equivalent to the above
}
```

---

#### Статични член-променливи и статични методи

<small>

- Те са част от класа, а не от конкретна негова инстанция (обект)
- Могат да се достъпват, без да е създаден обект: само с името на класа, точка, името на статичната член-променлива или метод

</small>

<br/>

```java
System.out.println(Math.PI);
System.out.println(Math.pow(3, 2));
```

@snap[south span-100]
@[1-1](3.141592653589793)
@[2-2](9.0)
@snapend

---

#### Статични член-променливи

@ul

- Статичните член-променливи имат едно-единствено копие, което се споделя от всички инстанции на класа
  - ако са константи, пестим памет (няма смисъл да се мултиплицират във всяка инстанция)
  - ако са променливи, всяка инстанция "вижда" и променя една и съща стойност, което е механизъм за комуникация между всички инстанции на дадения клас

@ulend

---

#### Статични методи

@ul

- Статичните методи имат достъп само до статичните член-променливи и други статични методи на класа
- Нестатичните методи имат достъп както до статичните, така и до нестатичните членове на класа

@ulend

---

```java
public class Utils {
    public static final double PI = 3.14;
    private static int radius = 10;
    private String fact5 = "5!";

    public static long fact(int n) {
        if (n == 1) { return 1; } else { return n * fact(n - 1); }
    }
    public String getFact() {
        return fact5;
    }
    public static void main(String[] args) {
        System.out.println("Perimeter is " + 2 * Utils.PI * radius);
        System.out.println(new Utils().getFact() + "=" + Utils.fact(5));
        Utils.getFact();
    }
}
```

@snap[south span-100]
@[2](constant)
@[3](static member)
@[4](non-static member)
@[6-8](static method)
@[9-11](non-static method)
@[15](won't compile)
@snapend

---

#### Ключовата дума `this`

@ul

- Референция към конкретния обект
- Неявно се подава като параметър на всеки конструктор и нестатичен метод на класа
- Употребява се за:
  - достъпване на член-променливи, "скрити" от едноименни параметри на метод или локални променливи
  - извикване от конструктор на друг overloaded конструктор в същия клас
  - извикване на произволен метод на класа

@ulend

---

```java
public class Human {

    private String name;

    public Human() {
        // Извикване на overload-натия конструктор със String параметър
        this("Unknown");
    }
    public Human(String name) {
        // Достъпване на член-променлива, скрита от едноименен параметър
        this.name = name;
    }

    public void whoAmI() {
        System.out.println("My name is " + name);
    }
}
```

---

#### Обект - конкретна инстанция на даден клас

```java
public class MainApp {
    
    public static void main(String[] args) {
        Human ivan = new Human("Ivan");
        ivan.whoAmI();
        Human petar = new Human("Petar");
        petar.whoAmI();
    }

}
```

---

#### Пакети

@ul

- Именувани групи от семантично свързани класове
- Служат за йерархично организиране на кода
- Съответстват на директорно дърво на файловата система
- Конвенция за именуване:
  - само малки букви, точка за разделител
  - компаниите използват обърнат домейн адрес
    - mail.google.com -> com.google.mail

@ulend

---

#### Пакети

- всеки Java клас се намира в някакъв пакет
- пакетът се указва в началото на сорс файла (преди дефиницията на класа) с ключовата дума `package`
- ако липсва `package` декларация, класът е в пакета по подразбиране (който няма име) - което е лоша практика

<br/></br>

```java
package bg.sofia.uni.fmi.mjt.example;

public class Example {
    // class Example is in package bg.sofia.uni.fmi.mjt.example
}
```

---

#### Достъп до клас от друг пакет

@ul

- Всеки клас има достъп по подразбиране (имплицитно) до:
  - класовете от собствения си пакет
  - класовете в пакета `java.lang`
- Ако искаме клас да има достъп до клас в някой друг пакет, трябва експлицитно да го заявим с `import` декларация, която поставяме над декларацията на класа
- `import` декларацията може да е за конкретен клас с пълното му име: име на пакет + име на клас, или на всички класове в даден пакет (т.нар. wildcard import: име на пакет + символа `\*`)

@ulend

---

```java
package bg.sofia.uni.fmi.mjt.example;

import java.util.Arrays;
import java.util.Scanner;

public class StringUtils {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        char[] tokens = scanner.nextLine().toCharArray();
        Arrays.sort(tokens);
        System.out.println(tokens);
    }

}
```

---

#### Достъп до клас от друг пакет

@ul

- Прието е `import`-ите да се подреждат в сортиран лексикографски ред по `<package>.<class>`
- По-чисто е да се изброят конкретните класове от пакета, вместо `import java.util.*;`

@ulend

---

#### Модификатори за достъп

<small>
за top-level клас, т.е. невложен в друг

| Модификатор      | Видимост                                         |
| ---------------- |:------------------------------------------------ |
| public           | Достъпен за всеки клас във всеки пакет           |
| без модификатор* | Достъпен само за класовете в собствения си пакет |

<br/></br>
\* казваме също "package-private", "default"
</small>

---

#### Модификатори за достъп

<small>
За член-променливи и методи на клас

| Модификатор | Клас | Пакет | Подклас | Всички други |
| ----------- |:----:|:-----:|:-------:|:------------:|
| public      | да   | да    | да      | да           |
| protected   | да   | да    | да      | не           |
| no modifier | да   | да    | не      | не           |
| private     | да   | не    | не      | не           |

</small>

---

#### Енкапсулация

Енкапсулацията адресира основния проблем, мотивирал създаването на ООП: по-добро менажиране на конкурентния достъп до споделени данни

---

#### Енкапсулация

@ul

- Множеството текущи стойности на член-данните на даден обект се наричат негово *състояние*
- Само вътрешните методи на даден обект имат достъп до неговото състояние, като правят невъзможни неочакваните промени на състоянието от външния свят
- В Java се постига чрез модификаторите за достъп

@ulend

---

#### Енкапсулация – пример за нарушаване

```java
public class Human {

    public String name;

    public Human(String name) {
        this.name = name;
    }
}

public class Main {

    public static void main(String[] args) {
        Human ivan = new Human("Ivan");
        ivan.name = "Faked Ivan";
    }
}
```

@snap[south span-100]
@[3-4](No encapsulation)
@[14-14](Hmm..)
@snapend

---

#### Енкапсулация – пример за спазване

```java
public class Human {

    private String name;

    public Human(String name) {
        this.name = name;
    }
}

public class Main {

    public static void main(String[] args) {
        Human ivan = new Human("Ivan");
        ivan.name = "Faked Ivan";
    }
}
```

@snap[south span-100]
@[3-4](Stays hidden.)
@[14-14](Won't compile)
@snapend

---

#### Наследяване

@ul

- Позволява преизползване и разширяване на състояние и поведение на вече съществуващи класове
- Когато клас наследява друг клас, за него казваме, че е *наследник*, или *дете*, или *подклас*, а втория клас наричаме *родител*, или *базов клас*, или *суперклас*
- В Java се реализира с ключовата дума `extends`
- Класът-наследник получава достъп до всички `public` и `protected` член-променливи и методи на родителския клас
- Java не поддържа множествено наследяване

@ulend

---

#### Наследяване и method overriding

@ul

- Класът-наследник може да предостави собствена дефиниция на (т.е. да предефинира) методи на родителския клас (*method overriding*)

@ulend

---

#### Наследяване и method overriding

@ul

  - Сигнатурата на метода в класа-родител и класа-наследник трябва да е идентична
  - Модификаторът за достъп на метод в класа–наследник трябва да съвпада или да разширява модификатора за достъп на метода в родителския клас (но не може да го свива/ограничава)
  - Типът на връщаната стойност трябва да е *съвместим* с този на override-вания метод. Съвместим означава идентичен или наследник (за референтните типове) - *return type covariance*
  - Методът в класа-наследник е препоръчително да се анотира с опционалната анотация `@Override`. Така компилаторът ще ни помага да не нарушаваме горните правила

@ulend

---

#### Ключовата дума super

@ul

- Референция към прекия родител на обекта
- Употребява се за:
  - достъпване на член-променливи на родителя
  - извикване от конструктор в текущия клас на конструктор в родителския клас
  - извикване на произволен метод на родителския клас

@ulend

---

#### Ключовата дума `super`

@ul

- Неявно се подава като параметър на всеки конструктор и нестатичен метод на класа
- Не нарушава енкапсулацията - през `super` може да достъпим само `public` и `protected` членове на родителския клас

@ulend

---


```java
public class Student extends Human {

    private int facultyNumber;

    public Student(String name, int facultyNumber) {
        super(name);
        this.facultyNumber = facultyNumber;
    }

    public static void main(String[] args) {
        Student ivan = new Student("Ivan", 61786);
        ivan.whoAmI();
    }

}
```

@snap[south span-100]
@[6-6](Извикване на родителски конструктор)
@[12-12](Наследен от родителя метод)
@snapend

---

#### Йерархията от класове в Java

@ul

- Всички класове в Java са (преки или косвени) наследници на класа `java.lang.Object`
- Липсата на множествено наследяване означава, че всеки клас има точно един родител (с изключение на един-единствен клас,  `java.lang.Object`, който няма родител).
- Следователно, йерархията от класове е дърво, с `java.lang.Object` в корена

@ulend

---

#### `java.lang.Object`

```java
boolean equals(Object obj)
int hashCode()
String toString()
Object clone()
```

---

#### `equals()`

@ul

- Трябва да го предефинираме, ако сравняваме два обекта за семантична (т.е. смислова) еднаквост, а не по референциите им (т.е. адреса им в паметта)
- Например, две инстанции на клас `Student` смислово са еднакви (отговарят на един и същи студент), ако факултетните им номера са еднакви – без значение дали референциите са еднакви или не

@ulend

---

#### `hashCode()`

@ul

- Трябва да го предефинираме, ако сме предефинирали equals()
- При предефинирането на `hashCode()`, ако `equals()` връща `true`, `hashCode`-ът на съответните обекти трябва да е равен
- Ако `hashCode`-ът на два обекта е равен, не е задължително `equals()` да връща `true`

@ulend

---

#### Операторът `instanceof`

@ul

- Използва се за type checking на референтните типове - дали даден обект е инстанция на даден клас

@ulend

---

```java
Student ivan = new Student("Ivan", 61786);
Human petar = new Human("Petar");
        
System.out.println(ivan instanceof Student);   // true
System.out.println(ivan instanceof Human);     // true
System.out.println(petar instanceof Student);  // false
System.out.println(petar instanceof Human);    // true

// arrays are reference types
int[] intArr = new int[2];
System.out.println(intArr instanceof int[]);   // true

System.out.println(null instanceof AnyClass);
System.out.println(ref instanceof Object);
```

@snap[south span-100]
@[13-13](false for any class: null is not an instance of anything)
@[14-14](true for any non-null ref, because any class extends java.lang.Object)
@snapend

---

#### Pattern matching for `instanceof`

```java
// until now
if (obj instanceof String) {
    int stringLength = ((String) obj).length();
}

// Java 14 & 15 preview feature: pattern matching for instanceof
if (obj instanceof String s) {
    int stringLength = s.length();
}
```

---

#### Ключовата дума `final`

- в декларация на променлива -> прави я константа
- в декларация на метод -> методът не може да се override-ва
- в декларация на клас -> класът не може да се наследява

---

#### Полиморфизъм

- От гръцки: poly (много) + morphe (форма)
- Дефиниция от биологията - съществуване на морфологично различни индивиди в границите на един вид
- В контекста на ООП, полиморфизъм е способността на даден обект да се държи като инстанция на друг клас или като имплементация на друг интерфейс

---

#### Полиморфизъм

- ООП - наследниците на даден клас споделят поведение от родителския клас, но могат да дефинират и собствено поведение
- Всички Java обекти са полиморфични, понеже всеки обект наследява `Object` класа

---

#### Method overriding vs method overloading

@ul

- Overriding - класът-наследник предефинира поведението на класа-родител
- Overloading - класът декларира методи с едно и също име и различен брой и/или тип параметри

@ulend

---

#### Runtime полиморфизъм чрез method overriding

```java
public class Human {
    private String name;

    public Human(String name) {
        this.name = name;
    }

    public void whoAmI() {
        System.out.println("My name is " + name);
    }
}
```

---

```java
public class Student extends Human {
    private int facultyNumber;

    public Student(String name, int facultyNumber) {
        super(name);
        this.facultyNumber = facultyNumber;
    }

    @Override
    public void whoAmI() {
        super.whoAmI();
        System.out.println("My faculty number is " 
            + this.facultyNumber); 
    }
}
```

---

#### Compile-time полиморфизъм чрез method overloading

```java
public class Human {
    public void move() {
        System.out.println("I am walking using two legs.");
    }
        
    public void move(String vehicle) {
        System.out.println("I move using a " + vehicle);
    }
}

public class Main {
    public static void main(String[] args) {
        Human ivan = new Human();
        ivan.move();
        ivan.move("Car");
    }
}
```

---

#### Method overriding vs method overloading

<table>
  <tr>
    <th></th>
    <th style="font-size:0.7em">Overloading</th>
    <th style="font-size:0.7em">Overriding</th>
  </tr>
  <tr style="font-size:0.7em">
    <td>Кога</td>
    <td>Compile-time</td>
    <td>Runtime</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>Къде</td>
    <td>В същия клас</td>
    <td>В класовете - наследници</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>Runtime performance</td>
    <td>Better</td>
    <td></td>
  </tr>
  <tr style="font-size:0.7em">
    <td>Return type</td>
    <td>Може да бъде различен</td>
    <td>Съвместим</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>static, private & final methods</td>
    <td>Да</td>
    <td>Не</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>Binding</td>
    <td>Статично</td>
    <td>Динамично</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>Списък от аргументи</td>
    <td>Различен</td>
    <td>Идентичен</td>
  </tr>
</table>

---

#### Non-polymorphic code


```java
Student ivan = new Student("Ivan", 61786);
Human petar = new Student("Petar", 74451);

Object[] objs = {ivan, petar};

for (Object obj : objs) {
    if (obj instanceof Student) {
        ((Student) obj).whoAmI();
    } else if (obj instanceof Human) {
        ((Human) obj).whoAmI();
    }
}
```

@snap[south span-100]
@[7-11](instanceof and explicit casts are the "red lights")
@snapend

---

#### Polymorphic code

```java
Human[] humans = {ivan, petar};

for (Human human : humans) {
    human.whoAmI();
}
```

---

#### Polymorphic code

```java
Human[] humans = {ivan, petar};

for (Human human : humans) {
    human.whoAmI();
}
```
<br/>
Полиморфният код е не само по-кратък и четим. Помислете как трябва да се променят двата фрагмента код, ако в бъдеще се появят нови класове – наследници на `Human`

---

#### Абстрактни класове

@ul

- Дефинират се с модификатора `abstract`
- Могат да имат методи без имплементация, които се декларират с модификатора `abstract`
- Не са напълно дефинирани (оставят на наследниците си да ги конкретизират/допълнят) 
    - не могат да се създават обекти от тях
- Един клас не може да бъде едновременно `abstract` и `final` – защо?

@ulend

---

#### Абстрактни класове - пример

```java
public abstract class Cat {
    public void move() {
        System.out.println("I am walking on 4 toes.");
    }

    public void communicate() {
        System.out.println("I mew.");
    }

    public abstract void eat();
}

public class DomesticCat extends Cat {
    public void eat() {
        System.out.println("I eat Whiskas.");
    }
}

public class Leopard extends Cat {
    public void eat() {
        System.out.println("I eat any prey.");   
    }
}
```

@snap[south span-100]
@[1-11](abstract class Cat)
@[13-17](class DomesticCat)
@[19-23](class Leopard)
@snapend

---

#### Интерфейси

@ul

- Съвкупност от декларации на методи без имплементация
- Описват формално поведение, без да го имплементират
- Може да съдържат `static` `final` член-променливи == константи

@ulend

---

```java
public interface Animal {
    void move();
    void communicate();
}

public class Human implements Animal {
    private String name;
    public Human(String name) {
        this.name = name;
    }
    public void move() {
        System.out.println("I am walking using two legs");
    }
    public void communicate() {
        System.out.println("I speak");
    }
}

public class Cat implements Animal {
    public void move() {
        System.out.println("I am walking using 4 toes");
    }
    public void communicate() {
        System.out.println("I mew");
    }
}
```

@snap[south span-100]
@[1-4](interface Animal)
@[6-18](class Human)
@[19-27](class Cat)
@snapend

---

#### Методи на интерфейсите

@ul

- Методите на интерфейсите са `public` и `abstract` по подразбиране
- Модификаторите `public` и `abstract` (заедно или поотделно) могат да бъдат указани и експлицитно
    - дали да бъдат експлицитно указани, е въпрос на стил - но е добре да сме консистентни
- Тъй като методите са абстрактни, не могат да бъдат декларирани като `final`

@ulend

---

#### Интерфейси и наследяване

@ul

- Интерфейсите могат да се наследяват
- Един интерфейс може да наследява множество интерфейси

@ulend

---

#### Интерфейсите и имплементаците им

@ul

- Интерфейсите не могат да се инстанцират
- Можем да инстанцираме (конкретни) класове, които ги имплементират
- Можем да присвояваме инстанция на клас на променлива от тип интерфейс, който класът имплементира
- Можем да проверяваме с `instanceof` дали клас имплементира даден интерфейс
- Един клас може да имплементира множество интерфейси

@ulend

---

#### Интерфейси и имплементациите им

@ul

- Ако даден клас декларира, че имплементира интерфейс, той трябва или
  - да даде дефиниции на *всичките* му методи, или
  - да бъде деклариран като абстрактен
- Като следствие, ако променим сигнатурата на метод(и) на интерфейса, или ако добавим нов(и) метод(и), трябва да променим и всички имплементиращи интерфейса класове
- Това често е проблем, а понякога е и невъзможно (нямаме контрол върху всички имплементации)

@ulend

---

#### Default методи в интерфейсите (от Java 8)

@ul

- Default-ен метод в интерфейс е метод, който
  - има имплементация
  - има модификатора `default` в декларацията си
- Имплементиращите класове имплицитно ползват default-ната имплементация на методите, но могат и да я предефинират

@ulend

---

#### Default методи в интерфейсите (от Java 8)

@ul

- Клас може да имплементира произволен брой интерфейси
- Ако два или повече от тях съдържат `default` метод с еднаква сигнатура, класът трябва задължително да предефинира този метод
- В предефинирания метод може експлицитно да се укаже, default-ната имплементация от кой родителски интерфейс да се ползва. В този случай, синтаксисът е, `<имеНаИнтерфейс>.super.<имеНаDefaultМетод>()`

@ulend

---

#### Статични методи в интерфейсите (от Java 8)

@ul

- От Java 8, интерфейсите могат да съдържат и статични методи с имплементация
- Една класическа употреба е, за *factory* методи (ще говорим за тях в лекцията за design patterns)

@ulend

---

#### Private методи в интерфейсите (от Java 9)

@ul

- От Java 9, интерфейсите могат да съдържат и `private` методи с имплементация
- Изполват се, когато в интерфейса има два ли повече default-ни или статични метода, чиято имплементация частично се дублира
    - тогава изнасяме повтарящия се код в `private` метод, за да предотвратим code duplication

@ulend

---

#### Интерфейсите - обобщение

@ul

- Интерфейсите могат да съдържат
  - Публични, абстрактни методи без имплементация
  - `static` `final` член-променливи == константи
  - `default` и `static` методи с имплементация (от Java 8)
  - `private` методи (от Java 9)

@ulend

---

#### Интересни частни случаи на интерфейси

@ul

- Интерфейс, който
    - не съдържа нито един метод, се нарича *маркерен*
    - има точно един публичен абстрактен метод, се нарича *функционален*

@ulend

---

#### Абстракция

@ul

- Абстракция означава, моделирайки в обектно-ориентиран език за програмиране обекти от реалния или виртуалния свят, да се ограничим само до съществените им за конкретната задача характеристики и да се абстрахираме (пропуснем) в модела несъществените или нерелевантни за задачата
    - Пример: моделирайки студент, да го характеризираме само с име и факултетен номер, абстрахирайки се от всички други характеристики на студента в реалния свят (напр. цвят на очите)

@ulend

---

#### Абстракция

@ul

- Абстракция също означава да работим с нещо, което знаем как да използваме, без да знаем как работи вътрешно. Всяка конкретна имплементация на поведение е скрита в своя обект, за външния свят е видимо само поведението (т.е. интерфейсът)
- Принципът за абстракция се постига в Java чрез интерфейси и абстрактни класове

@ulend

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend

## Обектно-ориентирано програмиране с Java

#### Част II

_28.10.2020_

---

#### Предната лекция говорихме за:

@ul

- Класове и обекти
- Абстрактни класове и интерфейси
- Фундаменталните ООП принципи
  - Енкапсулация
  - Наследяване
  - Полиморфизъм
  - Абстракция
@ulend

---

#### Днес ще разгледаме:

@ul

- Enums
- Records (Java 15 preview)
- Sealed класове и интерфейси (Java 15 preview)
- Изключения

@ulend

---

#### Предаване на аргументи в Java

@ul

- конструкторите и методите имат списък от (нула или повече) *параметри* (или *формални параметри*)
- параметрите са списък (наредена n-торка) от тип и име на параметъра
- при извикване на конструктора или метода, се подава списък от *аргументи* (или *фактически параметри*), които трябва да са съвместими като брой, подредба и тип със списъка параметри

@ulend

---

#### Предаване на примитивни типове като аргументи

<small>
Примитивните типове се предават по стойност, т.е. създават се техни копия и промяната на стойностите на параметрите вътре в конструктора или метода не се отразява на стойностите на променливите, подадени като аргументи.
</small>

<br/>

```java
public class PassPrimitiveByValue {
    public static void main(String[] args) {
        int x = 3;
        // invoke passMethod() with 
        // x as argument
        passMethod(x);
        // print x to see if its 
        // value has changed
        System.out.println("After invoking passMethod(), x = " + x);
    }
    // change parameter in passMethod()
    public static void passMethod(int p) {
        p = 10;
    }
}
```

---

#### Предаване на референтни типове като аргументи

<small>
Референтните типове (обекти, масиви) също се предават по стойност: референциите, подадени като аргументи, имат същата стойност (т.е. сочат към същото място в паметта), както и преди извикването.
Стойностите на член-данните на реферираните обекти обаче могат да се променят в метода, ако е налице необходимият достъп (в смисъл на енкапсулация) до тях.
</small>

<br/>

```java
public void moveCircle(Circle circle, int deltaX, int deltaY) {
    // code to move origin of circle to x+deltaX, y+deltaY
    circle.setX(circle.getX() + deltaX);
    circle.setY(circle.getY() + deltaY);
        
    // code to assign a new reference to circle
    circle = new Circle(0, 0);
}

// [...]

moveCircle(myCircle, 23, 56);
// myCircle reference remains unchanged,
// but coordinates of the referred circle are changed after the call
```

---

#### Декларация vs. инициализация, stack vs. heap

```java
public class Person {
    int id;
    String name;
 
    public Person(int id, String name) {
        this.id = id;
        this.name = name;
    }
}

public class PersonBuilder {
    private static Person buildPerson(int id, String name) {
        return new Person(id, name);
    }
 
    public static void main(String[] args) {
        int id = 23;
        String name = "John";
        Person person = null;
        person = buildPerson(id, name);
    }
}
```

@snap[south span-100]
@[1-9](клас Person)
@[11-22](клас PersonBuilder)
@snapend

---

![Stack vs. heap](images/03.0-stack-vs-heap.png)

---

#### Характеристики на stack паметта

@ul

- автоматично се заделя при извикване на метод и освобождава при приключването му
- променливите в стека съществуват, докато трае изпълнението на метода, който ги е създал (като параметри и локални променливи)
- ако стек паметта се запълни, се хвърля `java.lang.StackOverFlowError`
- обикновенно е с по-малък размер от heap паметта
- достъпът до стек паметта е бърз в сравнение с достъпа до heap паметта

@ulend

---

#### Характеристики на heap паметта

@ul

- динамична памет за обекти и масиви
- заделя се явно с оператора `new` или неявно, и се освобождава от garbage collector-a
- новосъздаваните обекти стоят в heap-a, а референциите към тях - в stack-а
- ако heap паметта се запълни, се хвърля `java.lang.OutOfMemoryError`
- достъпът до heap паметта е по-бавен в сравнение с достъпа до stack паметта

@ulend

---

#### Създаване и инициализация на обектите

@ul

- член-променливите на даден клас се инициализират със стойността по подразбиране на дадения тип
- може да ги инициализираме явно, с присвояване, като част от декларацията им
  - това е подходящо, ако е с литерал или прост израз, но не и ако инициализацията има по-сложна логика, например включва обработка на грешки, завъртане на цикъл за масиви и т.н.
- нестатичните член-променливи могат да се инициализират и в конструкторите
- за статичните член-променливи обаче, няма такава възможност. Затова са измислени т.нар. инициализационни блокове (*initializers*)

@ulend

---

#### Initializer

@ul

- представлява блок код, който
  - не е свързан с име или тип данни
  - намира се в тяло на дефиниция на клас, но извън конструктор или метод
- в даден клас може да има нула, един или няколко инициализационни блока
- могат да се ползват за инициализация на член-данните на класа (статични и нестатични)
- алтернативата е, инициализационната логика да е отделена в методи

@ulend

---

```java
public class InitializeMe {

    private int a;
    private static int b;

    static {
       // static initializer block
       b = 100;
    }

    {
        // initializer block
        a = 5;
    }
}
```

---

#### Ред на инициализация на обектите

@ul

1. инициализират се статичните член-променливи и се изпълняват статичните инициализатори на базовия клас, в реда на срещането им в дефиницията на класа
2. инициализират се статичните член-променливи и се изпълняват статичните инициализатори на класа, в реда на срещането им в дефиницията му
3. изпълняват се инициализаторите на базовия клас, в реда на срещането им
4. изпълнява се конструкторът на базовия клас
5. изпълняват се инициализаторите на класа, в реда на срещането им
6. изпълнява се конструкторът на класа

@ulend

---

### Enums

---

#### Enum

@ul

- Специален референтен тип (клас), представящ фиксирано множество от инстанции-константи
- Нарича се enum(eration), защото инстанциите се дефинират чрез изброяване

@ulend

---

```java
public enum Day {
    SUNDAY,
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY
}
```

---

#### Enum

@ul

- Всеки enum неявно наследява абстрактния клас `java.lang.Enum`
  - не може да наследява явно друг клас, защото би било множествено наследяване
  - може да имплементира интерфейси
- Тялото на `enum` класа може да съдържа член-променливи и методи
- Ако има конструктор, той трябва да е package-private или `private`
- Той автоматично създава константите в дефиницията на `enum`-a. Не може да се извиква явно

@ulend

---

```java
public class EnumExample {
    private Day day;
    public EnumExample(Day day) { this.day = day; }
    public void tellItLikeItIs() {
        String message = switch (day) {
            case MONDAY -> "Mondays are bad.";
            case FRIDAY -> "Fridays are better.";
            case SATURDAY, SUNDAY -> "Weekends are best.";
            default -> "Midweek days are so-so.";
        };
        System.out.println(message);
    }
    public static void main(String[] args) {
        EnumExample example = new EnumExample(Day.TUESDAY);
        example.tellItLikeItIs();
    }
}
```

---

#### Enum

@ul

- Компилаторът добавя автоматично и няколко специални статични методи:
  - `values()` - връща масив, съдържащ всички стойности в `enum`, в реда, в който са изброени в декларацията
  - `valueОf(String name)` - връща `enum` константата по даденото име

@ulend

---

### Records

---

#### Records (Java 15 preview)

@ul

- една от най-честите критики към Java е, че се пише доста boilerplate код
- например, за почти всеки клас, се налага да дефинираме публичен конструктор, getter методи, `toString()`, `equals()` и `hashCode()`
- за много класове, те имат стандартни, тривиални имплементации и могат да бъдат генерирани автоматично (IDE-тата имат такава функционалност)
- дори като автори на класа да ги генерираме автоматично обаче, проблемът остава за четящите кода

@ulend

---

#### Records

@ul

- както enums, records са нов реферетен тип и са (ограничен) вид клас
- описват компактно т.нар *value objects* - класове, които имат само състояние: състоят се от "полетата, само полетата и нищо освен полетата"
- може да мислим за тях като за именувана наредена n-торка стойности
- те са (shallowly) immutable агрегации на фиксирано множество от стойности, известни като *компоненти на record-a*

@ulend

---

#### Records

```java
public record Point(int x, int y) {}

// [...]

Point p = new Point(-1, 2);
System.out.println(p.x() + ", " + p.y());
```

---

#### Records

@ul

- компилаторът автоматично генерира boilerplate кода за
  - `private` `final` член-данна за всяко поле, със същото име и тип
  - *каноничен* конструктор: със списък с параметри, отговарящ на декларираното описание на състоянието
  - getter методи за полетата (имената им съвпадат с имената на съответните полета)
  - `equals()`, `hashCode()` и `toString()`
    - ако `r` е record от тип `R` с компоненти `c1, c2, ..., cN`, и създадем копие на инстанцията като `R copy = new R(r.c1(), r.c2(), ..., r.cN())`, то `r.equals(copy) == true`
  - компонентите на `record`-ите могат да имат анотации, например `@NotNull`


@ulend

---

#### Records

@ul

- инстанции се създават с оператора `new`
- всички records имплицитно наследяват абстрактния клас `java.lang.Record`, самите те са `final` и не могат да са `abstract`
- `java.lang.Record` не може да бъде явно наследяван
- той дефинира `equals()`, `hashCode()` и `toString()` като абстрактни методи

@ulend

---

#### Пример: без records

```java
public final class FXOrderClassic {
    private final int units;
    private final CurrencyPair pair;
    private final Side side;
    private final double price;
    private final LocalDateTime sentAt;

    public FXOrderClassic(int units, CurrencyPair pair, Side side,
                               double price, LocalDateTime sentAt) {
        this.units = units;
        this.pair = pair; // CurrencyPair is a simple enum
        this.side = side; // Side is a simple enum
        this.price = price;
        this.sentAt = sentAt;
    }

    public int units() { return units; }
    public CurrencyPair pair() { return pair; }
    public Side side() { return side; }
    public double price() { return price; }
    public LocalDateTime sentAt() { return sentAt; }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) 
            return false;
        FXOrderClassic that = (FXOrderClassic) o;

        if (units != that.units) return false;
        if (Double.compare(that.price, price) != 0) { return false; }
        if (pair != that.pair) return false;
        if (side != that.side) return false;
        return sentAt != null ? sentAt.equals(that.sentAt) : that.sentAt == null;
    }

    @Override
    public int hashCode() {
        int result;
        long temp;
        result = units;
        result = 31 * result + (pair != null ? pair.hashCode() : 0);
        result = 31 * result + (side != null ? side.hashCode() : 0);
        temp = Double.doubleToLongBits(price);
        result = 31 * result + (int) (temp ^ (temp >>> 32));
        result = 31 * result + (sentAt != null ? sentAt.hashCode() : 0);
        return result;
    }

    @Override
    public String toString() {
        return "FXOrderClassic{" +
                "units=" + units +
                ", pair=" + pair +
                ", side=" + side +
                ", price=" + price +
                ", sentAt=" + sentAt +
                '}';
    }
}
```

@snap[south span-100]
@[2-6](полета)
@[8-15](конструктор)
@[16-21](getter методи)
@[23-35](equals())
@[36-48](hashCode())
@[49-59](toString())
@snapend

---

#### Същия пример: с records

```java
public record FXOrder(int units,
                      CurrencyPair pair,
                      Side side,
                      double price,
                      LocalDateTime sentAt) {}
```

---

#### Records

@ul

- опционално, освен едноредова декларация, record-ите могат да съдържат допълнителни конструктори, методи, статични член-данни и статични factory методи
- ако обаче се изкушаваме да дефинираме такива, да имплентираме допълнителни интерфейси и т.н., вероятно по-добро дизайн решение би било да създадем обикновен клас

@ulend

---

#### Records


@ul

- изключение са т.нар. *компактни конструктори*: в тялото на каноничния конструктор, добавяме само валидация и/или нормализация на параметрите, а останалата част от кода (присвояванията на полетата) се осигурява от компилатора
- компактните конструктори нямат параметри, пропускат се дори празните скоби `()`
- кодът в компактния конструктор се добавя като допълнителен код в началото на дефиницията на каноничния конструктор (а не е отделен конструктор)

@ulend

---

#### Пример: record с компактен конструктор

```java
public record FXOrder(int units, 
                      CurrencyPair pair, 
                      Side side, 
                      double price, 
                      LocalDateTime sentAt, 
                      int ttl) {
    public FXOrder {
        if (units < 1) {
            throw new IllegalArgumentException(
                "FXOrder units must be positive");
        }
        if (price <= 0.0) {
            throw new IllegalArgumentException(
                "FXOrder price must be positive");
        }
    }
}
```

---

#### Пример: record със статичен factory метод

```java
public static FXOrder of(CurrencyPair pair, 
                             Side side, 
                             double price) {
        return new FXOrder(1, pair, side, price, 
                           LocalDateTime.now());
}
```

---

#### Локални интерфейси, enums и records (Java 15)

- Интерфейси, enums и records могат да бъдат дефинирани в тялото на метод, което ги прави локални за него
- Това подобрява енкапсулацията, ако въпросните типове са нужни само в имплементацията на метода

---

#### Sealed класове и интерфейси (Java 15 preview)

```java
public abstract sealed class Shape
    permits Circle, Rectangle {...}

public class Circle extends Shape {...} // OK
public class Rectangle extends Shape {...} // OK
public class Triangle extends Shape {...} // Compile error

// No need for default case if all permitted types are covered
double area = switch (shape) {
    case Circle c    -> Math.pow(c.radius(), 2) * Math.PI
    case Rectangle r -> r.a() * r.b()
};
```

@snap[south span-100]
@[1-2](sealed класовете декларират, кои класове могат да ги наследяват)
@[4-6](дефиниране на класове - наследници на sealed клас)
@[8-12](sealed класове като селектор на switch)
@snapend

---

#### Sealed класове

@ul

- наследниците на `sealed` клас могат да бъдат `final`, `non-sealed` или `sealed`
- `sealed` клас може да бъде и абстрактен
- `sealed` класът и неговите permitted класове трябва да са в един пакет
- ако `sealed` класовете са кратки и малък брой, те могат да се дефинират в същия сорс файл като родителския клас
  - в този случай, `permits` клаузата може да се пропусне - компилаторът приема за имплицитно permitted класовете в дадения сорс файл

@ulend

---

```java
public sealed class Plant permits Herb, Shrub, Climber {}

final class Herb extends Plant {}
non-sealed class Shrub extends Plant {}
sealed class Climber extends Plant permits Cucumber{}
final class Cucumber extends Climber {}
```

---

#### Sealed интерфейси

@ul

- `sealed` интерфейсите могат да специфицират, кои интерфейси могат да ги наследяват и кои класове могат да ги имплементират
  - интерфейс - наследник на `sealed` интерфейс може да е деклариран като `non-sealed` или `sealed`. Интерфейсите не могат да са `final`
  - клас, имплементиращ `sealed` интерфейс, може да бъде `final`, `non-sealed` или `sealed`
  - `record` също може да имплементира `sealed` интерфейс
    - Тъй като всеки `record` е имплицитно `final`, той няма нужда от явен модификатор

@ulend

---

```java
sealed public interface Move permits Athlete, Person, Jump, Kick {}

final class Athlete implements Move {}
record Person(String name, int age) implements Move {}
non-sealed interface Jump extends Move {}
sealed interface Kick extends Move permits Karate {}
final class Karate implements Kick {}
```

---

#### Сорс файлове на абстрактни класове, интерфейси, enums и records

@ul

- Важат същите правила като при конкретните класове:
  - абстрактните класове, интерфейсите, `enum`-ите и `record`-ите се записват във файл
    - с име, съвпадащо с името на абстрактния клас/интерфейс/`enum`/`record`
    - с разширение `.java`

@ulend

---

### Изключения

---

#### Изключение (Exception)

@ul

- Събитие (проблем), което се случва по време на изпълнение на дадена програма и нарушава нормалната последователност на изпълнение на инструкциите ѝ
- Още един начин за комуникация на метод с извикващите го: връщана стойност при нормално изпълнение и изключение при проблем

@ulend

---

#### Например...

@ul

- Подали сме невалидни входни данни
- Опитваме се да отворим несъществуващ файл
- Мрежата се е разкачила по време на комуникация
- Свършила е паметта на виртуалната машина
- ...

@ulend

---

#### Как се генерира ("хвърля") изключение?

```java
public Object pop() {
    if (size == 0) {
        throw new EmptyStackException();
    }

    // [...]
}
```

---

#### Как се обработва ("лови") изключение?

```java
try {
    // код, който може да хвърли изключение
} catch (Exception e) {
    // обработваме изключението ("exception handler")
    // може да има повече от един catch блок
} finally {
    // при нужда, някакви заключителни операции
    // finally блокът е optional, но ако го има,
    // се изпълнява задължително щом влезем в try-a
}
```

---

#### Catch block chain

```java
try { 
    // [...]
} catch (MostSpecificException mse) {
    // [...]
} catch (MoreGeneralException mge) {
    // [...]
} ... {
    // [...]
} catch (LeastSpecificException lse) {
    // [...]
}
```

---

#### Multi catch block

```java
try {
    // [...]
} catch (IOException | SQLException e) {
    // [...]
}
```

---

#### Стек на извикванията (call stack)

![Call stack](images/03.1-call-stack.jpg)

---

#### Видове изключения

@ul

- Изключителните събития могат да се дължат на грешка на потребителя, бъг в кода или физически ресурс, който не е достъпен
- Делят се на три вида:
  - Checked (Compile-time) exceptions
  - Unchecked (Runtime) exceptions
  - Errors

@ulend

---

#### Видове изключения

![Exceptions](images/03.2-exceptions.jpg)

---

#### Checked vs. unchecked exceptions

![Exceptions](images/03.3-exceptions.jpg)

---

#### Checked exceptions

@ul

- Наричат се още compile-time exceptions, защото компилаторът ни задължава да ги обработим
- Едно добре написано приложение, би трябвало да ги очаква и да се възстановява от тях

@ulend

---

#### Checked exceptions - примери

@ul

- `FileNotFoundException` при опит да отворим файл по име, какъвто не съществува
- `IOException` при проблем с четене или писане във файл

@ulend

---

#### Unchecked (Runtime) exceptions

@ul

- Възникват по време на изпълнение на приложението, затова се наричат още runtime exceptions
- Приложението обикновено не може да ги очаква или да се възстанови от тях
- Най-често, са резултат от бъгове (логически грешки) в кода, неправилно извикване на API-та и т.н.

@ulend

---

####  Unchecked (Runtime) exceptions - примери

@ul

- `ArithmeticException` при опит за деление на нула
- `ArrayIndexOutOfBoundsException` при опит да достъпим елемент на масив по индекс извън размера на масива
- `NullPointerException` при опит за достъпване на член-данна или метод на обект по референция, която е `null`
- `ClassCastException` при опит да се cast-не обект към клас, на който обектът не е инстанция

@ulend

---

#### Errors

@ul

- Проблеми, които възникват извън приложението, и приложението обикновено не може да ги очаква или да се възстанови от тях
- Обикновено се генерират от самата виртуална машина

@ulend

---

#### Errors - примери

@ul

- `OutOfMemoryError` при опит да заделим heap памет, когато свободната памет не е достатъчна (и не може да освободи с garbage collection)
- `StackOverflowError` когато метод извиква свое копие твърде много пъти (напр. при безкрайна рекурсия)

@ulend

---

#### Деклариране на хвърляни изключения

Ако метод не прехваща/обработва даден checked exception, който може да се хвърли в тялото му, той трябва да го декларира в сигнатурата си, за да "предупреди" тези, които го викат:

<br/>

```java
public void writeList() throws IOException, FileNotFoundException {
    // [...]
}
```

---

#### Chained exceptions

```java
try {
    // [...]
} catch (IOException e) {
    // прехващаме изключение, обработваме го 
    // и хвърляме ново, към което го "закачаме"
    throw new SampleException("Oopss..", e); 
}
```

---

#### Finally – не само за обработка на изключения

```java
try { 
    // тук може да се хвърлят изключения
    // или да има return/continue/break
} finally {
    // някакъв важен cleanup code -
    // ще се изпълни винаги*, независимо какво се случи в try блока
}
```

---

#### Подобрен NullPointerException (Java 15)

```java
public class HelpfulNPE {
    class A {
        public B b;
    }
    class B {
        public C c;
    }
    class C {
        public int number;
    }
    public void helpfulNPEDemo() {
        A a = new A();
        a.b.c.number = 100; // Line 13: will throw NullPointerException at runtime
    }
    public static void main(String[] args) {
        new HelpfulNPE().helpfulNPEDemo();
    }
}
```

---


#### Подобрен NullPointerException (Java 15)

before:
```bash
Exception in thread "main" java.lang.NullPointerException
    at HelpfulNPE.helpfulNPEDemo(HelpfulNPE.java:13)
    at HelpfulNPE.main(HelpfulNPE.java:16)
```

since Java 15:
```bash
Exception in thread "main" java.lang.NullPointerException:
                            Cannot read field "c" because "a.b" is null
    at HelpfulNPE.helpfulNPEDemo(HelpfulNPE.java:13)
    at HelpfulNPE.main(HelpfulNPE.java:16)
```

---

#### Защо да ползваме изключения?

@ul

- Отделяме кода за обработка на грешки от останалия ⇨ става по-четим
- "Препредаване" на грешки по стека на извикванията
- Групиране и диференциране на различните типове грешки

@ulend

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend

---

## Качествен (Clean) Code

_04.11.2020_

![Clean Code Zen](images/04.1-clean-code-zen.png)

---

#### Как мерим качеството на кода?

![Code Quality](images/04.2-wtfs-per-min.png)

---

#### Принципи на чистия код - именуване, конвенции и добри практики

@ul

- Имената на пакети, класове, интерфейси, член-променливи, методи, локални променливи трябва да са говорещи и да спазват установените конвенции

@ulend

---

#### Принципи на чистия код - именуване, конвенции и добри практики

@ul

- пакети
  - само малки букви, със смислена йерархия
  - `bg.sofia.uni.fmi.mjt`
- класове, абстрактни класове, интерфейси, enums, records
  - съществителни, започващи с главна буква (upper camel case)
    - `Student`, `GameBoard`
    - имената на интерфейси често са отглаголни съществителни
      - `Runnable`, `Serializable`

@ulend

---

#### Принципи на чистия код - именуване, конвенции и добри практики

@ul

- методи
  - глаголи, започващи с малка буква (camel case), без подчертавки
  - `reverseString()`, `calculateSalary()`
- променливи
  - започващи с малка буква (camel case)
- константи
  - all-caps, с подчертавки между думите
  - `MAX_NAME_LENGTH`

@ulend

---

#### Принципи на чистия код - Спазвай ООП принципите

- Енкапсулация
  - Свеждай публичните части до минимум
- Наследяване
  - Не допускай code duplication

---

#### Принципи на чистия код - Спазвай ООП принципите

- Полиморфизъм
  - Ползвай полиморфизъм винаги, когато е възможно
  - Използвай интерфейс за декларация, конкретна имплементация за инициализация
  - Предпочитай интерфейс вместо имплементация в сигнатурите на публичните ти методи

---

#### Стреми се към хубав ОО дизайн

@ul

- Използвай само по изключение пакета по подразбиране
- Един клас трябва да прави едно нещо
- Ако имаш "and" в името на класа, вероятно не е така
- Ако имаш "Helper", "Manager", "Utility" в името, *може би* има по-добър дизайн
- Един метод трябва да прави едно нещо
- Методът трябва да е кратък: < 20 реда код

@ulend

---

#### Стреми се към хубав ОО дизайн

@ul

- Ако имаш "and" в името на метод, може би той прави повечко неща: раздели го на няколко
- Ако имаш много параметри на метод:
  - може би не му е мястото в този клас (а там, откъдето се взимат стойностите за тези параметри)
  - или трябва да направиш *data object* / `record`, който да групира семантично свързаните от тях
- Не злоупотребявай със `static`

@ulend

---

#### Принципи на чистия код - форматирай

- Форматирай си кода
- Нямаш никакво оправдание да не го правиш: има IDE shortcuts
    - Ctrl+Alt+L (IntelliJ)
    - Ctrl+Shift+F (Eclipse)

---

#### Не използвай "magic numbers"

<small>Вместо "магически числа" в кода, ползвай подходящо именувани константи</small>

```java
// Bad
for (int i = 0; i < 16; i++) { /* what is 16?! */ }

if (message.startsWith("[ERROR] ")) { /* ?! */ }

// Good
public static final int MAX_PASSWORD_LENGTH = 16;
//  [...]
for (int i = 0; i < MAX_PASSWORD_LENGTH; i++) { /* do something */ }

private static final String ERROR_MESSAGE_PREFIX = "ERROR: ";
//  [...]
if (message.startsWith(ERROR_MESSAGE_PREFIX)) { /* do something */ }
```

---

#### Принципи на чистия код

```java
// Bad
if (x % 2 == 0)
    return x / 2;

// Good: Винаги ограждай в блок телата на if-else и цикли,
// дори да са с по един statement
if (x % 2 == 0) {
    return x / 2;
}
```

---

#### Принципи на чистия код

```java
// Bad
public int calculateSalary()
{

}

// Good: отварящата фигурна скоба на блок не стои на отделен ред
// Изключение: initializer блоковете
public int calculateSalary() {

}

```

---

#### Принципи на чистия код

```java
// Bad
if (x % 2 == 0) {
    return true;
} else {
    return false;
}
```
<p><p>

```java
// Good: Изразявай се кратко. Малко код == малко бъгове
return x % 2 == 0;
```

---

#### Принципи на чистия код

@ul

- Слагай коментари, без да прекаляваш
- Хубавият код е self-explanatory, и все пак, на места си трябва коментар
- Разделяй нормалната логика от exception логиката
- Ползвай изключения вместо error codes и печатане на съобщения в конзолата
- Не suppress-вай / swallow-вай exceptions
    - Никога не оставяй празен `catch`, или `catch` само с `e.printStackTrace()`

@ulend

---

```java
// Bad
try {
    // do something with the file system
} catch (FileNotFoundException e) {
    // I hope someone reads the logs
    e.printStackTrace();
} catch (IOException e) {
    // the admin should see this
    System.err.println("I/O exception accessing the file system.");
}
```

---

```java
// Good
try {
    // do something with the file system
} catch (FileNotFoundException e) {
    // catalog file is missing -
    // this is OK, first access should create an empty catalog
    createEmptyShoppingCatalog();
} catch (IOException e) {
    // catalog file is there but cannot be opened or read
    // calling method knows how to handle this
    throw new ShoppingException("Cannot get shopping catalog", e);
}
```

---

#### Разделяй I/O логиката от *бизнес* логиката

```java
// Bad
public static void factorial() { // swiss knife: all-in-one
    Scanner sc = new Scanner(System.in);
    int n = -1; long result = 1;
    do {
        System.out.println("Въведи число:");
        try {
            n = Integer.parseInt(sc.nextLine());
        } catch (Exception e) {
            continue;
        }
    } while (n < 0);
    for (int i = 2; i <= n; i++) {
        result *= i;
    }
    System.out.println("n! = " + result);
}

public static void main(String... args) {
    factorial();
}
```

---

#### Разделяй I/O логиката от *бизнес* логиката

```java
// Good
private static int readAndValidate(Scanner sc) { // handle input
    int n = -1;
    do {
        System.out.println("Въведи число:");
        try {
            n = Integer.parseInt(sc.nextLine());
        } catch (Exception e) {
            continue;
        }
    } while (n < 0);
    return n;
}

private static void printOutput(long result) { // handle output
    System.out.println("n! = " + result);
}
```

---

#### Разделяй I/O логиката от *бизнес* логиката

```java
    //Good
    public static long factorial(int n) { // business logic
        long result = 1;
        for (int i = 2; i <= n; i++) {
            result *= i;
        }
        return result;
    }

    public static void main(String... args) {
        int input = readAndValidate(new Scanner(System.in));
        long result = factorial(input);
        printOutput(result);
    }
```

---

#### Java код конвенции

<small>
Запознай се с цялостна Java код конвенция и се придържай към нея.
Две от най-популярните:
<p><p>
[Oracle Code Conventions for the Java Programming Language](https://www.oracle.com/technetwork/java/javase/documentation/codeconvtoc-136057.html)
<p>
[Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)
</small>

![Popular Java Code Conventions](images/04.3-oracle-google.png)

---

#### Инструменти за статичен код анализ

@ul

- Има инструменти за статичен код анализ, които
  - автоматизират придържането към код конвенции
  - намират и бъгове

@ulend

---

#### Най-популярните open-source инструменти

<small>
[checkstyle](http://checkstyle.sourceforge.net/index.html)<p>
[PMD](https://pmd.github.io/)<p>
[FindBugs](http://findbugs.sourceforge.net/index.html)
</small>

![Static Code Analyzers](images/04.4-static-code-analyzers.png)

---

#### Библията

![Clean Code](images/04.5-clean-code.png)

---

“Writing clean code is what you must do in order to call yourself a professional.
There is no reasonable excuse for doing anything less than your best.”

― Robert C. Martin, Clean Code: A Handbook of Agile Software Craftsmanship

---

#### PlanetGeek

[Clean Code Cheat Sheet](https://www.planetgeek.ch/wp-content/uploads/2014/11/Clean-Code-V2.4.pdf)

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend

---

## Структури от данни

_04.11.2020_

![Collections](images/04.6-collections.png)

---

## Структури от данни

@ul

- Хранилища за данни
- Основни операции
  - добавяне
  - триене
  - търсене
  - обхождане

@ulend

---

#### Масиви - предимства

@ul

- пределно прост "интерфейс"
- най-ефективни от гледна точка на използвана памет*
- бърз достъп на елемент по индекс: O(1)

@ulend

---

#### Масиви - недостатъци

@ul

- размерът им е фиксиран при инициализацията
- добавянето или изтриването на елемент (с изключение на последна позиция) е скъпа операция
- търсенето на елемент по стойност е бавно:
    - О(N) за произволен масив
    - O(logN) за сортиран масив

@ulend

---

#### Колекции

@ul

- Java предоставя т.нар. collections framework, съдържащ интерфейси, имплементации и алгоритми върху най-използваните структури от данни
- За разлика от масивите,
    - размерът им е динамичен
    - съдържат само референтни типове
- Всички* интерфейси и класове се намират в пакета `java.util`

@ulend

---

#### Колекции

Някои ползи от наличието на collections framework:
- Не се налага да преоткриваме топлата вода
- Увеличават се скоростта и качеството на програмите ни
- Стимулира се преизползването на код

---

#### Итератори

- Итераторите предоставят унифициран начин за обхождане на елементите на дадена колекция.
- Колекциите (както и масивите) могат да се обхождат с foreach loop

---

#### Интерфейси `Iterator` и `Iterable`

```java
public interface Iterator<E> {
    boolean hasNext();
    E next();
    void remove();
}

public interface Iterable<T> {
    Iterator<T> iterator();
}
```

---

#### `java.util.Iterator`

@ul

- Методът `remove()` премахва от колекцията елемента, последно върнат от `next()`
- Ако колекцията бъде модифицирана докато бъде итерирана, по какъвто и да е начин, различен от извикване на `remove()` на итератора, поведението на итератора е недефинирано
    - В частност, може да се хвърли `ConcurrentModificationException` (дори в еднонишков код)

@ulend

---

Основните структури от данни, използвани в имплементациите на колекциите, са

- Масиви
- Свързани списъци
- Хеш таблици
- Дървета

<br/>

![Basic Data Structures | 70%](images/04.7-basic-data-structures.png)

---

![Collection diagrams](images/04.8-collections-diagram.png)

---

![Map hierarchy](images/04.9-java-map-hierarchy.png)

---

#### Обхождане на колекции

```java
List<Float> nums = Arrays.asList(4.999f, 0.271f, 7.1f, -1f);
```

- Чрез enhanced for-loop:

```java
for (float current : nums) {
    System.out.printf("%.2f%n", current);
}
```

- Чрез итератор:

```java
Iterator<Float> iterator = nums.iterator();
while (iterator.hasNext()) {
    System.out.printf("%.2f%n", iterator.next());
}
```

---

#### Обхождане на `Map`

Според това какво ни е нужно, може да вземем от `Map`-a:

- множеството от ключовете
```java
Set<Integer> keys = map.keySet();
```
- колекция от стойностите
```java
Collection<String> values = map.values();
```

- колекция от двойките ключ-стойност
```java
Set<Entry<Integer, String>> s = map.entrySet();
```

---

__java.util.Collection__

```java
int size()
boolean isEmpty()
boolean contains(Object element)
boolean add(E element)
boolean remove(Object element)
Iterator<E> iterator()

boolean containsAll(Collection<?> c)
boolean addAll(Collection<? extends E> c)
boolean removeAll(Collection<?> c)
boolean retainAll(Collection<?> c)
void clear()

Object[] toArray()
<T> T[] toArray(T[] a)
```

@[1-6]
@[8-12]
@[14-15]

---

__List__

```java
boolean add(E e)
boolean contains(Object o)
E get(int index)
int indexOf(Object o)
boolean remove(Object o)
E remove(int index)
int size()
boolean isEmpty()
Object[] toArray()
List<E> subList(int fromIndex, int toIndex)
```

---

#### Имплементации на `List`

- `ArrayList` - resize-ващ се (динамичен) масив
- `LinkedList` - двойно свързан списък
- `Vector` - resize-ващ се (динамичен) масив. Synchronized. Legacy -> замества се от `ArrayList`
- `Stack` - наследява Vector. Legacy -> замества се от `Dequeue`

---

#### Алгоритмична сложност на основните операции

![ListComplexities](images/04.10-listperformance.png)

---

__Queue__


| Операция | хвърля изключение   | връща специална стойност |
|:---------|:--------------------|:-------------------------|
| Insert   | `add(e)`            | `offer(e)`               |
| Remove   | `remove()`          | `poll()`                 |
| Examine  | `element()`         | `peek()`                 |

---

#### Имплементации на Queue

- `PriorityQueue` - heap (пирамида)
- `LinkedList`
- `ArrayDeque` - resize-ващ се (динамичен) масив

---

#### Алгоритмична сложност на основните операции

![QueueComplexities](images/04.11-queueperformance.png)

---

__Set__

```java
boolean add(E e)
boolean contains(Object o)
boolean remove(Object o)
int size()
boolean isEmpty()
Object[] toArray()
```

---

#### Имплементации на `Set`

- `TreeSet` - `TreeMap`. Червено-черно дърво
- `HashSet` - хеш таблица
- `LinkedHashSet` - хеш таблица + двойно свързан списък
- `EnumSet` - битов масив

---

#### Конструктори на `HashSet`

```java
HashSet(); // default initial capacity (16) and load factor (0.75).
HashSet(Collection<? extends E> c);
HashSet(int initialCapacity);
HashSet(int initialCapacity, float loadFactor);
```

---

#### Конструктори на `TreeSet`

```java
TreeSet(); // natural ordering
TreeSet(Collection<? extends E> c);
TreeSet(Comparator<? super E> comparator);
TreeSet(SortedSet<E> s);
```

---

__java.lang.Comparable vs java.util.Comparator__


```java
// естествена подредба
public interface Comparable<T> {
    public int compareTo(T o);
}

public interface Comparator<T> {
    public int compare(T o1, T o2);
}
```

@[2-4]
@[6-8]

---

#### Консистентност на естествената подредба с `equals()`

Естествената подредба на клас С се нарича консистентна с `equals()`, ако и само ако
`e1.compareTo(e2) == 0` има същата булева стойност като `e1.equals(e2)`, за всеки два обекта e1 и е2 на С.

<br/>
Силно препоръчително е (макар и не задължително) естествената подредба да бъде консистентна с `equals()`.

---

#### `LinkedHashSet`

![LinkedHashSet](images/04.12.0-linkedhashset.png)

```java
Set<Character> sc = new LinkedHashSet<>();
Collections.addAll(sc, 'a', 'b', 'j');
```

---

#### Алгоритмична сложност на основните операции

![SetComplexities](images/04.12-setperformance.png)

<small>*h* - капацитет на хеш таблицата</small>

---

Операции над множества със __Set__

```java
Set<String> one = new HashSet<>();
one.add("foo");
one.add("bar");
Set<String> two = new HashSet<>();
two.add("foo");
two.add("baba");

Set<String> union = new HashSet<>(one);
union.addAll(two); // union = [baba, bar, foo]

Set<String> intersection = new HashSet<>(one);
intersection.retainAll(two); // intersection = [foo]

Set<String> difference = new HashSet<>(one);
difference.removeAll(two); // difference = [bar]
```

---

__Map__

```java
V put(K key, V value)
V get(Object key)
V remove(Object key)
boolean containsKey(Object key)
int size()
boolean isEmpty()
Set<K> keySet()
Collection<V> values()
```

@[1](Добавя двойка key-value. Ако има вече такъв ключ в Map-а, променя само value-то, и връща старото value като резултат)

---

#### Имплементации на `Map`

- `HashMap` - хеш таблица
- `LinkedHashMap` - хеш таблица + двойно свързан списък
- `EnumMap` - битов масив
- `TreeMap` - червено-черно дърво

---

#### Алгоритмична сложност на основните операции

![MapComplexities](images/04.13-mapperformance.png)

<small>*h* - капацитет на хеш таблицата</small>

---

#### Колекции с наредба vs Колекции без наредба

@ul

- `TreeMap`/`TreeSet` - червено-черни дървета. Запазват естествена наредба. Елементите трябва да имплементират интерфейса `Comparable` (или да се подава имплементация на `Comparator`). Логаритмична сложност за повечето операции
- `HashMap`/`HashSet` - хеш таблици. Нямат естествена наредба. Елементите трябва да имплементират методите `hashCode()` и `equals()`. Константна сложност за повечето операции

@ulend

---

![Cheat sheet](images/04.14-cheat-sheet.png)

---

### Колекции - операции

- Сортиране

```java
List<Integer> nums = new ArrayList<>();
nums.add(4);
nums.add(9);
nums.add(0);
nums.add(7);
nums.add(-1);

// nums = [4, 9, 0, 7, -1]
Collections.sort(nums);
// nums = [-1, 0, 4, 7, 9]
Collections.sort(nums, Collections.reverseOrder());
// nums = [9, 7, 4, 0, -1]
```

---

- Търсене: indexOf(), binarySearch()

```java
List<Integer> nums = Arrays.asList(4, 9, 0, 7, -1);

// nums = [4, 9, 0, 7, -1]
int index = nums.indexOf(7);
// index = 3

Collections.sort(nums);
index = Collections.binarySearch(nums, -1);
// index = 0
```

---

- Разбъркване: shuffle()

```java
List<Integer> nums = Arrays.asList(4, 9, 0, 7, -1);

// nums = [4, 9, 0, 7, -1]
Collections.shuffle(nums);
// nums = [?, ?, ?, ?, ?]
```

---

- Манипулации __copy()__, __fill()__, reverse(), swap()

```java
List<String> from = new ArrayList<>();
from.add("foo");
from.add("bar");
List<String> to = new LinkedList<>();
to.add("a");
to.add("b");

Collections.copy(to, from);
// to = [foo, bar]
```

```java
List<String> list = new ArrayList<>();
list.add("foo");
list.add("bar");
list.add("baz");

Collections.fill(list, "a");
// list = [a, a, a]
```

---

- Манипулация copy(), fill(), __reverse()__, __swap()__)

```java
List<String> list = new ArrayList<>();
list.add("1");
list.add("2");
list.add("3");

Collections.reverse(list);
// list = [3, 2, 1]

Collections.swap(list, 0, 1);
// list = [2, 3, 1]
```

---

- Статистики: min(), max(), frequency()

```java
Set<Integer> nums = Set.of(4, 9, 0, 7, -1);

int min = Collections.min(nums); // -1
int max = Collections.max(nums); // 9
int frequency = Collections.frequency(nums, 7); // 1
```

---

Намиране на всички уникални думи от дадено множество:

```java
import java.util.*;

public class FindDistinctWords {

  public static void main(String[] words) {
    Set<String> distinctWords = new TreeSet<>();
    for (String word : words) {
      distinctWords.add(word);
    }

    System.out.printf("%d distinct words: %s%n",
      distinctWords.size(), distinctWords);
  }
}
```

```bash
$ javac FindDistinctWords.java && \
  java FindDistinctWords "foo" "bar" "foo" "baz" "bar" "foo"
3 distinct words: [bar, baz, foo]
```

---

#### Премахване на елементи на колекция при итериране

```java
private static void filter(Collection<String> collection) {
  for (Iterator<String> it = collection.iterator();
     it.hasNext();) {
      if (it.next().charAt(1) == 'a') {
        it.remove();
      }
  }
}
```

```java
Set<String> words = new HashSet<>();
words.add("foo");
words.add("bar");
words.add("baz");

filter(words);
// words = [foo]
```

---

#### Collection factory методи

```java
List<String> list = List.of("Java", "9", "rulez");

Set<Integer> set = Set.of(1, 2, 3, 5, 8);

Map<String, Integer> cities = Map.of(
      "Brussels", 1_139_000,
      "Cardiff", 341_000
);

cities = Map.ofEntries(
      Map.entry("Brussels", 1_139_000),
      Map.entry("Cardiff", 341_000)
);
```

---

#### Collection factory методи

- Колекциите, създавани с factory методите, са immutable
- Заемат по-малко памет от mutable събратята си
- Не могат да съдържат null елементи
- При едно и също съдържание, могат да връщат нови инстанции или референции към съществуващи

---

#### Принципи на чистия код - ползвай интерфейс за декларация и конкретен клас за инициализация

```java
// Bad
ArrayList<String> stringList = new ArrayList<>();
public HashSet<Integer> filterPrimes(HashSet<Integer>);

// Good
List<String> stringList = new ArrayList<>();
public Collection<Integer> filterPrimes(Collection<Integer>);
```

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend

## Generics

_11.11.2020_

---

#### Предната лекция говорихме за:

@ul

- Качествен (Clean) Code
- Колекции (collections)

@ulend

---

![Data structures complexity](images/05.0.1-data-structures-complexity.png)

<small><small>source: [bigocheatsheet.com](https://www.bigocheatsheet.com/)</small></small>

---

![Algorithmic complexity chart](images/05.0.2-alg-complexity-chart.png)

<small><small>source: [bigocheatsheet.com](https://www.bigocheatsheet.com/)</small></small>

---

#### Днес продължаваме с:

@ul

- Generics

@ulend

---

#### Нуждата от Generics

```java
List list = new LinkedList();
list.add(new Integer(1));
Integer i = list.iterator().next();
```
@snap[south span-100]
@[1]
@[2]
@[3](няма да се компилира)
@snapend

---

#### Нуждата от Generics

```java
List list = new LinkedList();
list.add(new Integer(1)); 
Integer i = (Integer) list.iterator().next(); // explicit type cast
```

<br/><br/>
- трябва експлицитно да кастваме, което е досадно
- има вероятност да сгрешим в предположението си за типа и cast-ът да "гръмне" с `ClassCastException` по време на изпълнение

---

#### Нуждата от Generics

@ul

- би било много по-удобно
    - програмистът да може изрази намерението си да ползва определен тип и
    - компилаторът да може да гарантира коректността на програмата за този тип

@ulend

---

#### Нуждата от Generics

```java
List list = new LinkedList();
list.add(new Integer(1)); 
Integer i = (Integer) list.iterator().next(); // explicit type cast
```

```java
List<Integer> list = new LinkedList<>();
list.add(1); // autoboxing; compiler checks type compatibility
Integer i = list.iterator().next(); // no explicit cast needed
```

---

#### Generics

```java
List<E>
// Чете се "списък от E"
```

<br/>

Клас или интерфейс, в декларацията на който има един или повече параметри за тип, се нарича generic клас/интерфейс.

---

#### Не-generic кутия

Съдържа какъв да е обект

```java
public class Box {
    private Object value;

    public Object getValue() {
        return value;
    }

    public void setValue(Object value) {
        this.value = value;
    }
}
```

---

#### Generic кутия

```java
public class Box<T> {
    private T value;

    public T getValue() {
        return value;
    }

    public void setValue(T value) {
        this.value = value;
    }
}

```

---

#### Създаване на инстанции

```java
// The long way
Box<Integer> integerBox = new Box<Integer>();
```

```java
// Diamond operator
Box<Integer> integerBox = new Box<>();
```

---

Конвенция за именуване на параметрите за тип:
- E - Element
- T - Type
- K - Key
- V - Value
- N - Number
- S, U, V etc. - 2-ри, 3-ти, 4-ти тип

---

#### Generic методи

@ul

- Могат да ползват типовите параметри на класа/метода
- Могат да добавят нови параметри за тип, недекларирани от класа
- Новите параметри за тип са видими единствено за метода, който ги декларира
- Generic методите могат да са статични, нестатични или конструктори

@ulend

---

#### Generic методи – примери

```java
public class Pair<K, V> {
    private K key;
    private V value;

    // Generic constructor
    public Pair(K key, V value) {
        this.key = key;
        this.value = value;
    }

    // Generic methods
    public K getKey() { return key; }
    public void setKey(K key) { this.key = key; }
    public V getValue() { return value; }
    public void setValue(V value) { this.value = value; }
}
```

---

#### Generic методи – примери

```java
public class Util {

    // Generic static method
    public static <K, V> boolean areEqual(Pair<K, V> p1, Pair<K, V> p2) {
        return p1.getKey().equals(p2.getKey()) &&
                   p1.getValue().equals(p2.getValue());
    }

}
```

---

#### Generic методи - извикване

```java
Pair<Integer, String> p1 = new Pair<>(1, "apple");
Pair<Integer, String> p2 = new Pair<>(2, "pear");

// Full syntax
boolean areEqual = Util.<Integer, String>areEqual(p1, p2);

// Short syntax
areEqual = Util.areEqual(p1, p2);
```

---

#### Generic типове и наследяване

- `Integer` is-a `Object`
- `Integer` is-a `Number`
- `Double` is-a `Number`
- Обаче `Box<Integer>` is-not-а `Box<Number>`. Техният общ родител е `Object`

---

#### Generic типове и наследяване

- Подтип на generic клас или интерфейс получаваме чрез разширяване или имплементиране
- Ако аргументът за тип е еднакъв, то is-a връзката е в сила

---

#### Пример от Collections framework-a

![Collection subtypes](images/05.1.1-collections-subtypes.png)

---

#### Ограничени (bounded/restricted) Generic типове

<small>Може да се специфицира, че generic тип е съвместим само с даден тип или негови наследници/имплементации (upper bound).</small>


```java
public <T extends Number> List<T> fromArrayToList(T[] a) {
    // [...]
}

// Ако типовете са повече от един, те се разделят с &, като в този случай
// най-много един може да бъде клас (останалите трябва да са интерфейси)
// и ако има клас, той трябва да стои първи в списъка.
// Обърнете внимание, че въпреки че Comparable е интерфейс, а не клас,
// ключовата дума е пак extends.
public <T extends Number & Comparable> List<T> anotherMethod(T[] a) {
    // [...]
}
```

---

#### Проблемът с липсата на общ родител

<small>Представете си, че ви трябва метод, който извежда всички елементи на дадена колекция.
Ето как може да се направи без generics:</small>

```java
void printCollection(Collection c) {
    Iterator i = c.iterator();
    for (k = 0; k < c.size(); k++) {
        System.out.println(i.next());
    }
}
```

---

#### Проблемът с липсата на общ родител

<small>Наивно може да предположим, че с generics може да го реализираме така:</small>

```java
void printCollection(Collection<Object> c) {
    for (Object e : c) {
        System.out.println(e);
    }
}

// Проблемът е, че тази реализация всъщност е по-малко полезна от предната.
// Докато версията без generics може да се извиква с произволна колекция,
// тази версия може да приема само Collection<Object>, който тип, както
// видяхме вече, не е родител на Collection<Т> за никое T,
// т.е. не може да викнем метода с Collection<Integer> да речем.
```

---

#### Решението: wildcards

@ul

- Имат ли всички видове `Collection<T>` общ родител, различен от `java.lang.Object`?
- Отговорът е положителен
  - типът се записва `Collection<?>` и се чете "колекция от неизвестен тип". Такъв тип се нарича *wildcard* тип

@ulend

---

#### Решението: wildcards

```java
// този метод може да се извика с аргумент - произволна колекция
void printCollection(Collection<?> c) {
    for (Object e : c) {
        System.out.println(e);
    }
}
```

---

#### Generic типове с wildcards

@ul

- `?` – означава неизвестен тип
- Може да се използва за тип на:
  - параметър на метод
  - член-данна на клас
  - локална променлива
  - тип на връщаната стойност
- Не може да се използва за аргумент за тип при извикване на:
  - generic метод
  - създаването на инстанция на generic клас

@ulend

---

#### Wildcards, ограничени отгоре

<small>
Искаме да създадем метод, който намира сумата на елементите в списък от `Integer`, `Double`, `Float`, `Number`
</small>


```java
public static double sumOfList(List<? extends Number> list) {
    double sum = 0.0;
    for (Number current : list) {
        sum += current.doubleValue();
    }
    return sum;
}
```

---

#### Wildcards, ограничени отдолу

<small>
Искаме да създадем метод, който да добавя `Integer` обекти към списък.
Искаме методът да работи с колекции от `Integer`, `Number`, `Object`
</small>


```java
public static void addNumbers(List<? super Integer> list) {
    for (int i = 1; i <= 10; i++) {
        list.add(i);
    }
}
```

---

#### Неограничени wildcards

@ul

- Списък елементи от неизвестен тип - `List<?>`
- `List<?>` е еквивалентно на `List<? extends Object>`
- Използва се, когато:
  - Функционалността, която пишем, може да се имплементира единствено със знанието за методите в `java.lang.Object`
  - Не се интересуваме от типа на елементите в списъка, а се интересуваме от характеристики на самия списък – например размер на списъка

@ulend

---

#### The Get & Put Principle

@ul

- Използвай `extends` wildcard, когато само ще get-ваш стойности от структура
- Използвай `super` wildcard, когато само ще put-ваш стойности в структура
- Не използвай wildcard, когато ще правиш и двете

@ulend

---

#### Generics

- Подвеждащо приличат на шаблоните в C++, но се различават от тях:
    - синтактично: при влагане, в Java не е нужно да се разделят съседните `>>` с интервал
    - семантично: в Java се реализират чрез изтриване (*erasure*) на типовата информация, а не чрез създаване на отделна версия на класа за всяка употреба на шаблона с конкретен тип (*expansion*) като в C++

```c++
// C++: space between the two >> was mandatory until C++11
list<list<string> > list;
```
```java
// Java: spaces between < and List and between the two >> are optional
List<List<String>> list;
```

---

#### Изтриване на информацията за типовите аргументи

- Java компилаторът изтрива информацията за типовите аргументи и тази информация не е налична по време на изпълнение
- Всички типови параметри в generic класове и интерфейси се заместват...

---

#### Ако са неограничени или ограничени отдолу – заместват се с `java.lang.Object`:

```java
public class Box<T> {
    private T value;
    public T getValue() { return value; }
    public void setValue(T value) { this.value = value; }
}


public class Box {
    private Object value;
    public Object getValue() { return value; }
    public void setValue(Object value) { this.value = value; }
}
```

---

#### Ако са ограничени отгоре – заместват се с техния ограничителен тип

```java
class Shape { /* ... */ }
class Circle extends Shape { /* ... */ }
class Rectangle extends Shape { /* ... */ }
```

```java
public static <T extends Shape> void draw(T shape) { /* ... */ }


public static void draw(Shape shape) { /* ... */ }
```

---

#### Сурови типове (Raw types)

```java
Box rawBox = new Box();
```

<small>
Представляват името на generic клас или интерфейс без аргументите за тип.
Raw type на `Box<T>` е `Box`.
Отнемат възможността на компилатора да открива грешки. Оставени са в езика по backward compatibility причини. Избягвайте ги
</small>

---

#### Сурови типове (Raw types)

<small>
Може безопасно да се присвои инстанция на параметризиран тип на суровия му тип.
Обратното присвояване се компилира с предупреждение
</small>

```java
Box<String> stringBox = new Box<>();
Box rawBox = stringBox;

// rawBox is a raw type of Box<T>
Box rawBox = new Box();

// warning: unchecked conversion
Box<Integer> intBox = rawBox;
```

---

#### Сурови типове (Raw types)

<small>Също се генерира предупреждение, ако се опитаме да изпълним generic метод през инстанция на суров тип:</small>

```java
Box<String> stringBox = new Box<>();
Box rawBox = stringBox;

rawBox.setValue(8); // warning: unchecked invocation to setValue(T)
```

---

#### Raw types и съвместимост на типовете

```java
List raw;
// warning: List is a raw type.
// References to generic type List<E> should be parameterized

List<Object> objects;
List<String> strings = new ArrayList<>();

raw = strings; // ?
objects = strings; // ?
```

@snap[south span-100]
@[8-8](it's OK: List-of-Strings is-a List)
@[9-9](will not compile: incompatible types)
@snapend

---

#### Предпочитай List вместо масив

```java
// Fails at runtime
Object[] array = new Long[1];
array[0] = "I don't fit in"; // Throws ArrayStoreException

// Won't compile
List<Object> list = new ArrayList<Long>(); // Incompatible types
list.add("I don't fit in");
```

---

#### Ограничения при generic класове и интерфейси

<small>
Не могат да се създават инстанции от типов параметър.
Не могат да се декларират статични полета на клас от типа на типов параметър
</small>

```java
public static <E> void append(List<E> list) {
    E elem = new E(); // compile-time error: type parameter E
                      // cannot be instatiated directly
    list.add(elem); 
}

public class MobileDevice<T> {
    private static T os; // compile-time error
}
```

---

#### Ограничения при generic класове и интерфейси

<small>
Не може да се правят конвертирания между типове (casts).
Не може да се прилага `instanceof` операторът с generic типове
</small>

```java
public static <E> void rtti(List<E> list) {
    if (list instanceof ArrayList<Integer>) { // compile-time error
        // ...
    }
}
```

---

#### Ограничения при generic класове и интерфейси

<small>
Не може да се създават масиви от параметризиран тип
</small>

```java
// compile-time error
List<Integer>[] arrayOfLists = new List<Integer>[2];

// compiler error, but pretend it's allowed
Object[] stringLists = new List<String>[10];

// OK
stringLists[0] = new ArrayList<String>();

// An ArrayStoreException should be thrown,
// but the runtime can't detect it
stringLists[1] = new ArrayList<Integer>();
```

---

#### Ограничения при generic класове и интерфейси

<small>Не може да се дефинират два метода с формални параметри, които след изтриване на типовите параметри имат еднакви сигнатури</small>

```java
public class Example {
    // Compilation error: 'print(Set<String>)' clashes with
    // 'print(Set<Integer>)': both methods have same erasure
    public void print(Set<String> strSet) { }

    public void print(Set<Integer> intSet) { }
}
```

---

![Recommended Literature](images/05.2-o-reilly-generics-and-collections.png)

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend


## Unit Testing & Mocking

_18.11.2020_

---

#### Предната лекция говорихме за:

@ul

- Generics

@ulend

---

#### Днес ще разгледаме:

@ul

- Как се тества софтуер, и кому е нужно
- Какво е unit testing
- JUnit
- Test-Driven Development (TDD)
- Stubbing и mocking

@ulend

---

#### Защо е нужно да си тестваме кода?

<small>
*Chuck Norris doesn’t need unit tests because his code always works. ALWAYS.<p><p>
                                                                    — Wisdom of the Internet ;)*
</small>

---

#### Кога да тестваме?

![Relative cost of fixing defects](images/06.1-relative-cost.png)

---

#### Тестването не е фаза, а е процес

![Testing is a process](images/06.2-testing-process.png)

---

#### Основни видове тестове

@ul

- Ръчни
  - В професионалната софтуерна разработка, липса на автоматични тестове == липса на тестове въобще

- Автоматични
  - функционални
  - нефункционални

@ulend

---

@ul

- Функционални тестове
  - unit тестове
  - integration тестове

- Нефункционални тестове
  - performance тестове
  - stress тестове
  - crash тестове
  - security тестове
  - usability тестове

@ulend

---

#### Още видове тестове

![More test types](images/06.3-more-tests.png)

---

#### Unit Testing

@ul

- Unit test е код, който изпълнява специфична, „атомарна“ (т.е. която не може да се разбие по смислен начин на по-малки) функционалност на кода, която да бъде тествана
- Един unit test цели да тества малък фрагмент код - обикновено един метод или най-много един клас

@ulend

---

@ul

- Unit тестовете гарантират, че кодът работи както очакваме
- Подсигуряват, че кодът ще продължи да работи, както се очаква, в случай че го модифицираме, за да оправим бъг, рефакторираме или разширяваме функционалността

@ulend

---

#### Малко дефиниции

@ul

- *Продуктивен код* (a.k.a. *code under test*) – това е кодът, който реализира потребителските изисквания и удовлетворява сценариите на клиентите

- Процентът на продуктивния код, който се тества от автоматични тестове, се нарича *test coverage* или *code coverage*. Високият test coverage на кода ни дава увереност да разработваме функционалности, без да се налага да правим много ръчни тестове

@ulend

---

#### Още дефиниции

@ul

- *Test Driven Development* (TDD) е методология, при която кодът на тестовете се пише преди продуктивния код, така че щом даден тест бъде удовлетворен (т.е. минава успешно, стане „зелен“), съответният use-case е реализиран („done“)
- *Test fixture* е фиксирано състояние на софтуера, който тестваме, което е началното условие (предусловието) за изпълняване на тестовете

@ulend

---

@ul

- *Integration test* тества интеграцията на няколко класа (компонента)
- *Performance test* измерва бързодействието (ефективността) на даден софтуер по repeatable начин

@ulend

---

## JUnit

---

#### JUnit Framework

@ul

- JUnit е най-популярният и *de facto* стандартният testing framework в Java
- Open source проект в [GitHub](https://github.com/junit-team/junit5)
- Актуалната версия е [JUnit 5](https://junit.org/junit5/)
- Засега в курса ще ползваме [JUnit 4](https://junit.org/junit4/) (защо?)

@ulend

---

#### Защо ни трябват testing frameworks?

@ul

- Улесняват ни да пишем и изпълняваме тестове
- Стандартизират разработката и поддръжката на тестове

@ulend

---

#### JUnit

@ul

- JUnit се базира на анотации
- Всеки JUnit тест е метод, анотиран с `@Test`, съдържащ се в клас, който се използва само за тестване
- Такъв клас се нарича *test case*

@ulend

---

#### Пример за JUnit тест

```java
import static org.junit.Assert.assertEquals;

@Test
public void multiplicationOfZeroIntegersShouldReturnZero() {
	// MyClass is tested
	MyClass tester = new MyClass();

	// Tests
	assertEquals("10 x 0 must be 0", 0, tester.multiply(10, 0));
	assertEquals("0 x 10 must be 0", 0, tester.multiply(0, 10));
	assertEquals("0 x 0 must be 0", 0, tester.multiply(0, 0));
} 
```

---

#### Конвенции за именуване

@ul

- Прието е името на тестовия клас да се получава от името на класа, който тества, с добавяне на суфикса `Test`
- Популярна конвенция за имената на тестовите методи е, да започват с `test`, следвано от името на метода, който се тества, и кратко описание на тестовия сценарий, например `testLoginWithInvalidUserPassword`. Към нея се придържаме в нашите тестове за курса
- Името на теста трябва достатъчно ясно да описва сценария

@ulend

---

#### Статични методи на Assert класа

JUnit предоставя статични методи в класа `org.junit.Assert` за тестване на определени условия

---

__fail()__

@ul

- `fail(String message)` – фейлва теста
- Може да се използва за проверка, че определена част от кода не се достига или като временна dummy имплементация, която да се замести от реален тест

@ulend

---

@ul

- `assertTrue(String message, boolean condition)` – проверява, че булевото условие е истина
- `assertFalse(String message, boolean condition)` – проверява, че булевото условие е лъжа

@ulend

---

@ul

- `assertNull(String message, Object o)` – проверява, че обектът е null
- `assertNotNull(String message, Object о)` – проверява, че обектът не е null

@ulend

---

@ul

- `assertEquals(String message, expected, actual)` – проверява за равенство на два обекта
  - масивите се сравняват по референции, не по съдържание
- `assertArrayEquals(String message, expected, actual)` - проверява за равенство на два масива по дължина и съдържание

@ulend

---

@ul

- `assertEquals(String message, expected, actual, delta)` – проверява за равенство на числа с плаваща точка
  - делтата (delta) определя точността на сравнението

@ulend

---

@ul

- `assertSame(String message, expected, actual)` – проверява, че двете референции съвпадат
- `assertNotSame(String message, expected, actual)` – проверява, че двете референции са различни

@ulend

---

@ul

- Във всички assert методи, `String` параметърът (message) е опционален
- Добра практика да го подавате винаги и съобщението да е конкретно, подробно и смислено
- Важно е в случаите, в които различни програмисти пишат продуктивния код и тестовете

@ulend

---

#### Ред на изпълнение

@ul

- JUnit предполага, че всички тестови методи могат да се изпълняват в произволен ред
- Добре написаните тестове не трябва да разчитат на конкретен ред на изпълнение
    - т.е. тестовете не трябва да зависят от други тестове

@ulend

---

#### Ред на изпълнение

<small>От JUnit 4.11 натам, може явно, с анотация на класа, да определите реда на изпълнение да е лексикографският ред на имената на тестовите методи.</small>

```java
@FixMethodOrder(MethodSorters.NAME_ASCENDING)
```

---

#### JUnit анотации

- `@Test`
  - обозначава метод като тестов метод. Методът трябва да е `public` и `void`
<p>
- `@Test(expected = Exception.class)`
  - фейлва, ако методът не хвърли указаното изключение
<p>
- `@Test(timeout = 100)`
  - фейлва, ако изпълнението на метода продължи повече от 100 милисекунди

---

#### JUnit анотации

- `@Before public void method()` 
  - този метод се изпълнява преди всеки тест
  - използва се за подготовка на тестовата среда
<p>
- `@After public void method()`
  - този метод се изпълнява след всеки тест
  - използва се да зачисти тестовата среда

---

#### JUnit анотации

- `@BeforeClass public static void method()`
  - този метод се изпълнява еднократно преди стартиране на всички тестове
  - използва се за операции (особено, "скъпи") по инициализация на тестовата среда
  - методите с тази анотация трябва да са статични
<p><p>
- `@AfterClass public static void method()`
  - този метод се изпълнява еднократно след завършване на изпълнението на всички тестове
  - използва се за зачистване на ресурсите, създадени в `@BeforeClass` метода
  - методите с тази анотация трябва да са статични

---

#### Test Suites

Ако имате няколко тестови класа, може да ги обедините в *test suite*. Изпълнението на test suite ще изпълни всички тестови класове в него в указания ред.

---

#### Пример за JUnit test suite

```java
import org.junit.runner.RunWith;
import org.junit.runners.Suite;
import org.junit.runners.Suite.SuiteClasses;

@RunWith(Suite.class)
@SuiteClasses({
    MyClassTest.class,
    MySecondClassTest.class
})
public class AllTests {

}
```

---

#### Къде "живеят" unit тестовете?

@ul

- Обикновено unit тестовете се разполагат в отделен проект или в отделна source директория, за да са отделени от продуктивния код
- Няма единен стандарт - зависи с какви други tools (например за build) искате интеграция

@ulend

---

- Един вариант (maven)

```bash
fancy-project
  └─ src/main/java
    └─ (...)
  └─ src/test/java
    └─ (...)
```

- Друг вариант

```bash
fancy-project
  └─ src
    └─ (...)
  └─ test
    └─ (...)
```

---

#### Как се изпълняват?

@ul

- През IDE
- През конзола
- През build системи (maven, gradle)
- През Continuous Integration (CI) системи (Jenkins, Travis)
- Засега ще се ограничим да ги изпълняваме през IDE-то

@ulend

---

#### Code coverage plug-ins

@ul

- [EclEmma](https://www.eclemma.org/) for Eclipse
  - базирана е на open source проекта [JaCoCo](https://www.jacoco.org/jacoco/)
- [Code coverage runner](https://www.jetbrains.com/help/idea/code-coverage.html) for IntelliJ

@ulend

---

#### Best practices

@ul

- Не тествайте тривиален код като getters/setters
- Тествайте `private` методи само косвено
- Стремете се към 70-80% code coverage
- Пишете кратки, ясни и бързи unit тестове

@ulend

---

## JUnit 4 vs. JUnit 5

---

|                   | JUnit 4     | JUnit 5                 |
| ----------------- | ----------- | ----------------------- |
| Пакет             | `org.junit` | `org.junit.jupiter.api` |
| Анотиране на тест | `@Test`     | `@Test`                 |

---

#### Инициализация

|                    | JUnit 4        | JUnit 5       |
| ------------------ | -------------- | ------------- |
| Обща               | `@BeforeClass` | `@BeforeAll`  |
| Преди всеки тест   | `@Before`      | `@BeforeEach` |

---

#### Заключителни операции

|                 | JUnit 4       | JUnit 5      |
| --------------- | ------------- | ------------ |
| След всеки тест | `@After`      | `@AfterEach` |
| Общи            | `@AfterClass` | `@AfterAll`  |

---

#### Временно изключване на тестов метод или клас

| JUnit 4   | JUnit 5     |
| --------- | ----------- |
| `@Ignore` | `@Disabled` |

---

## Stubbing and mocking

---

#### Unit тестване на класове със зависимости

@ul

- Често клас използва в себе си други класове: има член-данни - референции към обект на друг клас
- Това се нарича *композиция* на класове
- Това е съвсем очаквано и нормално :)
- Как unit тестваме такива класове?
- Да разгледаме един такъв пример

@ulend

---

```java
public class UserService {

    private UserRepository repository;
    private MailService mailService;

    public User register(String email, String password) {
        if (repository.exists(email)) {
            throw new UserAlreadyExistsException();
        }

        User user = new User(email, password);
        repository.save(user);
        mailService.sendWelcomeMail(email);
        return user;
    }

}
```

@[3-4]
@[7]
@[12]
@[13]

---

@ul

- Нека `UserRepository` е интерфейс, чиято задача е да съхранява `User`-и (in-memory, file system, database, etc.)
- Нека `MailService` също е интерфейс, чиято задача е да праща мейли

@ulend

---

#### Test cases for register()

@ul

- Методът `register()` има 2 exit point-a - следователно имаме 2 сценария за покриване
- [TC1] `register()` хвърля подходящо изключение, когато мейл адресът вече съществува в хранилището
- [TC2] `register()` запазва подходящия user в хранилището и изпраща welcome мейл, когато мейл адресът не съществува в хранилището
- Как unit тестваме `UserService` класа?

@ulend

---

@ul

- При unit тестване се интересуваме от функционалната коректност само на класа, който се тества
- Трябват ни инструменти, чрез които да "изолираме" композираните класове
- Композираните класове могат да бъдат трудни за инстанциране
- Например, `UserRepository` изисква connectivity към база от данни

@ulend

---

@ul

- Доброто unit тестване се базира на изолация
- Изолацията се постига чрез т.нар *stub* или *mock* обекти

@ulend

---

#### Stubbing

@ul

- *Stub* наричаме клас, който отговаря на дадени извиквания на методи с предварително зададени отговори
- В unit тестването ни служат за справяне с проблема с композираните класове

@ulend

---

#### Stubbing

@ul

- Обикновено имплементират по минимален начин даден интерфейс и се подават на класа, който се тества
- Извън unit тестването, могат да бъдат използвани и като заместител на код, който още не е разработен

@ulend

---

__PositiveUserRepositoryStubImpl__

```java
public class PositiveUserRepositoryStubImpl implements UserRepository {

    @Override
    public boolean exists(String email) {
        return true;
    }

    @Override
    public void save(User user) {
        // Do nothing
    }
}
```

---

__InMemoryUserRepositoryStubImpl__

```java
public class InMemoryUserRepositoryStubImpl implements UserRepository {

    private Map<String, User> users = new HashMap<>();

    @Override
    public boolean exists(String email) {
        return users.containsKey(email);
    }

    @Override
    public void save(User user) {
        users.put(user.getEmail(), user);
    }

}
```

---

#### The stub way

```java
@Test(expected = UserAlreadyExistsException.class)
public void testRegisterThrowsAppropriateException() {
    UserService service =
            new UserService(new PositiveUserRepositoryStubImpl());

    service.register("test@test.com", "weak");
}
```

@[3-4]
@[6]
@[1]

---

#### Жизнен цикъл на тестване със stub

1. Setup data - подготвяме обекта, който ще се тества, както и stub събратята му
2. Exercise - извикваме метода, който искаме да тестваме
3. Verify state - използваме assertions, за да проверим състоянието на обекта
4. Teardown - освобождаваме използваните ресурси

---

#### Характеристики на stub-овете

@ul

- Могат да съдържат логика, която не е тривиална (напр. `InMemoryUserRepositoryStubImpl`) (+)
- Броят на stub-овете расте експоненциално (-)
- Не може да проверим дали даден метод на stub-a е извикан определен брой пъти (-)

@ulend

---

#### Mocking

@ul

- *Mock* наричаме конфигуриран обект с предварително зададени отговори на дадени извиквания на методи
- Динамични wrapper-и за композираните класове
- По подобие на stub-овете, ни служат за справяне с проблема с композираните класове

@ulend

---

#### The mock way

```java
@Test(expected = UserAlreadyExistsException.class)
public void testRegisterThrowsAppropriateException() {
    UserRepository mock = mock(UserRepository.class);
    when(mock.exists("test@test.com")).thenReturn(true);

    UserService service = new UserService(mock);
    service.register("test@test.com", "weak");

}
```

@[3]
@[6]
@[4]
@[7]
@[1]

---

#### Жизнен цикъл на тестване с mock

1. Setup data - подготвяме обекта, който ще се тества, както и mock събратята му
2. Setup expectations - задаваме желаните отговори
3. Exercise - извикваме метода, който искаме да тестваме
4. Verify expectations - уверяваме се, че правилният метод на mock-a се е извикал
5. Verify state - използваме assertions, за да проверим състоянието на обекта
6. Teardown - освобождаваме използваните ресурси

---

#### To mock or not to mock?

```java
public class Cinema {
    private Map<String, Projection> projections;

    public Cinema(Map<String, Projection> projections) {
        this.projections = projections;
    }

    public boolean buyTicket(String projection, int amount) {
        if (!projections.containsKey(projection)) {
            return false;
        }
        // [...]
        return true;
    }

}
```

---

#### Do not mock

```java
@Test
public void testBuyTicket() {
    Map<String, Projection> projections =
            Map.of("foo", new Projection("foo"));
    Cinema cinema = new Cinema(projections);

    boolean actual = cinema.buyTicket("bar", 3);
    assertFalse(actual);
}
```

---

#### To mock or not to mock?

```java
public class Cinema {
    private ProjectionService service;

    public Cinema(ProjectionService service) {
        this.service = service;
    }

    public boolean buyTicket(String projection, int amount) {
        if (!service.contains(projection)) {
            return false;
        }
        // [...]
        return true;
    }
}
```

---

#### Mock

```java
@Test
public void testBuyTicket() {
    ProjectionService mock = mock(ProjectionService.class);
    when(mock.contains("bar")).thenReturn(false);

    Cinema cinema = new Cinema(mock);

    boolean actual = cinema.buyTicket("bar", 3);
    assertFalse(actual);
}
```

---

#### Използвайте mock-ове, когато:

@ul

- Композираният клас се обръща към външен ресурс (мрежа, база данни, файлова система и т.н.)
- Логиката в композирания клас не е тривиална
- Не може да настроите test environment-a по тривиален начин

@ulend

---

#### Не използвайте mock-ове, когато:

@ul

- Композираният клас представлява value object, който може да подадете отвън
- Може тривиално да настроите test environment-a

@ulend

---

#### Mocking библиотеки

@ul

- [Mockito](https://github.com/mockito/mockito)
- [EasyMock](https://github.com/easymock/easymock)
- [PowerMock](https://github.com/powermock/powermock)
    - *Putting it in the hands of junior developers may cause more harm than good.*

@ulend

---

#### Mockito

<small>
    <ul>
        <li>Ще разглеждаме mockito (3.6.0) като mocking библиотека</li>
        <li>Възниква като разширение на функционалността на EasyMock</li>
        <li>Една от 10-те най-популярни Java библиотеки изобщо</li>
        <li>Open-source</li>
    </ul>
</small>

![Mockito](images/06.3.1-mockito.png)

---

#### Setup

@ul

- Mockito е външна библиотека
- Може да я изтеглите от [тук](https://mvnrepository.com/artifact/org.mockito/mockito-core/3.6.0)
- Изтеглете mockito-core jar-a и 3-те му compile dependency-та
- Ако ползвате IDE, добавете въпросните jar-ки в class path-a на проекта си
- Алтернативно, ако сте запознати с maven/gradle, ползвайте тях :)

@ulend

---

#### Setup

```bash
fancy-project
  └─ src/
    └─ (...)
  └─ test/
    └─ (...)
  └─ lib/
    └─ byte-buddy-1.10.15.jar
    └─ byte-buddy-agent-1.10.15.jar
    └─ mockito-core-3.6.0.jar
    └─ objenesis-3.1.jar
```

---

__mock() и verify()__

```java
import static org.mockito.Mockito.*;

List mockedList = mock(List.class);

mockedList.add("one");
mockedList.clear();
mockedList.get(0);

verify(mockedList).add("one");
verify(mockedList, atLeastOnce()).clear();
verify(mockedList, never()).add("two");
```

@[1]
@[3]
@[5-7]
@[9-11]

---

__when()__

```java
LinkedList mockedList = mock(LinkedList.class);

when(mockedList.get(0)).thenReturn("first");
when(mockedList.get(1)).thenThrow(new RuntimeException());

mockedList.get(0);
mockedList.get(1);
```

---

__Argument matchers__

```java
when(mockedList.get(anyInt())).thenReturn("element");

mockedList.get(999);
```

---

__@Mock анотацията__

```java
@RunWith(MockitoJUnitRunner.class)
public class UserServiceTest {
    @Mock
    private UserRepository repositoryMock;

    @Test(expected = UserAlreadyExistsException.class)
    public void testRegisterThrowsAppropriateException() {
        when(repositoryMock.exists("test@test.com"))
                .thenReturn(true);

    UserService service =
            new UserService(repositoryMock);

        service.register("test@test.com", "weak");
    }
}

```

---

#### Ограничения на Mockito

@ul

- Не може да mock-ва `static` методи (static is evil)
- Не може да mock-ва конструктори
- Не може да mock-ва `final` класове и методи (*)
- Не може да mock-ва методите `equals()` и `hashCode()`

@ulend

---

#### Добри практики

@ul

- Не правете йерархии от тестови класове
- Mock-вайте само толкова колкото ви трябва за конкретния тест
- Не mock-вайте value обекти
- Keep it short and simple (KISS)
- Redesign when you cannot test it

@ulend

---

#### Полезни четива

@ul

- [JUnit javadoc](https://junit.org/junit4/javadoc/latest/index.html)
- [Unit Testing with JUnit](http://www.vogella.com/tutorials/JUnit/article.html)
- [Mocks aren't stubs](https://martinfowler.com/articles/mocksArentStubs.html) by Martin Fowler
- [Writing good tests](https://github.com/mockito/mockito/wiki/How-to-write-good-tests) by Mockito team

@ulend

---

#### Полезни четива

![Practical unit testing](images/06.4-practical-unit-testing.png)

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend


## Входно-изходни потоци и файлова система

_25.11.2020_

![IO Streams](images/07.1-io-streams.png)

---

#### Честит празник!

![St Kliment of Ohrid](images/07.1.1-st-kliment-of-ohrid.jpg)

---

#### Предната лекция говорихме за:

@ul

- Как се тества софтуер, и кому е нужно
- Какво е unit testing
- JUnit
- Stubbing и mocking
- Mockito

@ulend

---

#### Днес ще разгледаме:

@ul

- Входно-изходни потоци
- Работа с файловата система

@ulend

---

#### Какво е поточна линия?

![Manufacturing Line](https://learnbookme.files.wordpress.com/2016/12/alienation.gif)

---

#### Входно-изходни потоци

@ul

- Концепцията за вход-изход в Java се основава на *потоци* (*streams*)
- *Потокът* е абстракция за безкраен поток от данни
- Може да се четат данни от поток или да се пишат данни в поток
- В Java потоците може да се основават на байтове или на символи

@ulend

---

#### Източник на данни и дестинация за данни

![Java App I/O](images/07.3-java-app-io.png)

---

#### Абстрактните класове в корена на I/O йерархията

![Java I/O Root Abstract Classes](images/07.4-java-io-root-abstract-classes.png)

<small>Намират се в пакета `java.io`</small>

---

#### Входно-изходни потоци: според източника/дестинацията на данните

Абстрактните класове `InputStream`, `OutputStream`, `Reader` и `Writer` имат много наследници, създадени за различни цели:

@ul

- Достъп до файлове
- Достъп до мрежи
- Достъп до буфери в паметта
- Междунишкова комуникация (Pipes)

@ulend

---

#### Входно-изходни потоци: според допълнителните си качества

@ul

- Буфериране
- Филтриране
- Парсване
- Четене и писане на текст
- Четене и писане на примитивни типове данни
- Четене и писане на обекти

@ulend

---

#### Видове потоци според нуждата

![Java I/O Root Abstract Classes](images/07.5-java-io-classes.png)

---

![Java Byte I/O Class Hierarchy](images/07.6-java-byte-io-classes-hierarchy.png)

---

![Java Char I/O Class Hierarchy](images/07.7-java-char-io-classes-hierarchy.png)

---

#### Wrapping lower-level I/O streams into higher-level ones

По-специализираните типове входно-изходни потоци...

- често се създават като wrapper около по-базови типове потоци
- и добавят свойства като буфериране, филтриране или работа на по-високо ниво на абстракция.
- За целта, повечето потоци имат oveloaded конструктори, които приемат поток като аргумент

<p>
`.close()`-ването на wrapper потока автоматично `.close()`-ва и тези, които той wrap-ва


---

#### Byte Streams vs. Char Streams при обработка на символи

- Byte Streams - извършват операции с "атомарни" данни до 8 бита включително (1 байт)

- Char Streams - извършват операции с "атомарни" данни (символи) до 16 бита включително (2 байтa)

---

#### Byte Streams - пример

```java
InputStream in = new ByteArrayInputStream("Ivan / Спасов".getBytes());
int current;
while ((current = in.read()) != -1) {
    // read() reads the next byte of data from the input stream.
    // The value byte is returned as an int in the range 0 to 255.
    // If no byte is available because the end of the stream
    // has been reached, the value -1 is returned
    System.out.print((char)current);
}
in.close();

// output:
// Ivan / Ð¡Ð¿Ð°ÑÐ¾Ð²
```

---

@ul

- символ от латинската азбука има размер до 8 бита
- символ от кирилицата - повече от 8 бита
- 'I' = 73<sub>(10)</sub> = 0b1001001<sub>(2)</sub> - това са 7 бита, които се допълват до 8 с водещи нули
- така се обработва всеки символ от символния низ
- 'С' = 1057<sub>(10)</sub> = 0b100010001<sub>(2)</sub> - 9 бита, което надхвърля 8

@ulend

---

#### Character Streams - пример

```java
Reader in = new InputStreamReader(
                    new ByteArrayInputStream("Ivan / Спасов".getBytes()));
int current;
while ((current = in.read()) != -1) {
    System.out.print((char)current);
}
in.close();

// output:
// Ivan / Спасов
```

---

#### Входно-изходни потоци: жизнен цикъл

Потоците се

@ul

- Създават
- Използват
- Затварят

@ulend

---

#### Пример с `InputStream`

```java
InputStream inputStream =
        new FileInputStream("c:\\data\\input-text.txt");

int data;
while ((data = inputStream.read()) != -1) {
    // doSomethingWithData(data);
}

inputStream.close();

```

---

#### `java.io.InputStream`

```java
int          available​();
void         close​();
void         mark​(int readlimit);
boolean      markSupported​();
abstract int read​();
int          read​(byte[] b);
int          read​(byte[] b, int off, int len);
byte[]       readAllBytes​();
int          readNBytes​(byte[] b, int off, int len);
void         reset​();
long         skip​(long n);
long         transferTo​(OutputStream out);
```

---

#### `java.io.OutputStream`

```java
void          close​();
void          flush​();
void          write​(byte[] b);
void          write​(byte[] b, int off, int len);
abstract void write​(int b);
```

---

#### Пример с `OutputStream`

```java
OutputStream os = new FileOutputStream("test.txt"));
os.write("Hello FMI!".getBytes());
os.flush();
os.close();
```

<small>
При конструирането на `FileOutputStream`, ако файлът не съществува, ще се направи опит да се създаде.
</small>

---

#### `FileOutputStream`: append vs. overwrite

```java
// appends to a file
OutputStream output =
        new FileOutputStream("c:\\data\\output-text.txt", true); 

// overwrites a file
OutputStream output =
        new FileOutputStream("c:\\data\\output-text.txt", false);
```

---

#### Пример с `DataInputStream`

```java
DataInputStream input =
        new DataInputStream(new FileInputStream("binary.data"));

int    aByte   = input.read();
int    anInt   = input.readInt();
float  aFloat  = input.readFloat();
double aDouble = input.readDouble();
// etc.

input.close();
```

---

#### Пример с `ObjectOutputStream`

```java
ObjectOutputStream objectOutputStream =
        new ObjectOutputStream(new FileOutputStream("persons.dat"));

Person object = new Person();

objectOutputStream.writeObject(object);

objectOutputStream.close();
```

---

#### `java.io.Serializable`

<small>
`Serializable` е маркерен интерфейс, който указва, че обектите на класа могат да се *сериализират* (т.е. конвертират в последователност от битове) и *десериализират* (т.е. (пре)създават от последователност от битове). Класове, обекти на които ще записваме или четем във файл или ще пращаме или получаваме по мрежата, трябва да са `Serializable`.
</small>

```java
import java.io.Serializable;

public class Person implements Serializable {
    // the particular version of the class definition is denoted by
    // the serial version unique identifier: IDEs can generate these
    private static final long serialVersionUID = 1234L;

    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

---

#### Има ли проблем в този код?

```java
InputStream inputStream = new FileInputStream("c:\\data\\input.txt");

int data;
while ((data = inputStream.read()) != -1) {
    // doSomethingWithData(data);
}

inputStream.close();
```

---

#### А тук?

```java
InputStream input = null;
try {
    input = new FileInputStream("c:\\data\\input.txt");
    int data;
    while ((data = input.read()) != -1) {
        // doSomethingWithData(data);
    }
} catch (IOException e) { // do something with e...
} finally {
    if (input != null) {
        input.close();
    }
}
```

---

#### Try-with-resources

- `try` блок, който декларира един или повече ресурси и автоматично затваря всеки ресурс в края на блока
- Ресурс може да е обект от произволен клас, който имплементира интерфейса `java.lang.AutoCloseable` (което включва всички класове, които имплементират `java.io.Closeable`)

---

#### Пример за try-with-resources

```java
static String readFirstLineFromFile(String path) throws IOException {
    try (BufferedReader br =
            new BufferedReader(new FileReader(path))) {
        return br.readLine();
    }
}
```

<small>Каквото е декларирано в кръглите скоби след `try`, се `.close()`-ва автоматично при излизане от `try` блока</small>

---

#### `java.io.Reader`

```java
abstract void close();
void          mark(int readAheadLimit);
boolean       markSupported();
int           read();
int           read(char[] cbuf);
abstract int  read(char[] cbuf, int off, int len);
int           read(CharBuffer target);
boolean       ready();
void          reset();
long          skip(long n);
```

---

#### `java.io.Writer`

```java
Writer        append(char c);
Writer        append(CharSequence csq);
Writer        append(CharSequence csq, int start, int end);
abstract void close();
abstract void flush();
void          write(char[] cbuf);
abstract void write(char[] cbuf, int off, int len);
void          write(int c);
void          write(String str);
void          write(String str, int off, int len);
```

---

#### Разделител на редовете в текстов файл

<small>
Различните операционни системи използват различен символ или последователност от символи, за да обозначат край на ред в текстов файл:
</small>

  - Windows: `\r\n`
  - UNIX/Linux: `\n`
  - MacOS: `\r`

<small>
За да си гарантирате, че Java кодът ви ще работи коректно на всяка OS, вместо тези символи, трябва да ползвате
</small>

  - `System.lineSeparator()`, или
  - `PrintWriter.println()`, или
  - `BufferedWriter.newLine()`

---

#### Пример с `BufferedReader`

```java
Reader reader = new FileReader("data/data.txt");
BufferedReader bufferedReader = new BufferedReader(reader);

String line;
while ((line = bufferedReader.readLine()) != null) {
    // process line
}
```

---

#### Трите системни потока

@ul

- `System.in`  (`InputStream`)
- `System.out` (`PrintStream`)
- `System.err` (`PrintStream`)

@ulend

---

#### `java.util.Scanner`

```java
Scanner scanner = new Scanner(System.in);
int i = scanner.nextInt();
String str = scanner.nextLine();
// [...]
```

---

#### `java.util.Formatter`

```java
StringBuilder sb = new StringBuilder();
// Send all output to the Appendable object sb
Formatter formatter = new Formatter(sb, Locale.US);

// Explicit argument indices may be used to re-order output.
formatter.format("%4$2s %3$2s %2$2s %1$2s", "a", "b", "c", "d")
// -> " d  c  b  a"

// Optional locale as the first argument can be used to get
// locale-specific formatting of numbers. The precision and width
// can be given to round and align the value.
formatter.format(Locale.FRANCE, "e = %+10.4f", Math.E);
// -> "e =    +2,7183"
```

---

#### `java.util.Formatter`

```java
// The '(' numeric flag may be used to format negative numbers
// with parentheses rather than a minus sign. Group separators
// are automatically inserted.
formatter.format("Amount diff since last statement: $ %(,.2f",
                    balanceDelta);
// -> "Amount diff since last statement: $ (6,217.58)"

// Writes a formatted string to System.out
System.out.format("Local time: %tT", Calendar.getInstance());
// -> "Local time: 13:34:18"
// Writes formatted output to System.err
System.err.printf("Unable to open file '%1$s': %2$s",
                     fileName, exception.getMessage());
// -> "Unable to open file 'food': No such file or directory"
```

---

## Въпроси

---

#### Файловата система

@ul

- Йерархична структура
- Състои се от директории и файлове
- Главна директория (корен)
- Текуща (работна) директория
- Пътища
    - Относителни
    - Абсолютни
- Symbolic links

@ulend

---

#### Java API-то за работа с файловата система

<small>NIO.2 (NIO == Non-blocking I/O)</small>

- Пакетът [`java.nio.file`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/nio/file/package-summary.html)
  - [`java.nio.file.Path`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/nio/file/Path.html)
  - [`java.nio.file.Files`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/nio/file/Files.html)

---

#### `java.nio.file.Path`

```java
// Класът Path служи за представяне на път
// Обозначава файл или директория
// Файлът или директорията може физически да съществуват или не
// Инстанции се създават чрез статични методи на java.nio.file.Paths,
// а от Java 11 - и на java.nio.file.Path

Path pathToUserHomeDir = Path.of("C:\\Users\\joe");
                         // C:\Users\joe
Path pathToAFile       = Path.of("C:\\Users\\joe\\orders.txt");
                         // C:\Users\joe\orders.txt
Path relPathToAFile    = Path.of("Users", "joe", "orders.txt");
                         // \Users\joe\orders.txt

Path linuxPathToAFile  = Paths.get("/home", "joe", "file.txt");
                         // /home/joe/file.txt
Path linuxRelativePath = Paths.get("documents", "FileIO.odp");
                         // documents/FileIO.odp
```

---

#### `java.nio.file.Path` - разделители

- Разделителят по подразбиране на имената в пътищата е OS-dependent
    - В UNIX, Linux и MacOS е forward slash: /
    - В Windows е back slash: \\
- Може да се вземе в Java код чрез `File.separator` или `FileSystem.getSeparator()`

---

<table>
  <tr>
    <th style="font-size:0.9em">Метод</th>
    <th style="font-size:0.9em">Връща под UNIX/Linux</th>
    <th style="font-size:0.9em">Връща под Windows</th>
  </tr>
  <tr style="font-size:0.7em">
    <td>toString()</td>
    <td>/home/joe/foo</td>
    <td>C:\home\joe\foo</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>getFileName()</td>
    <td>foo</td>
    <td>foo</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>getName(0)</td>
    <td>home</td>
    <td>home</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>getNameCount()</td>
    <td>3</td>
    <td>3</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>subpath(0, 2)</td>
    <td>home/joe</td>
    <td>home\joe</sup></td>
  </tr>
  <tr style="font-size:0.7em">
    <td>getParent()</td>
    <td>/home/joe</td>
    <td>\home\joe</sup></td>
  </tr>
  <tr style="font-size:0.7em">
    <td>getRoot()</td>
    <td>/</td>
    <td>C:\</td>
  </tr>
</table>

---

#### `java.nio.file.Path`: Преобразувания

```java
Path toAbsolutePath() // преобразува пътя до абсолютен, т.е.
                      // започващ от главната директория

Path toRealPath()     // преобразува пътя до реален, т.е.
                      //     - абсолютен
                      //     - с премахнати символни връзки
                      //     - с премахнати . и ..
Path resolve(Path anotherPath) // добавя относителен път по следния начин:
Path p1 = Paths.get("/home/joe/foo");
Path p2 = p1.resolve("bar"); // резултатът е /home/joe/foo/bar

```

---

#### `java.nio.file.Path`: Сравняване

```java
boolean equals(Path anotherPath)
boolean startsWith(Path anotherPath)
boolean endsWith(Path anotherPath)
```

---

#### Some legacy: `java.io.File`

<small>Дескриптор за файлове, аналог на `java.nio.file.Path`</small>
<small>във версиите преди Java 7. Присъства все още в много API-та.</small>

```java
// creation
File absoluteFile = new File("c:\\Users\\joe\\file.txt");
File absoluteFile = new File("c:\\Users\\joe", "file.txt");
File parentFile = new File("c:\\Users\\joe");
File absoluteFile = new File(parentFile, "file.txt");
URI fileUri = URI.create("file:///home/joe/file.txt");
File absoluteFile = new File(fileUri);

// conversion to and from java.nio.file.Path
Path absolutePath = absoluteFile.toPath();
File absoluteFile = absolutePath.toFile();
```

---

#### `java.nio.file.Files`: Метаданни

```java
long size(Path path)

boolean isRegularFile(Path path)
boolean isDirectory(Path path)
boolean isSymbolicLink(Path path)
boolean isHidden(Path path)


FileTime getLastModifiedTime(Path path)
FileTime setLastModifiedTime(Path path, FileTime time)

UserPrincipal getOwner(Path path)

Object getAttribute(Path path, String attribute)
Path setAttribute(Path path, String attribute, Object value)
```

---

#### `java.nio.file.Files`: Други проверки

```java
boolean exists(Path path)
boolean notExists(Path path)
boolean isReadable(Path path)
boolean isWritable(Path path)
boolean isExecutable(Path path)
boolean isSameFile(Path path1, Path path2)

```

---

#### `java.nio.file.Files`: Изтриване на файлове и директории

```java
void delete(Path path)
// ако path не съществува, хвърля NoSuchFileException
// ако path е непразна директория, хвърля DirectoryNotEmptyException

boolean deleteIfExists(Path path)
// ако path не съществува, връща false
// ако path е непразна директория, хвърля DirectoryNotEmptyException
```

---

#### `java.nio.file.Files`: Копиране на файлове и директории

```java
Path copy(Path source, Path target, CopyOption... options)

// съдържанието на директория не се копира
// options може да бъде една или повече от:
//    StandardCopyOption.COPY_ATTRIBUTES
//        копират се и атрибутите на файла/директорията,
//        например време на последна промянa
// StandardCopyOption.REPLACE_EXISTING
//        ако target е съществуващ файл, то той се презаписва
//        вместо да се хвърля FileAlreadyExistsException
```

---

#### `java.nio.file.Files`: Преместване/преименуване на файлове и директории

```java
Path move(Path source, Path target, CopyOption... options)

// директория може да се премести само на същата файлова система
// options може да бъде една или повече от:
//    StandardCopyOption.ATOMIC_MOVE
//        преместването е атомарно, а ако това не е възможно,
//        се хвърля `AtomicMoveNotSupportedException
//    StandardCopyOption.REPLACE_EXISTING`: ако target е
//    съществуващ файл, то той се презаписва вместо да се хвърля изключение
```

---

#### `java.nio.file.Files`: Създаване на директория

```java
Path createDirectory(Path dir)
// създава директория с път dir,
// ако родителската директория на този път вече съществува

Path createDirectories(Path dir)
// създава директория с път dir, създавайки
// и родителските директории, ако има нужда
```

---

#### `java.nio.file.Files`: Обхождане на директория

```java
DirectoryStream<Path> newDirectoryStream(Path dir)
// създава поток, от който могат да бъдат прочетени файловете
// и поддиректориите на директорията с път dir като инстанции на Path
// DirectoryStream прилича повече на колекция
// (защото е наследник на Iterable), отколкото на входно-изходен поток.

Path dir = ...;
try (DirectoryStream<Path> stream = Files.newDirectoryStream(dir)) {
    for (Path fileOrSubDir: stream) {
        // употреба на fileOrSubDir
    }
} catch (IOException | DirectoryIteratorException e) {
    // обработка на изключенията
}
```

---

#### Обхождане на директория с шаблони за търсене (globs, wildcards)

```java
DirectoryStream<Path> newDirectoryStream(Path dir, String glob)
// създава поток, който съдържа само файловете и поддиректориите,
// които отговарят на шаблона за търсене glob
// например, итерираме всички файлове с разширение .java


Path dir = ... ;

try (DirectoryStream<Path> stream =
        Files.newDirectoryStream(dir, "*.java")) {
    // [...]
}
```

---

#### Шаблони за търсене (globs, wildcards)

<table>
  <tr>
    <th style="font-size:0.9em">Шаблон</th>
    <th style="font-size:0.9em">Семантика</th>
  </tr>
  <tr style="font-size:0.7em">
    <td>\*</td>
    <td>замества произволен брой символи (вкл. николко) в рамките на едно име от пътя (т.е. не може да замести пътния разделител - / или \\)</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>\*\*</td>
    <td>като \*, но пресича границите на имената в пътя</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>?</td>
    <td>замества точно един символ</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>{subGlobl, …, subGlobN}</td>
    <td>замества някой от под-шаблоните</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>[c1...cN]</td>
    <td>замества някой от символите</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>[c1-c2]</td>
    <td>замества някой от символите в диапазона от c1 до с2</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>\</td>
    <td>използва се за escape на специалните символи, вкл. \
всеки друг символ - замества себе си</td>
  </tr>
</table>

---

#### Примерни шаблони за търсене

<table>
  <tr>
    <th style="font-size:0.9em">Шаблон</th>
    <th style="font-size:0.9em">Семантика</th>
  </tr>
  <tr style="font-size:0.7em">
    <td>/home/\*/file</td>
    <td>замества /home/joe/file (и други), но не и /home/joe/work/file</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>/home/\*\*/file </td>
    <td>замества /home/joe/work/file (и други)</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>{temp\*, tmp\*}</td>
    <td>замества всички имена, започващи с temp или tmp</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>[fmi]</td>
    <td>замества една от буквите f, m, и i</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>[a-z]</td>
    <td>замества една от малките латински букви</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>[fF]</td>
    <td>замества малко или голямо F</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>\\</td>
    <td>замества обратно наклонена черта</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>alabala</td>
    <td>замества alabala</td>
  </tr>
  <tr style="font-size:0.7em">
    <td>[!a].txt</td>
    <td>замества един символ, различен от ‘a’</td>
  </tr>
</table>

---

#### Прочитане или записване на цял файл с `java.nio.file.Files`

```java
// These are suitable for small files.
// For larger ones, use buffered streams
byte[] readAllBytes(Path file);
List<String> readAllLines(Path file, Charset cs);

Path write(Path file, byte[] bytes, OpenOption... options);
Path write(Path path, Iterable<? extends CharSequence> lines,
        Charset cs, OpenOption... options);

// Read/write entire file into a String: since Java 11
String readString(Path file); // UTF-8
String readString(Path file, Charset cs);

Path writeString(Path file, CharSequence lines,
        OpenOption[] options); // UTF-8
Path writeString(Path file, CharSequence lines,
        Charset cs, OpenOption[] options);
```

---

#### Сравнителен performance на различните методи за четене на файл

![File Reading Performance](images/07.8-file-reading-performance.png)

---

#### Временни файлове и директории

```java
Path createTempFile(Path dir, String prefix, String suffix)
// създава нов файл в директорията dir и с име,
// започващо с prefix и завършващо със suffix
Path createTempFile(String prefix, String suffix)
// създава нов файл в системната временна директория и с име,
// започващо с prefix и завършващо със suffix
Path createTempDirectory(Path dir, String prefix)
// създава нова поддиректория в директорията dir и с име,
// започващо с prefix
Path createTempDirectory(String prefix)
// създава нова поддиректория в системната временна директория и с име,
// започващо с prefix
```

---

#### Работа със ZIP файлове

@ul

- Класовете за работа със ZIP файлове се намират в пакета `java.util.zip`
  - `ZipFile` се използва за четене и взаимодействие със `ZipEntry` инстанции в ZIP архив
  - `ZipEntry` е абстракция за елемент (файл или директория) в ZIP архив (например, `ZipFile` инстанция)
  - `ZipOutputStream` е наследник на абстрактния `OutputStream` клас и се използва за записване на елементи в ZIP файл

@ulend

---

#### Как се unit-тества код, работещ с файлове?

@ul

- Пакетираме (статични) тестови файлове в (проекта на) тестовете
- Създаваме динамично тестови файлове преди изпълнението на тестовете и ги изтриваме след края на тестовете
- Заменяме прякото тестване с файлове (файлови потоци) с други I/О потоци (например `ByteArrayInputStream` или `StringReader`)
    - това обикновено изисква refactoring, но е най-сигурният и прост начин

@ulend

---

#### Clean Code принципи за код, работещ с потоци и файлове

  - винаги и гарантирано затваряй ресурсите (потоци, файлове), които създаваш
  - за целта, ползвай try-with-resources винаги, когато е възможно
  - ползвай `var` (с удоволствие и мярка)

<p>

```java
var input = new ByteArrayInputStream("Shorter is better".getBytes());
```

---

#### Обобщение

<small>В Java има голямо разнообразие от API-та за работа с файловата система.</small>
<small>Те се различават по сценариите, за които са подходящи, имат различни предимства и недостатъци и правят различен компромис между гъвкавост, бързодействие и сложност за употреба.</small>

![IO Streams](images/07.9-io-apis-wrapup.gif)

<small><small>API-тата, подредени от по-прости към по-сложни</small></small>

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend

## Ламбда изрази и Stream API

_02.12.2020_

---

#### Предната лекция говорихме за:

@ul

- Входно-изходни потоци
- Работа с файловата система

@ulend

---

#### Днес ще разгледаме:

@ul

- Lambda изрази
- Stream API

@ulend

---

#### Функционални интерфейси

@ul

- *Функционалните интерфейси* са интерфейси с точно един абстрактен метод
- Понякога се наричат още *SAM интерфейси* (Single Abstract Method))
- Няма проблем, освен абстрактния си метод, да имат произволен брой статични или `default` методи
- Могат да се анотират с незадължителната анотация `@FunctionalInterface`

@ulend

---

#### Един пример

```java
public class NamesSorter {
    public static void main(String[] args) {
        List<String> names =
                Arrays.asList("Peter", "Anna", "Mike", "Xenia");
        Collections.sort(names, new NamesComparator());
        System.out.println(names);
    }
}

class NamesComparator implements Comparator<String> {
    @Override
    public int compare(String o1, String o2) {
        return o1.compareTo(o2);
    }
}

// Налага се да създадем отделен клас, имплементиращ SAM интерфейс
```

---

#### Един пример

```java
// Може да го направим и с анонимен вътрешен клас,
// но пак има доста boilerplate код
public class NamesSorter {
    public static void main(String[] args) {
        List<String> names =
                Arrays.asList("Peter", "Anna", "Mike", "Xenia");
        Collections.sort(names, new Comparator<String>() {
            @Override
            public int compare(String a, String b) {
                return a.compareTo(b);
            }
        });
        System.out.println(names);
    }
}
// Има ли начин да подадем само дефиниция на функция като аргумент?
```

---

#### Един пример

```java
Collections.sort(names, new Comparator<String>() {
    @Override
    public int compare(String a, String b) {
        return a.compareTo(b);
    }
});

// define just the function
Collections.sort(names, (String a, String b) -> {
    return a.compareTo(b);
});

// omit {} and return
Collections.sort(names, (String a, String b) -> a.compareTo(b));

// infer argument types
Collections.sort(names, (a, b) -> a.compareTo(b));
```
@[1-6]
@[8-11]
@[13-14]
@[16-17]

---

#### Ламбда израз

- Функция, която няма име и не е метод на клас, се нарича *ламбда функция* или *ламбда израз*.
- Терминът идва от ламбда смятането - универсален модел за описание на изчисления (алгоритъм), който може да се използва за описание на произволна машина на Тюринг. Въведено е от Алонзо Чърч през 30-те години на 20-ти век.

---

#### Ламбда изрази - синтаксис

параметри -> тяло

<small>
- Списъкът с параметри се огражда с кръгли скоби, а параметрите се разделят със запетаи. Може да е празен ()
- Типът на параметрите може да бъде
    - експлицитно зададен
    - inferred: с `var` или въобще пропуснат
- Когато има един-единствен параметър и неговият тип може да бъде пропуснат, може да се пропуснат и скобите
- Тялото на ламбда израз се огражда с фигурни скоби {} и може да съдържа нула, един или повече изрази, разделени с ;
   - Когато има единствен израз в тялото, return клаузата може да се изпусне
   - Когато имаме повече от един израз, трябва експлицитно да предоставим return клауза

</small>

---

#### Ламбда изрази - примери

```java
// one parameter
(String name) -> System.out.println("Hello " + name);

// type inference
(name) -> System.out.println("Hello " + name);

// omit ()
name -> System.out.println("Hello " + name);

// three parameters
(int a, int b, double c) -> a + b + c;

// type inference
(a, b, c) -> a + b + c;

// empty body
() -> {};
```

---

#### Ламбда изрази - примери

```java
// omit {} and the return as there is single expression in the body
(a, b) -> a + b;

// multiple expressions in the body
(a, b) -> {a = 5; b = 2; return a + b;}; 

// body on multiple lines
(a, b) -> {
  a = 5;
  b = 2;
  return a + b;
};
```

---

#### Ламбда изразите като тип

<small>

- Java e статично типизиран език ⇨ ламбда изразите също си имат тип
- Типът на ламбда израз е някакъв функционален интерфейс
- По време на компилация, ламбда изразът трябва да съответства на абстрактния метод на функционалния интерфейс
    - следователно се знае типът и на параметрите на функцията, и на връщания резултат
- Може да декларираме променливи от тип функционален интерфейс и да им присвояваме ламбда изрази, или да декларираме методи с формални параметри - функционален интерфейс и да подаваме ламбда израз като аргумент

</small>

---

#### Стандартни функционални интерфейси

<small>
JDK-то съдържа множество стандартни функционални интерфейси. Намират се в пакета `java.util.function`.
Четирите най-използвани от тях са

| Интерфейс               | Ламбда нотация |
| ----------------------- |--------------- |
| Supplier<T>             | () -> T        |
| Consumer<T>             | (T) -> void    |
| Predicate<T>            | (T) -> boolean |
| Function<T, R>          | (T) -> R       |

</small>

---

#### `Supplier<T>: () -> T`

<small>Представлява операция без аргументи, която връща резултат.
Съдържа един абстрактен метод, `T get()`.</small>

```java
Supplier<Integer> supplyYear = () -> 2020;
System.out.println(supplyYear.get()); // 2020
```

---

#### `Consumer<T>: (T) -> void`

```java
// Представлява операция, която приема единствен аргумент като вход
// и не връща резултат. За разлика от повечето функционални интерфейси,
// Consumer<T> работи чрез странични ефекти.
// Съдържа един абстрактен метод, `void accept(T t)`.
// Съдържа и метод `default Consumer<T> andThen(Consumer<T> after)`,
// чрез който може да се chain-ва с други `Consumer<T>` операции.

Consumer<Double> inEUR = s -> System.out.println("EUR: " + s);
Consumer<Double> inUSD = s -> System.out.println("USD: " + s);

inEUR.accept(10.0); // EUR: 10.0
inEUR.andThen(inUSD).accept(10.0); // EUR: 10.0
                                   // USD: 10.0
```

---

#### `Predicate<T>: (T) -> boolean`

```java
// Представлява предикат: булева функция с един аргумент.

// abstract method: evaluates this predicate on the given argument
boolean test(T t);

// Returns a predicate that represents the logical negation
// of this predicate
default Predicate<T> negate();
// Returns a composed predicate that represents a short-circuiting
// logical AND of this predicate and another
default Predicate<T> and(Predicate<? super T> other); 
// Returns a composed predicate that represents a short-circuiting
// logical OR of this predicate and another
default Predicate<T> or(Predicate<? super T> other);
// Returns a predicate that tests if two arguments are equal
// according to Objects.equals(Object, Object)
static <T> Predicate<T> isEqual(Object targetRef);
```

---

#### `Predicate<T>: (T) -> boolean`

```java
Predicate<Integer> isLessThan10 = i -> i < 10;
Predicate<Integer> isGreaterThan0 = i -> i > 0;
System.out.println(isLessThan10.and(isGreaterThan0).test(5)); // true
System.out.println(isLessThan10.and(isGreaterThan0).test(10)); // false
```

---

#### `Function<T, R>: (T) -> R`

```java
// Представлява функция, която приема един аргумент и връща резултат

// abstract method: applies this function to the given argument
R apply(T t);

// Returns a composed function that first applies this function to its
// input, and then applies the after function to the result
default <V> Function<T,V>
        andThen(Function<? super R,? extends V> after);

// Returns a composed function that first applies the before function
// to its input, and then applies this function to the result
default <V> Function<V,R>
        compose(Function<? super V,? extends T> before);

// Returns a function that always returns its input argument
static <T> Function<T,T> identity();
```

---

#### `Function<T, R>: (T) -> R`

```java
Function<Integer, Integer> square = i -> i * i;
Function<Integer, Integer> subtractOne = i -> i - 1;
System.out.println(square.andThen(subtractOne).apply(3)); // 8
System.out.println(square.compose(subtractOne).apply(3)); // 4

// z1(x) = f(g(x))
Function<Integer, Integer> z1 = f.compose(g);

// z2(x) = g(f(x))
Function<Integer, Integer> z2 = f.andThen(g);
```

---

#### Други стандартни функционални интерфейси

<small>
Останалите 39 функционални интерфейси в `java.util.function` са вариации на четирите разгледани.
Създадени са, за да се постигне едно или няколко от следните:
- по-добро бързодействие чрез избягване на autoboxing чрез използване на примитивните типове `int`, `long` и `double`
- позволяване на два аргумента и/или по-кратка нотация

</small>

```java
// shorter notation without generics and avoiding autoboxing
IntFunction<R>
// function of two arguments
BiFunction<T, U, R>
// allows two input parameters of type T and returns a value of type T
BinaryOperator<T>
```

---

#### Контекст на ламбда израз

<small>
- Компилаторът определя типа на ламбда израз в зависимост от контекста на употребата му:
    - инициализация или присвояване на променлива
    - параметър на метод или конструктор
    - връщане на резултат от метод
    - сast операция
- Един и същ ламбда израз може да има различен тип в зависимост от контекста:

</small>

```java
Function<String, Integer> func = x -> 1;
Comparable<Double>        comp = x -> 1;
```

---

#### Variable capture

<small>
- Ламбда изразите могат да достъпват променливи, декларирани извън самия ламбда израз. Това може да са
    - локални променливи
    - член-променливи на обхващащия клас
    - статични член-променливи на обхващащия клас
- Ако ламбда израз използва локална променлива, декларирана извън него, тази променлива трябва да е `final` или *ефективно* `final` (т.е. да не си променя стойността в този контекст)
- Причината за това ограничение е, че ламбда функцията може да се предава като аргумент и изпълнява в различни контексти (например, различни нишки) и резултатът от изпълнението ѝ не трябва да зависи от контекста. Също, възможно е ламбда изразът да се изпълни след като локалната променлива е унищожена (например, ако метод връща такъв ламбда израз като резултат)

</small>

---

#### Variable capture

```java
int x = 7;
Function<Integer, Integer> multiply = i -> i * x;
// x++; would cause compilation error on the line above
```

---

#### Ключовата дума `this`

- Ключовата дума `this` в ламбда израз реферира инстанцията на обхващащия клас, която се нарича още *обхващаща инстанция (enclosing instance)*, *обхващащ контекст* или *обхващащ scope*.

---

#### Ламбда изрази: добри практики

- Препоръчва се ламбда изразите да не модифицират:
  - данните на източника (*non-interference*)
  - външни променливи (*stateless*)
- Препоръчва се ламбда изразите да са one-liners

---

#### Референции към методи

<small>Много често в ламбда изразите просто делегираме параметрите на някой съществуващ метод:</small>

```java
Comparator<String> comp1 = (s1, s2) -> s1.compareTo(s2);
```

<small>Референциите към методи са удобен синтаксис, с който може да се реферира съществуващ метод на клас:</small>

```java
Comparator<String> comp2 = String::compareTo;
Predicate<String> filter = "Ivan"::equalsIgnoreCase;
```

---

#### Референции към методи - видове

<small>Референция към статичен метод (ClassName::methName)</small>
```java
String::valueOf
```

<small>Референция към метод на конкретна инстанция от даден клас (instanceRef::methName)</small>
```java
"FPRocks!"::equals
```

<small>Референция към метод на произволна инстанция на даден клас (ClassName::methName)</small>
```java
String::toLowerCase
```

---

#### Референции към методи - видове

<small>Конструктор (ClassName::new)</small>
```java
String::new, String[]::new
```

<small>Метод на суперкласа (super::methName)</small>
```java
super::equals
```

---

## Въпроси

---

#### Java Stream API

<small>
Ламбда изразите, заедно с функционалните интерфейси, разширяват възможностите на Java с елементи на функционалното програмиране. Те позволяват предаването на поведение (функции) като параметри на библиотеки, оптимизирани за бързодействие при обработката на данни. По този начин, един app developer може да се фокусира върху бизнес логиката на приложението си, оставяйки аспекти като бързодействието на авторите на въпросните библиотеки.
Една такава основна библиотека е `java.util.stream`.
</small>

---

#### `java.util.stream`

<small>
Интерфейсите и класовете от пакета `java.util.stream`, които съвкупно наричаме Java Stream API, са предназначени за ефективната последователна или паралелна обработка на крайни или безкрайни потоци от данни. Алгоритмите, работещи с данни във вид на потоци, се реализират като последователност (pipeline) от операции върху елементите на потока.
</small>

---

#### Инициализация на поток от колекции, масиви и низове

Има множество начини да се инициализира поток:

```java
Stream.empty() // създава празен поток (без елементи)
Stream.of(T... values) // създава поток от елемеенти от тип T

// връща поток от елементите на дадената колекция
Collection.stream()

// връща паралелен поток от елементите на дадената колекция
Collection.parallelStream() 

Arrays.stream((T[] array)) // връща поток от елементите на масив

IntStream streamOfChars = "abc".chars(); // поток от символите на низ

Stream<String> streamOfString = // split-ва низ като поток по шаблон
        Pattern.compile(", ").splitAsStream("a, b, c");
```

---

#### Потоци от елементи от примитивен тип

<small>
`Stream<T>` е generic интерфейс и няма как да се използва за примитивни типове като параметър.
Затова съществуват три специализирани интерфейса за `int`, `long` и `double` потоци:

  - `IntStream`
  - `LongStream`
  - `DoubleStream`

Инстанции на примитивните потоци се създават със статичните `of`, `range()` и `rangeClosed()` методи на интерфейсите или индиректно, от API-та, които връщат примитивен поток.
</small>

```java
IntStream intStream = IntStream.of(1, 2, 3);
int[] intArray = {1, 2, 3};
IntStream intStreamFromArray = IntStream.of(intArray);
LongStream longsRange = LongStream.range(1, 3); // [1, 3)
LongStream longsRangeClosed = LongStream.rangeClosed(1, 3); // [1, 3]
```

---

#### Потоци от елементи от примитивен тип

`IntStream`, `LongStream` и `DoubleStream` имат допълнителни статистически методи:

- `average()`
- `max()`
- `min()`
- `sum()`

---

#### Инициализация на поток от съдържание на файл или директория

```java
// java.nio.file.Files

// създава поток от низове, представляващи редовете на даден текстов файл
Stream<String> lines(Path path)

// връща съдържанието на директория като поток от файлове и директории
Stream<Path> list(Path dir)

// връща съдържанието на директорно поддърво
Stream<Path> walk(Path start, FileVisitOption... options)

// връща съдържанието на директорно поддърво, което отговаря на зададения
// предикат, обхождайки до зададена дълбочина
find(Path start, int maxDepth,
        BiPredicate<Path, BasicFileAttributes> matcher,
        FileVisitOption... options)
```

---

#### Инициализация на поток от съдържание на файл или директория

```java
// java.io.BufferredReader

// създава поток от низове, представляващи редовете, прочитани от даден
// BufferredReader (най-често, от файл)
Stream<String> lines()
```

---

#### Инициализация на поток от псевдослучайни числа

```java
// java.util.Random

// създава безкраен поток от псевдослучайни double числа в интервала [0, 1)
DoubleStream doubles()

// създава безкраен поток от псевдослучайни int числа
IntStream ints()

// създава безкраен поток от псевдослучайни long числа
LongStream longs()
```

---

#### Инициализация на поток чрез итерация

```java
// java.util.Stream

// Създава безкраен последователен поток чрез итеративното прилагане
// на втория аргумент към първия аргумент.
// Елементите на потока са seed, f(seed), f(f(seed)), ...
Stream<T> iterate(T seed, UnaryOperator<T> f)

// Създава краен последователен поток чрез итеративното прилагане
// на третия аргумент към първия: // seed, f(seed), f(f(seed))
// докато вторият параметър връща true
Stream<T> iterate(T seed, Predicate<T> hasNext, UnaryOperator<T> f) 

Stream.iterate(1, i -> ++i) // 1, 2, 3, 4, 5, ...
Stream.iterate(1, i -> i < 4, i -> ++i) // 1, 2, 3
```

---

#### Инициализация на поток чрез `Supplier`

```java
// java.util.Stream

// създава безкраен поток, всеки елемент на който се генерира
// от подадената Supplier функция
Stream<T> generate(Supplier<T> supplier)

Stream.generate(() -> 1) // безкраен поток 1, 1, 1, 1, ...
```

---

#### Конкатенация на потоци

```java
// java.util.Stream

// създава поток, който представлява конкатенацията
// на подадените два потока
static <T> Stream<T> concat(Stream<? extends T> a,
                                       Stream<? extends T> b)

Stream<Integer> stream1 = List.of(1, 2).stream();
Stream<Integer> stream2 = List.of(2, 3, 4).stream();
Stream.concat(stream1, stream2) // 1, 2, 2, 3, 4
```

---

#### Операции върху потоци

<small>
- Много от методите на `Stream` интерфейса, онези, които имат параметър функционален интерфейсен тип, се наричат *операции*
- Stream API-то предоставя набор от функции от по-висок ред, чрез които декларативно можем да обработим данните

</small>

---

#### Операции върху потоци

<small>
- Операциите с потоци биват два вида:
  - *Междинни* – връщат `Stream` обект като резултат
  - *Терминални* – връщат обект, различен от `Stream`, или не връщат резултат

- Обработката на потоци типично се организира като pipeline
    - потокът се създава с инициализираща операция,
    - поредица от междинни операции обработват потока, като резултатът от всяка става вход за следващата във веригата
    - накрая терминална операция продуцира резултат или страничен ефект и приключва потока

</small>

---

#### Stream API pipeline

```java
List<Person> result = people.stream()
          .filter(p -> p.getFirstName().equals("Nikolay"))
          .filter(p -> p.getAge() < 25)
          .sorted(Comparator.comparing(Person::getLastName))
          .collect(Collectors.toList());
```

---

#### Междинни операции върху потоци

@ul

- Междинните операции връщат `Stream` обект
- който съдържа същите или модифицирани елементи,
- като типът на елементите може да е същият или различен от типа на елементите във входния поток.
- Според функционалността си, се разделят на *филтриращи*, *map-ващи* и *сортиращи*

@ulend

---

#### Филтриращи междинни операции: `filter`

```java
// Междинна операция, приема функция (T -> boolean), т.е. предикат
// и връща поток само с елементите, за които предикатът е true.

employees.filter(e -> e.getAge() < 25);
```

---

#### Филтриращи междинни операции: `limit`

```java
// Междинна операция, приема цяло число N и връща краен поток
// само с първите N елементa на входния поток. Особено често се използва,
// за да се обработи крайна част от безкраен поток.

employees.limit(100);
```

---

#### Филтриращи междинни операции: `distinct`

```java
// Междинна операция без аргументи, връща елементите на входния поток
// като премахва повтарящите се. Критерият за еднаквост е equals().

employees.distinct();
```

---

#### Филтриращи междинни операции: `skip`, `dropWhile`, `takeWhile`

```java
// Междинна операция, приема цяло число N и връща краен поток,
// игнорирайки (пропускайки) първите N елементa на входния поток.

employees.skip(10);

// пропуска първите елементи на потока, докато предикатът връща true

employees.dropWhile(e -> e.getAge < 18);

// допуска само първите елементи на потока, докато предикатът връща true

employees.takeWhile(e -> e.getName().startsWith("A"));
```

---

#### Map-ващи междинни операции: `map`

<small>
- Map-ващите операции за единствени междинни операции, които променят елементите на входния поток
- Те map-ват, (трансформират) всеки елемент на входния поток към нов елемент
- Map е междинна операция, приема функция (T -> V) и връща поток със същия брой елементи, но oт новия тип (V)

</small>

```java
employees.map(e -> e.getName());

// map операции, специализирани за примитивни потоци -
// mapToInt, mapToLong, mapToDouble

employees.mapToInt(e -> e.getAge());
employees.mapToDouble(e -> e.getSalary());

// the same as the above but with method reference
employees.mapToDouble(Employee::getSalary());
```

---

#### Map-ващи междинни операции: `flatMap`

<small>
Междинна операция, приема функция (T -> Stream[V]) и връща поток с линейна структура (flat), вместо поток от потоци.
</small>

```java
// Returns 1-dimensional stream with all employee bonuses
// Stream<T> -> flatMap -> Stream<V>
employees.flatMap(e -> Stream.of(e.getSalary(), e.getBonus()));
```

<small>
Има и `flatMap` операции, специализирани за примитивни потоци - `flatMapToInt`, `flatMapToLong`, `flatMapToDouble`
</small>

---

#### Сортиращи междинни операции: `sorted`

```java
// according to their natural order
employees.sorted();

// according to the specified Comparator
employees.sorted((e1, e2) -> e1.getSalary() < e2.getSalary());
```

<small>
Обърнете внимание, че тези операции не могат да приключат докато не се обработят всички елементи на потока.
Te са скъпи откъм ресурси и бавни откъм performance, така че трябва да се ползват само за малки потоци.

</small>

---

#### Терминални операции: обработка елемент по елемент с `forEach`

<small>Терминална операция, приема функция (T -> void) и не връща резултат (т.е. няма функционална природа)</small>

```java
// Prints the name and age of each employee
// Stream<T> -> forЕach -> void

employees.forEach(
        e -> System.out.println(e.getName() + " " + e.getAge()));
```

---

#### Терминални операции: `reduce`

<small>Терминална операция, приема функция ((T, T) -> T) и връща единичен резултат</small>

```java
// Returns the sum of employee salaries
// Stream<T> -> reduce -> T
employees.mapToDouble(Employee::getSalary)
     .reduce((res, el) -> res + el);
```

<small>
- Специализирани reduce операции: `min()`, `max()`
- Допълнителни reduce операции за `Int`/`Long`/`DoubleStream`: `sum()`, `average()`

</small>

---

#### `reduce` - обща форма

<small>Reduce има и по-обща форма, която дава възможност да се върне резултат, различен от типа на потока ((V, T) -> V)</small>

```java
// Stream<T> -> reduce -> V
double result = employees.reduce(
    0.0,                               // initial value
    (res, el) -> res + el.getSalary(), // accumulator
    (left, right) -> left + right);    // combiner
```

---

#### `collect`

<small>
- Възможно е reduce операция да върне резултат, който не е единичен обект, а колекция
- collect предоставя възможност за акумулиране на резултата в колекция

</small>

```java
List<Integer> list = Stream.of(1, 2, 3, 4, 5)
                           .collect(ArrayList::new, // supplier
                                    ArrayList::add, // accumulator
                                    ArrayList::addAll); // combiner
System.out.println(list); // [1, 2, 3, 4, 5]
```

---

#### `collect` с колектори

<small>
Тъй като `collect` в общия си вид изисква три функции, за улеснение в Stream API-то има клас `Collectors` със статични методи, създаващи "готови" специализирани `Collector` обекти за най-често срещаните случаи: `Collectors.toCollection()`, `Collectors.toList()`, `Collectors.toSet()`, `Collectors.toMap()`</small>

```java
List<Integer> list = Stream.of(1, 2, 3, 4, 5)
                           .collect(Collectors.toList());
System.out.println(list); // [1, 2, 3, 4, 5]
```

---

#### Още колектори

<small>
Класът `Collectors` също така предоставя полезни помощни функции за `reduce` oперации. Най-използваните са:
  - `groupingBy` – групира (агрегира) елементите по дадена класифицираща функция
  - `joining` – конкатенира елементите на потока в низ

</small>

```java
// The result is from type Map<Department, List<Employee>>
employees.collect(
        Collectors.groupingBy(Employee::getDepartment));

// The result is a String containing all empployee names
// separated by the specified separator string
employees.map(Employee::getName).collect(
        Collectors.joining(", "));
```

---

#### Short-Circuiting операции

Операции, които прекратяват обхождането на потока преждевременно. Полезни са при безкрайни потоци.

---

#### Short-Circuiting операции

<small>
- `findFirst()` – връща първия елемент на потока
- `findAny()` – връща произволен елемент от потока
- `allMatch(T -> boolean)` – дали всички елементи отговарят на дадено условие
- `anyMatch(T -> boolean)` – дали някой елемент отговаря на дадено условие
- `noneMatch(T -> boolean)` - дали никой от елементите не отговаря на дадено условие
- `limit(int n)` – връща `n` елементи (междинна операция)

</small>

---

#### Други терминални операции: `Count`

```java
long count = Stream.of(1, 2, 3, 4, 5).count();
System.out.println(count); // 5

// another way
long count = Stream.of(1, 2, 3, 4, 5).collect(Collectors.counting());
System.out.println(count); // 5
```

---

#### `java.util.Optional`

<small>
- Generic клас, контейнер за обект, който може да съдържа или не дадена стойност
- Някои от методите на Stream API-то връщат като резултат `Optional<Т>`
- Начин за избягване на проверки за `null` или `NullPointerException`

</small>

```java
// Check if value is present
boolean isPresent = optionalEmployee.isPresent();

// Executes the action only if the value is present
optionalEmployee.ifPresent(System.out::println);
```

---

#### `java.util.Optional`

```java
// Returns the container value
// or throws NoSuchElementException
Employee e = optionalEmployee.get();

// Returns default value if the value is not present
optionalEmployee.orElse(Employee.UNKNOWN);

// Throws given exception if the value is not present
optionalEmployee.orElseThrow(NoSuchElementException::new);

int result = Stream.of(1, 2, 3, 4, 5)
                .filter(i -> i > 10)
                .findAny()
                .orElse(-1);
System.out.println(result); // -1
```

---

#### Странични ефекти

@ul

- Страничен ефект е всяко действие във функция, което променя външно за нея състояние:
  - промяна на данни (външни за функцията)
  - I/O операция
  - хвърляне на изключение
  - извикване на друга функция, която предизвиква страничен ефект
- Всеки метод в Java, който е от тип `void`, извършва страничен ефект.

@ulend

---

#### Странични ефекти - пример

```java
public class BankAccount {

    private int balance = 100;

    public int transfer(int amount) {
        balance += amount;
        return balance;
    }

}
```

```java
BankAccount account = new BankAccount();
account.transfer(10); // 110
account.transfer(10); // 120
```

---

#### Чисти функции

@ul

- Чистите функции не извършват странични ефекти
- Винаги когато извикаме функцията с дадени параметри, е гарантиран един и същ резултат

@ulend

---

#### Чисти функции

@ul

- Резултатът им може да се запази и преизползва
- Извикването на функцията може да бъде заменено с резултата (referential transparency)
- Чистите функции са лесно композируеми
- Чистите функции са лесни за анализ на проблеми
- Позволяват изчислението да се паралелизира

@ulend

---

#### Чисти функции - пример

```java
public static int add(int a, int b) {
    return a + b;
}
```

```java
add(3, 5) // 8
add(3, 5) // 8
```

---

#### Изпълнение на stream pipeline

@ul

- Изпълнението може да бъде последователно или паралелно
- Може да превръщате
    - последователен поток в паралелен: чрез методa `parallel()`
    - паралелен поток в последователен: чрез методa `sequential()`
- Междинните операции се изпъляват *lazily*
- Терминалните операции се изпъляват *eagerly*

@ulend

---

#### Stream vs Collection

@ul

- Потоците не са алтернатива на колекциите
- Колекциите са отговорни за съхранение и достъп до данни

@ulend

---

#### Особености на Stream

@ul

- нямат собствено хранилище, а използват източник на данни (колекция, файл и т.н.)
- функционална същност – не модифицират вътрешните данни
- колекциите винаги имат краен брой елементи, докато Stream може да бъде безкраен
- елементите могат да се "консумират" само веднъж, подобно на итератор
- позволяват lazy операции
- позволяват паралелно изпълнение на операциите

@ulend

---

#### Stateless и stateful операции върху потоци

@ul

- Stream операциите могат да се разделят на *stateless* и *stateful*.
- Stateless операциите не съхраняват данни между обработката на отделните елементи на потока
    - `filter()`, `map()`, `flatMap()`
- Stateful операциите могат да предават състояние от вече обработените елементи към обработката на следващия
    - `distinct()`, `limit()`, `sorted()`, `reduce()`, `collect()`

@ulend

---

#### Паралелно изпълнение на stream операциите

@ul

- Stateless операциите не представляват проблем при паралелно изпълнение
- Stateful операциите
    - (без `limit()`), приложени към безкраен поток, не завършват никога
    - могат да дадат различен резултат според това дали се изпълняват последователно или паралелно
    - имат performance impact, защото често изискват обработка на всички елементи на няколко паса

@ulend

---

#### Паралелно изпълнение на stream операциите

@ul

- Малките потоци обикновено се обработват по-бързо последователно
- Ако stateful операциите не могат да се заменят със stateless, кодът трябва внимателно да се проектира за паралелно изпълнение, или да се избегне паралелизма

@ulend

---

#### Функции от по-висок ред

@ul

- Функции, които приемат като аргумент функция или връщат функция като резултат, се наричат *функции от по-висок ред*
- Функциите от по-висок ред ни предоставят средство, с което да композираме логика, комбинирайки функции

@ulend

---

#### Въпроси от студенти

@ul

- Как да извикаме чрез method reference overloaded методи и конструктори? [Отговор](https://github.com/fmi/java-course/tree/master/08-lambdas-and-stream-api/snippets/MethRefExample.java)
- `flatmap()` на произволна дълбочина (т.е. рекурсивно) ли работи?
- Как се обработват изключения по време на изпълнение на stream pipeline?
- Може ли да се направи stream от (инстанции на) анонимен клас?

@ulend

---

#### Полезни четива

- [The Java 8 Stream API Tutorial](https://www.baeldung.com/java-8-streams)
- [Package java.util.stream](https://docs.oracle.com/en/java/javase/15/docs/api/java.base/java/util/stream/package-summary.html)
- [Package java.util.function](https://docs.oracle.com/en/java/javase/15/docs/api/java.base/java/util/function/package-summary.html)

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend


## Многонишково програмиране с Java

_09.12.2020_

---

#### Предната лекция говорихме за:

@ul

- Lambda изрази
- Stream API

@ulend

---

#### Днес ще разгледаме:

@ul

- Concurrent и паралелно изпълнение на програми
- Многонишково програмиране (Multithreading)
    - Нишки и техния жизнен цикъл
    - Атомарни типове данни
    - Комуникация и синхронизиране между нишки

@ulend

---

![Meaning of Concurrent](images/09.0-meaning-of-concurrent.png)

---

#### Concurrency

<small>
@ul

- Concurrency е способността да се прави повече от едно нещо в един и същи момент
  - т.е. множество задачи започват, изпълняват се и приключват, в припокриващи се времеви периоди, в непредсказуем ред
  - например, мога да редактирам документ, докато слушам музика от друго приложение и свалям файл от Интернет от трето, *едновременно*
- Concurrency не предполага непременно няколко приложения. Едновременното изпълнение на части от едно приложение, също се нарича concurrency
  - например, текстов редактор форматира текста, прави spell-checking и respond-ва на keyboard events, *едновременно*

@ulend
</small>

---

#### Units of Concurrency

<small>
Concurrency е много общ термин и може да се използва на различни нива.

@ul

- *Multiprocessing* - много процесори, изпълняващи инструкции concurrently. Единицата е процесор (CPU)
- *Multitasking (Многозадачност)* - много задачи/процеси, изпълняващи се едновременно на един процесор. Единицата е процес
- *Multithreading (Многонишковост)* - множество части на една и съща програма се изпъляват concurrently. Единицата е нишка

@ulend
</small>

---

#### Процеси и нишки

<small>
@ul

- *Процес* е програма по време на изпълнение
    - има си собствено адресно пространство, call stack и handles към ресурси (например, отворени файлове)
- *Нишка* е път на изпълнение вътре в процес
    - всеки процес има поне една нишка, наричана *main*
    - всяка нишка може да създава допълнителни нишки
    - нишките в един процес споделят ресурсите му, в частност, памет или отворени файлове. Всяка нишка обаче си има собствен call stack

@ulend
</small>

---

#### Процеси и нишки

<small>

|               | Процеси     | Нишки             |
|:------------- |:------------|:----------------- |
| Стартиране    | Бавно       | Относително бързо |
| Изолация      | Да          | Не                |
| Комуникация   | Бавна       | Бърза             |

</small>

---

#### Concurrency: кратка история

@ul

- древното минало: преди появата на операционните системи
- еднозадачни операционни системи
- многозадачни операционни системи. Процеси. Комуникация между процеси
    - утилизиране на ресурсите
    - fairness
    - удобство
- едно- и многопроцесорни системи, hyper-threading (2002), многоядрени процесори (2005)

@ulend

---

![Multi-Core CPUs](images/09.1-multi-core-cpus.png)

---

#### Concurrent vs. паралелно изпълнение

<small>

@ul

- Concurrency не предполага непременно паралелно изпълнение
- Когато казваме "множество задачи, изпълняващи се едновременно", всъщност имаме предвид "множество задачи, прогресиращи през един и същи времеви интервал"
    - ОС превключва между задачите толкова често, че за потребителя изглежда, че тe се изпълняват едновременно, в един и същ физически момент
    - Всъщност, паралелно изпълнение е невъзможно на компютър с единствен (single-core, без hyperthreading) процесор
@ulend

</small>

---

![Multi-threading](images/09.2-multithreading.png)

---

![Concurrent vs. Parallel Execution](images/09.2.1-concurrent-parallel.png)

---

#### Ползи от многонишковостта

- Съществено увеличена производителност на програмите, чрез пълноценна употреба (utilization) на наличните ресурси, като CPU
- Подобрено потребителско изживяване (more responsive UIs)
- По-проста архитектура
    - сложен, асинхронен workflow може да се декомпозира до няколко прости, последователни workflows, изпълнявани в отделни нишки

---

#### Проблеми, свързани с concurrency

<small>
@ul

- Thread interference (Race Conditions)
    - когато множество нишки едновременно четат и пишат споделенни данни и тези операции се припокриват във времето
    - тогава резултатът зависи от реда на четенията и писанията, който е непредвидим
- Memory inconsistency
   - когато различни нишки "виждат" по различен начин едни и същи данни в един и същи момент
   - случва се, когато една нишка промени стойността на някаква споделена данна, но тази промяна не е "стигнала" до другите нишки, които продължават да виждат старата стойност
   - причината е, че компилаторът, JVM-ът и CPU-то правят оптимизации (разместват инструкции, кешират стойности от RAM паметта в регистри или кеш на CPU и т.н.)

@ulend
</small>

---

#### Проблеми, свързани с multithreading

@ul

- Кодът става по-сложен и неинтуитивен
- Ползваме повече ОС ресурси за многото нишки, например памет
- Нов източник на трудни за репродуциране и дебъгване грешки, поради race conditions и memory inconsistency
- [*Liveness*](https://en.wikipedia.org/wiki/Liveness), [*Starvation*](https://en.wikipedia.org/wiki/Starvation_(computer_science)) и *Performance* рискове
- Многонишкови фреймуърци като "черна кутия"

@ulend

---

#### Управление на нишки в Java

@ul

- жизнен цикъл: създаване, стартиране, изпълнение, приключване
  - текущо състояние
- синхронизация
- комуникация между нишки

@ulend

---

#### Създаване на нишка

@ul

- Всяка Java програма при стартирането си съдържа една нишка (main)
- За да създадем нова нишка в Java, наследяваме класа `java.lang.Thread` или имплементираме интерфейса `java.lang.Runnable`
- Логиката (инструкциите за изпълнение) е в метода `run()`

@ulend

---

#### Създаване на нишка

```java
// Option 1: extend java.lang.Thread
public class CustomThread extends Thread {
    public void run() {
        System.out.println("Hello world!");
    }
}

Thread customThread = new CustomThread();

// Option 2: implement java.lang.Runnable
public class CustomRunnable implements Runnable {
    public void run() {
        System.out.println("Hello world, from a Runnable!");
    }
}

Thread customThread = new Thread(new CustomRunnable());
```

---

#### Създаване на нишка

```java
public class CustomRunnable implements Runnable {
    public void run() {
        System.out.println("Hello world, from a Runnable!");
    }
}

Thread customThread = new Thread(new CustomRunnable());

Thread customThread2 = new Thread() {
    @Override
    public void run() {
        System.out.println("Hello world, from an anonymous class!");
    }
};

Thread customThread3 =
    new Thread(() -> System.out.println("Hello world, from a lambda!"));
```

---

#### Стартиране на нишка

- За да стартираме нишка, трябва
  - да извикаме метода `start()`
    - който вътрешно ще извика `run()`

---

#### Спиране на нишка

@ul

- Нишка не може да бъде спряна експлицитно, веднъж щом е стартирана
- Нишката прекратява изпълнението си автоматично след приключването на метода `run()`
- Нишката не може да бъде стартирана повторно

@ulend

---

#### `Thread` vs. `Runnable`

При употреба на `Runnable` сме по-гъвкави:

@ul

- можем да наследим друг клас
- можем да решим да изпълним имплементацията в:
  - нова нишка (като извикаме `start()`)
  - чрез thread pool (ще научим по-късно какво е това)
  - в текущата нишка (като извикаме директно `run()`)

@ulend

---

#### Thread API

<small>
Можем да дадем human-readable име на нишка чрез `setName()`. Имената нe са уникални.
Също така, нишките могат да се групират логически чрез `ThreadGroup`. Групата може да се задава само чрез конструктора.

</small>

```java
customThread.setName("Cool thread #1");

// Конструктор, който приема група и име
ThreadGroup coolThreads = new ThreadGroup("Cool thread group");
coolThread1 = new Thread(coolThreads, "Cool thread #1"); 
coolThread2 = new Thread(coolThreads, "Cool thread #2");
```

---

#### Thread API

```java
// Паузиране – нишката „заспива“ и не получава процесорно време
// за определен интервал време
Thread.sleep(long milliseconds)

// Референция към текущата нишка
Thread.currentThread()

// Stack trace-ът на нишката
Thread.getStackTrace()
```

---

#### Приоритет на нишки

```java
// Подсказка към диспечера на нишки, каква част от процесорното
// време да получи дадена нишка. Скалата е от 1 до 10.
// По-малко число означава по-висок приоритет
// Приоритетът по подразбиране е 5
void setPriority(int prio)

// Подсказка към диспечера на нишки, че текущата нишка се отказва
// от своето процесорно време в полза на друга,
// чийто приоритет е минимум колкото този на текущата
void yield()

// NB!
// Добре написано приложение не трябва да разчита на
// приоритетите на нишки или на yield за своята коректност
```

---

#### Присъединяване към друга нишка

Дадена нишка може да паузира изпълнението си, докато друга нишка приключи, чрез метода `join()`

![Thread Join](images/09.3-thread-join.png)

---

#### Присъединяване към друга нишка

```java
// Извикващата нишка блокира, докато нишката,
// на която е извикала join(), приключи
void join()

// Ако нишката приключи или зададеното време изтече,
// извикващата нишка ще продължи изпълнението си
void join(long millis)

// Можем да проверим, дали дадена нишка не е приключила изпълнението си
boolean isAlive()
```

---

#### Daemon нишки

@ul

- Според режима на работа, нишките в Java могат да бъдат два вида:
    - Стандартни (non-daemon) нишки
    - Демон (daemon) нишки

@ulend

---

#### Стандартни нишки

@ul

- изпълняват задачи, които са свързани с основната идея на програмата
- всяка JVM работи, докато има поне една работеща стандартна нишка

@ulend

---

#### Daemon нишки

<small>
- изпълняват задачи, които не са жизненоважни за програмата 
- JVM ще прекрати работата на нишките от този тип, ако няма поне една работеща стандартна нишка
- Нишките наследяват режима на работа от тази, която ги е създала, или го задават експлицитно


</small>


```java
// Може да сменим режима на нишка чрез:
void setDaemon(boolean flag)
```

---

#### Състояние на нишка

- Нишката може да бъде в различно състояние в даден момент от изпълнението си
- Методът `getState()` ни дава възможност да проверим моментното състояние на нишка

---

![Thread States](images/09.4-thread-states.jpg)

---

#### Thread.State

enum, съдържащ всички възможни състояния:

- NEW
- RUNNABLE
- BLOCKED
- WAITING
- TIMED_WAITING
- TERMINATED

---

#### Thread Safety

@ul

- Основна концепция в многонишковото програмиране
- Клас е thread-safe, ако работи коректно при conncurrent достъп от множество нишки
- Касае управлението на достъпа до състоянието на обектите
    - по-конкретно, на shared & mutable състоянието

@ulend

---

#### Thread Safety

@ul

- thread safety цели защитата на данните от неконтролиран concurrent достъп
- thread-safe класовете енкапсулират евентуалната необходима синхронизация, така че ползвателите им да не се грижат за нея

@ulend

---

#### Thread Safety

@ul

- Когато повече от една нишка достъпва състоянието на обект и поне една нишка може да го промени, всички тези нишки трябва да синхронизират достъпа си до това състояние
- Енкапсулацията и data hiding помагат за thread safety

@ul

---

#### Атомарност (Atomicity)

- Атомарни vs. съставни (compound) операции
- *race conditions*

---

#### Примери за race condition

- race condition тип *check-then-act*
    - lazy инициализация
- race condition тип *read-modify-write*
    - инкрементиране на брояч

---

#### Примери за race condition

```java
// check-then-act race condition
if (ref == null) {
    ref = new Something();
}
return ref;

// read-modify-write race condition
i++; // this is equivalent to i = i + 1,
     // which in fact consists of three operations
```

---

#### Атомарни типове данни

@ul

- Класове в `java.util.concurrent.atomic` пакета
- Предоставят атомарни имплементации на примитивните типове, масиви от примитивни типове и абстракция за атомарна референция
- `AtomicBoolean`, `AtomicInteger`, `AtomicLong`, `AtomicIntegerArray`, `AtomicLongArray`, `AtomicReference<ActualType>`

@ulend

---

#### Атомарни типове данни

@ul

- Предоставят възможност за атомарни съставни операции
- Използват специални CPU инструкции (“compare-and-swap”, CAS), които позволяват избягването на синхронизация чрез ключалки, което ги прави много бързи

@ulend

---

#### Атомарни операции

```java
// Всички имплементации имат методи get() и set() за достъп до
// съхраняваната променлива.
AtomicInteger atomicInt = new AtomicInteger();
atomicInt.set(2020);
System.out.println(atomicInt.get()); // 2020
```

---

#### Примери за атомарни операции

```java
// thread-safe вариант на ++i (i=i+1)
System.out.println(atomicInt.incrementAndGet()); // 2021

// thread-safe вариант на i += x (i=i+x)
System.out.println(atomicInt.addAndGet(5)); // 2026

AtomicReference<String> atomicRef = new AtomicReference<>();
// atomicRef не е null, но стойността, която съдържа (wrap-ва), е

// thread-safe вариант на if (ref == expected) { ref = update; }
// NB! Сравняваме референции затова използваме `==`, а не equals
atomicRef.compareAndSet(null, "Happy new year!");
System.out.println(atomicRef); // Happy new year!
```

---

#### Concurrent достъп до споделени ресурси

---

#### Синхронизирана (Критична) секция

@ul

- Когато две или повече нишки достъпват concurrently даден ресурс, който може да бъде променян, е необходима синхронизация
- Постига се чрез ключовата дума `synchronized`. Секцията се cъстои от:
    - монитор – логическа „ключалка“
    - блок код, който ще се изпълни ексклузивно от една нишка за даден монитор

@ulend

---

#### Синхронизирана секция

```java
public void depositMoney(BankAccount acc, double amount) {
    // Критична секция – една-единствена нишка за дадена сметка
    // acc може да изпълнява кода в синхронизираната секция
    synchronized (acc) {
        acc.deposit(amount);
    }

    // Не-критична секция - много нишки могат да бъдат едновременно тук
    System.out.println("Deposit completed");
}
```

---

#### Синхронизирана секция

@ul

- Всеки обект има вътрешен имплицитен монитор (ключалка, lock) т.е. може да се ползва за монитор
- Само една нишка в даден момент за даден монитор може да изпълнява кода (mutex == mutual exclusion)
- всеки достъп до дадено състояние, което може да бъде променено от друга нишка, трябва винаги да става в синхронизирана секция по един и същ монитор

@ulend

---

Мониторът се управлява имплицитно от JVM:

@ul

- при влизане, ако е свободен, се маркира за „зает“ от съответната нишка
- при влизане, ако не е свободен, нишката блокира и чака
- при излизане, lock-ът се освобождава и, ако има блокирани нишки, те могат да се опитат да вземат ключалката

@ulend

---

#### Синхронизиран метод

<small>Много често искаме да поставим цялото тяло на даден метод в критична секция. С цел по-четим код, Java ни предлага по-сбит вариант.</small>

```java
public void doSomeWork() {
    synchronized (this) {
        // Критична секция - само една нишка може да
        // изпълнява кода за конкретната инстанция 'this'
    }
}

public synchronized void doSomeWork() { 
    // Критична секция - само една нишка може да 
    // изпълнява кода за конкретната инстанция 'this' 
}
```

---

#### Синхронизирана секция или метод?

- Методът ce препоръчва само ако е достатъчно кратък (и бърз за изпълнение) и наистина има нужда цялото тяло да бъде „охранявано"
- Синхронизираната секция е за предпочитане, когато:
    - нуждаещото се от синхронизация парче код е малка част от метод
    - искаме да ползваме монитор, различен от `this`

---

#### Рекурсивност

<small>Lock-ът е рекурсивен (reentrant): нишката, която го „притежава“, може да извиква други критични секции по същия монитор.</small>

```java
class Demo {
    public void method1() {
        synchronized (this) {
            // изпълняващата нишка вече притежава lock-а,
            // следователно може да извика method2()
            method2();
        }
    }

    public synchronized void method2() {
    }
}
```

---

#### Използване на монитор, различен от `this`

<small>
- Може да изберем да синхронизираме достъпа в дадена инстанция на обект чрез член-променлива, създадена с целта, да се използва като ключалка
- понякога даден клас има нужда от различни монитори за "охраняване"" на различно състояние

</small>

```java
private final Object dedicatedMonitor = new Object();
```

---

#### Използване на няколко монитора

<small>Една нишка може да „притежава“ много на брой монитори, стига те да са свободни:</small>

```java
// Държането на няколко ключалки е лоша практика и 
// при възможност трябва да се избягва
public void multipleLocks() {
    synchronized (lock1) {
        // нишката притежава lock1
        synchronized (lock2) {
            // нишката притежава lock1 & lock2
            synchronized (lock3) {
                // нишката притежава lock1, lock2 & lock3
            }
            // нишката притежава lock1 & lock2
        }
        // нишката притежава lock1
    }
}
```

---

#### Синхронизация между множество инстанции на клас

@ul

- Подходящо е да ползваме ключалка, обща за класа
- удобно е да ползваме статична променлива за монитор

@ulend

---

<small>
Всяка инстанция на клас има статична референция към обекта на класа, към който принадлежи. Можем да я достъпим чрез:
</small>

```java
BankAccount.class // статично
this.getClass() // чрез ‘this’
```

---

#### Статични синхронизирани методи

```java
static void incrementOpCount() {
    synchronized (BankAccount.class) {
        opCount++;
    }
}

static synchronized void incrementOpCount() {
    opCount++;
}
```

---

#### Thread-safe обекти

Някои обекти са thread-safe по подразбиране:
- Локални обекти (локални променливи на метод)
- Stateless обекти
- Immutable обекти
- Обекти, които са ефективно final (read-only)

---

#### Съставни операции

Ако комбинираме няколко thread-safe операции в една по-сложна (обща), нямаме никаква гаранция, че те ще се изпълнят атомарно

---

```java
public synchronized void withdraw(double amount) {
    this.balance -= amount;
}

public synchronized double getBalance() {
    return balance;
}

// Бъг - този метод също трябва да е синхронизиран
public void verifyAndWithdraw(double amount) {
    if (getBalance() >= amount) {
        withdraw(amount);
    }
}
```

---

#### Мъртва хватка (Deadlock)

<small>Получава се, когато две или повече нишки се блокират една друга, всяка от тях притежаваща ключалка, от която друга нишка има нужда, но чакайки за ключалка, която някоя от другите нишки притежава.</small>

![deadlock](images/09.5-deadlock.jpg)

---

#### Мъртва хватка (Deadlock)

- Нишките не могат да бъдат прекратявани отвън
- Ключалките не могат да бъдат отнемани насилствено
- Единственият изход от мъртва хватка, е рестартиране на JVM

---

#### Предотвратяване на deadlock

@ul

- мониторите да се вземат винаги в същия ред
- използване на един общ монитор
- избягваме да притежаваме повече от един монитор
- подреждаме мониторите спрямо някакъв признак

@ulend

---

### Комуникация между нишки

---

#### Busy wait

<small>Неефективен (и възможно некоректен) начин за комуникация е т.нар. *busy wait*: в цикъл изчакваме събитието да се случи</small>

```java
// Всеки месец се пуска нова нишка, която тегли сумата на месечната вноска
// от сметката на кредитополучателя
public void withdrawCreditPayment(double monthFee) {
    while (this.balance < monthFee) {
        // Стоим в цикъла, докато няма достатъчно пари да погасят вноската
        Thread.sleep(1_000);
    }
    balance -= monthFee;
}
```

---

#### Изчакване чрез `wait()`

```java
// Нишка може да заяви, че иска да изчака, докато дадено събитие се случи
// в друга нишка, чрез метода wait() на java.lang.Object
public synchronized void withdrawCreditPayment(double monthFee) {
    while (this.balance < monthFee) {
        try {
            // Изчакваме и освобождаваме монитора this
            this.wait();
        } catch (InterruptedException e) {
            // хвърля изключение, ако нишката бъде прекъсната
        }
    }
    balance -= monthFee;
}
```

---

#### `java.lang.Object.wait()`

@ul

- извикването на `wait()` винаги става в критична секция по обекта, който ползваме за монитор
- в противен случай се хвърля `java.lang.IllegalMonitorStateException`
- `wait()` освобождава текущия монитор и нишката преминава в статус `WAITING`

@ulend

---

#### `java.lang.Object.wait()`

@ul

- Възможно е да извикаме `wait()` с аргумент за време – по този начин нишката ще се събуди, ако бъде известена или времето изтече
- Винаги след събуждане, трябва да проверяваме в цикъл дали събитието, за което сме чакали, в действителност е настъпило: шаблон, известен като *guarded wait*

@ulend

---

#### Известяване чрез `notify()`

```java
// Нишка може да извести чакащи нишки, че дадено събитие се е случило
// и те могат да продължат своето изпълнение. Това става чрез метода
// notify() на java.lang.Object

// При депозиране на пари по сметка, уведомяваме чакащите нишки,
// че са постъпили средства по сметката
public synchronized void deposit(double amount) {
    this.notify();
    this.balance += amount;
}
```

---

#### `java.lang.Object.notify()`

@ul

- Събужда една нишка, чакаща за съответния монитор
- Извикването на `notify()` винаги става в критична секция по обекта, който ползваме за монитор
- не освобождава монитора

@ulend

---

#### `notify()` vs. `notifyAll()`

<small>
- `notify()` – събужда една произволна нишка, чакаща за този монитор. Полезно е само когато сме сигурни, че само една нишка може да продължи изпълнението си, и не искаме да „платим“ цената да събудим всички
- `notifyAll()` – събужда всички нишки. В много случаи, повече от една нишка може да продължи действието си след известяването си. Нишките се изпълняват последователно в синхронизираната секция по монитора след събуждането си

</small>

---

#### `notify()` vs. `notifyAll()`

<small>
- Ако имаме няколко чакащи нишки за текущия монитор, нямаме възможност да кажем коя/кои нишки да бъдат събудени или да бъдат събудени първи
- В практиката по-често се ползва `notifyAll()`. Правилно имплементирана проверка в `while` може да ни гарантира същото поведение като при `notify()` – макар и събудени повече нишки – те ще заспят отново, след като видят, че не могат да продължат

</small>

---

#### Прекъсване на нишка

<small>
- Eдна нишка може да съобщи на друга да спре изпълнението си
- Какво действие ще се извърши в нишката, зависи изцяло от програмиста, възможно е сигналът да се игнорира
- Нишката може да провери дали е била прекъсната
- Някои методи, например `sleep()` или `join())` хвърлят изключение `java.lang.InterruptedException`, когато нишката e получила сигнал за прекъсване, докато те се изпълняват

</small>

```java
customThread.interrupt()

Thread.interrupted() // изчиства флага след прочитането (статичен)
isInterrupted() // не изчиства флага (не-статичен)
```

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend



## Многонишково програмиране с Java (част II)

_16.12.2020_

---

#### Предната лекция говорихме за:

@ul

- Concurrent и паралелно изпълнение на програми
- Многонишково програмиране (Multithreading)
    - Нишки и техния жизнен цикъл
    - Атомарни типове данни
    - Комуникация и синхронизиране между нишки

@ulend

---

#### Днес ще разгледаме:

@ul

- Thread pools / Executors API
- Concurrent колекции
- Мрежово програмиране

@ulend

---

#### Runnable vs. Callable

```java
// java.lang
@FunctionalInterface
public interface Runnable {

    public abstract void run();

}

// java.util.concurrent
@FunctionalInterface
public interface Callable<V> {

    V call() throws Exception;

}
```

---

#### Future<V>

```java
// java.util.concurrent
public interface Future<V> {

    boolean cancel(boolean mayInterruptIfRunning);

    boolean isCancelled();

    boolean isDone();

    V get() throws InterruptedException, ExecutionException;

    V get(long timeout, TimeUnit unit)
        throws InterruptedException, ExecutionException,
               TimeoutException;

}
```

---

#### Преизползване на нишки

---

#### Thread pool (Executor)

<small>
- Kонцепция в многонишковото програмиране, при която „рециклираме“ нишките след края на тяхното изпълнение, с цел оптимизация.
- Отделните `Runnable` или `Callable` обекти се третират като „задачи“ и се трупат в опашка, и когато има свободни нишки в pool-а, те изпълняват задачите, на базата на зададени правила.

</small>

![test](https://upload.wikimedia.org/wikipedia/commons/0/0c/Thread_pool.svg)

---

#### Executors API

```java
// централен интерфейс
java.util.concurrent.Executor
void execute(Runnable command)

// добавя възможност и за изпълнение на Callable обекти,
// които, за разлика от Runnable, могат да върнат резултат
java.util.concurrent.ExecutorService
<T> Future<T> submit(Callable<T> task)

// задачите могат да се пускат след опредено закъснение
// или периодично на зададен интервал
java.util.concurrent.ScheduledExecutorService
ScheduledFuture schedule(Runnable r,long delay, TimeUnit tu)
ScheduledFuture scheduleAtFixedRate(Runnable r, long delay, 
                                    long period, TimeUnit tu)
```

---

#### Създаване на Executor

```java
// предоставя статични factory методи за създаването на pools от нишки
java.util.concurrent.Executors

// pool-ът ще се състои само от една нишка, следователно
// задачите ще се изпълняват последователно
static ExecutorService newSingleThreadExecutor()

// създава pool, който ще се състои от фиксиран брой нишки.
// Ако в опашката има повече задачи, отколкото налични нишки,
// задачите не се обработват, докато не се освободи нишка
static ExecutorService newFixedThreadPool(int n)

// създава pool от нишки, който ще преизползва нишките,
// ако има налични, в противен случай ще направи нова.
// Нишките, които не се използвани през последната минута,
// ще бъдат премахнати
static ExecutorService newCachedThreadPool()

// pool, който изпълнява задачи периодично или със закъснение
static ScheduledExecutorService newScheduledThreadPool(int size)
```

---

#### Спиране на Thread pool

Executor обект винаги трябва да бъде експлицитно спрян с метода `shutdown()`

---

#### Thread-safe колекции: Синхронизирани колекции

- Collections API предоставя имплементации на няколко синхронизирани колекции като `
Vector` и `Hashtable`
- `java.util.Collections` предоставя factory метод, с който можем да създадем synchronized колекция от съществуваща обикновена колекция
- Синхронизираните колекции обаче не са достатъчно бързи при много едновременни ползватели и не предоставят възможност за атомарни операции

<br/>

```java
static <T> Collection<T> synchronizedCollection(Collection<T> c)
```

---

#### Thread-safe колекции: Concurrent колекции

- намират се в пакета `java.util.concurrent`
- създадени са специално за работа в concurrent среда
- добавят възможности за
  - Lock-free паралелен достъп
  - Fail-safe итератори
  - Атомарни операции (например, `putIfAbsent()`)

---

#### `CopyOnWriteArrayList`

- Алтернатива на синхронизираните имплементации на `ArrayList`
- Позволява lock-free паралелно четене
- “Fail-safe snapshot” итератор
- Всяка модификация предизвиква копиране на масива
- Атомарни операции: `boolean addIfAbsent(E e);`
- Използването на тази структура е подходящо, само когато броят на четенията от масива значително надвишава броя на модификациите. В противен случай, структурата е изключително неефективна

--- 

#### `ConcurrentHashMap`

- Алтернатива на синхронизираните версии на `java.util.HashMap`
- Паралелен lock-free достъп за четене
- Паралелен (но лимитиран) достъп за писане 
- Fail-safe и “Weakly consistent“ итератор
- Атомарни операции: `V putIfAbsent(K key, V value)`
- Най-популярната колекция от `java.util.concurrent` библиотеката, почти винаги е подходяща да се използва за замяната на старите синхронизирани варианти на `HashMap`

--- 

#### `BlockingQueue`

Имплементация на блокираща опашка (“Producer-Consumer” опашка).
Блокира, когато:
- опашката е празна и някой се опитва да чете от нея. При първи запис, бива нотифицирана
- oпашката е пълна и някой се опитва да пише в нея. При първо четене, бива нотифицирана
- `ArrayBlockingQueue` – основна имплементация. Опашката пази елементите си в масив, който не може да променя размера си.

<br/>

```java
BlockingQueue<String> queue = new ArrayBlockingQueue<>(4);
```

---

#### Multi-threading теми извън обхвата на курса

- Visibility & stale data. Volatile variables. Nonatomic 64-bit operations
- Explicit locks
- Synchronizers: Latches, Semaphores, Barriers

---

![Java Concurrency in Practice](images/09.6-java-concurrency-in-practice.jpg)

---

![dogs-meme](https://cdn-images-1.medium.com/max/1600/0*9LJYn6Tlc8q3qA3U.png)

---

## Мрежово програмиране с Java

_16.12.2020_

![Networking](images/10.0-networking.jpg)

---

#### Теми, които ще разгледаме

- Мрежови модели: клиент-сървър, peer-to-peer
- Мрежови протоколи
   - IP, UDP, TCP
- Мрежова комуникация в Java
    - blocking
    - non-blocking
- Network scalability

---

#### Модел Клиент-Сървър

<small>Клиент-сървър е разпределен изчислителен модел, при който част от задачите се разпределят между доставчиците на ресурси или услуги, наречени сървъри и консуматорите на услуги, наречени клиенти</small>

![Client-Server](images/10.4-client-server.png)

---

#### Модел Peer-to-peer

<small>
Peer-to-peer е разпределен архитектурен модел на приложение, при който задачите се разпределят по еднакъв начин между всички участници (peer, node). Всеки участник е едновременно и клиент, и сървър.</small>

![Peer-to-Peer](images/10.5-peer-to-peer.png)

---

#### Видове клиенти

- Според наличната функционалност в клиента:
    - Rich клиенти
    - Thin клиенти
- Според семантиката (протокола):
    - Web клиенти – Браузъри (Chrome, Firefox, IE).
    - Mail клиенти – POP/SMTP клиенти (MS Outlook, Lotus notes).
    - FTP клиенти – Total Commander, Filezilla, WinSCP.
    - …

---

#### Видове сървъри

- Файл сървър (Windows, Samba, UNIX NFS, OpenAFS)
- DB сървър (MySQL, PostgreSQL, Oracle, MS SQL Server, Mongo DB)
- Mail сървър (MS Exchange, GMail)
- Name сървър (DNS)
- FTP сървър (ftpd, IIS)
- Print сървър
- Game сървър
- Web сървър (Apache, GWS, MS IIS, nginx)
- Application сървър (Tomcat, TomEE, GlassFish, JBoss)
- ...

---

#### Предимства и недостатъци на Клиент-Сървър

- Висока сигурност: контролът за достъп до данните се осъществява на едно място: сървъра
- Консистентност на данните: всички клиенти в даден момент достъпват едни и същи данни
- Промени в данните се разпространяват много бързо в мрежата: при първото извикване от клиент към сървъра
- Single Point Of Failure (SPOF): ако сървърът е down, никой в мрежата не може да комуникира
- Увеличаването на броя на клиентите води до намаляване на производителността
- 70-95% от времето, през което работи, сървърът е idle

---

#### Предимства и недостатъци на Peer-to-Peer

- Няма SPOF
- Няма намаляване на производителността при увеличаване на броя на клиентите
- Проблеми със сигурността: има копия на даните из цялата мрежа
- Риск от умишлена промяна (подмяна) на съдържанието и различни версии на данните в различни възли на мрежата
- Липса на контрол върху съдържанието и възможност за загуба на съдържание
- Труден процес на поддръжка

---

#### Open Systems Interconnection (OSI) модел

![OSI Model](images/10.1-osi-model.png)

---

#### OSI модел: мрежови протоколи

<table style="font-size:0.5em; line-height=0.7em;">
  <tr>
    <th>#</th>
    <th>Слой</th>
    <th>Описание</th>
    <th>Протоколи</th>
  </tr>
  <tr>
    <td>7</td>
    <td>Application</td>
    <td>Позволява на потребителските приложения да заявяват услуги или информация, а на сървър приложенията — да се регистрират и предоставят услуги в мрежата.</td>
    <td>DNS, FTP, HTTP, NFS, NTP, DHCP, SMTP, Telnet</td>
  </tr>
  <tr>
    <td>6</td>
    <td>Presentation</td>
    <td>Конвертиране, компресиране и криптиране на данни.</td>
    <td>TLS/SSL</td>
  </tr>
  <tr>
    <td>5</td>
    <td>Session</td>
    <td>Създаването, поддържането и терминирането на сесии. Сигурност. Логически портове.</td>
    <td>Sockets</td>
  </tr>
  <tr>
    <td>4</td>
    <td>Transport</td>
    <td>Грижи се за целостта на съобщенията, за пристигането им в точна последователност, потвърждаване за пристигане, проверка за загуби и дублиращи се съобщения.</td>
    <td>TCP, UDP</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Network</td>
    <td>Управлява пакетите в мрежата. Рутиране. Фрагментация на данните. Логически адреси.</td>
    <td>IPv4, IPv6, IPX, ICMP</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Data Link</td>
    <td>Предаване на фреймове от един възел на друг. Управление на последователността на фреймовете. Потвърждения. Проверка за грешки. MAC.</td>
    <td>ATM, X.25, DSL, IEEE 802.11</td>
  </tr>
  <tr>
    <td>1</td>
    <td>Physical</td>
    <td>Отговаря за предаването и приемането на неструктурирани потоци от данни по физическия носител. Кодиране/декодиране на данните. Свързване на физическия носител.</td>
    <td>IEEE 802.11, IEEE 1394, Bluetooth</td>
  </tr>
</table>

---

#### java.net | Въведение

<small>Пакетът `java.net` предоставя класове, които използват и работят на различни нива от OSI модела.</small>

- Мрежов и data link слой
    - класът `NetworkInterface` предоставя достъп до мрежовите адаптери на компютъра
    - IP адреси - класът `InetAddress`
- Транспортен слой
    - TCP - класове `Socket` и `ServerSocket`
    - UDP - класове `DatagramPacket`, `DatagramSocket` и `MulticastSocket`
- Приложен слой
    - класовете `URL` и `URLConnection` за достъпването на HTTP и FTP ресурси
    - (от Java 11) класовете от пакета `java.net.http` за по-удобна работа с HTTP. Ще ги разгледаме на следващата лекция

---

#### java.net | Мрежови адаптери

- Мрежовият адаптер осъществява връзката между компютърна система и мрежа
- Мрежовите адаптери могат да бъдат физически или виртуални (софтуерни). Примери за виртуални са *loopback* интерфейсът и интерфейсите, създадени от виртуалните машини
- Една система може да има повече от един физически и/или виртуален мрежови адаптер
- Java предоставя достъп до всички мрежови адаптери чрез класа `java.net.NetworkInterface`

---

#### IP адрес

- Всеки компютър, свързан към мрежа, се идентифицира с логически адрес
- Най-разпространените протоколи за логически адреси в мрежата са IP (Internet Protocol) версия 4 и IP версия 6
- Адресите в IPv4 представляват 32-битови числа, а в IPv6 - 128-битови

<br/>

![IP v4 v6](images/10.2-ipv4-ipv6.png)

---

#### Портове

- В общия случай, компютърът има една физическа връзка към мрежата. По тази връзка се изпращат и получават данни от/за всички приложения. Портовете се използват, за да се знае кои данни за кое приложение са
- Предадените данни по мрежата винаги съдържат в себе си информация за компютъра и порта, към които са насочени
- Портовете се идентифицират с 16-битово число, което се използва от UDP и TCP протоколите, за да идентифицират за кое приложение са предназначени данните
- Портовете могат да бъдат от номер 0 до номер 65 535
- Портове с номера от 0 до 1023 са известни като *well-known ports*. За да се използват тези портове от вашето приложение, то трябва да се изпълнява с администраторски права

---

#### Адресиране в мрежата | `java.net.InetAddress`

<small>
- Инстанции се създават чрез статични методи на класа
- С `NetworkInterface`, може да вземете списък с всички мрежови адаптери или точно определен

</small>

```java
// създава инстанция по hostname или по текстово представяне на IP адрес
InetAddress address = InetAddress.getByName​("www.google.com");
System.out.println(address.getHostAddress()); // 172.217.169.164

InetAddress address = InetAddress.getByName("62.44.101.138");
System.out.println(address.getHostName()); // www.fmi.uni-sofia.bg
System.out.println(address.isReachable(5_000)); // true
InetAddress localhost = InetAddress.getLocalHost();

Collections.list(NetworkInterface.getNetworkInterfaces())
           .stream()
           .forEach(n -> {
                System.out.println("Disp. name: " + n.getDisplayName());
                System.out.println("Name: " + n.getName());
           });
```

---

#### Сокети (sockets)

- UDP и TCP се имплементират чрез *сокети* (*sockets*)
- Сокетите представляват крайните точки на двупосочна мрежова връзка (connection) между две приложения
- Всеки сокет се идентифицира чрез комбинация от IP адрес и номер на порт

---

#### UDP протокол

- позволява на приложенията да пращат съобщения, наречени *datagrams*, чрез прост, connection-less модел на комуникация
- няма *handshake* между двете страни на комуникацията, в следствие на което няма гаранция за доставка на съобщенията и за запазване на реда им

---

#### UDP протокол

- Datagram се представя от класа `java.net.DatagramPacket`
- `DatagramSocket` представлява connection-less сокет за пращане и получаване на datagram пакети чрез методите си `send` и `receive`

---

#### TCP протокол

- Надгражда IP протокола, затова също се нарича TCP/IP ("TCP over IP")
- Предава данните по надежден начин, т.е. с проверка за грешки, с гаранция за доставка и със запазване на реда на пакетите

---

#### TCP протокол

- Имплементира се със сокети - класовете `ServerSocket` и `Socket`, позволяващи пращането и получаването на съобщения между две приложения: сървър и клиент

---

#### TCP vs. UDP

<table style="font-size:0.5em; line-height=0.7em;">
  <tr>
    <th>Характеристика</th>
    <th>TCP</th>
    <th>UDP</th>
  </tr>
  <tr>
    <td>Connection</td>
    <td>connection-based</td>
    <td>connection-less</td>
  </tr>
  <tr>
    <td>Надеждност</td>
    <td>висока</td>
    <td>ниска</td>
  </tr>
  <tr>
    <td>Ред на пакетите</td>
    <td>гарантиран</td>
    <td>не гарантиран</td>
  </tr>
  <tr>
    <td>Скорост на доставка</td>
    <td>по-ниска от UDP</td>
    <td>по-висока от TCP</td>
  </tr>
  <tr>
    <td>Проверка за грешки</td>
    <td>да, с възстановяване</td>
    <td>да, но без възстановяване</td>
  </tr>
  <tr>
    <td>Потвърджаване при получаване</td>
    <td>да</td>
    <td>не</td>
  </tr>
</table>

---

#### Клиент-сървър имплементация със сокети

---

#### `java.net.ServerSocket`

```java
ServerSocket() // създава server socket, който не е свързан.
               // Изисква извикване на bind(), преди да се използва
ServerSocket(int port) // създава server socket, свързан с дадения порт.
                       // Стойноста на port е от 0 до 65535,
                       // като 0 означава автоматично определен
ServerSocket(int port, int backlog) // задава максимален брой чакащи
                                    // заявки за свързване
ServerSocket(int port, int backlog, InetAddress bindAddr)

void bind(SocketAddress endpoint) // свързва към конкретния IP адрес
void bind(SocketAddress endpoint, int backlog)

Socket accept() // блокира и чака заявка за свързване от клиент
```

---

#### `java.net.Socket`

```java
Socket() // създава socket, който не е свързан
Socket(String host, int port) // създава socket и го свързва
                              // със зададения host и порт
Socket(InetAddress address, int port)

void connect​(SocketAddress endpoint) // свързва сокета към сървъра
void connect​(SocketAddress endpoint, int timeout)

InputStream getInputStream() // връща входен поток за четене
OutputStream getOutputStream() // връща изходен поток за писане
```

---

#### Сокети (Sockets)

![Socket Calls](images/10.3-network-sockets.png)

---

#### java.net | TCP комуникация

![TCP Flow](images/10.7-java-net-tcp-flow.png)

---

#### java.net: blocking мрежова комуникация

![Blocking IO](images/10.6-java-net-blocking-io.png)

---

#### java.net | Клиент-сървър архитектура

![Java.net Architecture](images/10.8-java-net-architecture.png)

---

#### java.net | Архитектура

![Java.net Architecture](images/10.8.1-java-net-multithreading.png)

---

#### java.net | Предимства и недостатъци

- Предимства
  - Сравнително прост код: познатото I/O Stream API
  - Няма нужда от проверки за частично получени съобщения
    - нишката блокира, докато прочете цялото съобщение
- Недостатъци
  - Неефективно използване на нишките
    - Много нишки в waiting/blocked състояние, заради блокиращите операции
    - Допълнителна памет (за нишките)
  - Performance penalty заради context switching между нишките
  - Ограничен брой паралелни конекции, защото нишките на сървъра са краен брой

---

#### Мрежово програмиране с Non-blocking I/O (NIO)

- Java NIO API-то реализира алтернативен начин за мрежова комуникация, който позволява неблокиращи (асинхронни) входно-изходни операции
- Чрез него се реализират мрежови приложения, които работят ефективно с огромен брой паралелни клиенти и заявки

---

#### java.nio | Основни обекти

- **Буфер** (Buffer) - Блок от паметта, който се използва за временно съхранение на данни за четене или писане
- **Канал** (Channel) - Абстракция за комуникационна връзка (connection)
- **Селектор** (Selector) - Компонент, в който се регистрират множество канали, позволяващ обработката им в една нишка

---

#### java.nio | Буфери

- Буферът е контейнер, който съдържа временно данни, които ще бъдат записани или прочетени
- Представлява масив от примитивен тип с фиксиран размер, който пази състояние: докъде е запълнен, колко свободно място има, докъде са прочетени или записани данните
- Класът `Buffer` е абстрактен, но има наследници за всички не-булеви примитивни типове: `ByteBuffer`, `CharBuffer`, `ShortBuffer`, `IntBuffer`, `LongBuffer`, `FloatBuffer`, `DoubleBuffer`
- `java.nio` комуникацията се основава на буфери, за разлика от `java.io` комуникацията, основана на входно-изходни потоци

---

#### java.nio.Buffer

- Състоянието на буфера се определя от четири атрибута:
    - *капацитет* (capacity): максималния брой елементи, които може да съдържа буфера. Задава се при създаването му и не може да се променя
    - *лимит* (limit): първият индекс на буфера, който не трябва да се достъпва за четене или писане
    - *позиция* (position): индекса на следващия елемент на буфера за прочитане или за записване
    - *маркер* (mark): индекс, в който може да запомним текущата позиция, за да се върнем към нея по-късно
- Четирите индекса са в следната зависимост:
    0 <= mark <= position <= limit <= capacity

---

#### java.nio.Buffer

```java
int capacity()
int position()
Buffer position(int newPosition)
int limit()
Buffer limit(int newLimit)
Buffer mark()
Buffer reset()
```

---

#### java.nio.Buffer

```java
// Подготвя буфера за "източване" / прочитане.
// Лимитът става равен на позицията, а позицията на нула
Buffer flip()

// Подготвя буфера за ново запълване.
// Лимитът става равен на капацитета, а позицията на нула
Buffer clear()

// Подготвя буфера за повторно прочитане на данните,
// които вече съдържа. Лимитът остава без промяна,
// позицията се нулира
Buffer rewind()
```

---

#### java.nio.ByteBuffer

```java
byte get()
byte get(int index)
ByteBuffer put(byte b)
ByteBuffer put(int index, byte b)
```

---

#### java.nio | Как работи буферът

![NIO Buffer Operations](images/10.9-nio-buffer-operations.png)

---

#### java.nio | Директни и индиректни буфери

<small>
- Буферите биват *директни* и *индиректни*
- Директните буфери ще използват при възможност native I/O операции за четене и запис директно през операционната система
- Директният буфер представлява непрекъснат регион на постоянно място в паметта, индиректният е Java масив, може да не е непрекъснят регион и може да се мести от garbage collector-a
- Директният буфер е по-скъп за създаване, но ще работи по-ефективно за големи размери и ако живее дълго в паметта
- Индиректният буфер не е толкова ефективен като директният за повечето операции, но управлението на паметта му се осъществява от JVM-a (garbage collector-a) и е по-предсказуемо

</small>

<br/>

```java
ByteBuffer buffer = ByteBuffer.allocateDirect(1024); // direct buffer
ByteBuffer buffer = ByteBuffer.allocate(1024); // indirect buffer
```

---

#### Java I/O performance

![Java IO Performance](images/10.10-java-io-performance.png)

---

#### Канали (Channels)

- Каналите са абстракция за връзка ("тръба") за ефективно транспортиране на данни между byte буфери и обект на другия край на канала (най-често файл или сокет)
- Каналите позволяват с минимален overhead да се достъпват native входно-изходните услуги на операционна система, а буферите са вътрешните крайни точки, които каналите използват за изпращане и получаване на данни

---

#### java.nio.channels.ServerSocketChannel

```java
// Opens a server-socket channel
static ServerSocketChannel open()

// Accepts a connection made to this channel's socket
SocketChannel accept()

// Binds the channel's socket to a local address
// and configures the socket to listen for connections
ServerSocketChannel bind​(SocketAddress local) 

// Retrieves a server socket associated with this channel
ServerSocket socket()
```

---

#### java.nio.channels.SocketChannel

```java
// Opens a socket channel
static SocketChannel open()
// Opens a socket channel and connects it to a remote address
static SocketChannel open​(SocketAddress remote)

// Connects this channel's socket
boolean connect​(SocketAddress remote)

// Retrieves a socket associated with this channel
Socket socket() 

// Reads bytes from this channel into the given buffer
int read​(ByteBuffer dst) 
// Writes bytes to this channel from the given buffer
int write​(ByteBuffer src)
```

---

#### Selector и SelectionKey

<small>
Селекторите осигуряват възможността за избор (селектиране) на канали според готовността им за I/O операции (readiness selection), което е предпоставка за multiplexed I/O, т.е. с една нишка да обслужваме голям брой канали.

1. Регистрираме един или повече вече създадени канали с инстанция на селектор
2. Регистрирането връща ключ, който представлява релацията между канала и селектора
3. Ключът "помни" операциите върху даден канал, от които се интересуваме и следи готовността на канала да ги изпълнява
4. При извикване на select() метода на селектора, се актуализират всички асоциирани с този селектор ключове на канали
5. От селектора може да получим множеството от ключове, чиито канали са готови за операция
6. Итерираме това множество и обслужваме всеки от готовите канали

</small>

---

![Selectors and Channels](images/10.11-selectors-and-channels.jpg)

---

#### java.nio.channels.Selector

```java
// Opens a selector
static Selector open()

// Selects a set of keys whose corresponding channels are ready for I/O operations
int select()

// Returns this selector's selected-key set
Set<SelectionKey> selectedKeys()
```

---

#### java.nio.channels.SelectionKey

```java
public static final int OP_READ
public static final int OP_WRITE
public static final int OP_CONNECT
public static final int OP_ACCEPT

SelectableChannel channel();
Selector selector();
int interestOps();
int readyOps();

boolean isReadable()
boolean isWritable()
boolean isConnectable()
boolean isAcceptable()

Object attach(Object ob)
Object attachment()
```

---

#### java.nio.channels.ServerSocketChannel

```java
// ServerSocketChannel е канал, който може да слуша
// за входящи TCP заявки за свързване, точно както ServerSocket

ServerSocketChannel serverSocketChannel = ServerSocketChannel.open();
serverSocketChannel.bind(new InetSocketAddress(9999));
serverSocketChannel.configureBlocking(false);

while (true) {
    SocketChannel socketChannel = serverSocketChannel.accept();
    ...
}
```

---

#### java.nio | SocketChannel | Регистрация

```java

// SocketChannel представлява една TCP връзка. За да се използва
// асинхронно, трябва да се регистрира в селектор. Каналът трябва
// да се постави в nonblocking режим, преди да се регистрира със селектор.

Selector selector = Selector.open();
socketChannel.configureBlocking(false);
socketChannel.register(selector,
        SelectionKey.OP_READ | SelectionKey.OP_WRITE);
```

---

#### java.nio | SocketChannel | Регистрация

- Когато регистрираме `SocketChannel`, трябва да укажем, за какви операции да бъдем известени:
    - `OP_READ` – когато се получи нещо за четене от канала
    - `OP_WRITE` – когато каналът е готов за запис
    - `OP_CONNECT` – когато каналът е готов да завърши последователността си за свързване към отдалечената система
    - `OP_ACCEPT` – когато пристигне заявка за нова конекция

---

#### java.nio | SocketChannel | Notification

```java
// Получаване на известие за няколко канала
while (true) {
    int readyChannels = selector.select();
    if (readyChannels == 0) { continue; }

    Set<SelectionKey> selectedKeys = selector.selectedKeys();
    Iterator<SelectionKey> keyIterator = selectedKeys.iterator();
    while (keyIterator.hasNext()) {
        SelectionKey key = keyIterator.next();
        if (key.isReadable()) {
            // A channel is ready for reading
        }
        keyIterator.remove();
    }
}
```

---

#### java.nio | SocketChannel | Notification | Четене

```java
// Четене на данните от канал
if (key.isReadable()) {
    SocketChannel sc = (SocketChannel) key.channel();
    while (true) {
        buffer.clear();
        int r = sc.read(buffer);
        if (r <= 0) { continue; }
        buffer.flip();
        sc.write(buffer);
    }
} else if (key.isWritable()) {
...
}
```

---

#### java.nio | SocketChannel | Запис

```java
// Използваме SocketChannel канал (channel) и за изпращане на данни
// по TCP връзката (connection)

SocketChannel socketChannel = SocketChannel.open();
socketChannel.connect(new InetSocketAddress("127.0.0.1", 9999));

String newData = "Current time: " + System.currentTimeMillis();
ByteBuffer buf = ByteBuffer.allocate(48);

buf.put(newData.getBytes());
buf.flip();
while (buf.hasRemaining()) {
    socketChannel.write(buf);
}
```

---

#### java.nio | Изпращане на данни

![Java NIO Sending](images/10.11.1a-java-nio-sending.png)

---

#### java.nio | Изпращане на данни

![Java NIO Sending](images/10.11.1b-java-nio-sending.png)

---

#### java.nio | Изпращане на данни

![Java NIO Sending](images/10.11.1c-java-nio-sending.png)

---

#### java.nio | Изпращане на данни

![Java NIO Sending](images/10.11.1d-java-nio-sending.png)

---

#### java.nio | Получаване на данни

![Java NIO Receiving](images/10.11.2a-java-nio-receiving.png)

---

#### java.nio | Получаване на данни

![Java NIO Receiving](images/10.11.2b-java-nio-receiving.png)

---

#### java.nio | Получаване на данни

![Java NIO Receiving](images/10.11.2c-java-nio-receiving.png)

---

#### java.nio | Получаване на данни

![Java NIO Receiving](images/10.11.2d-java-nio-receiving.png)

---

#### java.nio | Архитектура

- Нишка селектор (Selector), която позволява обработването на няколко канала от една нишка
- Намалява броя на нишките, като премахва нуждата от отделна нишка за всяка връзка (connection)
- Асинхронни (неблокиращи) операции

---

![Java NIO Architecture](images/10.13-java-nio-architecture-2.png)

---

![Java NIO Architecture](images/10.14-java-nio-architecture-3.png)

---

![Java NIO Architecture](images/10.15-java-nio-architecture-4.png)

---

![Java NIO Architecture](images/10.16-java-nio-architecture-5.png)

---

![IO vs. NIO](images/10.17-io-vs-nio.png)

---

![Java NIO](images/10.18-java-nio-oreilly.jpg)

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend

## HTTP, REST, JSON и `HttpClient`

_06.01.2021_

---

#### Предната лекция говорихме за:

@ul

- Thread pools / Executors API
- Concurrent колекции
- Мрежово програмиране

@ulend

---

#### Днес ще разгледаме:

@ul

- HTTP
- REST
- JSON
- `HttpClient`

@ulend

---

#### Как работи Интернет?

![HTTP request](images/11.1-http-request.png)

---

#### Характеристики на HTTP

@ul

- HTTP (Hypertext Transfer Protocol) e приложен протокол
- Като транспортен протокол, почти винаги се ползва ТCP/IP, в редки случаи и UDP
- Модел заявка-отговор (request-response) - служи за комуникационен канал в клиент-сървър архитектура, като следва строги правила за ред и формат на съобщенията между участниците
- HTTP сървърите по подразбиране "слушат" на порт 80

@ulend

---

#### Характеристики на HTTP

@ul

- Не пази състояние (*stateless*) – всяка клиентска заявка е независима сама по себе си
- Сървърът не обвързва логически серия заявки от определен клиент
- Това води до липса на вграден в протокола механизъм за поддържане на сесии

@ulend

---

#### HTTP транзакция "от птичи поглед"

1. Клиентът отваря комуникационен канал (TCP сокет)
2. Клиентът изпраща заявка към сървъра
3. Сървърът връща отговор на клиента
4. Сървърът затваря сокета

---

#### Видове HTTP съобщения: Заявки

@ul

- *Заявка* – инициатор е клиентът – подава информация на сървъра, достъп до кой ресурс иска да получи и каква операция иска да извърши с него (и евентуални входни параметри). Клиент (условно наречен *User-Agent* в HTTP) може да бъде всяко софтуерно приложение, спазващо правилата на протокола на комуникация

@ulend

---

#### Видове HTTP съобщения: Отговори

@ul

- *Отговор* – изпраща се от уеб сървъра, като резултат от изпълнението на клиентска заявка. Под уеб сървър разбираме софтуерно приложение, служещо като доставчик на дадени услуги върху определени негови ресурси

@ulend

---

#### HTTP Заявка

- Начален ред
- Хедъри (headers)
- Тяло (данни)

---

#### HTTP Заявка: начален ред

@ul

- HTTP Метод (Глагол) – указва типа операция, която клиентът иска да извърши със заявения ресурс
- URL (Uniform Resource Locator) – уникален локатор на заявения ресурс
- Версия на HTTP – версията на протокола, която ще се ползва за комуникация

@ulend

---

#### HTTP Заявка: хедъри и данни

@ul

- *Хедъри* - Възможно е да дефинира множество хедъри, като всеки от тях заема точно един ред и следва формата: “Име на хедър: Стойност на хедър”
- *Данни (Тяло)* – опционални, може да съдържат множество редове, включително и празни

@ulend

---

#### HTTP Заявка - пример

```http
GET en.wikipedia.org/w/index.php HTTP/1.1
```

```http
Connection: Keep-Alive
Host: en.wikipedia.org
```

---

#### HTTP заявка - пример

![HTTP sample request](images/11.2-http-sample-request.png)

---

#### HTTP ресурси

Унифициран локатор на ресурси (URL) - стандартизиран адрес на даден мрежов ресурс (документ или страница).

![URL](images/11.3-url.png)

---

### Основни HTTP методи

@ul

- GET – за зареждане на ресурс от сървъра
- HEAD - идентичен с GET, с разликата, че отговорът няма да върне тяло, а само хедъри

@ulend

---

### Основни HTTP методи

@ul

- POST - изпраща данни (например от HTML форма) за обработка от сървъра. Данните се съдържат в тялото на заявката
- PUT – ъплоудва даден ресурс
- DELETE – трие даден ресурс

@ulend

---

#### HTTP отговор

@ul

- Начален ред – съдържа 3 елемента, разделени с празно пространство помежду си:
  - Версия на HTTP
  - Статус код – обяснява резултата от изпълнението на заявката
  - Причина – кратко обяснение на статус-кода
- Хедъри
- Данни (Тяло) – отговорите обикновено връщат данни, като тук най-често се съдържа HTML документът, получен на базата на клиентската заявка.

@ulend

---

#### HTTP отговор - пример

```http
HTTP/1.1 200 OK
```

```http
Date: Tue, 18 Oct 2018 19:08:15 GMT
Server: Apache
```

---
#### HTTP отговор - пример

![HTTP response](images/11.4-http-sample-response.png)

---

#### HTTP статус кодове

- Трицифрени кодове, идентифициращи какъв е резултът от обработката на клиентската заявка
- Групирани са в 5 категории, на базата на цифрата на стотиците

---

#### HTTP статус кодове: група 100

Не дават индикация дали заявката е била успешна или не. Служат за „временни“ кодове, т.е. заявката е пристигнала, но сървърът все още не е готов с резултата.

```http
100 Continue
101 Switching protocols
```

---

#### HTTP статус кодове: група 200

Сървърът е обработил успешно клиентската заявка

```http
200 OK
206 Partial content
```

---

#### HTTP статус кодове: група 300

Ресурсът е наличен, но е разположен на друго място

```http
301 Moved permanently
304 Not Modified
307 Temporary redirect
```

---

#### HTTP статус кодове: група 400

Клиентска грешка

```http
400 Bad Request
401 Not Authorized
404 Not Found
408 Request Timeout
```

---

#### HTTP статус кодове: група 500

Сървърна грешка

```http
500 Internal Server Error
501 Not Implemented
503 Service Unavailable
```

---

#### HTTP хедъри: Основни (General Headers)

Могат да се ползват едновременно и в заявки, и в отговори. Съдържат информация (мета-данни) за самото съобщение или за метода на комуникация

```http
Connection: keep-alive
Date: Sat, 17 Nov 2018 16:08:15 GMT
```

---

#### HTTP хедъри: Заявка (Request Headers)

Специфични са само за заявките и могат да съдържат данни за самата заявка или за клиента


```http
Accept: text/html
Accept-Charset: utf-8
Accept-Language: en-US
User-Agent: Mozilla/4.0 
```

---

#### HTTP хедъри: Отговор (Response Headers)

Съдържат информация (мета-данни) за сървъра и формата на съобщението


```http
Server: Apache
Allow: GET, HEAD
```

---

#### HTTP хедъри: Същински (Entity Headers)

Информация за самото съдържание на данни (тяло) и/или за ресурса, заявен от клиента


```http
Content-Language: en
Content-Encoding: gzip
Content-Length: 8582
Last-Modified: Tue, 15 Nov 2018 12:45:26 GMT
```

---

#### HTTP хедъри: User Agent

*User Agent* е софтуер, който извършва действие от името на потребителя: E-mail клиенти, Web Browser-и, Месинджъри: Skype, WhatsApp

Примерeн низ за Google Chrome Web Browser:

```http
Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML,
          like Gecko) Chrome/38.0.2125.101 Safari/537.36
```

---

#### HTTP сесии - механизми

<small>
Понеже HTTP протоколът няма вградена поддръжка на сесии, ако има нужда сървърът да може да корелира заявките, идващи от един и същи клиент като логически принадлежащи към една последователност, обикново се ползва един от следните начини:

- *Бисквитки* (*Cookies*): Cookie-тата са малки текстови файлове, генерирани от сървъра и изпратени на клиента в header-ите. Чрез информацията в тях може да се идентифицира сесията
- Hidden fields в HTML forms: HTML страницата съдържа форма с поле, което е скрито и не се визуализира в браузъра, но стойността му се праща като част от заявката и стойността му идентифицира сесията (`<input type="hidden">`)
- URL rewriting: добавяме в края на всяко URL данни, които да идентифицират сесията

</small>

---

#### HTTP vs HTTPS

![HTTPS](images/11.5-https.png)

---

#### HTTP/2

- Появява се през 2015-та
- Какви проблеми на HTTP 1.x решава?

---

#### HTTP/2 vs HTTP 1.1

@ul

- двоичен, вместо текстови (⇨ по-компактен)
- напълно multiplexed, вместо подреден и блокиращ
- постига паралелизъм само с една TCP връзка между клиента и сървъра
- Използва компресия на хедърите
- Разрешава сървърите да “push”-ват HTTP response-и проактивно към клиента

@ulend

---

#### HTTP/2 Multiplexing

![HTTP2 Multiplexing](images/11.6-http2-multiplexing.png)

---

#### HTTP 1.1 vs. HTTP/2 response time

![HTTP2 Response Time](images/11.7-http2-response-time.png)

---

#### HTTP/2: поддръжка към днешна дата

@ul

- практически всички web browsers
- 50% от всички web sites към януари 2021 (43% през януари 2020)
- HttpClient-a в Java 11

@ulend

---

## REST

---

#### REpresentational State Transfer (REST)

@ul

- REST е стил софтуерна архитектура за реализация на уеб услуги.
  - REST не е спецификация или протокол
- Състои се от 6 принципа, които допринасят към това уеб услугата да бъде проста, бързодействаща и скалируема.

@ulend

---

#### REST (2)

@ul

- Има за цел да подобри и улесни комуникацията между две системи.
- Уеб услугите, които покриват REST принципите, се наричат RESTful уеб услуги.
- WWW е RESTful

@ulend

---

#### Принципи на REST архитектурата

@ul

- REST е клиент-сървър архитектура
- REST предоставя единен интерфейс (контракт)
- REST не пази състояние (stateless)
- REST предлага възможности за кеширане
- REST е многослойна система
- REST предоставя code on demand

@ulend

---

#### REST is client-server architecture

@ul

- Клиентът и сървърът са отделни компоненти
- Separation of concerns:
  - Сървърът съдържа бизнес логиката и се грижи за съхранението на данните
  - Клиентът извлича данни от сървъра и се грижи за представянето на данните:
    - уеб клиенти - браузъри
    - конзолни клиенти
    - ...

@ulend

---

#### REST is client-server architecture (2)

@ul

- Единният интерфейс позволява разделянето на клиент и сървър.
- Клиентът и сървърът могат да бъдат променяни независимо един от друг, стига това да не променя единния интерфейс помежду им.

@ulend

---

#### Пример за клиент-сървър

@ul

- Дa предположим, че искаме да извлечем информация за даден потребител от GitHub. REST API документация за въпросната операция - [link](https://docs.github.com/en/free-pro-team@latest/rest/reference/users#get-a-user).
- Можем да го направим през:
  - уеб клиент - @size[1.0em](https://github.com/{username})
  - Java клиент - [hub4j/github-api](https://github.com/hub4j/github-api/)
  - заявка към REST API-то
    - @size[0.75em]($ curl https://api.github.com/users/{username})
  - ...

@ulend

---

#### Ресурси

@ul

- REST въвежда концепцията за ресурс.
- Всяка информация, която може да бъде именувана, може да бъде ресурс.
- Ние, като програмисти, дефинираме кои са ресурсите, с които ще оперира нашата уеб услуга.
- В примера, който разгледахме, ресурси бяха дадените GitHub потребители.
- Ресурси могат да бъдат html страници, js файлове, изображения, потребители и др.

@ulend

---

#### Идентификатори на ресурси

<small>
- Всеки ресурс се идентифицира чрез URI (uniform resource identifier)
- Примери:

</small>

```bash
# Get all repos in fmi organisation
$ curl https://api.github.com/orgs/fmi/repos
# Get fmi/java-course repo
$ curl https://api.github.com/repos/fmi/java-course
```

---

#### Представяне на ресурси

@ul

- Ресурсите са концептуално разделени от представянията, които се връщат към клиентите.
- Например сървър пази ресурсите си в база от данни и на файловата система, а връща на клиентите ресурси под формата на HTML, JSON и XML.
- Не винаги върнатото представяне е вътрешното представяне.

@ulend

---

#### REST provides a uniform interface

<small>
- REST предоставя единен интерфейс (контракт) между клиента и сървъра.
- Контрактът се изгражда въз основа на ресурсите.
- [Github REST API](https://developer.github.com/v3/)

</small>

```bash
# Github API does not support text/html
# instead use application/json
$ curl --header "Accept: text/html" \
  https://api.github.com/repos/fmi/java-course
# repozzz resource does not exist
$ curl https://api.github.com/repozzz/fmi/java-course
```

---

## JSON

---

@ul

- Форматите за обмен на данни са зависими от използваната архитектура:
  - Уеб услуги, базирани на SOAP - само XML
  - Уеб услуги, базирани на REST - JSON, XML и други.

@ulend

---

#### JavaScript Object Notation (JSON)

@ul

- един от най-популярните формати за обмен на данни
- произлиза от JavaScript
- използва се за предаване на структурирани данни по мрежова комуникация
- намира широко приложение в RESTful уеб приложенията за предоставяне на данни

@ulend

---

#### JSON - характеристики

@ul

- web friendly - тривиално парсване (за разлика от XML)
- кратък и интуитивен
- разбираем едновременно от човек и машина
- езиково независима спецификация - [RFC 7159](https://tools.ietf.org/html/rfc7159)
- почти всички езици поддържат JSON

@ulend

---

#### Пример

```bash
$ curl https://api.github.com/users/kelseyhightower
```

```json
{
  "login": "kelseyhightower",
  "name": "Kelsey Hightower",
  "company": "Google, Inc",
  "location": "Portland, OR",
  "email": null,
  "hireable": true,
  "followers": 10041,
  "following": 13
}
```

---

#### Типове данни

@ul

- Boolean - `true` / `false`
- Number - `42`, `3.14156`, `-1`
- String - `"foo"`, `"bar"`
- Array - `["John", "Anna", "Peter"]`
- Object - `{"name": "John", "age": 30}`
- Поддържа `null`, `{}`, но не и функция, дата или `undefined`

@ulend

---

#### Пример (2)

```bash
$ curl https://api.github.com/repos/kubernetes/kubernetes/tags
```

```json
[
  {
    "name": "v1.14.0-alpha.0",
    "commit": {
      "sha": "1f56cd801e795fd063ec3e61fe4f6fa8841f4222"
    }
  },
  {
    "name": "v1.13.2-beta.0",
    "commit": {
      "sha": "efe48f3cd6436737d37fd2fcd6beb9e2328f7cce"
    }
  }
]
```

---

#### Java библиотеки за работа с JSON


@ul

- [google/gson](https://github.com/google/gson)
- [FasterXML/jackson](https://github.com/FasterXML/jackson)
- ...

@ulend

---

#### `google/gson`

@ul

- Предоставя лесен механизъм за преобразуване от Java обект към JSON и обратно
    - .toJson() и .fromJson()
- Не изисква добавяне на анотации или прекомпилиране
- Позволява вмъкването на custom serializer/deserializer
- Комплексен Builder
- [Gson User Guide](https://github.com/google/gson/blob/master/UserGuide.md)

@ulend

---

#### `.toJson(Object src)`

```java
public class Developer {
    private String name;
    private int age;
    public Developer(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

```java
Developer dev = new Developer("Kelsey", 28);
Gson gson = new Gson();
String json = gson.toJson(dev);
// {"name":"Kelsey","age":28}
System.out.println(json);
```

---

#### `.fromJson(String json, Class<T> classOfT)`

```java
String json = "{\"name\": \"Wesley\", \"age\": 20 }";
Gson gson = new Gson();
Developer dev = gson.fromJson(json, Developer.class);
// Wesley, 20 years old
System.out.printf("%s, %d years old%n",
    dev.getName(), dev.getAge());
```

---

#### `.fromJson(Reader json, Class<T> classOfT)`

```java
Gson gson = new Gson();
FileReader reader = new FileReader(new File("devs.json"));
// unchecked conversion
List<Developer> devs = gson.fromJson(reader, List.class);
```

---

#### `.fromJson(String json, Type typeOfT)`

```java
List<Developer> devs = List.of(
        new Developer("Kelsey", 28),
        new Developer("Wesley", 20));
Gson gson = new Gson();
String json = gson.toJson(devs);
Type type = new TypeToken<List<Developer>>(){}.getType();
List<Developer> devsAgain = gson.fromJson(json, type);
System.out.println(devsAgain.size()); // 2
```

---

## Java HTTP Client

@ul

- Част от JDK-то от Java 11 (септември 2018)
- Използва се за request-ване на HTTP ресурси по мрежата и обработка на response-а
- Поддържа HTTP/1.1 и HTTP/2
- Поддържа както синхронни, така и асинхронни заявки
- Състои се от няколко класа и интерфейса в пакета `java.net.http`

@ulend

---

#### Пример: GET заявка, която печата тялото на reponse-a като низ

```java
HttpClient client = HttpClient.newHttpClient();
HttpRequest request = HttpRequest.newBuilder()
      .uri(URI.create("http://wikipedia.org/"))
      .build();
client.sendAsync(request, BodyHandlers.ofString())
      .thenApply(HttpResponse::body)
      .thenAccept(System.out::println)
      .join();
```

---

#### `HttpClient`

<small>
- "Входната точка" на API-то. Представлява клиент за пращане на HTTP заявки и получаване на отговори
- Инстанция на `HttpClient` се създава от статичен builder метод на класа
- Builder-ът може да се ползва за конфигуриране на клиента (предпочитана версия на протокола, да следва ли redirects, ползва ли прокси и т.н.)
- веднъж създаден, е immutable, но може да се ползва за пращане на много заявки

</small>

```java
var client = HttpClient.newHttpClient();
var client = HttpClient.newBuilder().build(); // equivalent
```

---

#### Пример

```java
HttpClient client = HttpClient.newBuilder()
      .version(Version.HTTP_2)
      .followRedirects(Redirect.SAME_PROTOCOL)
      .proxy(ProxySelector.of(
              new InetSocketAddress("www-proxy.com", 8080)))
      .authenticator(Authenticator.getDefault())
      .build();
```

---

#### `HttpRequest`

- Клас, представляващ HTTP заявка, включително URI, метод, хедъри и т.н.
-  `HttpRequest` инстанция се създава от статичен builder метод на класа
- Builder-ът може да се ползва за конфигуриране на
  - URI и метод на заявката, хедъри, тяло (ако има)
- съдържа тези "готови" методи: `GET()`, `POST()`, `DELETE()` и `PUT()`. Останалите се конфигурират с `method()`
  - методът по подразбиране е GET() и може да се пропусне
- веднъж създаден, е immutable, но може да се праща многократно

---

#### Пример: Създаване на `HttpRequest`

```java
var request1 = HttpRequest.newBuilder(URI.create("https://www.apple.com/"))
        .build();
var request2 = HttpRequest.newBuilder()
        .uri(URI.create("https://www.apple.com/"))
        .build(); // equivalent

var request3 = HttpRequest.newBuilder()
        .uri(URI.create("http://openjdk.java.net/"))
        .timeout(Duration.ofMinutes(1))
        .header("Content-Type", "application/json")
        .POST(BodyPublishers.ofFile(Paths.get("file.json")))
        .build();
```

---

#### `HttpRequest.BodyPublisher`

<small>
- Ако заявката има тяло (например POST заявка), този клас отговаря за "публикуването" на съдържанието на тялото от даден източник, например низ
- В класа `BodyPublishers` има factory методи за получаване на готови често използвани типове

</small>

```java
BodyPublishers::ofString
BodyPublishers::ofFile
BodyPublishers::ofByteArray
BodyPublishers::ofInputStream
```

---

#### `HttpResponse`

<small>
- Интерфейс, представляващ HTTP response, включително header-а и body-то (ако има)
- Инстанции на имплементации на този интерфейс се получават в резултат на пращане на `HttpRequest` от `HttpClient`

</small>

```java
T body()                     // тялото на отговора
HttpHeaders headers()        // хедърите на отговора
HttpRequest request()        // HttpRequest-а, отговарящ на този отговор
int statusCode()             // HTTP статус кода
URI uri()                    // URI-то на заявката
HttpClient.Version version() // версията на HTTP протокола
```

---

#### `HttpResponse.BodyHandler`

<small>
- Функционален интерфейс, който приема информация за response-a (статус код и хедъри) и връща `BodySubscriber`, който се грижи за "консумирането" (т.е. обработката) на тялото на response-a
- В класа `BodyHandlers` има фактори методи за получаване на готови често използвани типове

</small>

```java
BodyHandlers::ofByteArray
BodyHandlers::ofFile
BodyHandlers::ofString
BodyHandlers::ofInputStream
```

---

#### `HttpResponse.BodySubscriber`

- "Абонира се" за тялото на response-a и трансформира байтовете му в друга форма (низ, файл и т.н.)
- В класа `BodySubscribers` има factory методи за получаване на готови често използвани типове

---

#### Синхронни и асинхронни заявки

- Зявките могат да се пращат синхронно или асинхронно
- Синронното API блокира, докато не се върне `HttpResponse`
- Асинхронното API връща веднага инстанция на `CompletableFuture`, което завършва с `HttpResponse`, когато стане наличен
- `BodyHandler`-ът за всяка заявка определя как да се обработи тялото на response-а, ако има такова

---

#### Синхронни и асинхронни заявки

```java
HttpResponse<String> response =
      client.send(request, BodyHandlers.ofString());
System.out.println(response.statusCode());
System.out.println(response.body());
```

```java
client.sendAsync(request, BodyHandlers.ofString())
      .thenApply(response -> { System.out.println(response.statusCode());
                               return response; } )
      .thenApply(HttpResponse::body)
      .thenAccept(System.out::println);
```

---

#### HTTP/2

- Java HTTP Client-ът поддържа както HTTP/1.1, така и HTTP/2
- По подразбиране, клиентът праща заявките по HTTP/2
- Заявките към сървъри, които не поддържат HTTP/2, автоматично се "downgrade"-ват до HTTP/1.1

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend


## Design Patterns

_13.01.2021_

---

#### Предната лекция говорихме за:

@ul

- HTTP
- REST
- JSON
- `HttpClient`

@ulend

---

#### `CompletableFuture<T>` под лупа

<small>
- `CompletableFuture<T>` е клас в пакета `java.util.concurrent`
- имплементира интерфейсите `Future<T>` и `CompletionStage<T>`
- позволява chain-ване на CompletableFutures, т.е. изпълнението им един след друг

</small>

```java
// Връща нов CompletionStage, който ще се изпълни след дадения с резултата
// му като аргумент на дадената функция
<U> CompletionStage<U> thenApply​(Function<? super T,​? extends U> fn)

// Връща нов CompletionStage, който ще се изпълни след дадения с резултата
// му като аргумент на дадения action
CompletableFuture<Void> thenAccept​(Consumer<? super T> action)

// Блокира и изчаква завършването на операцията, и връща резултата ѝ
T get()
// Блокира и връща резултата след успешно приключване на операцията,
// или хвърля uncheck exception при неуспех
T join()
```

---

#### Асинхронна обработка на заявки и резултата им

<small>
- `sendAsync()` изпраща заявката в отделна нишка (взима се от default-ния (common) thread executor на JVM-a или от custom executor-a, зададен при конструирането на `HttpClient`-a) и връща веднага инстанция на `CompletableFuture<HttpResponse>`
- dependent методите на този `CompletableFuture` (`thenApply()`, `theAccept()`, ...) се изпъляват в отделна нишка
  - ако са няколко chained, chain-ът се изпълява от една нишка
  - ако държим chained метод да се изпълни в различна нишка, асинхронно спрямо останалия chain, може да ползваме async вариантите на dependent методите: `thenApplyAsync()`, `thenAcceptAsync()`
  - ако искаме да се изпълнят не само в различна нишка, но и тази нишка да е от избран от нас thread pool, трябва да ползваме overloaded вариантите им, които приемат `executor`

</small>

---

#### Днес ще разгледаме:

@ul

- S.O.L.I.D. дизайн принципите
- Design Patterns

@ulend

---

#### S.O.L.I.D дизайн принципи

![S.O.L.I.D.](images/12.1-solid.png)

---

#### S.O.L.I.D: Single responsibility principle

@ul

- A class should have only a single responsibility (i.e. changes to only one part of the software's specification should be able to affect the specification of the class)
- "A class should have only one reason to change."

@ulend

---

#### S.O.L.I.D: Open/closed principle

@ul

- software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification

@ulend

---

#### S.O.L.I.D: Liskov substitution principle

@ul

- objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program

@ulend

---

#### S.O.L.I.D: Interface segregation principle

@ul

- A client should not be forced to implement an interface that it doesn’t use
- Many client-specific interfaces are better than one general-purpose interface

@ulend

---

#### S.O.L.I.D: Dependency inversion principle

@ul

- high level modules must not depend on low level modules, but they should depend on abstractions
- one should “depend upon abstractions, not concretions”

@ulend

---

#### Design Patterns

Шаблоните за дизайн са

@ul

- обобщени добри практики
- стандартни решения на общи / често срещани проблеми

@ulend

---

![Design Patterns](images/12.2-design-patterns.jpg)

---

#### Design Patterns - ползи

@ul

- Използване на колективния опит за софтуерно проектиране за доказани решения на често срещани проблеми
- Поощряват reusability на кода, което води до по-качествен и лесен за поддръжка код
- Обща терминология, която помага на програмистите да се разбират лесно

@ulend

---

#### Design Patterns - видове

@ul

- Creational Patterns
- Structural Patterns
- Behavioral Patterns

@ulend

---

#### Creational Patterns

@ul

- Осигуряват начин да се създават обекти на класове, скривайки логиката по създаването им (вместо да се инстанцират директно чрез оператора `new`)
- Factory, Abstract Factory, Builder, Singleton, Prototype

@ulend

---

#### Structural Patterns

@ul

- Осигуряват различни начини за създаване на по-сложни класове чрез наследяване и композиция на по-прости класове
- Adapter, Composite, Proxy, Flyweight, Facade, Bridge, Decorator

@ulend

---

#### Behavioral Patterns

@ul

- Свързани са с комуникацията между обекти
- Template Method, Mediator, Chain of Responsibility, Observer, Strategy, Command, State, Visitor, Interpreter, Iterator, Memento

@ulend

---

#### Factory

![Factory](images/12.3-factory.png)

---

#### Factory

@ul

- creational pattern
- създаваме обект без да expose-ваме логиката по създаването му на клиента
- използва се, когато имаме родителски клас с няколко наследници и искаме да създаваме един от наследниците на родителския клас според подаден параметър
- примери от JDK-то: `valueOf()` метода на wrapper класовете като `Boolean`, `Integer` и т.н., `of()` методите на `List`, `Set`, `Map`, `of()` метода на `Path`, `of()` метода на `Stream`


@ulend

---

#### Factory

![Factory](images/12.4-factory-demo-diagram.png)

---

#### Builder

![Builder](images/12.5-builder.png)

---

#### Builder

@ul

- creational pattern
- решава някои проблеми на Factory pattern-а за класове с много атрубути, от които много са optional
- примери от JDK-то: `StringBuilder`, `StringBuffer`, `HttpClient`, `HttpRequest`

@ulend

---

#### Builder - имплементация

@ul

- Създаваме `static` вложен клас и копираме всички параметри от външния клас в builder класа
- builder класът трябва да има публичен конструктор с всички задължителни атрибути като параметри
- setter методи за всички опционални параметри, които връщат същата builder инстанция
- `build()` метод, който връща обекта (`this`)

@ulend

---

#### Singleton

![Singleton](images/12.6-singleton.png)

---

#### Singleton

@ul

- creational pattern
- клас, от който може да съществува най-много една инстанция
- имплементация
  - `private` конструктор
  - `private static` член-променлива от тип същия клас, която реферира единствената инстанция на класа
  - `public static` метод, който връща инстанцията на класа

@ulend

---

#### Singleton

@ul

- типични употреби: logging, caching, thread pools
- В други design patterns (Factory, Builder, Facade, Prototype, …)

@ulend

---

#### Flyweight

![Flyweight](images/12.7-flyweight.png)

---

#### Flyweight

@ul

- structural pattern
- позволява да се съберат повече обекти в наличната памет чрез споделяне на общите части на state-a между множество обекти
- намалява memory footprint-а на програмата
- може също да подобри бързодействието в приложения, където инстанцирането на обектите е скъпа операция

@ulend

---

#### Flyweight

@ul

- flyweight обектите са immutable: всяка операция, която променя състоянието им трябва да се изпълнява от factory-то
- примери от JDK-то: `String` с имплементацията на string pool-a, `Integer.valueOf(int)`, `Byte.valueOf(byte)` и подобните са останалите wrapper типове

@ulend

---

#### Flyweight - имплементация

@ul

- интерфейс, който дефинира операциите, които клиентския код може да извършва върху flyweight обектите
- една или повече конкретни имплементации на този интерфейс
- factory, което отговаря за инстанциране и кеширане

@ulend

---

#### Iterator

![Iterator](images/12.8-iterator.png)

---

#### Iterator

@ul

- behavioral pattern
- позволява последователното обхождане на поредица от обекти
- примери от JDK-то: `java.util.Iterator` и обхождането на колекции

@ulend

---

#### Iterator

![Iterator](images/12.9-iterator-demo-diagram.png)

---

#### Command

![Command](images/12.10-command.png)

---

#### Command

@ul

- behavioral pattern
- използва се за имплементиране на loose coupling в модел тип заявка-отговор
- пример от JDK-то: `java.lang.Runnable`

@ulend

---

#### Command

![Command](images/12.11-command-demo-diagram.png)

---

#### Observer

![Observer](images/12.12-observer.png)

---

#### Observer

@ul

- behavioral pattern
- удобен е, когато се интересуваме от състоянието на даден обект и искаме да бъдем нотифицирани, когато има промяна в състоянието
- обектът, който наблюдава за промяна на състоянието на друг обект, се нарича *Observer*, а наблюдаваният обект се нарича *Subject*
- пример от JDK-то: `java.util.Observer`, `java.util.Observable`

@ulend

---

#### Observer

![Observer](images/12.13-observer-demo-diagram.png)

---

#### Strategy

![Strategy](images/12.14-strategy.png)

---

#### Strategy

@ul

- behavioral pattern
- прилага се, когато имаме множество алгоритми за дадена задача и клиентът решава по време на изпълнение, коя имплементация на алгоритъм да се ползва
- примери от JDK-to: `Collections.sort()`, който сортира по различен критерий/алгоритъм в зависимост от подадения `Comparator`

@ulend

---

#### Design Patterns - примери с код

@ul

- може да разгледате приложените [code snippets](https://github.com/fmi/java-course/tree/master/12-design-patterns/snippets/design-patterns)
- хубави обяснения и примери с псевдокод [Refactoring Guru: Design Patterns](https://refactoring.guru/design-patterns)
- тук може да намерите информация и примери с код на Java за голям брой design patterns (не само 23-те от *Gang-of-Four*): [Java Design Patterns](https://github.com/iluwatar/java-design-patterns)

@ulend

---

## Въпроси

@snap[south span-100]
@fab[github] [fmi/java-course](https://github.com/fmi/java-course)
@fab[youtube] [MJT2021](https://www.youtube.com/playlist?list=PLew34f6r0Pxy8PvaJ83pa4r76XCmZR657)
@snapend

Design Patterns
13.01.2021

Предната лекция говорихме за:
@ul

HTTP
REST
JSON
HttpClient
@ulend

CompletableFuture<T> под лупа
- `CompletableFuture` е клас в пакета `java.util.concurrent` - имплементира интерфейсите `Future` и `CompletionStage` - позволява chain-ване на CompletableFutures, т.е. изпълнението им един след друг
// Връща нов CompletionStage, който ще се изпълни след дадения с резултата
// му като аргумент на дадената функция
<U> CompletionStage<U> thenApply​(Function<? super T,​? extends U> fn)

// Връща нов CompletionStage, който ще се изпълни след дадения с резултата
// му като аргумент на дадения action
CompletableFuture<Void> thenAccept​(Consumer<? super T> action)

// Блокира и изчаква завършването на операцията, и връща резултата ѝ
T get()
// Блокира и връща резултата след успешно приключване на операцията,
// или хвърля uncheck exception при неуспех
T join()
Асинхронна обработка на заявки и резултата им
- `sendAsync()` изпраща заявката в отделна нишка (взима се от default-ния (common) thread executor на JVM-a или от custom executor-a, зададен при конструирането на `HttpClient`-a) и връща веднага инстанция на `CompletableFuture` - dependent методите на този `CompletableFuture` (`thenApply()`, `theAccept()`, ...) се изпъляват в отделна нишка - ако са няколко chained, chain-ът се изпълява от една нишка - ако държим chained метод да се изпълни в различна нишка, асинхронно спрямо останалия chain, може да ползваме async вариантите на dependent методите: `thenApplyAsync()`, `thenAcceptAsync()` - ако искаме да се изпълнят не само в различна нишка, но и тази нишка да е от избран от нас thread pool, трябва да ползваме overloaded вариантите им, които приемат `executor`
Днес ще разгледаме:
@ul

S.O.L.I.D. дизайн принципите
Design Patterns
@ulend

S.O.L.I.D дизайн принципи
S.O.L.I.D.

S.O.L.I.D: Single responsibility principle
@ul

A class should have only a single responsibility (i.e. changes to only one part of the software's specification should be able to affect the specification of the class)
"A class should have only one reason to change."
@ulend

S.O.L.I.D: Open/closed principle
@ul

software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification
@ulend

S.O.L.I.D: Liskov substitution principle
@ul

objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program
@ulend

S.O.L.I.D: Interface segregation principle
@ul

A client should not be forced to implement an interface that it doesn’t use
Many client-specific interfaces are better than one general-purpose interface
@ulend

S.O.L.I.D: Dependency inversion principle
@ul

high level modules must not depend on low level modules, but they should depend on abstractions
one should “depend upon abstractions, not concretions”
@ulend

Design Patterns
Шаблоните за дизайн са

@ul

обобщени добри практики
стандартни решения на общи / често срещани проблеми
@ulend

Design Patterns

Design Patterns - ползи
@ul

Използване на колективния опит за софтуерно проектиране за доказани решения на често срещани проблеми
Поощряват reusability на кода, което води до по-качествен и лесен за поддръжка код
Обща терминология, която помага на програмистите да се разбират лесно
@ulend

Design Patterns - видове
@ul

Creational Patterns
Structural Patterns
Behavioral Patterns
@ulend

Creational Patterns
@ul

Осигуряват начин да се създават обекти на класове, скривайки логиката по създаването им (вместо да се инстанцират директно чрез оператора new)
Factory, Abstract Factory, Builder, Singleton, Prototype
@ulend

Structural Patterns
@ul

Осигуряват различни начини за създаване на по-сложни класове чрез наследяване и композиция на по-прости класове
Adapter, Composite, Proxy, Flyweight, Facade, Bridge, Decorator
@ulend

Behavioral Patterns
@ul

Свързани са с комуникацията между обекти
Template Method, Mediator, Chain of Responsibility, Observer, Strategy, Command, State, Visitor, Interpreter, Iterator, Memento
@ulend

Factory
Factory

Factory
@ul

creational pattern
създаваме обект без да expose-ваме логиката по създаването му на клиента
използва се, когато имаме родителски клас с няколко наследници и искаме да създаваме един от наследниците на родителския клас според подаден параметър
примери от JDK-то: valueOf() метода на wrapper класовете като Boolean, Integer и т.н., of() методите на List, Set, Map, of() метода на Path, of() метода на Stream
@ulend

Factory
Factory

Builder
Builder

Builder
@ul

creational pattern
решава някои проблеми на Factory pattern-а за класове с много атрубути, от които много са optional
примери от JDK-то: StringBuilder, StringBuffer, HttpClient, HttpRequest
@ulend

Builder - имплементация
@ul

Създаваме static вложен клас и копираме всички параметри от външния клас в builder класа
builder класът трябва да има публичен конструктор с всички задължителни атрибути като параметри
setter методи за всички опционални параметри, които връщат същата builder инстанция
build() метод, който връща обекта (this)
@ulend

Singleton
Singleton

Singleton
@ul

creational pattern
клас, от който може да съществува най-много една инстанция
имплементация
private конструктор
private static член-променлива от тип същия клас, която реферира единствената инстанция на класа
public static метод, който връща инстанцията на класа
@ulend

Singleton
@ul

типични употреби: logging, caching, thread pools
В други design patterns (Factory, Builder, Facade, Prototype, …)
@ulend

Flyweight
Flyweight

Flyweight
@ul

structural pattern
позволява да се съберат повече обекти в наличната памет чрез споделяне на общите части на state-a между множество обекти
намалява memory footprint-а на програмата
може също да подобри бързодействието в приложения, където инстанцирането на обектите е скъпа операция
@ulend

Flyweight
@ul

flyweight обектите са immutable: всяка операция, която променя състоянието им трябва да се изпълнява от factory-то
примери от JDK-то: String с имплементацията на string pool-a, Integer.valueOf(int), Byte.valueOf(byte) и подобните са останалите wrapper типове
@ulend

Flyweight - имплементация
@ul

интерфейс, който дефинира операциите, които клиентския код може да извършва върху flyweight обектите
една или повече конкретни имплементации на този интерфейс
factory, което отговаря за инстанциране и кеширане
@ulend

Iterator
Iterator

Iterator
@ul

behavioral pattern
позволява последователното обхождане на поредица от обекти
примери от JDK-то: java.util.Iterator и обхождането на колекции
@ulend

Iterator
Iterator

Command
Command

Command
@ul

behavioral pattern
използва се за имплементиране на loose coupling в модел тип заявка-отговор
пример от JDK-то: java.lang.Runnable
@ulend

Command
Command

Observer
Observer

Observer
@ul

behavioral pattern
удобен е, когато се интересуваме от състоянието на даден обект и искаме да бъдем нотифицирани, когато има промяна в състоянието
обектът, който наблюдава за промяна на състоянието на друг обект, се нарича Observer, а наблюдаваният обект се нарича Subject
пример от JDK-то: java.util.Observer, java.util.Observable
@ulend

Observer
Observer

Strategy
Strategy

Strategy
@ul

behavioral pattern
прилага се, когато имаме множество алгоритми за дадена задача и клиентът решава по време на изпълнение, коя имплементация на алгоритъм да се ползва
примери от JDK-to: Collections.sort(), който сортира по различен критерий/алгоритъм в зависимост от подадения Comparator
@ulend

Design Patterns - примери с код
@ul

може да разгледате приложените code snippets
хубави обяснения и примери с псевдокод Refactoring Guru: Design Patterns
тук може да намерите информация и примери с код на Java за голям брой design patterns (не само 23-те от Gang-of-Four): Java Design Patterns
@ulend





