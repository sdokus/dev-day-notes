# Controllers, Containers, Providers

## First off, big picture 'What are we talking about?'
Think of building a WordPress plugin like managing a workshop.
- **Dependency Injection (DI)** is like having tools handed to you as you work, so you don’t have to rummage around to find them.
- **Containers** are like toolboxes where all your tools are neatly organized, ready to be grabbed when needed.
- **Service Locators** are like a big board on the wall where you list where each tool is stored, so you can go and fetch it.
- **Service Providers** are like the folks who set up the workshop, making sure all the tools are in the right places and ready for use.

## Big Picture Why?
- **Performance** - Efficient resource management through controlled instantiation and lazy loading.
    - AKA only load things when they're needed and being used.
- **Organization** - Clean, modular code structure with centralized dependency management and predictability.
    - An analogy is like car designs - even though car models differ, the key elements (steering wheel, gas pedal, etc) are typically in the same predictable places so any driver can drive any car.
    - AKA it's easier to find things when they're broken up versus on giant monolith file, while still keeping things consistent throughout the code.
- **Testing** - Easier, more isolated testing with the ability to inject mocks and test-specific configurations.
    - AKA keeping things separated makes it easy to mix and match different scenarios when writing tests.

## Dependency Injection
- Instead of having a class build everything it needs within the class itself every time it is instantiated, DI pulls the dependencies out of the class and then passes them back in.
- By pulling out the variables that the class is dependent on and then passing them in to the class, making the class more flexible.
- Also makes testing easier because it's easy to mock data and then pass/inject it into the class before testing.
- [Video](https://drive.google.com/file/d/1RBp5ea2myjQ6Fclf3UQR9iLxu3BOySXp/view?usp=drive_link)

## Containers
- Containers can be set up (bound) as `key, value` pairs - with the key typically being a string and the value being what is instantiated (usually either an object or a function)
- A container is not a _blueprint_ like a class; instead, it’s a _system_ that holds and manages the **creation** and **delivery** of different classes (or services).
    - It’s like a storage system where you define how various objects are created and how they relate to each other.
- `tribe()` is a container
    - This is how we're able to do things like `tribe( 'Something::class' )->get();`
- Instead of building everything yourself, you ask the container to provide you with what you need, and it takes care of the details.
    - Can use the metaphor of a menu
        - the dishes are the various classes or services in your application
        - the ingredients are the underlying dependencies that the dishes need
        - ordering off the menu allows the dish to be delivered without you needing to involved in the cooking.
- [Video](https://drive.google.com/file/d/1B2egQ9ldce_djDTO3cA2GIt3vsdvd6CH/view?usp=drive_link)
- There are some important built in methods in containers:
    - `->get( $key )` - retrieves an instance of a class or service from the container
    - `->bind( $key , $value, [ $optional_methods_to_automatically_call ] )` - used to tell the container how to create a specific class or service when it’s requested.
    - `->singleton()` - similar to bind, but ensures that the container only creates one instance of the bound class or service. Any subsequent calls to get will return the same instance.
    - `->when()->needs()->give()` - Contextual Binding AKA auto-wiring
- Auto-wiring is a way to automatically pass dependencies within containers and can be set up conditionally.
- [Auto-Wiring Video](https://drive.google.com/file/d/1b5JwYRYyiBbu54Ouez9zK-a0ZgHcT25I/view?usp=drive_link)

## Service Locators
- Basically shorthand for containers - Matt says it's not a good pattern, but we use it all the time.
- Example = `get_option()` function - it’s essentially a service locator for your site’s configuration. You’re asking WordPress, “Where’s the option I need?” instead of injecting that option directly into your code.
    - According to wikipedia (& Matt mentions this) it's not ideal because it's an "anti-pattern", meaning it hides dependencies, making the code harder to test and understand
- [Service Locators Wikipedia Entry](https://en.wikipedia.org/wiki/Service_locator_pattern)
- [Video](https://drive.google.com/file/d/19GXuMGn5hn-0redLj7OduDkA7T8IWGsR/view?usp=drive_link)

## Service Providers
- Service Providers are classes that group together related services and dependencies.
    - AKA Controllers in TEC
- Each provider is responsible for registering and sometimes booting (initializing) a set of related services.
- `register()` (or `do_register()` in Controllers) is expected/required.
- Our entire plugin suite is one single container, but made up of a bunch of Service Providers/Controllers which allow us to modularize our code.
- By modularizing our code using Service Providers, we can conditionally and easily control which parts of the code are 'on' or 'off'.
- [Video](https://drive.google.com/file/d/1LPR3TsSKG_jLcClD4-BLcDqTlYhjVbah/view?usp=drive_link)
- [TEC Examples Video](https://drive.google.com/file/d/1Q_RQQwZ6dgLjSQfostN6OK5_pSVQug_h/view?usp=drive_link)

## Other Important Concepts
- [di52](https://github.com/lucatume/di52) = a library that Luca wrote to expand on Containers/Service Providers.
- **Interface** =  A contract that a class must fulfill. It defines what methods a class should have, ensuring consistency. If a class implements an interface, it’s like agreeing to include all the methods defined in that interface. This is crucial in WordPress development for maintaining consistency and reliability across different parts of a plugin or theme.
