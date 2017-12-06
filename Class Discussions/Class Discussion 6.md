MSSA Cohort 3
Course: ISTA-320
Lesson Plan: 06
Name: Lee Sarduy

Can a UWP app directly access a relational database by using technologies provided by Microsoft? Why or why not?
UWP apps cannot directly access a relational database by using technologies provided by Microsoft (although some third-party database solutions are available). This might sound like a severe restriction, but there are sensible reasons for this limitation. Primarily, it eliminates dependencies that a UWP app might have on external resources, making the app a standalone item that can be easily packaged and downloaded from the Windows Store without requiring users to install and configure a database-management system on their computer.

Describe how the Entity Framework works.
Essentially, the Entity Framework implements a mapping layer between a relational database and your app; it generates an entity model that consists of collections of objects that your app can use just as it would any other collection. A collection typically corresponds to a table in the database, and each row in a table corresponds to an item in the collection. You perform queries by iterating through the items in a collection, usually with Language-Integrated Query (LINQ). Behind the scenes, the entity model converts your queries into SQL SELECT commands that fetch the data. You can modify the data in the collection, and then you can arrange for the entity model to generate and perform the appropriate SQL INSERT, UPDATE, and DELETE commands to perform the equivalent operations in the database. In short, the Entity Framework is an excellent vehicle for connecting to a database and retrieving and managing data without requiring you to embed SQL commands in your code.

What is the difference between the code- first and the database- first approaches to developing UWP apps?
In the database-first approach, the Entity Framework generates classes based on the definitions of tables in the database. The Entity Framework also provides a code-first approach; that strategy can generate a set of tables in a database based on classes that you have implemented in your app.

What is a partial class? Why would we want to create partial classes?
A partial class is a class in which the code is split across one or more source files. This approach is useful for tools such as the Entity Framework because it enables you to add your own code without the risk of having it accidentally overwritten if the Entity Framework code is regenerated at some point in the future.

Describe a RESTful web api. (Not in book.) Write a brief description of Representational State Transfer. What problem was it designed to solve?
REST is an architectural pattern which is based on HTTP and uses HTTP requests, responses, verbs and status codes to communicate. The fact that REST services use HTTP means they can be consumed by almost any ‘online’ device or application (including IoT devices such as toasters, cars, pedometers etc) – no proprietary knowledge of the API is required. Web API in .net is the way you write REST APIs services in .net. Web API gives you all the benefits of the .net framework and deals with a lot of the complexities of content negotiation, model binding etc that you’d have to deal with yourself without Web API. To summarise, use of an API will make the architecture of your application much cleaner, making it easier to add features and fix bugs as your project progresses. (retrieved from: https://blogs.msdn.microsoft.com/martinkearn/2015/01/05/introduction-to-rest-and-net-web-api/).

Give a brief description of the functionalities of these HTTP commands: GET, POST, PUT, DELETE. 
GET allows you to retrieve resources.
POST allows you to create resources.
PUT allows you to modify resources.
DELETE allows you to remove resources.