- 👋 Hi, I’m @MattPY1 or Matt
- 💙👍 I’m interested in programming and Basketball
- 🪬I’m currently learning 
- 📈 I want to collaborate with others on web projects
class Calculator:
    def __init__(self):
        self.result = None
        self.operand = None
        self.operator = None
        self.wait_for_number = True

    def process_input(self, item):
        if self.wait_for_number:
            try:
                self.operand = float(item)
                self.wait_for_number = False
            except ValueError:
                return f"'{item}' is not a number. Try again."
        else:
            if item in ('+', '-', '*', '/'):
                if self.operator is not None:
                    return f"You entered operator '{item}' twice in a row. Try again."
                self.operator = item
                self.wait_for_number = True
            else:
                return f"'{item}' is not '+', '-', '*', or '/'. Try again."

            if self.operator is not None and self.operand is not None:
                if self.operator == '+':
                    self.result = self.result + self.operand if self.result is not None else self.operand
                elif self.operator == '-':
                    self.result = self.result - self.operand if self.result is not None else -self.operand
                elif self.operator == '*':
                    self.result = self.result * self.operand if self.result is not None else 0
                elif self.operator == '/':
                    if self.operand != 0:
                        self.result = self.result / self.operand if self.result is not None else 0
                    else:
                        return "Division by zero. Try again."

                self.operator = None

        return None

    def get_result(self):
        return f"Result: {self.result}"


# Приклад використання:

calculator = Calculator()
test_sequence = ["10", "+", "5", "6", "/", "3", "-", "a", "2", "*", "6", "="]

for item in test_sequence:
    result = calculator.process_input(item)
    if result is not None:
        print(result)

print(calculator.get_result())