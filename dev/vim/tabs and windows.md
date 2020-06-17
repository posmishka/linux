tabs and windows
====

vim -p 1 2 3 # open files in tabs 

**Создать новую**	

    :tabe <filepath>
    
**Следующая**

	:tabn
	
**Предидущая**

	:tabp
	
**Закрыть**

	:q / :wq
	
	
<https://www.youtube.com/watch?v=B-EPvfxcgl0>


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
                           
:tabe
                          
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