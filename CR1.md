# CS2021

## Часто задаемые вопросы

### Хочу превратить string в другие типы

Лучше всего использовать TryParse:

```
// s - ваша строка
int x;
if (int.TryParse(s, out x))
{
	// Здесь какие-нибудь действия
}

// s - ваша строка
double y;
if (double.TryParse(s, out y))
{
	// Здесь какие-нибудь действия
}
```

### Хочу разобрать строку по какому-то символу

Вам нужно расщепить строку, например, по пробелу:

```
// s - ваша строка
var a = s.Split(new string[] { " " }, StringSplitOptions.RemoveEmptyEntries)
```

### Хочу инициализировать максимум(минимум)

```
int max = int.MinValue;
double min = double.MaxValue;
```

### Хочу читать из бинарного файла

```
using (BinaryReader br = new BinaryReader(File.Open(path, FileMode.Open), Encoding.ASCII))
{
    while (br.PeekChar() != -1)
	{
		// тут используем br.ReadInt32() или br.ReadDouble()
	}
}
```

### Хочу читать из текстового файла

```
using (StreamReader sr = new StreamReader(path))
{
	while (!sr.EndOfStream)
		Console.WriteLine(sr.ReadLine());
}
```

### Хочу записать во вспомогательный, а потом старый заменить на новый

```
File.Delete(old_path);
File.Move(new_path, old_path);
```

### А как решать?

1. Запишем в переменную результат ReadAllLines, открываем на запись новый файл, для каждой строки из ReadAllLines сплитим строку по пробелу,
проходим по каждой подстроке, проверяем число-не число, если число, сравниваем на максимум/минимум. Записываем максимум/минимум столько раз, сколько элементов в
массиве подстрок.
2. Первый проход. Читаем файл - ищем минимум (сумму).
Второй проход. Пока можно читать, читаем по два числа. Если второе из них кратно (меньше) первого, то делаем сдвиг на 8 влево (double по 8 бит).
Записываем и вновь сдвигаем на 8 влево.
3. Пользуемся MakeTempFileName для создания нового имени файла. Открываем старый на чтение, новый на запись. Пользуйтесь методом Contains для строк.
4. 1) ReadAllLines, Select, char.IsDigit, тернарный оператор, Replace, WriteAllLines.
4. 2) ReadAllLines, Select, char.IsLower/IsUpper, тернарный оператор, ToLower/ToUpper, WriteAllLines.
