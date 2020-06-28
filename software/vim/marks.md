marks
=====

`ma`                        установить локальный маркер a
mB                        установить глобальный маркер B
`c                        перейти к локальному маркеру c
`0                        вернуться на позицию, на которой закончили
                            работу при закрытии vim
:marks                    просмотр маркеров
set viminfo='1000,f1      маркеры пишутся в ~/.viminfo, восстанавливаясь
                            при следующем запуске vim. маркер " хранит
                            последнюю позицию курсора в файле

**Each file a ; one file A**

		ma	set mark a at current cursor location
		'a	jump to line of mark a (first non-blank character in line)
		`a	jump to position (line and column) of mark a
		d'a	delete from current line to line of mark a
		d`a	delete from current cursor position to position of mark a
		c'a	change text from current line to line of mark a
		y`a	yank text to unnamed buffer from cursor to position of mark a
		:marks	list all the current marks
		:marks aB	list marks a, B
		
**-= Navigate =-**
	
		]'	jump to next line with a lowercase mark
		['	jump to previous line with a lowercase mark
		]`	jump to next lowercase mark
		[`	jump to previous lowercase mark
		
**-= Special marks =-**
	
		`.	jump to position where last change occurred in current buffer
		`"	jump to position where last exited current buffer
		`0	jump to position in last file edited (when exited Vim)
		`1	like `0 but the previous file (also `2 etc)
		''	jump back (to line in current buffer where jumped from)
		``	jump back (to position in current buffer where jumped from)
		`[ or `]	jump to beginning/end of previously changed or yanked text
		`< or `>	jump to beginning/end of last visual selection
	
**Delmarks**
	
		:delmarks a	delete mark a
		:delmarks a-d	delete marks a, b, c, d
		:delmarks abxy	delete marks a, b, x, y
		:delmarks aA	delete marks a, A
		:delmarks!	delete all lowercase marks for the current buffer (a-z)