## Pets project
[Home](https://henryelle.github.io) | [Code] hey you're _here!_ | [Studies](https://henryelle.github.io/studies.html) | [Contact](https://henryelle.github.io/contact.html)

This project was my first attempt at creating classes and objects using C#.

Program.cs:

```C#
using System;

namespace Pets
{
    class Program
    {
        static void Main(string[] args)
        {
            Pet pet1 = new Pet("dog", "Shadow", "Jose", 42.6);

            Console.WriteLine("Name: " + pet1.name);
            Console.WriteLine("Weight: " + pet1.weight);
            Console.WriteLine(pet1.getTag());
            Console.Write("\n");

            Dog dog1 = new Dog("Daisy", "Kent", 23.4);

            Console.WriteLine("Name: " + dog1.name);
            Console.WriteLine("Weight: " + dog1.weight);
            Console.WriteLine(dog1.getTag());       
            Console.WriteLine(dog1.bark(4));
            Console.Write("\n");


            Cat cat1 = new Cat("Simba", "Maria", 5.2);

            Console.WriteLine("Name: " + cat1.name);
            Console.WriteLine("Weight: " + cat1.weight);
            Console.WriteLine(cat1.getTag());
            Console.WriteLine(cat1.meow(3));
            Console.Write("\n");

        }
    }
}
```

Pet class:

```C#
namespace Pets
{

public class Pet
{
    public string type = "";
    public string name = "";
     public string owner = "";
     public double weight = 0;
    
    public Pet(string typeName, string petName, 
    string ownerName, double petWeight) //constructor
    {
        type = typeName;
        name = petName;
        owner = ownerName;
        weight = petWeight;

    }

    public string getTag()
    {
        return "If lost, call " + owner;
    }

}
}
```

Dog class:

```C#
namespace Pets
{
    public class Dog : Pet
    {
         public Dog(string dogName, 
         string dogOwner, double dogWeight) : base
         ("dog", dogName, dogOwner, dogWeight) 
         {
             //typeName = "dog";
             name = dogName;
             owner = dogOwner;
             weight = dogWeight;
         }

         public string bark(int count)
         {
             string barks = "";
             for(int i = 0; i <= count - 1; i++){
                 barks += "Bark! ";

             }
             return barks;
         }

    }
}
```

Cat class:

```C#
namespace Pets
{
    public class Cat : Pet
    {
         public Cat(string catName, 
         string catOwner, double catWeight) : base("cat", catName, catOwner, catWeight) 
         {
             name = catName;
             owner = catOwner;
             weight = catWeight;
         }

           public string meow(int count)
         {
             string kittyspeakin = "";
             for(int i = 0; i <= count - 1; i++){
                 kittyspeakin += "meeeow...";

             }
             return kittyspeakin;
         }
    }
}
```
**Navigation**  
[Home](https://henryelle.github.io) | [Code] hey you're _here!_ | [Studies](https://henryelle.github.io/studies.html) | [Contact](https://henryelle.github.io/contact.html)
