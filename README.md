<h1 align="center">
	Poo_2-2
</h1>

<h3 align="center">
	Data manipulation with C Sharp
</h3>

<p align="center">
	<img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square"/>
	<img src="https://img.shields.io/github/languages/count/IgorSilvaMedeiros/poo_2-2?color=green"/>
</p>

<h4 align="center">
	Status: 🚀 Finished
</h4>

<p align="center">
	<a href="#about">About</a> •
	<a href="#tech-stack">Tech Stack</a> •
	<a href="#installation">Installation</a> •
	<a href="#usage">Usage</a> • 
	<a href="#contact">Contact</a> 
</p>

## About
EN = This project is intended as a grade for the college's Object Oriented Programming II subject, The purpose of this project is to access the MongoDB database with the C Sharp programming language and consult and change the data with the same.

PT = Esse projeto tem como finalidade como nota para a matéria de Programação Orientada a Objetos II da faculdade, o objetivo da prova e acessar o banco de dados em MongoDB com a linguagem de programação C Sharp e consultar e alterar os dados com a mesma.

## Tech Stack
<img src="https://img.shields.io/badge/Csharp-05122A?style=flat&logo=csharp" alt="csharp Badge" height="25">&nbsp;

## Installation
To Install this project, follow the steps above:
```
# Install MongoDB Community Server
https://www.mongodb.com/try/download/community

# Install .Net
https://dotnet.microsoft.com/en-us/download

# Install Visual Studio Code
https://code.visualstudio.com/

# Add extension C# in Visual Studio Code
https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
```

## Usage
To use this project, follow the steps above:
```bash
# Start Serve MongoDB
$ sudo systemctl start mongod

# Check status from MongoDB
$ sudo systemctl status mongod

# create DB "testdb"
$ mongo testdb

# insert some values ​​into the database
db.cars.insert({name: "Audi", price: 52642})
db.cars.insert({name: "Mercedes", price: 57127})
db.cars.insert({name: "Skoda", price: 9000})
db.cars.insert({name: "Volvo", price: 29000})
db.cars.insert({name: "Bentley", price: 350000})
db.cars.insert({name: "Citroen", price: 21000})
db.cars.insert({name: "Hummer", price: 41400})
db.cars.insert({name: "Volkswagen", price: 21600})

# Add MongoDB.Driver in project through the terminal
dotnet add package MongoDB.Driver --version 2.15.1

# Run the program
dotnet run

# MongoDB find all documents

using MongoDB.Driver;
using MongoDB.Bson;

namespace FindAll
{
    class Program
    {
        static void Main(string[] args)
        {
            var dbClient = new MongoClient("mongodb://127.0.0.1:27017");
            IMongoDatabase db = dbClient.GetDatabase("testdb");

            var cars = db.GetCollection<BsonDocument>("cars");
            var documents = cars.Find(new BsonDocument()).ToList();

            foreach (BsonDocument doc in documents)
            {
                Console.WriteLine(doc.ToString());
            }
        }
    }
}

# MongoDB insert document

using MongoDB.Driver;
using MongoDB.Bson;

namespace InsertDocument
{
    class Program
    {
        static void Main(string[] args)
        {
            var dbClient = new MongoClient("mongodb://127.0.0.1:27017");

            IMongoDatabase db = dbClient.GetDatabase("testdb");

            var cars = db.GetCollection<BsonDocument>("cars");

            var doc = new BsonDocument
            {
                {"name", "BMW"},
                {"price", 34621}
            };

            cars.InsertOne(doc);
        }
    }
}

# MongoDB delete document

using MongoDB.Driver;
using MongoDB.Bson;

namespace DeleteDocument
{
    class Program
    {
        static void Main(string[] args)
        {
            var dbClient = new MongoClient("mongodb://127.0.0.1:27017");

            IMongoDatabase db = dbClient.GetDatabase("testdb");

            var cars = db.GetCollection<BsonDocument>("cars");
            var filter = Builders<BsonDocument>.Filter.Eq("name", "BMW");

            cars.DeleteOne(filter);
        }
    }
}

```

## Contact
<img align="left" src="https://avatars.githubusercontent.com/igorsilvam?size=100">

Made with ❤️ by [Igor Silva](https://github.com/igorsilvam), get in touch!

<a href="mailto:igoratendimento@outlook.com.br" target="_blank"><img src="https://img.shields.io/badge/Email-D14836?style=flat&logo=gmail&logoColor=white" alt="Email Badge" height="25"></a>&nbsp;
<a href="https://www.linkedin.com/in/igor-da-silva/" target="_blank"><img src="https://img.shields.io/badge/Linkedin-0077B5?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn Badge" height="25"></a>&nbsp;

<br clear="left"/>
