vim hard
========

vim hard

:help ^w
:help NERDTree

let g:pymode_python = 'python3'

:sudo update-alternatives --config editor
sudo update-alternatives --set vim /usr/bin/vim.nox-py2
sudo update-alternatives --set vim /usr/bin/vim.gtk3

Файл настройки: ~/.vimrc
Можно редактировать файлы через сеть, например
:e <scp|ftp|ftps>://user@host/path/to/the/file.txt
:Ex или :e ./ - файловый менеджер


== Основы ==
hjkl                      перемещение в разные стороны
i                         режим вставки
I                         добавление в начало строки
a                         режим добавления
A                         добавление в конец строки
o                         добавить строку сразу за текущей
O                         добавить строку перед текущей
R                         писать поверх имеющегося текста
u, :u[ndo]                отмена предыдущего действия (undo)
CTR-R, :red[o]            отмена отмены предыдущего действия (redo)
dd                        вырезать (удалить) строку
cc                        удалить и начать редактирование
yy                        копировать строку
p                         вставить из буфера обмена
<n>d                      удалить n+1 строку
<n>y                      скопировать n+1 строку
ESC                       перейти в режим просмотра
DEL                       удалить следующий символ
:<n>                      перейти на строку #n
%                         перейти к парной скобке
:e **/filename.c          редактировать файл (с поиском по имени)
:w [fname]                записать изменения
:wa                       сохранить изменения во всех файлах
:q                        выйти из редактора
:q!                       выйти из редактора, не сохраняя изменения
:color <name>             выбор цветовой схемы. цветвые схемы:
                            /usr/local/share/vim/vim72/colors/*.vim
:pwd                      текущий каталог
:cd [path]                перейти в другой каталог
:!команда                 выполнить команду - man, git, и так далее
                            стрелочками веерх и вниз можно автодополнять
                            команды и искать по истории
CTR+p или CTR+n           автоматическое дополнение текста
                            (в режиме редактирования)
CTR+r,=,<expr>            вставить выражение, например 5*2 - 3
                            (в режиме редактирования)
CTR+u, CTR+d              Page Up / Page Down
CTR+y, CTR+e              Перемотка вверх/вниз без движения курсора               


== Подсветка синтаксиса ==
:syntax on                включить подсветку
:syntax off               выключить подсветку (по умолчанию)


== Перенос строк ==
:set wrap                 разрешить word wrap (по умолчанию)
:set nowrap               запретить word wrap


== Печать ==
:ha[rdcopy]                   распечатать документ
:set printoptions=duplex:off  отключить двустороннюю печать


== Сворачивание ==
zc                        свернуть блок
zo                        развернуть блок
zM                        закрыть все блоки
zR                        открыть все блоки
za                        инвертирование
zf                        см :set foldmethod=manual
:set foldenable           включить свoрачивание
:set foldmethod=syntax    сворачивание на основе синтаксиса
:set foldmethod=indent    сворачивание на основе отступов
:set foldmethod=manual    выделяем участок с помощью v и говорим zf
:set foldmethod=marker    сворачивание на основе маркеров в тексте
:set foldmarker=bigin,end задаем маркеры начала и конца блока


== Маркеры ==
ma                        установить локальный маркер a
mB                        установить глобальный маркер B
`c                        перейти к локальному маркеру c
`0                        вернуться на позицию, на которой закончили
                            работу при закрытии vim
:marks                    просмотр маркеров
set viminfo='1000,f1      маркеры пишутся в ~/.viminfo, восстанавливаясь
                            при следующем запуске vim. маркер " хранит
                            последнюю позицию курсора в файле
== Сессии ==
mksession file.session    сохранить текущую сессию
source file.session       восстановить ранее сохраненную сессию


== Макросы ==
qa                        записать макрос с именем a
q                         в режиме записи макроса: закончить запись
@a                        выполнить макрос с именем a
@@                        повторить последний макрос


== Регистры ==
"ayy                      скопировать строку в регистр a
"bdd                      вырезать строку и поместить в регистр b
"С2d                      вырезать три строки и дописать в конец
                            регистра C
:reg [name1][name2][...]  просмотреть содержимое регистров


== Выделение ==
v + hjkl                  выделение текста
SHIFT + v                 выделить строку
CTR + v                   выделение прямоугольника
v$                        выделить от курсора до конца строки
p                         вставить
y                         копировать
d                         удалить
gu                        к нижнему регистру
gU                        к верхнему регистру
gv			  повторить сброшенное выделение
o, SHIFT + o		  изменить выделение с противоположного края (углы для блоков)

== Отступы ==
[#]>                      сдвинуть выделенное вправо
[#]<                      сдвинуть выделенное влево
[#]>>                     сдвинуть строку вправо
[#]<<                     сдвинуть строку влево
set tabstop=#             для табуляции используется # пробелов
set shiftwidth=#          в командах отступа используется # пробелов 
set [no]expandtab         заменять ли табуляцию на соответствующее
                            число пробелов


== Поиск и замена в файле ==
/Выражение               поиск выражения в файле
\cВыражение              поиск без учета регистра
n                        следующее совпадение
N                        предыдущее совпадение
:%s/foo/bar/gi           замена строк, см http://eax.me/regular-expr/


== Поиск по всему проекту ==
:vimgrep /EXPR/ **/*.c   поиск по регулярному выражению
:copen                   показать все найденные места
:close                   скрыть все найденные места
:cn                      переход к следующему результату
:cp                      переход к предыдущему результату


== Нумерация строк ==
:set number              включить нумерацию строк
:set nonumber            отключить нумерацию строк


== Работа с вкладками (a.k.a табами) ==
:tabnew [fname]          создать таб
:tabs                    вывести список табов
:tabn                    следующий таб
:tabp                    предыдущий таб
<n>gt                    перейти на таб #n
gt                       следующий таб
gT                       предыдущий таб
:tabm +1                 переместить таб вперед на одну позицию
:tabm -1                 переместить таб назад на одну позицию
:tabm 2                  переместить таб на заданную позицию
                           (нумерация начинается с нуля)


== Работа с окнами ==
:split                   горизонтальное разбиение
:vsplit                  вертикальное разбиение
Ctr+W, затем
  с                      закрыть окно
  +-                     изменение высоты текущего окна
  <>                     изменение ширины текущего окна
  =                      установить равный размер окон
  hjkl или стрелочки     перемещение между окнами


== Проверка орфографии ==
    mkdir -p ~/.vim/spell
    cd ~/.vim/spell
    wget http://ftp.vim.org/vim/runtime/spell/ru.koi8-r.sug
    wget http://ftp.vim.org/vim/runtime/spell/ru.koi8-r.spl
    wget http://ftp.vim.org/vim/runtime/spell/en.ascii.sug
    wget http://ftp.vim.org/vim/runtime/spell/en.ascii.spl


:set spell spelllang=ru,en       включить проверку орфографии
:set nospell                     выключить проверку орфографии
]s                               следующее слово с ошибкой
[s                               предыдущее слово с ошибкой
z=                               замена слова на альтернативу из списка
zg                               good word
zw                               wrong word
zG                               ignore word


== Работа с кодировкой ==
e ++enc=<имя кодировки>         Редактирование файла в ??? кодировке
w ++enc=<имя кодировки>         Сохранить файл в новой кодировке
set fileencodings=utf-8,koi8-r  Список автоматически определяемых
                                  кодировок в порядке убывания
                                  приоритета


== Другое ==
:set [no]wildmenu          При авто-дополнении в командной строке над
                             ней выводятся возможные варианты
:set list                  Отображать табуляцию и переводы строк
q:                         История команд
.                          Повторение последней команды




vip - выделить параграф
viw - выделить слово
Shift+v или 0v$ - выделить строку
^v$ - выделить строку, начиная с первого непробельного символа
vi( - выделить всё между ближайшими круглыми скобками (аналогично 'vi[' и 'vi{' для квадратных и фигурных скобок)
va( - выделить всё между ближайшими круглыми скобками, включая сами скобки
v2j - выделить на две строки вниз
dip - вырезать параграф
di( - вырезать содержимое круглых скобок
da( - вырезать содержимое круглых скобок и сами скобки
y2y - скопировать две строки
yy - скопировать строку
yiw - скопировать слово
p - вставить после курсора
[p - вставить перед курсором
xp - поменять две буквы местами
vt, - выделить всё до ближайшей запятой




И так, буфер это некий сеанс редактирования определённого файла. К примеру если вы открыли .vimrc и в запущенном виме выполнели :e .bashrc, то откроется .bashrc. Тем не менее буфер с .vimrc останется открытым и доступным для редактирования. Вот основные команды для работы с буферами:
:bn следующий буфер
:bp предыдущий
:ls просмотреть открытые буферы
:b имя_буфера переключиться на буфер, очень удобно комбинируется с табом, к примеру пишем :b domain, жмём таб и нам подставляется открытый iis_domain.cpp
:bd удалить текущий буфер, правда стоит заметить, что если этот буфер единственное окно то vim закроется
:bd имя_буфера удалить буфер по имени


Чем хороши буферы по сравнению с табами? Во первых в vim табы — это теже буферы, только навигация по ним проходит по иному. Проблема табов в том, что они нацелены на визуальную навигацию, а когда вы увлечённо программируете в vim, вам как и мне наверное лень тянуться до мыши и вы точно знаете какой файл хотите редактировать, пишите :b имя — и всё! Ну это конечно же моё имхо :)


С буферами разобрались, поехали дальше. Как я сказал в первом абзаце — иногда нужно часто скакать между файлами, и не табы не буферы просто так проблему не решают. Гораздо удобнее было бы разбить окно на два по вертикали или горизонтали. Сразу из места в карьер, боевой пример: вам нужно узнать определение какой-то функции, если тэги сгенерированны, то достаточно нажать Ctrl-] чтобы перейти на него. Но откроется новый буфер, что не очень удобно. Если же нажать Ctrl-w ] то окно будет разбито по вертикали, и в новом окне будет определение.
Удобно? Мне да. Окошко можно закрыть старым добрым :q или удалить буфер :bd. Чтобы сделать окно единственным (читай развернуть), то выполняем комбинацию Ctrl-w o. Краткое описание работы с окнами:
Ctrl-w стрелочки :) — переместиться на окно влево/вправо/вверх/вниз
Сtrl-w o — развернуть окно
Ctrl-w c — закрыть
Ctrl-w s — разделить окно по горизонтали
Ctrl-w v — тоже, только по вертикали
Ctrl-w ] — разделить и перейти на определение чего-то, что под курсором
Ctrl-w f — разделить и в новом окне открыть файл путь к которому находится под курсором, очень удобно делать на инклюдах
Команды:
:split — разделить, если указан файл то открыть его
:vsplit — тоже только по вертикали
:sb[uffer] — разделить и редактировать буффер. Важный момент: если заново открыть файл (к примеру через :split) то буфер сбрасывается, вместе с историей отмен и положением курсора


100 команд vim, которые должен знать каждый
Поиск

/word	Искать слово “word” сверху вниз
?word	Искать слово “word” снизу вверх
/jo[ha]n>	Искать “john” или “joan”
/\< the	Искать слова, начинающееся на “the”
/the\>	Искать слова, заканчивающиеся на “the”
/\< the\>	Искать “the” (точное соответствие)
/\< …. \>	Искать слова из четырех символов
/fred\|joe	Искать “fred” или “joe”
/\<\d\d\d\d\>	Искать 4 цифры подряд
/^\n\{3}	Искать 3 пустые строки
:bufdo /searchstr/	Искать во всех открытых файлах
Удаление

d^	Удалить все символы от текущей позиции до начала строки
d$	Удалить все символы от текущей позиции до конца строки
d/word	Удалить всё от текущей позиции до слова "word"
dfx	Удалить всё от текущей позиции до символа "x"
Замена

:%s/old/new/g	Заменить все вхождения “old” на “new”
:%s/old/new/gw	Заменить все вхождения “old” на “new” с запросом подтверждения
:2,35s/old/new/g	Заменить все вхождения “old” на “new” между 2 и 35 строками
:5,$s/old/new/g	Заменить все вхождения “old” на “new” начиная с 5 строки и до конца файла
:%s/^/hello/g	Добавить “hello” в начало каждой строки
:%s/$/Harry/g	Добавить “Harry” в конец каждой строки
:%s/onward/forward/gi	Заменить “onward” на “forward” с учетом регистра
:%s/ *$//g	Убрать все пробелы
:g/string/d	Удалить все строки, содержащие “string”
:v/string/d	Удалить все строки, не содержащие “string”
:s/Bill/Steve/	Заменить первое вхождение “Bill” на “Steve” в текущей строке
:s/Bill/Steve/g	Заменить все вхождения “Bill” на “Steve” в текущей строке
:%s/\r//g	Убрать символ возврата каретки (Такие тексты обычно приходят от windows-пользователей)
:%s#>[^<]\+>##g	Очистить текст от HTML-тегов
:%s/^\(.*\)\n\1$/\1/	Удалить строки, повторяющиеся дважды
Ctrl+a	Увеличить число под курсором на единицу
Ctrl+x	Уменьшить число под курсором на единицу
ggVGg?	Преобразовать текст в Rot13
Комментарий к замене: ...мне нужно во всем файле совершить замену

Abs[ 'выражение' ] -> | 'выражение' |

Если при описании разыскиваемой последовательности заключить какое-нибудь выражение в скобки \( \), то Vim поместит его в память под соответствующим номером (первое выражение под номером один, второе — два) и позволит в дальнейшем вызывать командой \x, где x — номер, под которым выражение было помещено в память.

Таким образом, нужная команда будет выглядеть примерно так:

:%s/Abs\[\([^\]]*\)\]/|\1|/g

Здесь стоит отметить, что для буквального совпадения квадратные скобки предваряются слешами, поскольку являются спецсимволами. Вообще любой спецсимвол, если должен участвовать в поиске, обозначая свое непосредственное значение, предваряется слешем: \^; \* и т.д. Сам слеш предваряется также слешем. Выглядит это так: для поиска последовательности '\cos' надо ввести '\\cos'.

...совершить замену вида

'Заглавная латинская буква''цифра' -> 'Заглавная латинская буква'_'цифра'

Самое тривиальное решение, которое напрашивается — перебрать все комбинации, если их немного. То есть, запустить замену сначала 'U1' -> 'U_1', потом 'U2' -> 'U_2' и т.п. Понятно, что это не наш метод. Мы вспомним, что есть квадратные скобки. И для того, чтобы найти одну заглавную латинскую букву, достаточно ввести шаблон '[A-Z]'. Но и это не предел. Для такого шаблона у Vim есть специальная аббревиатура: '\u' (от 'uppercase'). Для цифр же есть '\d' (от 'digit'). Подробнее о таких конструкциях можно почитать по адресу :help pattern.txt. С использованием этих аббревиатур команда для поиска примет вид

:%s/\(\u\)\(\d\)/\1_\2/g

Тут опять встречается группировка круглыми скобками: она позволяет при поиске поместить найденную букву и цифру в память под соотвествующими номерами, и впоследствии их оттуда извлечь, вызывая командами с теми же номерами: '\1' вызовет букву, а '\2' — цифру.
Регистр

Vu	Перевести строку в нижний регистр
VU	Перевести строку в верхний регистр
g~~	Инвертировать регистр
vEU	Перевести слово под курсором в верхний регистр
vE~	Инвертировать регистр слова
ggguG	Перевести весь текст в нижний регистр
:set ignorecase	Регистронезависимый поиск
:set smartcase	Игнорировать регистр при поиске, если в искомом выражении нет символов верхнего регистра
:%s/\<./\u&/g	Перевести первую букву каждого слова в верхний регистр
:%s/\<./\l&/g	Перевести первую букву каждого слова в нижний регистр
:%s/.*/\u&	Перевести первую букву первого слова в каждой строке в верхний регистр
:%s/.*/\l&	Перевести первую букву первого слова в каждой строке в нижний регистр
Чтение/запись файлов

:1,10 w outfile	Записать в outfile с первой по десятую строки
:1,10 w >> outfile	Добавить в outfile с первой по десятую строки
:r infile	Вставить содержимое файла infile
:23r infile	Вставить содержимое файла infile после 23 строки
Навигация по ФС

:e .	Открыть встроенный файл-менеджер
:Sex	Разбить окно и открыть встроенный файл менеджер
:browse e	Графический файл-менеджер
:ls	Список буферов
:cd ..	Перейти в родительскую директорию
:args	Список открытых файлов
:args *.php	Открыть все файлы с расширением *.php
:grep expression *.php	Показать список файлов с расширением php, содержащих в имени expression
gf	Открыть файл с именем, равным слову, находящемуся под курсором
Взаимодействие с ОС

:!pwd	Выполнить команду pwd и вернуться
!!pwd	Выполнить команду pwd и вставить результат в редактор
:sh	Открыть шелл
$exit	Вернуться в редактор из шелла
Выравнивание

:%!fmt	Выровнять все строки
!}fmt	Выровнять все строки в текущей позиции
5!!fmt	Выровнять следующие 5 строк
Вкладки

:tabnew	Создать новую вкладку
gt	Перейти на следующую вкладку
:tabfirst	Перейти на первую вкладку
:tablast	Перейти на последнюю вкладку
:tabm n(position)	Изменить порядок вкладок
:tabdo %s/foo/bar/g	Выполнить команду во всех вкладках
:tab ball	Поместить все открытые файлы во вкладки
Разделение окна

:e filename	Редактировать filename в текущем окне
:split filename	Разделить окно и открыть filename
ctrl-w + стрелка ВВЕРХ	Переместить курсор в верхнее окно
ctrl-w ctrl-w	Переместить курсор в следующее окно
ctrl-w ctrl-p	Переместить курсор в предыдущее окно(вернуться назад)
ctrl-w ctrl-x	Поменять окна местами
ctrl-w_	Максимизировать текущее окно
ctrl-w=	Подогнать окна по размеру
10 ctrl-w+	Увеличить текущее окно на 10 строк
:vsplit file	Вертикально разделить окно
:sview file	Разделить окно и открыть file только для чтения
:hide	Закрыть текущее окно
:only	Закрыть все окна, кроме текущего
:b 2	Открыть #2 в текущем окне
Автодополнение

Ctrl+n Ctrl+p (в режиме вставки)	Дополнить слово
Ctrl+x Ctrl+l	Дополнить строку
:set dictionary=dict	Установить словарь
Ctrl+x Ctrl+k	Дополнение из словаря
Метки

mk	Пометить текущую позиция как k
‘k	Перейти к метке k
d’k	Удалить все до метки k
d’a,’k	Удалить все от метки a до метки k
Сокращения

:ab mail mail@provider.org	Определить mail как сокращение от mail@provider.org
Отступы

:set autoindent	Включить автоматическую расстановку отступов
:set smartindent	Включить “умную” расстановку отступов
:set shiftwidth=4	Установить отступ равный 4 пробелам
ctrl-t, ctrl-d	Убрать/добавить отступ в режиме вставки
<<	Добавить отступ
>>	Убрать отступ
set syntax on		 "подсветка кода
set syntax on		 "подсветка кода
Подсветка синтаксиса

:syntax on	Включить подсветку
:syntax off	Выключить подсветку
:set syntax=perl	Установить режим подсветки


Вставить  символ в начало большого количества подряд идущих строк:

Вариант 1

Use Ctrl+v to select the first column of text in the lines you want to comment.

Then hit 'I' and type the text you want to insert.

Then hit 'Esc', wait 1 second and the inserted text will appear on every line.

Вариант 2
This replaces the beginning of each line with "//":


:%s!^!//!

This replaces the beginning of each selected line (use visual mode to select) with "//":


:'<,'>s!^!//! 

---
What if you’ve forgot to give sudo when you’ve opened the /etc/group file as shown below? In this case, instead of coming out of the file (and loosing all your changes) and executing the vim command with sudo, you can do the following.

$ vim /etc/group

:w !sudo tee %



Note: “:w !sudo tee %” will save the file as root privilege, even if you didn’t use sudo command to open it.
---
Использование стиля “подсветил — посмотрел — выполнил” совместно с визуальным режимом оказалось очень удобной практикой. Такое комбинирование стилей выделения используется при решении задач типа “в данной функции переименовать переменную foo в bar” и подобных. Такая (и подобные) задачи решаются последовательностью действий:

Подсвечиваем foo командой *

Переходим в режим визуального выделения и выделяем текущую функцию

Отдаем команду замены :’<,’>s//bar/g


Символы ’<,’>, означающие начало и конец текущего выделенного блока, и определяющие диапазон применения команды :s, Vim подставляет автоматически при отдаче любой команды из режима визуального выделения. Также опущен первый аргумент команды :s, т. к. набирать его нет необходимости — когда он опущен, Vim использует в качестве этого аргумента содержимое регистра текущего поиска. То есть именно то, что подсвечено желтым.

:g//t$ — скопировать строки, содержащие подсвеченное значение, в конец файла. Если, например, надо быстро понять, как глобальная переменная (sic! — а что делать, в legacy-коде они встречаются) используется в модуле.

:g//d — удалить строки, содержащие подсвеченное значение
:g!//d — удалить стрки, НЕ содержащие подсвеченного значения

Заменить каждое вхождение нескольких пустых строк на одну пустую строку (чтобы между параграфами стал одинаковый промежуток в одну линию):
:v/./,/./-j

Убрать пустые строки (в визуальном режиме)
:'<,'>g/^$/d

Раздвинуть подряд идущие строки (обратное предыдущему действие, каждая строка станет параграфом)
Нужно при форматировании текста под 76 символов, из формата, как его сохраняет Word, когда каждый абзац становится строкой в текстовом файле.
:'<,'>s/$/\r/g

быстро вставить текст при включенном autoindent (set ai)  - борьба с "лесенкой"

:r !cat

Очень удобная есть штука — диграфы (на Хабре писали). Работает просто: в режиме вставки нажимаете Ctrl+K и двухбуквенный код.

Коды обычно вполне интуитивные, например, значок ≤ вводится как =<, копирайт (©) через Co, а кавычки-ёлочки с помощью скобок << и >>. Но т. к. необходимость некоторые символы вводить появляется не слишком часто, всё равно забывается нафиг. Поэтому для удобства решил сделать табличку с некоторыми символами.

Символ	Название	Код после Ctrl+K
«»	русские кавычки	<< и >>
—	тире	M-
…	многоточие	не нашёл, подскажите
[скрытый]	неразрывный пробел	NS
[скрытый]	мягкий перенос	--
±	плюс-минус	+-
©	знак копирайта	Co
²	вторая степень	2S
³	и в куб можно	3S
€	значок Евро	Eu
°	градус	DG
℃	градус Цельсия (Фаренгейта угадайте)	oC
µ	микро	My
∞	бесконечность	00
½	одна вторая	12 (другие дроби аналогично)
√	знак корня	RT
≈	приблизительно	?2
≠	неравенство	!=
← ↑ → ↓	стрелки, соответственно	<- -! -> -v

.