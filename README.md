# Домашнее задание к занятию «Наследование и расширяемость систем. Проблемы наследования»

##  Инструкция к выполнению домашнего задания

Перед тем как отправить своё решение на проверку преподавателю, сверьтесь с чеклистом.

<details>
  <summary> 1. В решении выполнены все требования задания</summary>

Убедитесь, что все требования задания выполнены. Для этого перед отправкой внимательно прочтите весь текст условия задания и соотнесите сказанное в нём с вашим решением. Навык самопроверки работы перед ревью пригодится вам как при обучении, так и на работе.

  ---

</details>
<details>
   <summary>2. Правильно настроен Maven-проект, тесты проходят</summary>

Репозиторий должен быть папкой вашего Мавен-проекта. Обратите внимание, что репозиторием не должна быть папка, в которой лежит папка Мавен-проекта, он сам должен быть папкой проекта. В нём должны быть соответствующие файлы и папки — `pom.xml`, `src` и другие.

Не забудьте создать .gitignore-файл в корне проекта и добавить туда в игнорирование автогенерируемую папку `target`.

Общая схема вашего `pom.xml`-файла:

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>ru.netology</groupId>
    <artifactId>НАЗВАНИЕ-ВАШЕГО-ПРОЕКТА-БЕЗ-ПРОБЕЛОВ</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven.compiler.source>11</maven.compiler.source>
        <maven.compiler.target>11</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>


    <dependencies>
        <dependency>
            ...
        </dependency>
        ...
    </dependencies>


    <build>
        <plugins>
            <plugin>
              ...
            </plugin>

            <plugin>
              ...
              <executions>
                <execution>
                  ...
                </execution>
                ...
              </executions>
            </plugin>
            ...
        </plugins>
    </build>

</project>
  ```

#### JUnit
Обратите внимание, что у артефакта нет `-api` на конце. Если у вас автоматически добавилась зависимость вида `<artifactId>junit-jupiter-api</artifactId>`, то лучше поменять артефакт на тот, что ниже, иначе будут сюрпризы в работе.

  ```xml
          <dependency>
              <groupId>org.junit.jupiter</groupId>
              <artifactId>junit-jupiter</artifactId>
              <version>5.7.0</version>
              <scope>test</scope>
          </dependency>
  ```

#### Surefire
Без этого плагина тесты могут Мавеном не запускаться, хоть в идее через кнопки они и будут проходить. Чтобы лишний раз убедиться, что всё работает, нажмите `Ctrl+Ctrl` и затем `mvn clean test`.

  ```xml
              <plugin>
                  <groupId>org.apache.maven.plugins</groupId>
                  <artifactId>maven-surefire-plugin</artifactId>
                  <version>2.22.2</version>
                  <configuration>
                      <failIfNoTests>true</failIfNoTests>
                  </configuration>
              </plugin>
  ```
  
---

</details>

<details>
   <summary> 3. Что делать, если возникли сложности </summary>

Это здорово. Если их преодолевать правильно, то можно получить большую образовательную пользу для себя. Периодическое возникновение вопросов, недопонимание пройденного материала — нормальная и неотъемлемая часть обучения. А мы здесь, чтобы помочь вам пройти этот путь.

### Что делать, если непонятна теория
1. Если подобный вопрос разбирался на лекции, посмотрите ещё раз раздел с этой темой в видеозаписи.
1. Если вопрос не решился, попробуйте поискать ответ самостоятельно в интернете, этот навык пригодится вам в работе.
1. Если самостоятельно разобраться не удалось, задайте вопрос в общем чате, мы обязательно поможем.

### Что делать, если непонятно условие задания
1. Прежде чем задать вопрос по условию задачи, перечитайте его ещё раз и убедитесь, что в тексте условия нет прямого ответа на этот вопрос. Умение работать с текстом — важный навык работы с информацией.
1. Если ответа на свой вопрос в тексте условия не увидели, задайте его в общем чате, мы раскроем детали условия.

### Что делать, если не получается задача
Если ваша проблема — это **ошибка компиляции** — подчёркивает красным, не даёт запустить программу, сборки проекта, CI и прочие подобные ошибки, то:
1. Найдите и прочитайте текст ошибки, который вам подсвечивает идея или логи. «Подчёркивает красным» — это не описание ошибки.
1. Попробуйте понять текст ошибки, при необходимости воспользуйтесь переводчиком. Не страшно, если вы переведёте неточно, тут главное — сам процесс: со временем и с нашей помощью вы будете это делать лучше и лучше, но, пропуская этот этап, вы не сможете научиться это делать.
1. Если не получилось понять ошибку по её тексту, попробуйте её загуглить и изучить подобную ошибку у других людей. Попробуйте примерить решения их проблем на свой код. Соотнесите найденные описания ошибки с пройденной теорией.
1. Если всё равно ваши трудности не разрешились, напишите в общий чат, обязательно указав:
    1. название задачи и ссылку на условие;
    1. ссылку на вашу работу;
    1. текст и скриншот, не фотографию, ошибки;
    1. ваши размышления и описание шагов, которые вы совершили для решения.

Если ваша проблема — это **ошибка исполнения**, программа умирает уже после запуска, или она **отрабатывает неправильно**, из-за чего ваши тесты не проходят, то:
1. Воспользуйтесь отладчиком для пошагового анализа работы вашей программы. Так вы или убедитесь в неправильности придуманного вами алгоритма, или найдёте конкретное место, где ожидаемое поведение программы разошлось с фактическим.
1. Если проблему найти не получилось, напишите в общий чат, обязательно указав:
    1. название задачи и ссылку на условие;
    1. ссылку на вашу работу;
    1. конкретное и подробное описание проблемы или затруднения при решении задачи. «Помогите, что-то не так» — это не описание;
    1. подробное описание вашего анализа программы с помощью отладчика вместе со скринами;
    1. ваши размышления и описание шагов, которые вы совершили для решения.
  ---

</details>

<details>
  <summary>4. Отформатирован код</summary>

Кроме правил, нарушение которых приводит к ошибкам компиляции, есть ещё и [правила форматирования кода](https://google.github.io/styleguide/javaguide.html), соблюдение которых обязательно при написании программ.

С большинством проблем может справиться автоформатирование в идее. Для этого выберите `Code -> Reformat code` в меню или используйте горячие сочетания клавиш. В меню будет показано актуальное сочетание для вашей операционной системы. Так, идея поправит неправильные отступы, пробелы и некоторые другие ошибки. Следите, чтобы у `if-else`, `for`, `while` всегда были `{}`.

Проблемы с именованием сущностей нужно решать самим. Так, все ячейки, кроме `final`-констант, и методы должны писаться [камелкейсом](https://ru.wikipedia.org/wiki/CamelCase) с **маленькой** буквы, а классы и интерфейсы — камелкейсом с **большой** буквы.

Мы вам настоятельно советуем всегда держать код в отформатированном виде во время разработки, со временем глаз привыкнет, и вы почувствуете, насколько это облегчает поиск ошибок в коде и его анализ. В любом случае перед отправкой кода на проверку его обязательно нужно отформатировать, иначе он может быть отправлен на доработку без более глубокой проверки на этой итерации.
</details>


<details>
  <summary>5. Настроен Github CI с verify-сборкой Maven и JaCoCo в режиме генерации отчётов с покрытием на 100% по бранчам методов с логикой </summary>

#### CI
После связывания локального репозитория с удалённым и первого пуша в заготовки проекта, время настроить CI на основе GitHub Actions. Шаблон вашего maven.yml должен выглядеть вот так, убедитесь, что всё совпадает с вашим шаблоном, например, что вы указали фазу `verify`, а не `package`:
  ```yml
  name: Java CI with Maven

  on: [push, pull_request]

  jobs:
    build:

      runs-on: ubuntu-latest

      steps:
      - uses: actions/checkout@v2
      - name: Set up JDK 11
        uses: actions/setup-java@v2
        with:
          java-version: '11'
          distribution: 'adopt'
      - name: Build with Maven
        run: mvn -B -e verify
  ```

#### JaCoCo

  ```xml
              <plugin>
                  <groupId>org.jacoco</groupId>
                  <artifactId>jacoco-maven-plugin</artifactId>
                  <version>0.8.5</version>
                  ...
  ```

Инициализация:
  ```xml
                      <execution>
                          <id>prepare-agent</id>
                          <goals>
                              <goal>prepare-agent</goal>
                          </goals>
                      </execution>
  ```

В режиме генерации отчётов:
  ```xml
                      <execution>
                          <id>report</id>
                          <phase>verify</phase>
                          <goals>
                              <goal>report</goal>
                          </goals>
                      </execution>
  ```

В режиме проверки и обрушения сборки по уровню покрытия:
  ```xml
                      <execution>
                          <id>check</id>
                          <goals>
                              <goal>check</goal>
                          </goals>
                          <configuration>
                              <rules>
                                  <rule>
                                      <limits>
                                          <limit>
                                              <counter>LINE</counter>
                                              <value>COVEREDRATIO</value>
                                              <minimum>100%</minimum>
                                          </limit>
                                      </limits>
                                  </rule>
                              </rules>
                          </configuration>
                      </execution>
  ```

</details>


# Задание 1. Менеджер товаров (обязательное к выполнению)

Вам необходимо реализовать менеджер товаров, который умеет:

* добавлять товары в репозиторий,
* искать товары.

Что нужно сделать:
1. Разработайте базовый класс `Product`, содержащий `ID`, название, стоимость.
1. Разработайте два унаследованных от `Product` класса: `Book` с текстовыми полями «название» и «автор» и `Smartphone` с текстовыми полями «название» и «производитель»; общие поля вынесите в родителя.
1. Разработайте репозиторий, позволяющий сохранять `Product`, получать все сохранённые `Product` и удалять по `ID`. Для этого репозиторий будет хранить у себя поле с типом `Product[]` (массив товаров).
1. Разработайте менеджера, который умеет добавлять `Product` в репозиторий и осуществлять поиск по ним. Для этого вам нужно создать класс, конструктор которого будет принимать параметром репозиторий, а также с методом `publiс void add(Product product)` и методом поиска (см. ниже).

#### Как осуществлять поиск

У менеджера должен быть метод `searchBy(String text)`, который возвращает массив найденных товаров.

```java
public class ProductManager {
  // добавьте необходимые поля, конструкторы и методы

  public Product[] searchBy(String text) {
    Product[] result = new Product[0]; // тут будем хранить подошедшие запросу продукты
    for (Product product: repository.findAll()) {
      if (matches(product, text)) {
        // "добавляем в конец" массива result продукт product
      }
    }
    return result;
  }

  // метод определения соответствия товара product запросу search
  public boolean matches(Product product, String search) {
    if (product.getName().contains(search)) {
      return true;
    } else {
      return false;
    }
    // или в одну строку:
    // return product.getName().contains(search);
  }
}
```

Менеджер при переборе всех продуктов, хранящихся в репозитории, должен для каждого продукта вызывать определённый в классе менеджера же метод `matches`, который проверяет, соответствует ли продукт поисковому запросу.

При проверке на соответствие запросу товара мы проверяем вхождение запроса в текст названия товара.

Напишите тесты на менеджер и репозиторий, добившись 100% покрытия по бранчам методов с логикой.

Итого: отправьте на проверку ссылку на репозиторий GitHub с вашим проектом. 