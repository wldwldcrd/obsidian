## Ch 5
int *f(); /* f - функция, возвращающая указатель на int */
int (*pf)(); /* pf - указатель на функцию, возвращающую int */
`char **argv
argv: pointer to pointer to char
{argv: указатель на указатель на char)
`int (*daytab)[13]
daytab: pointer to array[13] of int
{daytab: указатель на массив[13] типа int)
`int *daytab[13]
daytab: array[13] of pointer to int
(daytab: массив[13] указателей на int)
`void *comp()
comp: function returning pointer to void
{comp: функция, возвращающая указатель на void)
`void (*comp)()
comp: pointer to function returning void
{comp: указатель на функцию, возвращающую void)
`char (*(*x()) []) ()
x: function returning pointer to array[] of
pointer to function returning char
(x; функция, возвращающая указатель на массив []
указателей на функцию, возвращающую char)
`char (*(*x[3]) ()) [5]
х: array[3] of pointer to function returning
pointer to array[5] of char
(x; массив [З] указателей на функцию, возвращающую
указатель на массив[5] типа char)
## Ch 7
* printf string:
``:%S: :hello, world:
``:%10s: :hello, world:
``:%.10s: :hello, wor:
``:%-10s: :hello, world:
``:%.15s: :hello, world:
``:%-15s: :hello, world      :
``:%15.10s: :     hello, wor:
``:%-15.10s: :hello, wor     :
* Print max symbols from s: `printf("%.*sM, max, s);
### Строки
streat (s, t) присоединяет t в хвост к s
strncat (s, t, n) присоединяет п символов из t в хвост к s
strcmp (s,t) дает отрицательное, нуль или положительное число при s < t, s == t, s > t соответственно
strncmp (s, t, n) то же, что strcmp, но выполняется над первыми п символами
strcpy(s,t) KonnpyeTtBs
strncpy (s, t, n) копирует не более п символов t в s
strlen (s) вычисляет длину s
strchr (s, с) возвращает указатель на первый символ с в s или null, если символ не найден
strrchr (s, с) возвращает указатель на последний символ с в s или null, если символ не найден
### Символы
i salpha (с) не нуль, если с — алфавитный символ; 0, если нет
isupper (с) не нуль, если с — буква в верхнем регистре; 0, если нет
islower (с) не нуль, если с — буква в нижнем регистре; 0, если нет
isdigit (с) не нуль, если с - цифра; 0, если нет
isalnum(c) не нуль, если выполняется isalpha (с) или isdigit (с); 0, если нет
isspace(c) не нуль, если с— пробел, табуляция, конец строки, возврат каретки, перевод страницы, вертикальная табуляция
toupper (с) возвращает символ с, приведенный к верхнему регистру
tolower (с) возвращает символ с, приведенный к нижнему регистру

int ungetc(int с, FILE *fp) - помещает символ с назад в файл f p и возвращает либо с, либо EOF в случае ошибки. Для каждого файла гарантирован возврат только одного символа. Функцию ungetc можно использовать совместно с любой из функций ввода scanf, getc или getchar.
### Выполнение команд
Функция system (char *) выполняет команду, содержащуюся в символьной 
строке s, а затем возобновляет выполнение текущей программы.
### Управление памятью
`void *malloc(size_t n)` - возвращает указатель на n байт неинициализированной памяти или NULL
`void *calloc(size_t n, size_t size)
Возвращают void *, поэтому нужно привести к нужному типу:  `ip = (int *) calloc(n, sizeof(int));
`free(p)` освобождает участок памяти, полученный !только malloc или calloc
### Математические функции
s in (х) синус х, х в радианах
cos (x) косинус х, х в радианах
atan2 (у, х) арктангенс отношения у/х в радианах
exp (x) экспоненциальная функция (е в степени х)
log(x) натуральный логарифм х (х > о)
logio(x) десятичный логарифм х (х > о)
pow(x,y) х в степени у
sqrt(x) квадратный корень из х (при условии х >= о)
fabs(x) абсолютное значение х
### Генерирование случайных чисел
* *`rand()` вычисляет последовательность псевдослучайных целых чисел в
диапазоне от 0 до RAND_MAX— величины, определенной в файле <stdlib.h>.
* *`#define frand() ((double) rand() / (RAND_MAX+1.0))`
* Функция `srand (unsigned)` устанавливает для rand инициализирующее значение.
# Unix
Перенаправление стандартных потоков ввода-вывода: `prog <infile >outfile`
`int n_read = read(int fd, char *buf, int n);`
`int n_written = write(int fd, char *buf, int n);`
