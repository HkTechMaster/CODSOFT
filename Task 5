import pickle

class Task:
    def __init__(self, description, completed=False):
        self.description = description
        self.completed = completed

    def __str__(self):
        return f"{'[x]' if self.completed else '[ ]'} {self.description}"

# Global list to store tasks
tasks = []

def add_task(description):
    if description:
        tasks.append(Task(description))
        save_tasks()
        print("Task added successfully.")
    else:
        print("Task description cannot be empty")

def update_task(index, new_description):
    if 0 <= index < len(tasks):
        tasks[index].description = new_description
        save_tasks()
        print("Task updated successfully.")
    else:
        print("Task not found!")

def delete_task(index):
    if 0 <= index < len(tasks):
        tasks.pop(index)
        save_tasks()
        print("Task deleted successfully.")
    else:
        print("Task not found!")

def view_tasks():
    if not tasks:
        print("No tasks available.")
    else:
        for i, task in enumerate(tasks):
            print(f"{i + 1}. {task}")

def save_tasks():
    with open("tasks.pkl", "wb") as file:
        pickle.dump(tasks, file)

def load_tasks():
    global tasks
    try:
        with open("tasks.pkl", "rb") as file:
            tasks = pickle.load(file)
    except FileNotFoundError:
        tasks = []

def main():
    load_tasks()
    while True:
        command = input("Enter command (add/view/update/delete/exit): ").strip().lower()
        if command == "add":
            description = input("Enter task description: ")
            add_task(description)
        elif command == "view":
            view_tasks()
        elif command == "update":
            try:
                index = int(input("Enter task number to update: ")) - 1
                new_description = input("Enter new description: ")
                update_task(index, new_description)
            except ValueError:
                print("Invalid input. Please enter a number.")
        elif command == "delete":
            try:
                index = int(input("Enter task number to delete: ")) - 1
                delete_task(index)
            except ValueError:
                print("Invalid input. Please enter a number.")
        elif command == "exit":
            break
        else:
            print("Unknown command")

if __name__ == "__main__":
    main()
