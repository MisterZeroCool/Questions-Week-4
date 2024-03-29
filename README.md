# <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">Вопросы: Неделя 4!<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">

# Содержание
# [Concurrency](#concurrency)
   - [Q1a](#q1a) Какие проблемы может решить многопоточность?
   - [Q2a](#q2a) Какие проблемы может создать многопоточность?
   - [Q3a](#q3a) С помощью чего организуется многопоточность?
   - [Q4a](#q4a) Конструкторы Thread
   - [Q5a](#q5a) Методы Thread для управления потоками
   - [Q6a](#q6a) Thread Scheduler (тред скедилор)(планировщик потоков)
   - [Q7a](#q7a) synchronized
   - [Q8a](#q8a) Монитор (mutex)
   - [Q9a](#q9a) Методы монитора
   - [Q10a](#q10a) Состав пакета java.util.concurrent
   - [Q11a](#q11a) Concurrent Collections
   - [Q12a](#q12a) Synchronizers (синхронизаторы)
   - [Q13a](#q13a) Executors
   - [Q14a](#q14a) Какие пулы потоков может создавать Executors?
   - [Q15a](#q15a) Lock
   - [Q16a](#q16a) Методы Lock
   - [Q17a](#q17a) Condition, ReadWriteLock, ReentrantLock
   - [Q18a](#q18a) Плюсы и минусы Lock API
   - [Q19a](#q19a) Атомарная операция
   - [Q20a](#q20a) Atomics
   - [Q21a](#q21a) AtomicInteger
 
     ## Concurency в Android
   - [Q22a](#q22a) Looper
   - [Q23a](#q23a) Handler
   - [Q24a](#q24a) Методы Handler
   - [Q25a](#q25a) MessageQueue
   - [Q26a](#q26a) Как взаимодействуют Looper, Handler и MessageQueue?
   - [Q27a](#q27a) Что такое HandlerThread?
   - [Q28a](#q28a) AsyncTask
   - [Q29a](#q29a) Какие методы AsyncTask необходимо переопределить?

# [RxJava](#RxJava)
   - [Q30a](#q30a) Реактивное программирование
     
   - [Q31a](#q31a) Поток данных
   - [Q32a](#q32a) Что нам дает RxJava?
   - [Q33a](#q33a) Observer
   - [Q34a](#q34a) Observable, Observer в RxJava
   - [Q35a](#q35a) Какие события генерирует Observable?
   - [Q36a](#q36a) Какие виды Observable существуют в RxJava?
   - [Q37a](#q37a) Backpressure
   - [Q38a](#q38a) Стратегии по работе с Backpressure в RxJava?
   - [Q39a](#q39a) Disposable
   - [Q40a](#q40a) Чем отличается subscribeOn и observeOn в RxJava?
   - [Q41a](#q41a) Scheduler
   - [Q42a](#q42a) Какие шедулеры (Schedulers) есть в RxJava?
   - [Q43a](#q43a) Чем отличаются hot и cold Observables в RxJava?
   - [Q44a](#q44a) Subject
   - [Q45a](#q45a) Какие бывают Subjects в RxJava?
   - [Q46a](#q46a) Операторы создания
   - [Q47a](#q47a) Операторы преобразования
   - [Q48a](#q48a) Операторы объединения
   - [Q49a](#q49a) flatMap, concatMap, switchMap
  

  
# Concurrency<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">

### Q1a
### Какие проблемы может решить многопоточность?
-одновременное выполнение нескольких действий.

-ускорение вычислений.

-разгрузка пользовательского интерфейса (Android).

[Содержание](#содержание)

### Q2a
### Какие проблемы может создать многопоточность?
-состояние гонки (race condition)-явление, при котором потоки делят между собой некоторый ресурс и код написан таким образом, что не предусматривает корректную работу в таком случае.

-взаимная блокировка (deadlock)-взаимная блокировка, ситуация, когда два или более потока зависают в вечном ожидании ресурсов, захваченных друг другом.

-голодание потоков (livelock)-заключается в том, что потоки внешне как бы живут, но при этом не могут ничего сделать, т.к. условие, по которым они пытаются продолжить свою работу, не могут выполниться. По сути livelock похож на deadlock, но только потоки не "зависают" на системном ожидании монитора, а что-то вечно делают.

-starvation - потоки с более высоким приоритетом получают больше времени на выполнение задачи, а потоки с меньшим приоритетом из за этого страдают и не могут выполнить свою задачу.

[Содержание](#содержание)

### Q3a
### С помощью чего организуется многопоточность?
-интерфейс Runnable.

-класс Thread, который реализует Runnable.

-класса реализующего интерфейс Callable (при выполнении возвращает результат).

[Содержание](#содержание)

### Q4a
### Конструкторы Thread

-Thread()-конструктор без параметров.

-Thread(group:ThreadGroup, target:Runnable, name:String)-конструктор с 3 параметрами где target-экземляр класса реализующего интерфейс Runnable, name-имя создаваемого потока, group-группа к которой относится поток.

[Содержание](#содержание)

### Q5a
### Методы Thread для управления потоками
-getId-получение идентификатора потока.

-getName-получение имени потока.

-getPriority-получение приоритета потока.

-getState-определение состояние потока.

-interrupt-прерывание выполнение потока.

-isAlive-проверка, выполняется ли поток.

-isDaemon-проверка, является ли поток "daemon" (потоки для фоновых действий по обслуживанию основных потоков, имеют меньший приоритет выполнения по сравнению с пользовательскими потоками).

-run-напрямую просто выполняет код синхронно (в том же потоке).

-start-запуск новый поток.

-join-ожидание завершения потока. Также можно указать сколько милисекунд ждать (join(mills)).

-setDaemon-определение "daemon" потока.

-setPriority-определение приоритета потока.

-notify-"пробуждение" отдельного потока, ожидающего "сигнала".

-notifyAll-"пробуждение" всех потоков, ожидающих "сигнала".

-sleep-приостановка потока на заданное время.

-wait-приостановка потока, пока другой поток не вызовет метод notify. Также можно указать сколько милисекунд должна длиться приостановка (wait(mills)).

[Содержание](#содержание)

### Q6a
### Thread Scheduler (тред скедилор)(планировщик потоков)
-контролирует все запущенные потоки во всех программах и решает, какие потоки должны быть запущены, и какая строка кода выполняется. Планировщик идентифицирует процесс по приоритетам потоков и по тому, является ли поток демоном.

[Содержание](#содержание)

### Q7a
### synchronized
-позволяет заблокировать доступ к методу или части кода, если его уже использует другой поток. Нельзя использовать в переменных или атрибутах в определении класса. Гарантирует что несколько потоков не смогут выполнять метод одновременно.

[Содержание](#содержание)

### Q8a
### Монитор (mutex)

-механизм взаимодействия и синхронизации потоков, обеспечивающий доступ к неразделяемым ресурсам. Когда какому-нибудь потоку, нужен общий для всех потоков объект, он проверяет mutex, связанный с этим объектом. Если mutex свободен, то поток блокирует его и начинает его использование. После выполнения всех задач потока mutex разблокируется.

-если поток хочет использовать объект, а mutex заблокирован, то поток засыпает в ожидании. Когда mutex осовобождается, поток тут же заблокирует его и приступит к работе. Встроен в класс Object, т.е. есть у каждого объекта.

-в kotlin, mutex является объектом синхронизации, который может быть использован для координации доступа к общим ресурсам между потоками. mutex обеспечивает взаимное исключение, т.е. только один поток может получить доступ к общему ресурсу в определенный момент времени.

[Содержание](#содержание)

### Q9a
### Методы монитора
-lock()-блокирует ресурс и ожидает, пока он не станет доступным.

-tryLock()-пытается заблокировать ресурс, но не блокирует текущий поток.

-unlock()-освобождает ресурс, ранее заблокированный с помощью lock.

-isLocked()-указывает заблокирован ресурс или нет.

-withLock (action()->Unit)-обеспечивает блокировку и выполнение указанного действия.

-holdsLock (owner:Any?=null)-проверяет, заблокирован ли этот мьютекс указанным владельцем.

[Содержание](#содержание)

### Q10a
### Состав пакета java.util.concurrent
-Concurrent Collections-набор коллекций, более эффективно работающх в многопоточной среде нежели стандартные универсальные коллекции. Используется подход copy-on-write, т.е. при чтении области данных используется общая копия, в случае изменения данных-создается новая копия.

-Synchronizers (синхронизаторы)-вспомогательные утилиты для синхронизации потоков, которые дают возможность разработчику регулировать и/или ограничивать работу потоков и предоставляют более высокий уровень абстракции, чем основные примитивы языка (мониторы).

-Executors-содержит интерфейсы Executor, ExecutorService, SchedulerExecutorService (скедулар) и класс Executors.

-Locks

-Atomics

[Содержание](#содержание)

### Q11a
### Concurrent Collections
-CopyOnWriteArrayList-блокирующий на запись, не блокирующий на чтение список. Любая модификация создает новый экземпляр массива в памяти.

-ConcurrentHashMap-ключ-значение структура, основанная на hash-функции. Отсутствуют блокировки на чтение. При записи блокируется только часть Map (сегмент). Кол-во сегментов ограничено ближайшей к concurrencyLevel степени 2.

-ArrayBlockingQueue-честная очередь для передачи сообщения из одного потока в другой. Поддерживает блокирующие (put,take) и неблокирующие (offer,pool) методы. Запрещает null значения. Емкость очереди должна быть указана при создании.

12. Synchronizers (синхронизаторы)
-CountDownLatch()-счетчик с обратным отсчетом. Останавливает пришедшие потоки, пока внутренний счетчик не достигнет нуля. Начальное значение счетчика задается параметром конструктора, затем уменьшается на 1 методом countDown().

-семафор-счетчик, который можно увеличивать и уменьшать из разных потоков. Уменьшение до 0 блокирует уменьшающий поток. Используется когда необходимо ограничить доступ к некоторому общему ресурсу.


[Содержание](#содержание)

### Q12a
### Synchronizers (синхронизаторы)
-CountDownLatch()-счетчик с обратным отсчетом. Останавливает пришедшие потоки, пока внутренний счетчик не достигнет нуля. Начальное значение счетчика задается параметром конструктора, затем уменьшается на 1 методом countDown().

-семафор-счетчик, который можно увеличивать и уменьшать из разных потоков. Уменьшение до 0 блокирует уменьшающий поток. Используется когда необходимо ограничить доступ к некоторому общему ресурсу.

[Содержание](#содержание)

### Q13a
### Executors
-Executor-интерфейс, содержащий метод execute для запуска Runnable.
(обеспечивает эффективное распределение и управление потоками выполнения для выполнения задач в фоновом режиме.

Использование Executors позволяет упростить многопоточное программирование и повысить производительность приложения за счет эффективного использования доступных ресурсов.

С помощью Executors можно создавать различные типы исполнителей, такие как однопоточный исполнитель (SingleThreadExecutor), исполнитель с фиксированным пулом потоков (FixedThreadPoolExecutor) и исполнитель с кэширующим пулом потоков (CachedThreadPoolExecutor).

Одна из основных функций Executors — планирование и выполнение асинхронных задач. Он предоставляет методы для создания задач, представленных интерфейсом Runnable или Callable, и помещения их в очередь на выполнение в пуле исполнителей.

Также Executors позволяет контролировать количество активных потоков выполнения, устанавливать ограничения на максимальное количество потоков и управлять их жизненным циклом.)

-ExecutorService-более широкий интерфейс, включает в себя метод submit, который аналогичен методу execute, но перегруженные методы submit могут принимать как Runnable так и Callable.
-SchedulerExecutorService-схож с ExecutorService, но добавлена возможность планировать отложенное выполнение.

-класс Executors-включает в себя методы для создания различных типов служб-исполнителей. С помощью этого класса можно создавать пулы потоков.


[Содержание](#содержание)

### Q14a
### Какие пулы потоков может создавать Executors?
-пул потоков-своего рода контейнер, в котором содержатся потоки, которые могут выполнять задачи, и после выполнения одной самостоятельно переходить к следующей. Есть следующие виды пулов потоков:

--newSingleThreadExecutor-пул потоков, в котором есть только один поток.

--newFixedThreadPool-пул потоков, который содержит фиксированное количество потоков.

--newCachedThreadPool-возвращает пул потоков, если в пуле не хватает потоков, в нем будет создан новый поток.

--newScheduledThreadPool-этот пул потоков позволяет запускать задания с определенной периодичностью или один раз по истечении промежутка времени.

[Содержание](#содержание)

### Q15a
### Lock
-обечпечивает все функции ключевого слова synchronized, добавляя новые методы 
для удобной работы.

[Содержание](#содержание)

### Q16a  
### Методы Lock
 -lock-используется для того, чтобы получить lock для работы.

-unlock-освободить lock.

-tryLock-для ожидания лока на протяжении определенного времени.

-newCondition-создает Condition и т.п.
 
[Содержание](#содержание)

### Q17a   
### Condition, ReadWriteLock, ReentrantLock
-Condition-похож на wait-notify. Создается с помощью объекта Lock. Метод await похож на wait, методы signal и signalAll на notify и notifyAll.

-ReadWriteLock-содержит пару связанных локов: первый только для чтения, второй для записи. Лок для чтения может предоставлять доступ одновременно для нескольких потоков.

-ReentrantLock-реализация интерфейса Lock. Один и тот же поток может перезахватывать уже захваченный лок.
    
[Содержание](#содержание)

### Q18a
### Плюсы и минусы Lock API
+обеспечивает больше возможностей для блокировки, в отличие от synchronized, где поток может бесконечно ожидать лок. Можно использовать метод tryLock, чтобы ожидать лок только определенное время.

+блоки синхронизации могут покрывать только один метод, в то время как Lock API позволяет получить лок в одном месте, а снять его в другом.

-синхронизированный код намного чище и проще в поддержке. При использовании Lock API необходимо писать try-finally блоки.
  
[Содержание](#содержание)

### Q19a
### Атомарная операция
-операция либо применится полностью, либо не применится вообще.
  
[Содержание](#содержание)

### Q20a
### Atomics
-классы с поддержкой атомарных операций над примитивами и ссылками. Для решения проблем, которые могут возникнуть в многопоточной среде, в Java Persistence API реализован механизм под названием Optimistic Lock, который позволяет нескольким потокам одновременно изменять данные не мешая друг другу.

[Содержание](#содержание)

### Q21a   
### AtomicInteger
-предоставляет операции с базовым значением int, которые могут быть прочитаны и записаны атомарно, а также содержит расширенные атомарные операции. AtomicInteger поддерживает атомарные операции с базовой переменной int. У него есть методы get и set, которые работают как чтение и запись по переменным.

[Содержание](#содержание)

## ⭐Concurency в Android

### Q22a
### Looper
-запускает цикл обработки сообщений, связанный с потоком. Поток работает, пока связанный с ним лупер не будет остановлен. 

-для создания лупера, вызывается статический метод Looper.prepare(). Созданный лупер будет связан с потоком, в котором вызван этот метод. Для старта лупера используется статический метод Looper.loop(). Для остановки лупера используется метод quit() или quitSafely(). Разница между этими методами в том, что quit() останавливает лупер незамедлительно, а quitSafely() завершает обработку сообщений, которые уже добавлены в очередь.

[Содержание](#содержание)

### Q23a
### Handler
-класс, который используется для работы с очередью сообщений, связанной с потоком. Хэндлер позволяет отправлять сообщения в другие потоки с задержкой или без, а также обрабатывать полученные сообщения. 

-хэндлер всегда связан с лупером, который в свою очередь связан с каким-либо потоком. При создании хэндлера в конструктор можно передать объект Looper. Если используется дефолтный конструктор, то хэндлер создается на текущем потоке. Если с потоком не связан лупер, то при создании хэндлера бросается RuntimeException.
  
[Содержание](#содержание)

### Q24a
### Методы Handler
-sendMessage-помещает сообщение в очередь немедленно (в конец очереди).

-sendMessageAtFrontofQueue-помещает сообщение в очередь немедленно с приоритетом над другими сообщениями.

-sendMessageAtTime-помещает сообщение в очередь в установленное время в миллисекундах.

-sendMessageDelayed-помещает сообщение в очередь после задержки, выраженной в милисекундах.

[Содержание](#содержание)

### Q25a
### MessageQueue
-очередь сообщений с которой работают Looper и Handler. Message-контейнер для набора инструкций, которые будут выполнены в заданном потоке, или в том же потоке, если он не был задан.

[Содержание](#содержание)

### Q26a
### Как взаимодействуют Looper, Handler и MessageQueue?
-по своей сути Looper, Handler и MessageQueue реализуют шаблон producer/consumer. Тред-продюсер отправляет сообщения через Handler в коллекцию-буфер, реализованную классом MessageQueue. Тред-потребитель блокирован с помощью класса Looper, который ожидает и принимает сообщения из MessageQueue и передает их на обработку хэндлеру.

[Содержание](#содержание)

### Q27a
### Что такое HandlerThread?
-наследник класса Thread, который создан для облегчения работы с лупером. При старте потока HandlerThread, looper инициализируется методом Looper.prepare() и вызывается HandlerThread.onLooperPrepared(). 
-HandlerThread.onLooperPrepared() можно переопределить в наследнике класса HandlerThread и использовать для выполнения подготовки перед зацикливанием лупера. После onLooperPrepared() HandlerThread вызывает looper.loop(). Также HandlerThread имеет методы quit() и quitSafe(), которые делегируют вызовы на соответствующие методы класса Looper.

[Содержание](#содержание)

### Q28a
### AsyncTask
-используется для выполнения тяжелых задач и передачи в UI-поток результатов работы. Чтобы работать с AsyncTask, надо создать класс-наследник и в нем прописать свою реализацию необходимых нам методов. Метод execute используется 
для получения данных.

[Содержание](#содержание)

  ## ⭐Broadcasts

### Q29a
### Какие методы AsyncTask необходимо переопределить?
-doInBackground-будет выполнен в новом потоке,  здесь решаем все свои тяжелые задачи. Нет доступа к UI.

-onPreExecute-выполняется перед doInBackground, имеет доступ к UI.

-onPostExecute-выполняется после doInBackground. Не сработает если AsyncTask отменен. Имеет доступ к UI.
  

[Содержание](#содержание)

## ⭐RxJava

### Q30a
### Реактивное программирование
  -парадигма программирования, ориентированная на потоки данных и распространение изменений. А по простому, на работу с асинхронными потоками данных.

[Содержание](#содержание)

### Q31a
### Поток данных
-последовательность, состоящая из постоянных событий, отсортированных по времени.

#-[Содержание](#содержание)

## ⭐Content provider

### Q32a  
### Что нам дает RxJava?
-обеспечение многопоточности.

-управление потоками, обработка потоков данных.

-обработка ошибок, а также дополнительные обработчики состояний.

-работа с трансформациями кода.

-приемлимый код (при использовании лямбда-выражений).

#-[Содержание](#содержание)

### Q33a
### Observer
-паттерн проектирования, который создает механизм подписки, позволяющий одним объектам следить и реагировать на события, происходящие в других объектах.

[Содержание](#содержание)

### Q34a
### Observable, Observer в RxJava

-Observable генерирует событие, а Observer получает его. В RxJava события, 
которые Observable передает в Observer, можно рассматривать как поток данных. 

[Содержание](#содержание)

### Q35a
### Какие события генерирует Observable?
-next-очередная порция данных.

-error-произошла ошибка.

-completed-поток завершен и данных больше не будет.

[Содержание](#содержание)

### Q36a
#### Какие виды Observable существуют в RxJava?

    1. Single - представляет собой результат выполнения операции, который может либо завершиться успешно с одним значением, либо завершится неудачно.
    2. Completable - представляет операцию, которая либо завершится успешно, либо неудачно без генерации значений.
    3. Maybe - представляет собой результат операции, который может завершиться успешно либо неудачно, либо не вернуть никакого значения.
Кроме того, существуют и более распространенные виды Observable:
    1. Observable - представляет последовательность значений, которые могут быть преобразованы, фильтрованы и обработаны.
       
    2. Flowable - представляет последовательность значений с управлением памятью для поддержки обработки большого объема данных.


-Observable–представляет собой поток (стрим) объектов. Подписчики на Observable имеют коллбэки onNext(value), onComplete(), onError(throwable). 
	onNext() может не вызываться, или вызываться произвольное количество раз. При завершении стрима вызывается onComplete() или onError().

-Single–отправляет объект, который принимается в коллбэке onSuccess(value), или бросает исключение в коллбэк onError(throwable) в случае ошибки.

-Completable–не возвращает никакого значения. На подписчиках вызывается onComplete() при удачном завершении или onError(throwable) в случае ошибки.

-Maybe–может отработать как Single или как Completable. На подписчиках вызывается один из трех коллбэков: onSuccess(value), onComplete() без какого-либо значения, или onError(throwable). Каждый из коллбэков может быть вызван один раз или не вызван вообще.

-ConnectableObservable-не начинает эмитить элементы, пока не будет вызван метод connect(). Это позволяет подписчикам подключаться к одному и тому же потоку данных, начиная с одного и того же момента времени, независимо от того когда они подключаются, т.е. позволяет создать горячий источник данных.

-Flowable–работает как Observable, но поддерживает backpressure по умолчанию. Используется когда требуется обрабатывать более 10000 событий.

[Содержание](#содержание)

### Q37a
#### Backpressure
-ситуация, когда Rx-продюсер (Observable) производит больше элементов, чем может обработать консьюмер (Observer). В случаях когда возможна ситуация backpressure, следует использовать Flowable в качестве Rx-стрима.

[Содержание](#содержание)

### Q38a
### Стратегии по работе с Backpressure в RxJava?
-MISSING-продюсер не имеет стратегию работы с backpressure. В этом случае консьюмер должен решать проблему переполнения.

-ERROR-в случае backpressure бросается исключение MissingBackpressureException.

-BUFFER-все элементы добавляются в буфер, пока не будут обработаны консьюмером.

-DROP-все новые элементы, которые консьюмер не успевает обработать, удаляются и не доставляются консьюмеру.

-LATEST-консьюмер получает только самый последний элемент, созданный продюсером, когда освобождается.

[Содержание](#содержание)

### Q39a
### Disposable

-механизм управления подпиской. С помощью метода dispose() можно отписаться, а с помощью isDisposed() проверить текущий статус подписки.

-для работы с подпиской можно использовать DisposableObserver (одновременно Observer и Disposable). Также DisposableObserver сам реализует метод onSubscribe и скрывает его от вас.

[Содержание](#содержание)


### Q40a
### Чем отличается subscribeOn и observeOn в RxJava?

-subscribeOn()–задает Scheduler (поток), на котором выполняется подписка на Observable. Другими словами, код метода Observable.create() выполняется в потоке, заданном subscribeOn(). При использовании нескольких используется первый.

-observeOn()–задает Scheduler (поток), на котором выполняются операторы, следующие после observeOn(). В Rx-стриме может быть несколько observeOn(), каждый из которых будет менять поток выполнения.


[Содержание](#содержание)

### Q41a
### Scheduler
-это обертка над Executor. Observable поручит выполнение кода шедулеру, а тот уже выполнит его в потоке своего Executor.

[Содержание](#содержание)

### Q42a
### Какие шедулеры (Schedulers) есть в RxJava?
-Schedulers.io()-выполнение задач, которые не сильно нагружают процессор, но являются долгими, сетевые запросы, база данных.

-Schedulers.computation()-основывается на ограниченном пуле потоков с размером в количество доступных ядер процессора. Тяжелые вычислительные задачи, нагружающие CPU.

-Schedulers.single-основывается на единственном потоке, который используется для последовательного выполнения задач.

-Schedulers.newThread-новый поток для каждой новой задачи.

-Schedulers.immediate-выполнение задачи в том же потоке.

-AndroidSchedulers.mainThread-главный поток Android приложения.

[Содержание](#содержание)

### Q43a
### Чем отличаются hot и cold Observables в RxJava?
-Cold Observable (interval, from):

--Не рассылает объекты, пока на него не подписался хотя бы один подписчик.

--Если observable имеет несколько подписчиков, то он будет рассылать всю последовательность объектов каждому подписчику.

-Hot Observable (Subject, ConnectedObservable):

--Рассылает объекты, когда они появляются, независимо от того есть ли подписчики.

--Каждый новый подписчик получает только новые объекты, а не всю последовательность.

[Содержание](#содержание)

### Q44a
### Subject
-объект, который является одновременно и Observer и Observable. Т.е. он может подписываться на Observable и получать от них данные, и, в то же время, у него могут быть подписчики, которым он эти данные будет пересылать.

[Содержание](#содержание)

### Q45a
### Какие бывают Subjects в RxJava?
-Publish Subject-подписчики получают только те элементы, которые отправляются после момента подписки.

-ReplaySubject-по-умолчанию каждый новый подписчик получает все элементы, которые были отправлены до подписки, и все последующие элементы.

-BehaviorSubject-отправляет каждому новому подписчику последний элемент, который был разослан до подписки, и все последующие элементы.

-AsyncSubject-подписчики получают только последний элемент, который был отправлен перед вызовом onComplete(). Если onComplete не вызовется, элемент получен не будет.


[Содержание](#содержание)

### Q46a
#### Операторы создания
-map-преобразует все элементы Observable, применяя функцию к каждому элементу.

-buffer-собирает элементы и по мере накопления заданного количества отправляет их дальше одним пакетом.

-ToList/toSortedList/toMap и др.-преобразует данные в различные коллекции. После преобразования, коллекции обернуты в Single.

[Содержание](#содержание)

### Q47a
### Операторы преобразования

-map-преобразует все элементы Observable, применяя функцию к каждому элементу.

-buffer-собирает элементы и по мере накопления заданного количества отправляет их дальше одним пакетом.

-ToList/toSortedList/toMap и др.-преобразует данные в различные коллекции. После преобразования, коллекции обернуты в Single.

[Содержание](#содержание)

### Q48a
### Операторы объединения
-zip-по парно сопоставит элементы из двух Observable. Из каждой пары элементов с помощью функции будет получен один элемент, который будет добавлен в итоговый Observable.

-combineLatest-аналогичен zip, но в отличие от него, не ждет, когда придет самый медленный элемент пары, а просто берет последние полученные элементы с каждого Observable каждый раз когда приходит новый элемент из любого Observable.

-merge-объединяет элементы из нескольких Observable в один. Не гарантирует порядок, т.к. позволяет вставлять элементы параллельно. Позволяет задать maxConcurrent - количество Observable.

-concat-это merge c maxConcurrent = 1. Он всегда будет последовательно запускать переданные ему Observable, т.е. он сохраняет порядок.


[Содержание](#содержание)

### Q49a
### flatMap, concatMap, switchMap
-flatMap-преобразует элементы, излучаемые Observable в Observables. Не поддерживает порядок эмиссии данных.

-concatMap-аналогичен flatMap, но поддерживает порядок эмиссии данных и ожидает исполнения текущего Observable.

-switchMap-аналогичен concatMap, но эмитит данные только из текущего Observable, т.е. как только стартует следующий Observable, предыдущий останавливается.
