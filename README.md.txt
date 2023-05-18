# Описание действий JVM при залуске программы

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

1.  В stack создаётся frame для метода main(). В frame(main()) помещается переменная примитивного типа int i = 1.

2.  В heap создается объект класса Object, в frame (main()) помещается ссылка на о .

3.  В heap создается объект класса Integer со значением 2, в frame (main()) помещается ссылка на ii.

4.  В stack создаётся новый frame для метода printAll().Туда записываются переменные o, i, ii.

5.  В heap создается объект класса Integer со значением 700, в frame(printAll()) помещается ссылка на uselessVar.

6.  В stack создается frame для метода println(), куда направляются все ссылки переменных из фреймов main() 
    В stack создается frame для метода toString(), в heap сохраняется результат работы метода.

7.  После выхода из метода printAll() сборщик мусора удаляет этот frame.
    Создается frame для метода println(). В heap помещается String("finished").
    
    После выполнения метода main() удаляется фрейм этого метода.
