# thoughts
Just some random thoughts and answers found on the internet.


1 - Whenever you're developing a mobile project, you need to separate your business logic from your UI logic and the same goes for your model.

This is done to give your mobile application the ability to be mantainable for the long run, because as you incorporate bug fixes or new functionalities, if you have too much code in one class, finding your way in it will be complete chaos.

With that set, I'll propose to you a mobile application arquitecture that might help you:

UI: Dedicate a package to hold all of your Activities, you can place your Fragments in a separate one. Keep your code free or anything related to database access or modifying your model classes. You want your UI classes free of any code non-related to handling events, presenting UI changes (like changing text, styles, images, loading Fragments, etc). If you need something beyond this scope, then use objects from the other layers I'm about to describe.
Data Access Objects: Anything related to read from files, accessing an internal database, storing information in either, should go in a different package, these classes should handle any connection to these store places and return the information to be consumed by your UI or other layers.
Data Transfer Objects: Keep the classes that will represent the information you'll be presenting on your UI free of any complex logic, these classes need to be just POJO to hold information that will be served on the UI or sent across the net.
Network: If you have to consume web services or connect to remote servers to retrieve any kind of data, you should place the classes for that here.
Business: Need to retrieve a List of Persons from database using a Data Access Object but filtered by some rule or to handle image processing or some complex operation? Classes like that should be placed here.
Services: Your services or tasks should be placed in their own package too, avoid declaring them inside your Activities.
If your application need more functionality and you think some of these layers don't work for you, you should add more or remove those you won't be using, in the end the final goal is to keep your project code easy to read and to mantain.

Some might think it's a hassle to have to separate your code into classes, but having a monster class that handles everything will do more harm to you.

Of course, you shouldn't make everything into a class, you can group similar logic into generic type methods and make use of anonymous classes if you have interfaces with only one method.

The end goal is to make your development time and maintainance time less troublesome.
