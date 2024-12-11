##############Task-1 to-do-list
import os

def show_tasks(tasks):
    if not tasks:
        print("No tasks found!")
    else:
        print("\nYour Tasks:")
        for index, task in enumerate(tasks, 1):
            print(f"{index}. {task}")

def add_task(tasks):
    task = input("Enter the task: ")
    tasks.append(task)
    print(f"Task '{task}' added!")

def remove_task(tasks):
    show_tasks(tasks)
    try:
        task_num = int(input("Enter the task number to remove: "))
        if 0 < task_num <= len(tasks):
            removed_task = tasks.pop(task_num - 1)
            print(f"Task '{removed_task}' removed!")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Invalid input. Please enter a number.")

def update_task(tasks):
    show_tasks(tasks)
    try:
        task_num = int(input("Enter the task number to update: "))
        if 0 < task_num <= len(tasks):
            new_task = input("Enter the new task: ")
            tasks[task_num - 1] = new_task
            print(f"Task updated to '{new_task}'")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Invalid input. Please enter a number.")

def save_tasks(tasks):
    with open("tasks.txt", "w") as file:
        for task in tasks:
            file.write(task + "\n")
    print("Tasks saved!")

def load_tasks():
    if os.path.exists("tasks.txt"):
        with open("tasks.txt", "r") as file:
            return [task.strip() for task in file.readlines()]
    return []

def main():
    tasks = load_tasks()
    
    while True:
        print("\nTo-Do List Menu:")
        print("1. Show tasks")
        print("2. Add task")
        print("3. Remove task")
        print("4. Update task")
        print("5. Save tasks")
        print("6. Exit")
        
        choice = input("Choose an option: ")
        
        if choice == "1":
            show_tasks(tasks)
        elif choice == "2":
            add_task(tasks)
        elif choice == "3":
            remove_task(tasks)
        elif choice == "4":
            update_task(tasks)
        elif choice == "5":
            save_tasks(tasks)
        elif choice == "6":
            save_tasks(tasks)
            print("Goodbye!")
            break
        else:
            print("Invalid option, please try again.")

if __name__ == "__main__":
    main()
