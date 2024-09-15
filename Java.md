### Examples of different Java codes

public class Main {
  public static void main(String[] args) {

   // +5 wear super warm 
    // +5 to 15 warm
    // 15 to 30 normal 
    // 30+ cooling 
    
    double temp = -15.0;

    if (temp <= 5) {
      System.out.println("Wear super warm");
    }
    else if (temp <= 15) {
      System.out.println("Wear warm");
    }
    else if (temp <= 30) {
      System.out.println("Wear normal");
    }
    else {
      System.out.println("You need cooling");
    }
}
}
