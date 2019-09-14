# RabbitMQ-Demo-App

Setup

Now let's generate two projects, one for the publisher and one for the consumer:

# Project 1
dotnet new console --name Send
mv Send/Program.cs Send/Send.cs
dotnet new console --name Receive
mv Receive/Program.cs Receive/Receive.cs

This will create two new directories named Send and Receive.

Then we add the client dependency.

cd Send
dotnet add package RabbitMQ.Client
dotnet restore
cd ../Receive
dotnet add package RabbitMQ.Client
dotnet restore

Open two terminals.

Run the consumer:

cd Receive
dotnet run
Then run the producer:

cd Send
dotnet run


# Project 2

we need to generate two projects.

dotnet new console --name NewTask
mv NewTask/Program.cs NewTask/NewTask.cs
dotnet new console --name Worker
mv Worker/Program.cs Worker/Worker.cs
cd NewTask
dotnet add package RabbitMQ.Client
dotnet restore
cd ../Worker
dotnet add package RabbitMQ.Client
dotnet restore


You need three consoles open. Two will run the Worker program. These consoles will be our two consumers - C1 and C2.

# shell 1
cd Worker
dotnet run
# => [*] Waiting for messages. To exit press CTRL+C


# shell 2
cd Worker
dotnet run
# => [*] Waiting for messages. To exit press CTRL+C
In the third one we'll publish new tasks. Once you've started the consumers you can publish a few messages:


# shell 3
cd NewTask
dotnet run "First message."
dotnet run "Second message.."
dotnet run "Third message..."
dotnet run "Fourth message...."
dotnet run "Fifth message....."
Let's see what is delivered to our workers:
