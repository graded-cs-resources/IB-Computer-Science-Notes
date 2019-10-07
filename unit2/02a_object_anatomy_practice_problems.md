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

4. Write a class called `Bobbies` that has one private instance variable, `jo` with an initial value of "what?" and an empty constructor. Add a static method named `merles` that accepts formal parameters `wagging` and `reaching` as numbers, finds their sum, stores the result in a local variable call `verbs` then returns the value of `verbs`.  Outside the class, create a new Boobies object named `b`, then call the `merles` method with the values 2 and 3, storing the result in a global variable called `yo`.
   
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