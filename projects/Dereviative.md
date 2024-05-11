---
layout: project
type: project
image: img/micromouse/micromouse-square.jpg
title: "Derivative Calculator"
date: 2022
published: true
labels:
  - Python
  - Java
summary: "Passion project, derivative calculator made from Java."
---

This project was born out of boredom, I sat there in my calculus class watching my professor explain the different rules and identities of each of the common mathematical functions and their respective derivatives and anti-derivatives. I thought to myself, \"hey, these rules are kind of straight forward maybe I can write them into a code database and calculate the answers to my homework\". 

I spent the next few nights and days furiously clacking away at my laptop, coding my derivative calculator program. Although I still need to run a few more test to ensure I covered all, if not most of the common mathematical functions and their respective differentiation and integration rules.  

```java

import java.util.Scanner; 
public class Assignment07 {
    
    public static void main(String args[]) {
        
    Scanner input = new Scanner(System.in);    
    String userIn = "";
    String userPass = "";
    int i = 0; // used to keep count of trials
    String nP = "";
    String rnP = "";
    String changePassword = "";
    
    System.out.print("Username: ");
    userIn = input.nextLine();
    System.out.print("Type your current password: ");
    userPass = input.nextLine();
    
    if (userPasswordMatch(userIn, userPass) == false) { // in case credentials is wrong, have user try again two more times
        while (i < 2) { // i is capped at two becuase one trial is used on lines 16-19
            System.out.println("Username or password incorrect.");
            System.out.println("Try again.");
            System.out.println();
            System.out.print("Username: ");
            userIn = input.nextLine();
            System.out.print("Type your current password: ");
            userPass = input.nextLine();
            i = i + 1;  // counts the number of tries 
            //System.out.println(i); test to keep count of i 
            if (userPasswordMatch(userIn, userPass) == true) {
            i = i + 3; // added this to make it end the loop/jump out of the loop if correct credentials were entered during loop
            }
            if (i == 2) { // after the thrid failed attempt, end loop with statemeny 
            System.out.println("Username or password incorrect.");
            System.out.println("Too many attempts.");
            }
            if (i >= 3) { // statement for sucessful login during the loop 
                System.out.println("Login successful.");
                System.out.println();
                System.out.print("Type a new password: "); // lines 42 - 51 is extra credit portion password changer
                nP = input.nextLine();
                System.out.print("Retype the new password: ");
                rnP = input.nextLine();
                if (passwordChecker(nP,rnP) == true) {
                    System.out.println();
                    System.out.println("Your password was changed to: " + nP);
                }
                else {
                    System.out.println();
                    System.out.println("Your password was not changed.");
                }
            }
        }
        input.close();
    }
    
    else if (userPasswordMatch(userIn, userPass) == true) { // statement for correct credentials during first try 
        System.out.println("Login successful.");
        System.out.println();
        System.out.print("Type a new password: "); // lines 59 - 68 is extra credit portion password changer 
        nP = input.nextLine();
        System.out.print("Retype the new password: ");
        rnP = input.nextLine();
        if (passwordChecker(nP,rnP) == true) {
            System.out.println();
            System.out.println("Your password was changed to: " + nP);
        }
        else {
            System.out.println();
            System.out.println("Your password was not changed.");
        }
    }    
}
    
    public static boolean userPasswordMatch (String userIn, String userPass) { // checks credentials 
        
    boolean u1 = (userIn.equals("alpha") && userPass.equals("alpha1"));
    boolean u2 = (userIn.equals("beta") && userPass.equals("beta1"));
    boolean u3 = (userIn.equals("gamma") && userPass.equals("gamma1"));
    boolean u4 = (userIn.equals("delta") && userPass.equals("delta1"));
        
    if (u1 == true || u2 == true || u3 == true || u4 == true) {
        return true;
    }
    else {
        return false;
    }
    }
    public static boolean passwordChecker(String nP, String rnP) {
        int x = nP.length(); // used to compare new password to condition of 6 or more characters 
        boolean b1 = nP.contains("!"); // lines 78-80 used to find multiple special characters 
        boolean b2 = nP.contains("$");
        boolean b3 = nP.contains("?");
        
        if ((x < 6) && (!nP.equals(rnP)) && (nP.contains(" ")) && (!(b1==true || b2==true || b3==true))) { // lines 82 - 148 covers every single error
            System.out.println();
            System.out.println("Your new password must contain 6 or more characters."); // message of every possible combination of an error  
            System.out.println("Your new passwords must match.");
            System.out.println("Your new password can not have spaces.");
            System.out.println("Your new password must contain ! or $ or ?.");
            return false;
        }
        else if ((x < 6) && (!nP.equals(rnP)) && (nP.contains(" "))) {
            System.out.println();
            System.out.println("Your new password must contain 6 or more characters.");
            System.out.println("Your new passwords must match.");
            System.out.println("Your new password can not have spaces.");
            return false;
        }
        else if ((!nP.equals(rnP)) && (nP.contains(" ")) && (!(b1==true || b2==true || b3==true))) {
            System.out.println();
            System.out.println("Your new passwords must match.");
            System.out.println("Your new password can not have spaces.");
            System.out.println("Your new password must contain ! or $ or ?.");
            return false;
        }
        else if ((x < 6) && (nP.contains(" ")) && (!(b1==true || b2==true || b3==true))) {
            System.out.println();
            System.out.println("Your new password must contain 6 or more characters.");
            System.out.println("Your new password can not have spaces.");
            System.out.println("Your new password must contain ! or $ or ?.");
            return false;
        }
        else if ((x < 6) && (!nP.equals(rnP)) && (!(b1==true || b2==true || b3==true))) {
            System.out.println();
            System.out.println("Your new password must contain 6 or more characters.");
            System.out.println("Your new passwords must match.");
            System.out.println("Your new password must contain ! or $ or ?.");
            return false;
        }
        else if ((x < 6) && (!nP.equals(rnP))) {
            System.out.println();
            System.out.println("Your new password must contain 6 or more characters.");
            System.out.println("Your new passwords must match.");
            return false;
        }
        else if ((!nP.equals(rnP)) && (nP.contains(" "))) {
            System.out.println();
            System.out.println("Your new passwords must match.");
            System.out.println("Your new password can not have spaces.");
            return false;
        }
        else if ((nP.contains(" ")) && (!(b1==true || b2==true || b3==true))) {
            System.out.println();
            System.out.println("Your new password can not have spaces.");
            System.out.println("Your new password must contain ! or $ or ?.");
            return false;
        }
        else if ((x < 6) && (!(b1==true || b2==true || b3==true))) {
            System.out.println();
            System.out.println("Your new password must contain 6 or more characters.");
            System.out.println("Your new password must contain ! or $ or ?.");
            return false;
        }
        else if (x < 6) {
            System.out.println();
            System.out.println("Your new password must contain 6 or more characters.");
            return false;
        } 
        else if (!nP.equals(rnP)) {
            System.out.println();
            System.out.println("Your new passwords must match.");
            return false;
        }
        else if (nP.contains(" ")) {
            System.out.println();
            System.out.println("Your new password can not have spaces.");
            return false;
        }
        else if (!(b1==true || b2==true || b3==true)) {
            System.out.println();
            System.out.println("Your new password must contain ! or $ or ?.");
            return false;
        }
        return true;
    }
}
```
