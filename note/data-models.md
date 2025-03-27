# Data Models

A **data model** is simply an **exemplary role model** for organizing data, that is, how certain data should look, be organized, and behave in general.

> [!WARNING]
> 
> **Update 27 March 2025:** Significant addition and revision on the [Relationships](#relationships) section. This includes differentiating a Relation (which is practically known as a Table) with a Relationship (as in "... between two tables").
> 
> Also, Reinhart is now studying for Master of Cybersecurity in Monash University. (#- );

In software design, data models are fundamental to **Object-Oriented Programming (OOP)** (as object classes or interfaces) and **Database Design** (as entities). In fact, many programmers like Reinhart unify both concepts into one<sup>[A]</sup>, so it's easier to remember the **properties** (aka. the quantified characteristics) and **actions** (what the model could do or be used for; also known as *methods*) of the model, from their favorite database systems up to their programming languages.

> [!NOTE]
> 
> This article is primarily written for beginners, and oriented towards computer software compared to computer systems.
> 
> The difference between these two is that a computer system may consist of more than one piece of software, and because of that, they often favor towards more abstract concepts and terms such as "relation" over "table" and "class".

When we talk about a data model, we're not talking about one specific kind of data, but **a group of data assigned according to a related context.** It means that each data contained **inside** a data model should be related in a certain way. And that also means, data models are an efficient way to [organize data to produce an information](/note/data-information-knowledge).

> [!NOTE]
> 
> <sup>[A]</sup> One of them is through the concept of **object-relation mapping**, aka. ORM, where each struct or object class is directly correlated to a data model in database, also known as a table (in relational database systems) or an entity (in Entity Relationship Diagrams).

## Classes

The first thing to define a data model is defining its **class**, that is, what the data do actually represent. Do they represent a certain fruit? Or a certain information about a place? Or a unique internet user like you? Or some exotic abstract things such as `Ext4FileSystemConnector`?

+ In [relational algebra](https://en.wikipedia.org/wiki/Relational_algebra), the popular mathematical concept behind database systems, these things are simply called **Relations**. The word "relation" here do **not** describe the [relationship](#relationships) between one "class" and another. In fact a "relation" *is* the same thing as the "class" as described throughout this article.
+ In (mainly relational and document-based NoSQL) database systems, it is possible to organize similar entries into **Entity Sets** or **Tables**. Each entity set has their own [properties](#properties), as we'll learn shortly, which will translate into a set of columns in a large table.
+ Same thing with "object classes" in OOP, or simply **"Class"**. Each class can have multiple **instances** of it, just like multiple rows of data in *that* table.
+ Classical **structs** in some programming languages (that rejects or predates the age of OOP) provides similar functionality with object classes in OOP. Just that the concept of [inheritance and polymorphism](#inheritance-and-polymorphism) wasn't well-baked in structs.

## Interfaces

Now, there's another geeky term, I mean, Object-Oriented term called the **Interface**. An interface acts as a glue between data models (classes) which allows a computer program to treat one data class similar to another class in a certain way, **defined by how both classes should have and behave.**

> [!IMPORTANT]
>
> Interfaces are fundamentally different than **type unions** in some programming languages like TypeScript. A type union between A and B simply instructs a variable or a property to accept either A or B just the way they are.
> 
> Meanwhile, an Interface adopted by A and B means that both class contain these similar things, and a variable or a property accepting the interface means that it will treat A and B as common through the same agreed set of shared properties and actions. That means that any methods calling the variable cannot call A or B-specific actions which are not covered by the interface, unless through type-checking and casting mechanisms.

Interface is an advanced topic commonly not covered in databases, as every table or entity set in the database virtually contain these same common [actions](#actions) and even [traits](#properties):

+ **A metadata that indicates the time when the data object was created or modified.** Many ORM libraries and frameworks often add these metadata properties, like `created_at` and `updated_at` in [GORM](https://gorm.io) and [Laravel](https://laravel.com).
+ A way to **create and insert** a new group of data into the model. Yep, I mean things like SQL's `INSERT` command.
+ A way to **get some or a specific group of data** that's classified under this model. Yep, I mean things like SQL's `SELECT` command.
+ A way to **modify** some or a specific group of data that's classified under this model. Yep, I mean things like SQL's `UPDATE` command.
+ A way to **delete** some or a specific group of data that's classified under this model. Yep, I mean things like SQL's `DELETE` command.

Anyway, these last four things are commonly known as **Create-Read-Update-Delete (CRUD)** operations.

Unlike regular classes and their [actions](#actions), interfaces are just a set of rules that classes need to implement in order to be declared compatible with the interface. These rules are none other than a set of shared [properties](#properties) and [actions](#actions), each with the exact kind of input **and** the exact kind of output.

## Properties

We commonly define a property as a **standard context** or "trait" that maps into the data. For example, the properties "latitude" and "longitude" on a data model representing a specific hotel as the place's geographical coordinates.

Well, it's still possible to define structs or OOP classes with zero properties, but that means that the data itself wasn't assigned with any meaningful context<sup>[B]</sup>, making the data itself feel even worthless. And we don't want that, right?

> [!NOTE]
> 
> <sup>[B]</sup> Unless if we care about [inheritance](#inheritance-and-polymorphism) and the difference between class names in OOP, like `BaseError` vs `NetworkRequestError`.

If you prefer the visual way to explain this, take an entity set out from **Entity Relationship Diagram (ERD)**, for example.

<pre class="mermaid">
erDiagram
  CAR {
    VARCHAR(255) registration_number PK "NOT NULL"
    VARCHAR(255) make "NOT NULL"
    VARCHAR(255) model "NOT NULL"
    DATE created_at "NOT NULL DEFAULT NOW()"
    DATE updated_at
  }
</pre>

You might recognize this similar to **Class Diagrams**, and they do in some ways.

<pre class="mermaid">
classDiagram
  class Car {
    + String registrationNumber
    + String make
    + String model
    + Date createdAt
    + Date? updatedAt
  }
</pre>

This data model represents a certain car with four required and one optional (`updated_at`) property. You'll also notice two things here, that every property must be **assigned to the same data type** (e.g. must be in string, integer, or other data model)

Yes, in Object-Oriented Programming and some NoSQL databases, you can tell to expect the value of a property **to be another data model** (e.g. the `Date` object), and it's possible for an attribute of a `Car` to be directly another `Car`!

## Actions

Each data model should be able to do something. If not, at least there should be a way to be used for something. This is where **data actions** come in, also known as **methods** and **functions** in many programming languages.

For database systems, there are some standard actions that are available to *all* entities (or tables, duh), as explained more in [Interfaces](#interfaces). Similarly, we commonly associate data models deep into our [common REST API designs](/note/rest-api-conventions.md), where we define a standard way (i.e. a set of endpoints) to create, read, update, and delete the model.

In many cases, we may simply need to create, read, update, and delete. That's what CRUD stands for. To simplify things up from similar concepts in databases, OOP, and HTTP/REST, we found out people commonly define these six action types in their applications.

| Action | Definition | Common term in OOP | Common term in SQL | Common term in HTTP and REST API |
|---|---|---|---|---|
| Define | Define a new form of data model | Declare a Class/Interface/Type (TypeScript) | CREATE/ALTER TABLE | *None* |
| Create | Create a new **data group** that follows the properties and actions of the model | Constructor, Setters, and some static methods to aid constructors | INSERT | POST |
| Search/Query | Search for instances of data that match a specific criteria, usually in a list, set, or hashmap | (Related to list, set, and map-based data types) `filter()`, `foreach()`, `map()` | SELECT | GET or POST |
| Read | Get one or some specific property of the grouped data | Public properties and Getters | SELECT | GET |
| Update | Update one or more properties of the data group | Setters | UPDATE | POST or PUT |
| Delete | Update one or more properties of the data group | Setters | UPDATE | DELETE |

There are also "static methods" in OOP, but that's quite out-of-scope from understanding the basics of the data models. Note that some of those methods do not actually relate to the data model, especially if the returned data type is neither the model nor the specific property of a model itself.

## Relationships

Alright, so with data models, we can systematically assign the context for each groups of data. But another important part of constructing useful information and knowledge from these data is to learn how these models and groups **relate to each other**.

You might find some arrows in Entity Relation and Class Diagrams quite intimidating. Like, the one that looks like ">&#124;———O<"?

Good news! Actually, we can actually simplify these into 3 kinds of **Connectivity**. Note that some computer science courses call this instead as **Multiplicity**, which is an umbrella term for both Connectivity and Cardinality. We'll explain the difference between the two later.

Let's say that the relationship from a model (A) to another (B) is:

1. **Exactly, requires a specific amount (e.g. one) of B.** That means each data classified under the model A must be assigned to an *N* amount of data classified under B.
2. **Could be as many as possible.** Quite self-explanatory, but remember. that these could either mean "at least 1 but could end up many", or simply "optional and unlimited".
3. **Could be in a range of of amounts.** It could be "between 2 to 5 amounts of B" and so on.

We commonly define the connectivity of relationships by describing the rules for each ends. For example, a "one-to-many" relationship from A to B means that A could have an unlimited number of relationships to B, but every data under B must be related to exactly one instance of A.

While many system designers are satisfied enough with this, others do not. For example, how to denote a relationship where a `Team` may only have up to 5 `Member`s? This is why **Cardinality**, a stricter form of Connectivity, is being used. Insteead of symbols like "->&#124;———O<-", they simply use numbers and alphabets. Here is a difference between the two:

| Relationship Type | Connectivity | Cardinality |
|---|---|---|
| Zero or One ("Optional, but only up to one allowed") | -O&#124;——— | (0,1) |
| One and only One (always required) | -&#124;&#124;——— | (0,1) |
| Zero or Many ("OK to be empty, OK to be so many") | ->O——— | (0,M) |
| One or Many ("At least one, but can be more") | ->&#124;——— | (1,M) |

And there's some things Cardinality can represent but not Connectivity, such as **(2,5)** to represent "between 2 and 5 instances/occurences/amounts of B".

If you ever being presented with a diagram that shows these symbols, the symbols on one side (Class / Entity Set / Relation) applies to the opposing side of it.

That means if "[A] ->&#124;———O<- [B]", A may be connected to zero or many instances of B, but B **must** be connected to at least 1 or more instances of A.

## Inheritance and Polymorphism

And lastly, **polymorphism** is the ability for a data model to transform into a specific model with a more unique or restricted set of [properties](#properties) and [actions](#actions). This is common in Object-Oriented Programming and niche database systems like PostgreSQL, but this is rarely adopted in database because it isn't as efficient as in OOP programming languages.

For example, the data model `Place` could be extended into specific place types like `Hotel`, `Market`, `Office` and so, each with an additional set of properties and actions, like the `Hotel`'s ability to search for available rooms to book, while it's not possible to reserve a visit to a `Market`. These `Hotel`, `Market`, `Office` data models hence **inherits** the core properties and actions of a generic `Place`. That's what **inheritance** is all about.

In database, however, you might not always need to use inheritance and polymorphism. You can define external attributes as optional (aka. "nullable"), and simply use a new fixed-value attribute (e.g. `place_type`) that differentiates between these three models. It's technically simpler and more efficient to search and sort for places here, since the database engine does not need to look for multiple tables that inherits the properties of a certain table, making the search process more complicated.

### "Interface in Polymorphism"

"Interface in Polymorphism" is a [running slogan](https://reinhart1010.id/computer-systems-multiculturalism) on our community, which roughly translates into "unity in diversity" using the terms originally meant to explain the concepts of object-oriented programming. Like, there's a [polymorphism](#inheritance-and-polymorphism) between [`Class`es](#classes) that we can unite with [`Interface`s](#interfaces)!

## Further Reading

This knowledge is compiled from various sources, based on both theoretical and practical experiences from designing structs in C and Go, objects in Java, JavaScript/Typescript, Python, and Swift, working with countless SQL database systems, Apache CouchDB, and mongoDB, and even more. Not to mention working with certain frameworks like Laravel and React. Not to mention those early days working as a [Webcompat](https://webcompat.com/about) contributor back then investigating those HTTP requests. And of course, working with UML and ERD diagrams for systems design.

### A Note about JavaScript

JavaScript's "objects" and "classes" (a newer kind of objects introduced in 2015) are technically more related to a **hash map** that allows each key's values to be virtually *anything*, rather than traditional structs.

Unlike others, you can still add new attributes and methods to an existing instantiated object without a single error!

```js
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
}

const myCar1 = new Car("Ford", 2014);
myCar1.altName = "Honda"
const myCar2 = new Car("Audi", 2019);

// Still returns as "Honda Audi" instead of a "nonexistent object member error".
document.getElementById("demo").innerHTML =
myCar1.altName + " " + myCar2.name;
```

This is fundamentally different than the concept of "class" and "objects" in other OOP-compliant languages like C# and Java and Python, and that's another reason we discourage people to use JavaScript first (even though Reinhart did) to learn how to be a polyglot developer (who's capable of writing code in many different programming languages!)

TypeScript, however, put some restrictions to the defined classes and objects

### BINUS School of Computer Science Reference Textbooks

At School of Computer Science, BINUS University, we commonly have a standard list of textbooks that primarily shaped our CS curriculum. Here are some of the sanctioned ones for computer system and database design. And if you are currently majoring in CS, chances that you have the same textbooks, too.

+ Connolly, T. M., & Begg, C. E. (2015). *Database systems: A practical approach to design, implementation, and management* (6. ed., global ed). Pearson.
+ Dennis, A., Wixom, B. H., & Roth, R. M. (2018). *Systems analysis and design* (7th ed). Wiley.
+ Satzinger, J. W., Jackson, R. B., & Burd, S. D. (2016). *Systems analysis and design: In a changing world* (Seventh edition). Cengage Learning.

### Monash University Reference Textbooks

+ Coronel, C., & Morris, Steven (2023). *Database Systems: Design, implementation, and management* (14th ed.). Cengage Learning.

### Some Useful Free Resources

Unfortunately, the best resources for your learning path depend on the programming languages you currently working on. Some languages like Python do not follow things that Java did in terms of OOP.

But one of the best parts in OOP is that the more you understand the core concepts, you'll be more able to learn other OOP-based programming languages by simply for searching things like "how to do inheritance in Ruby". Many well-known OOP languages support creating constructors, private/public attributes, and even other fancy stuff like abstract classes and interfaces.

We acknowledge some great alternative definitions of data models and related keywords (e.g. "Class" in OOP), which might also be helpful to you with different learning styles and objectives. Take this one from FreeCodeCamp:

> **Classes** are simply blueprints for creating objects. Think of a class like an architect's blueprint for building a house.
> 
> An architect's blueprint defines the structure, layout, and shape of the house. Similarly, a class defines the structure and behavior of an object.
> 
> In OOP, **attributes** are like the different characteristics of a puzzle piece. They define the properties of an object, just like how the shape, color, and design of a puzzle piece define its role in completing the puzzle.
> 
> In OOP, **methods** define the actions that objects can perform.
> 
> Fulsundar, A. (2023). "Object Oriented Programming Basics – OOP, Classes, and Objects in Java." *FreeCodeCamp*. Online: *https://www.freecodecamp.org/news/object-oriented-programming-basics-oop-classes-and-objects-in-java/*.

For those who are learning Swift, Apple have published some simple guides for creating apps with it, which briefly covers some advanced topics such as structs (the precursor of classes).

> Swift comes with many useful types for representing data like numbers, text, collections, and true or false values. **But as you get into building apps, you’ll find you want to create your own data types, with properties and functions of your own design.**
> 
> You create a custom data type by declaring a structure. **A structure combines one or more variables into a single type.** You can define functionality by adding type and instance methods to a structure.
> 
> Apple Education. (2021). *Develop in Swift Fundamentals* (Xcode 13 ed.). Online: *https://itunes.apple.com/WebObjects/MZStore.woa/wa/viewBook?id=1581182804*

And lastly, your might-be-favorite W3Schools have summarized most of these into an elementary school-like introduction to OOP.

> + In real life, **objects** are things like: houses, cars, people, animals, or any other subjects.
> + A real life car has **properties** like weight and color. Car objects have the same **properties**, but the values differ from car to car.
> + A real life car has **methods** like start and stop. Car objects have the same methods, but the methods are performed at different times.
> 
> Refsnes Data. (n.d.) "JavaScript Objects." *W3Schools*. Online: *https://www.w3schools.com/js/js_objects.asp*

Looks like something straight from [*JavaScript for Babies*](https://www.amazon.com/Javascript-Babies-Code-Sterling-Childrens/dp/1454921579), but still helps for those first-time learners making sense out of Object-Oriented Programming.
