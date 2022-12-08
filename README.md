# JVM

## Памятка к домашнему заданию
Перед тем, как отправить своё решение на проверку преподавателю, сверьтесь с чеклистом

<details>
  <summary> Что делать, если возникли сложности? </summary>

И это здорово! Если их преодолевать правильно, то можно получить большую образовательную пользу для себя. Периодическое возникновение вопросов, недопонимание пройденного материала - нормальная и неотъемлемая часть обучения. А мы здесь, чтобы помочь вам пройти этот путь.

### Что делать, если непонятна теория?
1. Если подобный вопрос разбирался на лекции, посмотрите еще раз раздел с этой темой в видеозаписи.
1. Если вопрос не решился, попробуйте поискать ответ самостоятельно в интернете, этот навык пригодится вам в работе.
1. Если самостоятельно разобраться не удалось, задайте вопрос в общем чате, мы обязательно поможем.

### Что делать, если непонятно условие задания?
1. Прежде чем задать вопрос по условию задачи, перечитайте его ещё раз и убедитесь, что в тексте условия нет прямого ответа на этот вопрос. Умение работать с текстом - важный навык работы с информацией.
1. Если ответа на свой вопрос в тексте условия не увидели, задайте его в общем чате, мы раскроем детали условия подробнее. Не забудьте при этом скинуть и ссылку на условие задания, про которую у вас вопрос.

### Что делать,если не получается задача?
Если ваша проблема это **ошибка компиляции** (подчёркивает красным, не даёт запустить программу), сборки проекта, CI и прочие подобные ошибки, то:
1. Найдите и прочитайте текст ошибки, который вам подсвечивает реплит, идея (или логи); "подчёркивает красным" - это не описание ошибки.
1. Попробуйте понять текст ошибки, при необходимости воспользуйтесь переводчиком. Нестрашно, если вы переведёте неточно, тут главное сам процесс: со временем и с нашей помощью вы будете это делать лучше и лучше, но, пропуская этот этап, вы не сможете научиться это делать.
1. Если не получилось понять ошибку по её тексту, попробуйте её загуглить и изучить подобную ошибку у других людей. Попробуйте примерить решения их проблем на свой код. Соотнесите найденные описания ошибки с пройденной теорией.
1. Если все равно вашу трудности не разрешились, напишите в общий чат, обязательно указав:
    1. Название задачи и ссылку на условие
    1. Ссылку на вашу работу
    1. Текст и скриншот (не фотография) ошибки.
    1. Ваши размышления и описание шагов, которые вы совершили для решения.

Если ваша проблема это **ошибка исполнения** (программа умирает уже после запуска) или она **отрабатывает неправильно**, то:
1. Воспользуйтесь отладчиком для пошагового анализа работы вашей программы. Так вы либо убедитесь в неправильности придуманного вами алгоритма или найдёте конкретное место, где ожидаемое поведение программы разошлось с фактическим.
1. Если проблему найти не получилось, напишите в общий чат, обязательно указав:
    1. Название задачи и ссылку на условие
    1. Ссылку на вашу работу
    1. Конкретное и подробное описание проблемы или затруднения при решении задачи ("Помогите что не так" - это не описание)
    1. Подробное описание вашего анализа программы с помощью отладчика вместе со скринами
    1. Ваши размышления и описание шагов, которые вы совершили для решения.
  ---

</details>

<details>
  <summary> В решении выполнены все требования задания </summary>

Убедитесь, что все требования задания выполнены. Для этого перед отправкой внимательно прочтите весь текст условия задания и соотнесите сказанное в нём с вашим решением. Навык самопроверки работы перед ревью пригодится вам как при обучении, так и на работе.

  ---

</details>

<details>
  <summary>Сдаём через гитхаб </summary>

Время пришло познакомиться с профессиональными инструментами для контроля версий вашего кода. Теперь мы не сдаём домашние задания в реплите, а заливаем проект из идеи сразу же в публичный гитхаб-репозиторий. Одна задача - один репозиторий.

Для того чтобы в репозитории не отслеживался всякий мусор, не забывайте добавлять `.gitignore`.
В нём должны игнорироваться файлы идеи (правила `*.iml` и `.idea`), папки для автогенерируемых результатов сборки (`out`, позже - `target`).
Этот файл должен находиться в корне вашего репозитория, а сам репозиторий должен быть инициализирован в корне вашего проекта.
Т.е. открывая репозиторий вы должны сразу видеть папку `src`.
Если вы забыли проигнорировать какие-либо файлы и они попали в репозиторий, используйте команду `git rm`.

</details>

## Задача 1 (обязательная)

# Задача "Понимание JVM"

## Описание
Просмотрите код ниже и опишите (текстово или с картинками) каждую строку с точки зрения происходящего в JVM

Не забудьте упомянуть про:
- ClassLoader'ы,
- области памяти (стэк (и его фреймы), heap)
- сборщик мусора

## Код для исследования
```java

public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1
        Object o = new Object();        // 2
        Integer ii = 2;                 // 3
        printAll(o, i, ii);             // 4
        System.out.println("finished"); // 7
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5
        System.out.println(o.toString() + i + ii);  // 6
    }
}

```

Ответ оформите в виде README.md в публичном гитрепо. На проверку скиньте ссылку на этот README.md в вашем репозитории.

___________
# РЕШЕНИЕ
public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1  Объявлена переменная целых числел с наименованием i.
                                        //    Переменная будет храниться в stack.

        Object o = new Object();        // 2  ClassLoader загружает класс Object.
                                        //    Создан объект класса Object в heap (куча) (т.к. создали объект). 
                                        //    Добавлена ссылка на объекта в stack.

        Integer ii = 2;                 // 3  ClassLoader загружает класс Integer.
                                        //    Ссылка переменной ii (Integer) будет храниться в stack.
                                        //    Значение переменной будет храниться в heap. 

        printAll(o, i, ii);             // 4  Вызов метода printAll().
                                        //    В stack выделится память (frame), необходимая для выполнения метода.

        System.out.println("finished"); // 7  В heap создается объект типа String "finished". 
                                        //    String передается методу println() для вывода в консоли.
                                        //    После окончания работы метода println(), работа метода main() завершается, и его frame удаляется из stack.
    }

    private static void printAll(Object o, int i, Integer ii) {

        Integer uselessVar = 700;       // 5  Переменная uselessVar типа Integer будет создана в stack.
                                        //    Значение переменной будет храниться в heap.
                                       
    System.out.println(o.toString() + i + ii); 
                                        //6   Объект типа String создается heap.
                                        //    String передается методу println().
                                        //    После окончания работы метода println() его frame удаляется из stack.
    }
    }
