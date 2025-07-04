# super-cricket
you can play a cricket game against your computer bot!
import random

def toss():
    choice = input("Choose Head or Tail: ").lower()
    toss_result = random.choice(['head', 'tail'])
    if choice == toss_result:
        print("You won the toss!")
        return input("Choose to Bat or Bowl: ").lower()
    else:
        print("Computer won the toss!")
        return random.choice(['bat', 'bowl'])

def batting(player):
    runs = 0
    while True:
        try:
            player_run = int(input("Enter your run (1-6): "))
            if player_run < 1 or player_run > 6:
                print("Invalid input. Enter a number between 1 and 6.")
                continue
        except ValueError:
            print("Enter a valid number!")
            continue

        computer_run = random.randint(1, 6)
        print(f"Computer bowled: {computer_run}")
        
        if player_run == computer_run:
            print("You're OUT!")
            break
        runs += player_run
        print(f"Your current score: {runs}")
    return runs

def bowling():
    runs = 0
    while True:
        try:
            player_bowl = int(input("Enter your bowl (1-6): "))
            if player_bowl < 1 or player_bowl > 6:
                print("Invalid input. Enter a number between 1 and 6.")
                continue
        except ValueError:
            print("Enter a valid number!")
            continue

        computer_bat = random.randint(1, 6)
        print(f"Computer played: {computer_bat}")
        
        if player_bowl == computer_bat:
            print("Computer is OUT!")
            break
        runs += computer_bat
        print(f"Computer's current score: {runs}")
    return runs

def game():
    print("Welcome to Hand Cricket Game!")
    user_choice = toss()

    if user_choice == 'bat':
        user_score = batting("player")
        print(f"Your final score: {user_score}")
        print("Computer is batting now. Try to bowl them out!")
        computer_score = bowling()

    else:
        computer_score = bowling()
        print(f"Computer's final score: {computer_score}")
        print("Your turn to bat. Try to beat the score!")
        user_score = batting("player")

    print("\n--- Match Result ---")
    if user_score > computer_score:
        print("You Win! 🎉")
    elif user_score < computer_score:
        print("Computer Wins! 🤖")
    else:
        print("It's a Tie! 🤝")

if __name__ == "__main__":
    game()

