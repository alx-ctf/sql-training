# opisanye
- Таблица: users
- Поля: id, login, pass
- Введите запрос к базе данных: 


# writeup
```sql
select id, login, pass from users
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
9 	fghgf 	fghfghgfh
10 	fghfghfg 	fghfgh
11 	fghgfh 	fghgfh
12 	fghfgh 	QwErTy
```

Ура, я знаю ответ (пароль пользователя с id=12): 
```result
QwErTy
```