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



