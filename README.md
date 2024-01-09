import random

def determine_winner(user_choice, computer_choice):
    if user_choice == computer_choice:
        return "It's a tie!"
    elif (user_choice == "rock" and computer_choice == "scissors") or \
         (user_choice == "scissors" and computer_choice == "paper") or \
         (user_choice == "paper" and computer_choice == "rock"):
        return "You win!"
    else:
        return "You lose!"

def play_game():
    user_score = 0
    computer_score = 0

    while True:
        # User input
        user_choice = input("\nChoose rock, paper, or scissors: ").lower()

        # Validate user input
        if user_choice not in ["rock", "paper", "scissors"]:
            print("Invalid choice. Please choose rock, paper, or scissors.")
            continue

        # Computer selection
        computer_choice = random.choice(["rock", "paper", "scissors"])

        # Determine the winner
        result = determine_winner(user_choice, computer_choice)

        # Update scores
        if "win" in result:
            user_score += 1
        elif "lose" in result:
            computer_score += 1

        # Display choices and result
        print(f"\nYou chose {user_choice}")
        print(f"Computer chose {computer_choice}")
        print(result)

        # Display scores
        print(f"\nScores - You: {user_score}, Computer: {computer_score}")

        # Ask if the user wants to play again
        play_again = input("\nDo you want to play again? (yes/no): ").lower()
        if play_again != "yes":
            print("Thanks for playing!")
            break

# Start the game
play_game()
