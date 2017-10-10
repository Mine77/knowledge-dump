In .Net, it is allowed to create a new class with `Extensions` in the end of existing class to write some custom method.  
Sample code:  

```
...
internal static class IEnumerableExtensions
{
    public static int AddIncome(this IEnumerable<Person> persons) 
    {
        int result = 0;
        foreach (var person in persons)
        {
            result += person.income;
        }
        return result;
    }
}
...
```
```
...
public class Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public int income { get; set; }
}
...
```
```
...
List<Person> persons = new List<Person> ();
persons.Add(new Person
{
    FirstName = "fName_0",
    LastName = "Lname_0",
    income = 30
});
persons.Add(new Person
{
    FirstName = "fName_1",
    LastName = "Lname_1",
    income = 60
});

Console.WriteLine(persons.AddIncome());
...
```
Output is:
```
90
```