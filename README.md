# AFH-ForPyram

As we can see, the main difference between while and do-while loop is that in the first case the condition is checked before executing the body of the loop, while in the second case — after.

## for loop

For loop looks like this:

``` java
for ( init ; condition ; incr ) {
      // ...
      // ...
}
```

where (below, by expression we mean anything that has a value)

- **init**: one declaration (possibly of several variables of the same type), or zero or more comma-separated expressions;
- **condition**: expression with a value of type boolean; if left empty – interpreted as true;
- **incr**: zero or more comma-separated expressions.

Any (or even all) of the three parts may be empty, but exactly two semicolons are always required.

The execution of a loop proceeds as follows:

1. The `init` part will be executed once only, before entering the loop. If it is a declaration of one or more variables of the same type, they will exist only within the body of the loop — they are not visible (in fact, they don’t even exist) when the flow of control goes out of the loop.
2. The `condition` part will be evaluated next (if left empty, it will be assumed true). If it evaluates to false, the loop ends and the flow of control goes out of the loop. If it evaluates to true then the body of the loop is executed.
3. When execution of the body of the loop is completed, the `incr` part is executed, and then we go back to item 2 (evaluation of the condition).

Here is your provided text, corrected and formatted for GitHub Markdown:

```markdown
For example, the following snippet calculates and prints the sum of all natural numbers from the range [1, 1000]:

```java
int sum = 0;
for (int i = 1; i <= 1000; ++i) {
    sum += i;
}
System.out.println("Sum is " + sum);
```

In the example above, the braces could have been omitted, because the body of the loop consists of only one statement:

```java
int sum = 0;
for (int i = 1; i <= 1000; ++i)
    sum += i;
System.out.println("Sum is " + sum);
```

Note that we cannot declare `sum` in the `init` part of the loop:

```java
for (int i = 1, sum = 0; i <= 1000; ++i)
    sum += i;
System.out.println("Sum is " + sum);
// no 'sum' here!
```

because it would not exist after exiting the loop, so we would not be able to print its value.

In the following example we have nested for-loops: in each iteration of the main (outer) loop, the program executes two inner loops which print first some spaces and then some asterisks in such a way that a “pyramid” is formed with number of asterisks in the bottom line equal to a number read from input:

## Listing 20 AFH-ForPyram/Stars.java Page 42

```java
import java.util.Scanner;

public class Stars {
    public static void main (String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.print("Enter a positive odd number: ");
        int n = scan.nextInt();
        scan.close();

        for (int len=1, sp=n/2; len <= n; len+=2, --sp) {
            for (int i = 0; i < sp; ++i)
                System.out.print(" ");
            for (int i = 0; i < len; ++i)
                System.out.print("*");
            System.out.println();
        }
    }
}
```

For example, if the input is 9, the program prints

```
        *
       ***
      *****
     *******
    *********
```
