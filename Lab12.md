# Лабораторная 12

## Классы

### Поля

*Полями* класса будем называть переменные, хранящие информацию об экземпляре данного класса.

```csharp
class Product
{
	private string name;
	private double price;
}
``` 

В данном случае, у класса *Product* есть два поля: имя *name* и стоимость *price*.

*Замечание.* Поля всегда закрытые (*private*)!!!

### Методы

*Методами* класса будем называть функции (процедуры), описанные в классе.

```csharp
class Product
{
	...
	
	// Метод ничего не знает о конкретном экземпляре класса
	public static double F1()
	{
		...
	}
	
	// Метод знает о конкретном экземпляре класса
	public double F2()
	{
		...
	}
}

...

static void Main()
{
	// Статический метод
	double a = Product.F1()
	
	// Экземплярный метод
	Product p = new Product();
	double b = p.F2();
}


``` 

#### Геттеры и сеттеры

Если поля всегда *private*, то как же их узнавать и менять в основной программе? Классический способ - геттеры и сеттеры.

```csharp
public string GetName()
{
	return name;
}


public string SetName(string name)
{
	// Компилятор отличает name класса (this.name) от нового name 
	this.name = name;
}
```