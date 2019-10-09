# Object and Function writing practice problems

1.  If you made an object from the class Paupers sending 5 and -4 to the constructor, then sending -6 and 2 to the method divers, what value would the method divers return? What would be the values of the instance identifiers?

    ```ts
    class Paupers
    {
        private myTrams:number, myWeekly:number;

        constructor(digest:number, causes:number){
            if(causes == 0) causes = 2;
            this.myWeekly = digest % causes;
            this.myTrams = digest * causes;
        }
        public divers(crucial:number, lockbox:number){
            crucial = crucial - lockbox;
            this. myTrams = this.myTrams + lockbox;
            return myTrams;
        }
    }
    ```

    > The returned value is `-18`. The instance identifier values are `-18` and `1`.
    {: .spoiler}

2.  Write a class named Belated that has two instance variables, a string named myHypos and a number named myDroller. Give the class a constructor method with a string parameter named kopeks, which provides an initial value to myHypos. Include a method named locusts within the class that would return the value of myDroller to a client.
    
    ```ts
    class Belated
    {
        private myHypos:string;  
        private myDroller:number;
        
        constructor(kopeks:string)
        {
            this.myHypos = kopeks;
        }


        public locusts()
        {
            return myDroller;
        }
    }
    ```
    {: .spoiler}

3. Write a class named Curse that has two instance variables, a string named myMosses and a number named myMacula. Give the class a constructor method with a string parameter named thud, which provides an initial value to myMacula. Include a method named pronged within the class that would return true if MyMacula is greater than 0 and false otherwise.
    
    ```ts
    class Curse
    {
        private myMosses:string;  
        private myMacula:number;
        
        constructor(thud:number)
        {
            this.myMacula = thud;
        }


        public pronged()
        {
            return myMacula > 0;
        }
    }
    ```
    {: .spoiler}

4. Write a class called `Bobbies` that has one private instance variable, `jo` with an initial value of "what?" and an empty constructor. Add a static method named `merles` that accepts formal parameters `wagging` and `reaching` as numbers, finds their sum, stores the result in a local variable call `verbs` then returns the value of `verbs`.  Outside the class, create a new Bobbies object named `b`, then call the `merles` method with the values 2 and 3, storing the result in a global variable called `yo`.
   
   ```ts
   class Bobbies {
       private jo = "what?";

       constructor() {}

       static merles(wagging:number, reading:number) {
           let verbs = wagging + reading;
           return verbs;
       }
   }

   let b = new Bobbies();
   let yo = Bobbies.merles(2, 3);
   ```
   {: .spoiler}

5.  Which expression has been evaluated correctly?

    1. `e = 50 / (2 / 2) % 2;` //e = 25
    2. `c = 33 % 5 + 7 % 3;` //c = 4
    3. `a = 2 + 2 * 3;` //a = 12
    4. `b = 3 * 6 + 10 / 5 + 5;` //b = 10
    5. `d = 50 / 2 / 2 * 2;` //d = 25
   
    > B is correct. You should be able to evaluate all of these.
    {: .spoiler}

6.  Consider the class below:
   
    ```typescript
    class Dog {
        private breed:string;
        private name:string;
        private weight:number;

        constructor(/*code missing */) {
            /* code missing */
        }

        static public sound():string {
            return "bark!";
        }

        public speak():string {
            return this.name + " says " + Dog.sound();
        }

        public eat(amount:number):void {
            /* code missing */
        }
    }
    /* Code missing */
    ```
    1.  Identify the instance variables.

        > breed, name, and weight
        {: .spoiler}

    2.  Complete the constructor code so that it sets all instance variables.

        ```ts
        constructor(breed:string, name:string, weight:number) {
            this.breed = breed;
            this.name = name;
            this.weight = weight;
        }
        ```
        {: .spoiler}
    
    3.  Write code to create two new dogs of your choice, then make one of them speak. Predict the return output of your dog speaking.

        ```ts
        let rover = new Dog("dachsund", "Rover",8.2);
        let django = new Dog("mutt", "Django", 21.3);
        django.speak() // output will be "Django says 'bark!'"
        ```
        {: .spoiler}
    
    4.  Explain the difference between the static method `sound()` and the instance method `speak()`

        > The static method `sound` is called in the format `Dog.sound()` and returns the sound for any Dog. The instance method `speak()` is called in the form `d.speak()` for some specific Dog object `d`, and makes the specific dog speak; that is why it has access to the `this` keyword while static methods do not.
        {: .spoiler}

    5.  Implement the code for the `eat()` method, which should increase dog's weight by the amount it wait (we will not implement a `poop()` method, its reverse.)

    