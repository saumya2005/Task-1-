# Task-1-
import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int lowerBound = 1;
        int upperBound = 100;
        int maxAttempts = 10;
        int score = 0;
        boolean playAgain = true;

        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("I've selected a number between " + lowerBound + " and " + upperBound + ".");
        System.out.println("You have " + maxAttempts + " attempts to guess it.");

        while (playAgain) {
            int numberToGuess = random.nextInt(upperBound - lowerBound + 1) + lowerBound;
            int numberOfAttempts = 0;
            boolean hasGuessedCorrectly = false;

            while (!hasGuessedCorrectly && numberOfAttempts < maxAttempts) {
                System.out.print("Attempt " + (numberOfAttempts + 1) + ": Enter your guess: ");
                int userGuess = scanner.nextInt();
                numberOfAttempts++;

                if (userGuess < lowerBound || userGuess > upperBound) {
                    System.out.println("Please enter a number between " + lowerBound + " and " + upperBound + ".");
                } else if (userGuess < numberToGuess) {
                    System.out.println("Try a higher number.");
                } else if (userGuess > numberToGuess) {
                    System.out.println("Try a lower number.");
                } else {
                    System.out.println("Congratulations! You've guessed the number " + numberToGuess + " in " + numberOfAttempts + " attempts.");
                    score++;
                    hasGuessedCorrectly = true;
                }
            }

            if (!hasGuessedCorrectly) {
                System.out.println("Sorry, you've run out of attempts. The correct number was " + numberToGuess + ".");
            }

            System.out.print("Do you want to play again? (yes/no): ");
            String playAgainChoice = scanner.next().toLowerCase();
            if (!playAgainChoice.equals("yes")) {
                playAgain = false;
            }
        }

        System.out.println("Game over! Your final score: " + score);
        scanner.close();
    }
}
