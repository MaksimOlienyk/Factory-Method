# Factory Method — Патерн Проєктування

Цей приклад демонструє шаблон **Factory Method** у мові C#.

Factory Method дозволяє **делегувати створення об’єктів дочірнім класам**, замість того щоб створювати їх безпосередньо у базовому коді.

---

## Ідея патерна

> Клас **не створює об'єкти напряму**.  
> Замість цього він викликає **фабричний метод**, який визначається у підкласах.

Це дозволяє:
- замінювати тип створюваних об'єктів без зміни базової логіки;
- розширювати програму новими типами продуктів;
- зменшувати залежність від конкретних класів.

---

## Структура

| Роль | Опис |
|------|------|
| `IProduct` | Інтерфейс продукту |
| `ProductA` | Конкретний продукт |
| `Creator` | Абстрактний клас, що містить Factory Method |
| `CreatorA` | Конкретний творець, що створює `ProductA` |

---

## Код:

```csharp
abstract class Creator
{
    public abstract IProduct FactoryMethod();
}

interface IProduct
{
    void Operation();
}

class ProductA : IProduct
{
    public void Operation() => Console.WriteLine("ProductA created");
}

class CreatorA : Creator
{
    public override IProduct FactoryMethod() => new ProductA();
}

## Приклад використання
class Program
{
    static void Main()
    {
        Creator creator = new CreatorA();
        IProduct product = creator.FactoryMethod();
        product.Operation();
    }
}
## CreatorA - визначає який саме продукт потрібно створити || Program - працює через абстракції, не знаючи про конкретні типи

