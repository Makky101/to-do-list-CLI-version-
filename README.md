# to-do-list-CLI-version-
# A simple to-do list app
tasks = []

while True:
    print("Welcome to the to-do list app")
    print("1. Add a task")
    print("2. View tasks")
    print("3. Remove a task")
    print("4. Exit")

    choice = input("Enter your choice: ")
    try:
        choice = int(choice)
        if not (1 <= choice <= 4):
            print("Pick a number between 1 and 4")
            continue
    except ValueError:
        print("Invalid choice. Please enter a valid number.")
        continue

    if choice == 1:
        task = input("Enter a task: ")
        tasks.append(task)
        print("Your task has been added successfully")
    elif choice == 2:
        if not tasks:
            print("No tasks found")
        else:
            print("Your tasks:")
            for i, task in enumerate(tasks, 1):
                print(f"{i}. {task}")
    elif choice == 3:
        if not tasks:
            print("No tasks found")
        elif input("Do you want to clear all tasks? (y/n): ").lower() == "y":
            tasks.clear()
            print("All tasks have been cleared")
        else:
            try:
                task_number = int(input("Enter the number of the task to remove: "))
                if 1 <= task_number <= len(tasks):
                    removed_task = tasks.pop(task_number - 1)
                    print(f"Task '{removed_task}' has been removed")
                else:
                    print("Invalid task number")
            except ValueError:
                print("Please enter a valid number.")
    elif choice == 4:
        print("Exiting the program")
        break
