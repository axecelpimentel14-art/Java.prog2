
java.prog2
import java.util.Scanner;

public class LostAndFoundSystem {

    static Scanner sc = new Scanner(System.in);

    static String[] lostItems = new String[10];
    static String[] foundItems = new String[10];

    static String[] lostLocations = new String[10];
    static String[] foundLocations = new String[10];

    static int lostCount = 0;
    static int foundCount = 0;

    public static void main(String[] args) {

        System.out.println("=====================================");
        System.out.println(" CAMPUS LOST AND FOUND MANAGEMENT ");
        System.out.println("=====================================");

        System.out.print("Do you want to login? (yes/no): ");
        String login = sc.nextLine();

        if(login.equalsIgnoreCase("yes")){

            System.out.print("Enter Username: ");
            String user = sc.nextLine();

            System.out.print("Enter Password: ");
            String pass = sc.nextLine();

            if(!user.isEmpty() && !pass.isEmpty()){

                System.out.println("Login successful! Welcome, " + user);

                int option;

                do{
                    System.out.println("\n========= MAIN MENU =========");
                    System.out.println("1. Report Lost Item");
                    System.out.println("2. Report Found Item");
                    System.out.println("3. Search Item");
                    System.out.println("4. Display Lost Items");
                    System.out.println("5. Display Found Items");
                    System.out.println("6. Logout");
                    System.out.println("=============================");

                    System.out.print("Choose option: ");

                    while(!sc.hasNextInt()){
                        System.out.print("Invalid input. Enter number: ");
                        sc.next();
                    }

                    option = sc.nextInt();
                    sc.nextLine();

                    switch(option){

                        case 1:
                            reportLostItem();
                            break;

                        case 2:
                            reportFoundItem();
                            break;

                        case 3:
                            searchItem();
                            break;

                        case 4:
                            displayLostItems();
                            break;

                        case 5:
                            displayFoundItems();
                            break;

                        case 6:
                            System.out.println("Logging out...");
                            break;

                        default:
                            System.out.println("Invalid option. Try again.");
                    }

                } while(option != 6);

            } else {
                System.out.println("Username and password cannot be empty.");
            }

        } else {
            System.out.println("Exiting program...");
        }

        System.out.println("Program Ended.");
    }

    public static void reportLostItem(){

        if(lostCount >= lostItems.length){
            System.out.println("Lost items list is FULL.");
            return;
        }

        System.out.print("Enter lost item name: ");
        String item = sc.nextLine();

        System.out.print("Enter location lost: ");
        String location = sc.nextLine();

        lostItems[lostCount] = item;
        lostLocations[lostCount] = location;
        lostCount++;

        System.out.println("Submitting lost report...");
        System.out.println("Your report has been submitted successfully.");
    }

    public static void reportFoundItem(){

        if(foundCount >= foundItems.length){
            System.out.println("Found items list is FULL.");
            return;
        }

        System.out.print("Enter found item name: ");
        String item = sc.nextLine();

        System.out.print("Enter location found: ");
        String location = sc.nextLine();

        foundItems[foundCount] = item;
        foundLocations[foundCount] = location;
        foundCount++;

        System.out.println("Submitting found report...");
        System.out.println("Your report has been submitted successfully.");
    }

    public static void searchItem(){

        System.out.print("Enter item to search: ");
        String search = sc.nextLine();

        boolean found = false;

        for(int i = 0; i < lostCount; i++){
            if(lostItems[i].toLowerCase().contains(search.toLowerCase())){
                System.out.println("Item found in LOST list: " + lostItems[i] + " | Location: " + lostLocations[i]);
                found = true;
            }
        }

        for(int i = 0; i < foundCount; i++){
            if(foundItems[i].toLowerCase().contains(search.toLowerCase())){
                System.out.println("Item found in FOUND list: " + foundItems
