def calculator(num1,num2,operation):
  if operation == '+':
    return num1 + num2
  elif operation == '-':
    return num1 - num2
  elif operation == '*':
    return num1 * num2
  elif operation == '/':
    return num1 / num2
  else:
    print("An error occured")
num1=float(input("Enter first number: "))
num2=float(input("Enter second number: "))
operation=input("Enter operation(+,-,*,/): ")
print(calculator(num1,num2,operation))
