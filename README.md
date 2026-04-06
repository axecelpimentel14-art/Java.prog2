# Java.prog2
import java.util.Scanner;

public class LostAndFoundSystem {

    static Scanner sc = new Scanner(System.in);

    static String[] lostItems = new String[10];
    static String[] foundItems = new String[10];

    static int lostCount = 0;
    static int foundCount = 0;

    public static void main(String[] args) {

        System.out.println("Campus Lost and Found Management System");

        System.out.print("Do you want to login? (yes/no): ");
        String login = sc.nextLine();

        if(login.equalsIgnoreCase("yes")){

            System.out.print("Enter Username: ");
            String user = sc.nextLine();

            System.out.print("Enter Password: ");
            String pass = sc.nextLine();

            if(user.equals("admin") && pass.equals("1234")){

                int option;

                do{
                    System.out.println("\n===== MAIN MENU =====");
                    System.out.println("1. Report Lost Item");
                    System.out.println("2. Report Found Item");
                    System.out.println("3. Search Item");
                    System.out.println("4. Display Lost Items");
                    System.out.println("5. Display Found Items");
                    System.out.println("6. Logout");

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
                            System.out.println("Invalid option.");
                    }

                }while(option != 6);

            }else{
                System.out.println("Invalid username or password.");
            }

        }else{
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

        lostItems[lostCount++] = item;

        System.out.println("Lost item reported successfully.");
    }

    public static void reportFoundItem(){

        if(foundCount >= foundItems.length){
            System.out.println("Found items list is FULL.");
            return;
        }

        System.out.print("Enter found item name: ");
        String item = sc.nextLine();

        foundItems[foundCount++] = item;

        System.out.println("Found item reported successfully.");
    }

    public static void searchItem(){

        System.out.print("Enter item to search: ");
        String search = sc.nextLine();

        boolean found = false;

        for(int i = 0; i < lostCount; i++){
            if(lostItems[i].toLowerCase().contains(search.toLowerCase())){
                System.out.println("Found in LOST: " + lostItems[i]);
                found = true;
            }
        }

        for(int i = 0; i < foundCount; i++){
            if(foundItems[i].toLowerCase().contains(search.toLowerCase())){
                System.out.println("Found in FOUND: " + foundItems[i]);
                found = true;
            }
        }

        if(!found){
            System.out.println("Item not found.");
        }
    }

    public static void displayLostItems(){

        if(lostCount == 0){
            System.out.println("No lost items reported.");
            return;
        }

        System.out.println("\nLost Items List:");
        for(int i = 0; i < lostCount; i++){
            System.out.println((i + 1) + ". " + lostItems[i]);
        }
    }

    public static void displayFoundItems(){

        if(foundCount == 0){
            System.out.println("No found items reported.");
            return;
        }

        System.out.println("\nFound Items List:");
        for(int i = 0; i < foundCount; i++){
            System.out.println((i + 1) + ". " + foundItems[i]);
        }
    }
}
