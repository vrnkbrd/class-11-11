# class-11-11
### Task 7kyu 
The task:
You have to make a program capable of returning the sum of all the elements of a triangle with side of size n+1n+1n+1.

The problem
Your solution has to support 0≤n≤1060\leq n \leq 10^60≤n≤10 
6
 . Brute-forcing will not work!

The definition
A triangle element aija_{ij}a 
ij
​
  where iii is the column and jjj is the row can be defined as aij=2j+i+1a_{ij}=2j + i + 1a 
ij
​
 =2j+i+1 where 0≤j≤i≤n0\leq j\leq i\leq n0≤j≤i≤n
#### My solution
public class TriangleSum {
  public static long getSum(int m){
    long n = m + 1;
    return n * (n + 1) * (4 * n - 1) / 6;
  }
}
##### Fav solution:
interface TriangleSum {
  static long getSum(long n) {
    return ++n * (4 * n - 1) * ++n / 6;
  }
}

### Task 2 7 kyu 
In a small town the population is p0 = 1000 at the beginning of a year. The population regularly increases by 2 percent per year and moreover 50 new inhabitants per year come to live in the town. How many years does the town need to see its population greater or equal to p = 1200 inhabitants?

At the end of the first year there will be: 
1000 + 1000 * 0.02 + 50 => 1070 inhabitants

At the end of the 2nd year there will be: 
1070 + 1070 * 0.02 + 50 => 1141 inhabitants (** number of inhabitants is an integer **)

At the end of the 3rd year there will be:
1141 + 1141 * 0.02 + 50 => 1213

It will need 3 entire years.
More generally given parameters:

p0, percent, aug (inhabitants coming or leaving each year), p (population to equal or surpass)

the function nb_year should return n number of entire years needed to get a population greater or equal to p.

aug is an integer, percent a positive or null floating number, p0 and p are positive integers (> 0)

Examples:
nb_year(1500, 5, 100, 5000) -> 15
nb_year(1500000, 2.5, 10000, 2000000) -> 10
Note:
Don't forget to convert the percent parameter as a percentage in the body of your function: if the parameter percent is 2 you have to convert it to 0.02.

#### My solution: 
class Arge {
    
   public static int nbYear(int p0, double percent, int aug, int p) { 
    int years = 0;
    while (p0 < p) {
      p0 = (int) (p0 + (p0 * (percent/100)) + aug);
      years++;
    }
    return years;
  }
}
#### Fav solution: 
class Arge {
    
    public static int nbYear(int p0, double percent, int aug, int p) {
        int years = 0;
        for ( double principal = p0; principal < p; principal = aug + principal + principal * ( percent / 100 ) , years++ );
        return years;
    }
}
