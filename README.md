
import java.util.Scanner; // Will be used to get input from the user
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;

public class ATM {
    
// Initialize account information
    private static final String Account_Name = " Fawad Ahmed Baig";
    private static final int    Account_Number = 642597;
    private static double          Account_Balance = 1000;
    private static final int    Account_Pin = 1122;
    private static final int    Account_Number_HBL = 1234567;
    private static  double         Account_Balance_HBL = 100;
    private static final int    Account_Number_UBL = 12345678;
    private static  double         Account_Balance_UBL = 200;
// Display main menu options
public static void mainManu(){ 
    System.out.println("\n");
    System.out.println("\t ATM options");

    System.out.println("------------------------");
    System.out.println("1.Check Balance ");
    System.out.println("2.Withdraw Balance");
    System.out.println("3.Deposit Balance");
    System.out.println("4.Fund Transfer");
    System.out.println("5.Exit");
    System.out.println("\n------------------------");
    System.out.print("\t ENTER A NUMBER : ");
    
    }
 public static void Store_Bank_Balance(){
                try{
                    File Hbl = new File("HBL Balance.txt");
                    FileWriter w = new FileWriter(Hbl);
                    w.write(Double.toString(Account_Balance_HBL));
    
                    w.close();
                    System.out.println("Successfully wrote to the file.");
                }
                catch(IOException e){
                    System.out.println("An error occurred!");
                    e.printStackTrace();
                }
}

    public static void Store_HBL_Balance(){
            try{
                File bank = new File("Bank Balance.txt");
                FileWriter wrt = new FileWriter(bank);
            wrt.write(Double.toString(Account_Balance));
                wrt.close();
                System.out.println("Successfully wrote to the file.");
            }
            catch(IOException e){
                System.out.println("An error occurred!");
                e.printStackTrace();
            }         
}

    public static void Store_UBL_Balance(){
            try{
                File Ubl = new File("UBL Balance.txt");
                FileWriter wr = new FileWriter(Ubl);
            wr.write(Double.toString(Account_Balance_UBL));
                wr.close();
                System.out.println("Successfully wrote to the file.");
            }
            catch(IOException e){
                System.out.println("An error occurred!");
                e.printStackTrace();
            }         
}
    
    private static void load_Bank_Balance() {
        try {
            
            File file = new File("Bank Balance.txt"); // Create a File object for the balance file
            if (file.exists()) { // Check if the balance file exists
                Scanner scanner = new Scanner(file); // Create a Scanner object to read the file
                Account_Balance = Double.parseDouble(scanner.nextLine());
                scanner.close(); // Close the Scanner
            } else {
               
                Account_Balance = 1000;// If the balance file doesn't exist, set a default initial balance
            }
        } catch (IOException e) {
            System.out.println("An error occurred while loading the balance.");
        }
    }
    
    private static void load_HBL_Balance() {
        try {
            
            File file = new File("HBL Balance.txt"); // Create a File object for the balance file
            if (file.exists()) { // Check if the balance file exists
                Scanner scanner = new Scanner(file); // Create a Scanner object to read the file
                Account_Balance_HBL = Double.parseDouble(scanner.nextLine());
                scanner.close(); // Close the Scanner
            } else {
               
                Account_Balance_HBL = 100;// If the balance file doesn't exist, set a default initial balance
            }
        } catch (IOException e) {
            System.out.println("An error occurred while loading the balance.");
        }
    }
    
        private static void load_UBL_Balance() {
        try {
            
            File file = new File("UBL Balance.txt"); // Create a File object for the balance file
            if (file.exists()) { // Check if the balance file exists
                Scanner scanner = new Scanner(file); // Create a Scanner object to read the file
                Account_Balance_UBL = Double.parseDouble(scanner.nextLine());
                scanner.close(); // Close the Scanner
            } else {
               
                Account_Balance_UBL = 100;// If the balance file doesn't exist, set a default initial balance
            }
        } catch (IOException e) {
            System.out.println("An error occurred while loading the balance.");
        }
    }

    
public static void main(String[] args) {
    load_UBL_Balance();
    load_HBL_Balance();
    load_Bank_Balance();
// Initialize scanner to read input from user
    Scanner sc = new Scanner(System.in);
    while(true){// Display welcome message and login page
        System.out.println("===================================");
        System.out.println("* WELCOME TO THE JAVA BANK LIMITED *");
        System.out.println("===================================\n");
    System.out.println();
    System.out.println("     <<<<<<< LOGIN PAGE >>>>>>>>>\n");
    System.out.print("Please enter your Account Number: ");
    double num =sc.nextInt(); // Read account number from user
    System.out.print("Please enter your pin:");
    double pin =sc.nextInt();  // Read PIN from user
    
    // Check if account number and PIN are correct
    if (pin == Account_Pin && num == Account_Number){
     System.out.println("WELCOME! "+ Account_Name);
    
     while(true){ 
          // Display main menu options
            mainManu();
            int op =sc.nextInt();
            switch(op){ 
                
            case 1:  // Display current account balance
                // Clear the console screen
                for (int i = 0; i < 15; i++) {
                System.out.println();}
                System.out.println("Your current balance is : " + Account_Balance +"$");

                break;
            case 2:  // Withdraw money from account
                // Clear the console screen
                for (int i = 0; i < 15; i++) {
                System.out.println();}


                System.out.print("Enter amount that you want to Withdraw : ");
                int amount =sc.nextInt();
                if(amount>Account_Balance){
                System.out.println("Insufficient Balance!");
                break; }
                else
                System.out.println("Process successfully done ");
                System.out.println("You have withdrawn "+amount+"$"+" and now your BANK balance is : " + (Account_Balance - amount)+"$");
                Account_Balance = Account_Balance - amount;
                Store_Bank_Balance();
                
                break;
            case 3: // Display deposit options
                // Clear the console screen
                for (int i = 0; i < 15; i++) {
                System.out.println();}

                        System.out.println("----Cash Deposit Selected---");
                        System.out.print("Enter amount that you want to Deposit : ");
                        int deposit = sc.nextInt();

                        // Clear the console screen
                        for (int i = 0; i < 15; i++) {
                        System.out.println();}

                        System.out.println("Process successfully done ");
                        System.out.println("You have withdrawn "+deposit+"$"+" and now your BANK balance is : " + (Account_Balance + deposit)+"$");
                        Account_Balance = Account_Balance + deposit;
                        Store_Bank_Balance();

                break;
                            
            case 4:
                // Clear the console screen
                for (int i = 0; i < 15; i++) {
                System.out.println();}

                while (true){
                System.out.println("--FUND TRANSFER--");
                System.out.println("");
                System.out.println("HERE ARE SOME AVAILABLE ACCOUNTS FOR FUND TRANCEFER");
                System.out.println("1-Habib Bank Limited (HBL)");
                System.out.println("2-United Bank Limited (UBL)");
                System.out.println("");
                System.out.println("Select Account");
                int y = sc.nextInt();

                  switch(y){
                    case 1:
                            System.out.println("----HBL Selected---");
                            System.out.println("");
                            System.out.print("Enter Account Number : ");
                            int num1 = sc.nextInt();
                            if(num1 != Account_Number_HBL){
                            System.out.println("SORRY INVALID ACCOUNT NUMBER ");
                            continue; }
                            System.out.print("Enter Amount : ");
                            int a1 = sc.nextInt();
                            if(a1>Account_Balance){
                            System.out.println("Insuffient Balance!");
                            break; }
                            else
                            // Clear the console screen
                            for (int i = 0; i < 15; i++) {
                            System.out.println();}
                            System.out.println("Process successfully done ");
                            Account_Balance = Account_Balance - a1;
                            Account_Balance_HBL =  Account_Balance_HBL + a1;
                            System.out.println("--TRANSCRIPT--");
                            System.out.println("you have a Transaction of  "+a1+"$"+" and now your BANK balance is : " + (Account_Balance)+"$");
                            System.out.println("your HBL Account Balance is : "+Account_Balance_HBL + "$");
                            Store_Bank_Balance();
                            Store_HBL_Balance();  
                            System.exit(0);
                            // Clear the console screen

                        break;
                    case 2:
                            System.out.println("----UBL Selected---");
                            System.out.println("");
                            System.out.print("Enter Account Number : ");
                            int num2 = sc.nextInt();
                            if(num2 != Account_Number_UBL){
                            System.out.println("SORRY INVALID ACCOUNT NUMBER ");
                            continue; }
                            System.out.print("Enter Amount : ");
                            int a2 = sc.nextInt();
                            if(a2>Account_Balance){
                            System.out.println("Insufficient Balance! ");
                            break; }
                            else
                            // Clear the console screen
                            for (int i = 0; i < 15; i++) {
                            System.out.println();}
                            System.out.println("Process successfully done ");
                            Account_Balance = Account_Balance - a2;
                            Account_Balance_UBL =  Account_Balance_UBL + a2;
                            System.out.println("--TRANSCRIPT--");
                            System.out.println("you have a Transaction of  "+a2+"$"+" and now your BANK balance is : " + (Account_Balance)+"$");
                            System.out.println("your UBL Account Balance is : "+Account_Balance_UBL + "$");
                            Store_Bank_Balance();
                            Store_UBL_Balance();
                            System.exit(0);
                            break;
                            // Clear the console screen
                    default : // excute at invalid choice
                            // Clear the console screen
                            for (int i = 0; i < 15; i++) {
                            System.out.println();}

                            System.out.println("Invalid Choice  ");

                    }
                    
                }
           


            case 5:
                // Clear the console screen
                for (int i = 0; i < 15; i++) {
                System.out.println();}


                System.out.println("Thanks for using ATM ");
                Store_Bank_Balance();
                Store_HBL_Balance();
                Store_UBL_Balance();
                    
                System.exit(0);

    
                break;
            default :
                // Clear the console screen
                for (int i = 0; i < 15; i++) {
                System.out.println();}

                System.out.println("Invalid Choice  ");
            }
        }
     }
    else
        // Clear the console screen
        for (int i = 0; i < 25; i++) {
        System.out.println();}

        System.out.println("Invalid Account number or Pin !?");
     return;
    }
    
}
}
   
