import java.util.Random;
import java.util.Scanner;

public class GuessTheNumber {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int lowerBound = 1;
        int upperBound = 100;
        int rounds = 3; // Number of rounds
        int totalScore = 0;

        System.out.println("Welcome to Guess the Number!");

        for (int round = 1; round <= rounds; round++) {
            int targetNumber = random.nextInt(upperBound - lowerBound + 1) + lowerBound;
            int attempts = 0;
            int score = 0;

            System.out.println("\nRound " + round + ": Guess a number between " + lowerBound + " and " + upperBound);

            while (true) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempts++;

                if (userGuess == targetNumber) {
                    System.out.println("Congratulations! You guessed the correct number in " + attempts + " attempts.");
                    score = calculateScore(attempts);
                    System.out.println("Round Score: " + score);
                    totalScore += score;
                    break;
                } else if (userGuess < targetNumber) {
                    System.out.println("Try again! The number is higher.");
                } else {
                    System.out.println("Try again! The number is lower.");
                }

                if (attempts == 3) {
                    System.out.println("Sorry, you've reached the maximum number of attempts. The correct number was " + targetNumber);
                    break;
                }
            }
        }

        System.out.println("\nGame Over! Total Score: " + totalScore);
        scanner.close();
    }

    private static int calculateScore(int attempts) {
        if (attempts == 1) {
            return 10;
        } else if (attempts <= 3) {
            return 5;
        } else if (attempts <= 6) {
            return 2;
        } else {
            return 0;
        }
    }
}
