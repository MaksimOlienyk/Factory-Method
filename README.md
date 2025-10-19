# Factory-Method
```cs
﻿abstract class Creator { public abstract IProduct FactoryMethod(); }
interface IProduct { void Operation(); }

class ProductA : IProduct { public void Operation() => Console.WriteLine("ProductA created"); }
class CreatorA : Creator { public override IProduct FactoryMethod() => new ProductA(); }

class Program
{
    static void Main()
    {
        Creator creator = new CreatorA();
        creator.FactoryMethod().Operation();
    }
}
