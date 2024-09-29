class GradeManager:
    def __init__(self):
        self.grades = {}
        self.grade_scale = {
            "A": 4.0,
            "B": 3.0,
            "C": 2.0,
            "D": 1.0,
            "F": 0.0
        }
    def input_grades(self):
        print("Enter grades for different subjects or assignments (Enter 'done' to stop):")
        while True:
            subject = input("Enter subject or assignment name: ")
            if subject.lower() == "done":
                break
            try:
                grade = float(input(f"Enter grade for {subject} (0-100): "))
                if 0 <= grade <= 100:
                    self.grades[subject] = grade
                else:
                    print("Please enter a grade between 0 and 100.")
            except ValueError:
                print("Invalid input. Please enter a numerical value for the grade.")
    def calculate_average(self):
        if not self.grades:
            return 0
        total = sum(self.grades.values())
        return total / len(self.grades)
    def get_letter_grade(self, grade):
        if grade >= 90:
            return "A"
        elif grade >= 80:
            return "B"
        elif grade >= 70:
            return "C"
        elif grade >= 60:
            return "D"
        else:
            return "F"
    def calculate_gpa(self, letter_grades):
        gpa_points = [self.grade_scale[letter] for letter in letter_grades]
        return sum(gpa_points) / len(gpa_points) if gpa_points else 0
    def display_results(self):
        if not self.grades:
            print("No grades entered.")
            return
        print("\nStudent Grades:")
        letter_grades = []
        for subject, grade in self.grades.items():
            letter_grade = self.get_letter_grade(grade)
            letter_grades.append(letter_grade)
            print(f"{subject}: {grade} -> {letter_grade}")
        average_grade = self.calculate_average()
        overall_letter_grade = self.get_letter_grade(average_grade)
        gpa = self.calculate_gpa(letter_grades)
        print(f"\nAverage Grade: {average_grade:.2f}")
        print(f"Overall Letter Grade: {overall_letter_grade}")
        print(f"GPA: {gpa:.2f}")
grade_manager = GradeManager()
grade_manager.input_grades()
grade_manager.display_results()
