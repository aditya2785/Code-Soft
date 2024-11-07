# Code-Soft
This is Code Soft Internship tasks


# To-Do List Application

class ToDoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        """Add a task to the list."""
        self.tasks.append({"task": task, "done": False})
        print(f"Task '{task}' added.")

    def view_tasks(self):
        """Display all tasks."""
        if not self.tasks:
            print("Your To-Do list is empty.")
        else:
            print("\nYour To-Do List:")
            for index, task in enumerate(self.tasks, start=1):
                status = "Done" if task["done"] else "Not done"
                print(f"{index}. {task['task']} [{status}]")

    def mark_done(self, task_number):
        """Mark a task as done."""
        try:
            task = self.tasks[task_number - 1]
            task["done"] = True
            print(f"Task '{task['task']}' marked as done.")
        except IndexError:
            print("Invalid task number.")

    def delete_task(self, task_number):
        """Delete a task from the list."""
        try:
            task = self.tasks.pop(task_number - 1)
            print(f"Task '{task['task']}' deleted.")
        except IndexError:
            print("Invalid task number.")

def display_menu():
    print("\nTo-Do List Application")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Mark Task as Done")
    print("4. Delete Task")
    print("5. Exit")

def main():
    todo_list = ToDoList()

    while True:
        display_menu()
        choice = input("Choose an option (1-5): ")

        if choice == '1':
            task = input("Enter the task: ")
            todo_list.add_task(task)
        elif choice == '2':
            todo_list.view_tasks()
        elif choice == '3':
            todo_list.view_tasks()
            try:
                task_number = int(input("Enter the task number to mark as done: "))
                todo_list.mark_done(task_number)
            except ValueError:
                print("Please enter a valid number.")
        elif choice == '4':
            todo_list.view_tasks()
            try:
                task_number = int(input("Enter the task number to delete: "))
                todo_list.delete_task(task_number)
            except ValueError:
                print("Please enter a valid number.")
        elif choice == '5':
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
