# CS2021

## Часто задаемые вопросы

### Я - число или вы хотите превратить string в int

Лучше всего использовать TryParse:

```
// s - ваша строка
int x;
if (int.TryParse(s, out x))
{
	// Здесь какие-нибудь действия
}
```

### Ломай строку полностью или надо разобрать строку по какому-то символу

Вам нужно расщепить строку, например, по пробелу

```
// s - ваша строка
var a = s.Split(' ', StringSplitOptions.RemoveEmptyEntries)
```

Нужно больше символов для разбиения!!!

```
var a = s.Split(new string[] { " ", "!", ",", ";" }, StringSplitOptions.RemoveEmptyEntries)

```