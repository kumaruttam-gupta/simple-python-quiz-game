# Quiz Data
quiz = [
    {
        "question": "What is the capital of France?",
        "options": ["A. Berlin", "B. Madrid", "C. Paris", "D. Rome"],
        "answer": "C"
    },
    {
        "question": "What is 5 + 3?",
        "options": ["A. 5", "B. 8", "C. 10", "D. 15"],
        "answer": "B"
    },
    {
        "question": "Which programming language is known for its simplicity?",
        "options": ["A. Python", "B. C++", "C. Java", "D. Ruby"],
        "answer": "A"
    }
]

# Function Definitions
def display_question(question_data):
    print("\n" + question_data["question"])
    for option in question_data["options"]:
        print(option)

def validate_input(user_input, options):
    return user_input.upper() in options

def check_answer(user_answer, correct_answer):
    return user_answer.upper() == correct_answer

def display_score(score, total_questions):
    print(f"\nYour final score is {score}/{total_questions}.")
    if score == total_questions:
        print("Excellent job!")
    elif score > total_questions // 2:
        print("Well done!")
    else:
        print("Keep practicing!")

# Main Program
def main():
    score = 0
    for question in quiz:
        display_question(question)
        user_answer = input("Enter your answer (A/B/C/D): ").strip().upper()
        while not validate_input(user_answer, ['A', 'B', 'C', 'D']):
            print("Invalid input. Please enter A, B, C, or D.")
            user_answer = input("Enter your answer (A/B/C/D): ").strip().upper()

        if check_answer(user_answer, question["answer"]):
            print("Correct!")
            score += 1
        else:
            print(f"Wrong. The correct answer is {question['answer']}.")

    display_score(score, len(quiz))

# Run the game
if __name__ == "__main__":
    main()
