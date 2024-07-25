import java.util.Random;
import java.util.Scanner;

public class GuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        
        int minRange = 1;
        int maxRange = 100;
        int maxAttempts = 10;
        int totalRounds = 0;
        int totalScore = 0;
        String playAgain;

        do {
            int targetNumber = random.nextInt(maxRange - minRange + 1) + minRange;
            int attempts = 0;
            boolean guessedCorrectly = false;

            System.out.println("Welcome to the Guessing Game!");
            System.out.println("I have generated a random number between " + minRange + " and " + maxRange + ".");
            System.out.println("You have " + maxAttempts + " attempts to guess the number.");

            while (attempts < maxAttempts && !guessedCorrectly) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempts++;

                if (userGuess < targetNumber) {
                    System.out.println("Too low!");
                } else if (userGuess > targetNumber) {
                    System.out.println("Too high!");
                } else {
                    System.out.println("Correct! You've guessed the number in " + attempts + " attempts.");
                    guessedCorrectly = true;
                }
            }

            if (!guessedCorrectly) {
                System.out.println("Sorry, you've used all " + maxAttempts + " attempts. The correct number was " + targetNumber + ".");
            }

            totalRounds++;
            totalScore += maxAttempts - attempts + 1; // Higher score for fewer attempts

            System.out.print("Do you want to play again? (yes/no): ");
            playAgain = scanner.next();
        } while (playAgain.equalsIgnoreCase("yes"));

        System.out.println("Game over! You've played " + totalRounds + " rounds.");
        System.out.println("Your total score is " + totalScore + ".");
        System.out.println("Thank you for playing!");

        scanner.close();
    }
}
