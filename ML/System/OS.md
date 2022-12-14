* Слово состояния программы (PSW) - 128-разрядная область данных в процессоре, содержащая адрес следующей выполняемой инструкции и флаги, необходимые для выполнения (режим ядра, активность прерываний ввода-вывода, внешних прерываний ...).
	* Каждый процессор имеет только одно текущее слово состояния. Для обработки прерываний требуется 3: текущее, новое, старое: текущее сохраняется в старое, новое - в текущее.
## Процессы
* Демон - фоновый процесс, активирующийся по прерыванию (поступление данных, действие).
* Дочерний процесс создаёт копию адресного пространства родителя, но физически память разная. Могут использовать совместно память родительского, но при записи копируется и совместно не используется.
* Процесс может сообщить ОС, какие ошибки будет обрабатывать самостоятельно
* Unix - иерархия, процессы не могут лишиться наследственной связи. Корень дерева всех процессов - init - инициализирует UNIX
* Windows - единственная связь с дочерним процессом - дескриптор (используется для управления процессом), который можно передать другому процессу.
* Состояния процесса:
	* Выполняемый - выполняется на ЦП
	* Готовый - приостановленный планировщиком
	* Заблокированный - ожидание внешнего события
* Таблица процессов - структура, данные которой позволяют менять состояние процесса.
|Управление процессом|Управление памятью|Управлене файлами|
|---|---|---|
|Регистры|Указатель на инструкцию|Корневой каталог|
|Счётчик команд|Указатель на данные|Рабочий каталог|
|Слово состояния программы|Указатель на стек|Дескрипторы файлов|
|Указатель стека||Идентификатор пользователя|
|Состояние процесса||Идентификатор группы|
|Приоритет|||
|Параметры планирования|||
|Идентификатор процесса|||
|Родительский процесс|||
|Группа процесса|||
|Сигналы|||
|Время запуска процесса|||
|Использованное время процессора|||
|Время процессора, использованное дочерними процессами|||
|Время следующего аварийного сигнала|||
* Вектор прерываний - таблица адресов обработчиков прерываний (обычно фиксированная область в нижних адресах)
* Обработка прерываний
	1. Счётчик команд помещается в стек
	2. Новый счётчик команд загружается из вектора прерывания
	3. Процедура на ASM сохраняет регистры
	4. Процедура на ASM устанавливает указатель на новый стек
	5. Запускается процедура на C, обслуживающая прерывание (как правило, считывает входные данные, помещает их в буфер)
	6. Планировщик выбирает следующий процесс
	7. Процедура на C возвращает управление ASM коду
	8. Процедура на ASM запускает новый текущий процесс
## Потоки (управления)
* Процесс имеет адресное пространство и поток управления.
	* Потоки похожи на процессы с общим адресным пространством. Процесс внутри процесса. Например, потоки в текстовом редакторе: обработка ввода, поток форматирования, поток сохранения резервной копии, поток поиска.
	* Легче / быстрее создавать (в 10-100 раз)
	* Позволяют параллелить вычисления (загружать ЦП или использовать несколько)
	* Позволяют распараллелить выполнение при сохранении идеи последовательных процессов, осуществляющих блокирующие системные вызовы.
* Варианты распараллеливания
	* Потоки - параллель, блокирующие системные вызовы
	* Однопоточный процесс - последовательная обработка, блокирующие системные вызовы
	* FSM - параллель, неблокирующие вызовы, прерывания - усложняет программирование
* Процесс - объединение связанных ресурсов. Поток - набор инструкций, выполняемых с общими ресурсами.
	* Общие глобальные переменные
	* Доступ к стеку других потоков - по одному фрейму на каждую вызванную, но не вернувшую управление, процедуру: локальные переменные и адрес возврата.
	* Защиты между потоками нет
	* Общие дочерние процессы
|Элементы процесса|Элементы потока|
|---|---|
|Адресное пространство|Счётчик команд|
|Глобальные переменные|Регистры|
|Открытые файлы|Стек|
|Дочерние процессы|Состояние|
|Необработанные аварийные сигналы||
|Сигналы и обработчики сигналов||
|Учётная информация||
Сложности:
* fork - создавать ли у дочернего процесса столько же потоков, как у родительского
* Блокировка родительского потока блокирует аналогичный поток дочернего? Входные данные копируются для потока каждого процесса?
* Закрытие файла, используемого потоком другого процесса. Выделение доп. памяти в приостановленном процессе выделения памяти (дочерний + родительский)
### POSIX
Стандарт Pthreads (IEEE 1003.1c), например:
* pthread_create - создание нового потока
* pthread_exit - завершение работы вызвавшего потока
* pthread_join - ожидание выхода из указанного потока
* pthread_yield - освобождение ЦП для другого потока
* pthread_attr_init - создание и инициализация структуры атрибутов потока
	* размер стека, параметры планирования и другие элементы, необходимые для использования потока
* pthread_attr_destroy - удаление ---
* 
