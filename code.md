## Pets project
This project was my first attempt at creating classes and objects using C#.

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
    
    public Pet(string typeName, string petName, string ownerName, double petWeight)//constructor?
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
