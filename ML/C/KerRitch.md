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
## Ch 6
