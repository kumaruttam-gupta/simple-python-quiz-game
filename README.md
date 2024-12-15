def display_question(question, options, correct_answer):
    """Displays a question and its options. Returns True if the answer is correct."""
    print(f"\n{question}")
    for i, option in enumerate(options, start=1):
        print(f"{i}. {option}")

    while True:
        try:
            user_input = int(input("Your answer (1/2/3/4): "))
            if 1 <= user_input <= len(options):
                break
            else:
                print("Invalid choice. Please choose a valid option.")
        except ValueError:
            print("Invalid input. Please enter a number.")

    if options[user_input - 1] == correct_answer:
        print("Correct!")
        return True
    else:
        print(f"Wrong! The correct answer is: {correct_answer}")
        return False

def run_quiz(questions):
    """Runs the quiz game."""
    score = 0
    total_questions = len(questions)

    for q in questions:
        is_correct = display_question(q['question'], q['options'], q['answer'])
        if is_correct:
            score += 1

    print("\nQuiz Completed!")
    print(f"Your final score is {score}/{total_questions}")

    if score == total_questions:
        print("Excellent work!")
    elif score > total_questions // 2:
        print("Good job! Keep practicing.")
    else:
        print("Better luck next time. Keep learning!")

def main():
    """Main function to execute the quiz."""
    # Define quiz questions, options, and answers
    questions = [
        {
            'question': "What is the capital of France?",
            'options': ["Berlin", "Madrid", "Paris", "Rome"],
            'answer': "Paris"
        },
        {
            'question': "Which programming language is known for its snake logo?",
            'options': ["Java", "C++", "Python", "Ruby"],
            'answer': "Python"
        },
        {
            'question': "What is 5 + 3 * 2?",
            'options': ["16", "13", "11", "10"],
            'answer': "11"
        }
    ]

    print("Welcome to the Basic Quiz Game!")
    run_quiz(questions)

if _name_ == "_main_":
    main()
