# To_Do_List_Manager_project

# File name where tasks will be stored

file_name = "tasks.txt"

# Function to show all tasks
def show_tasks():
    try:
        file = open(file_name, "r")
        tasks = file.readlines()
        file.close()

        if len(tasks) == 0:
            print("No tasks found.")
        else:
            print("\nYour Tasks:")
            for i in range(len(tasks)):
                print(i + 1, tasks[i].strip())
    except:
        print("No tasks file found.")

# Function to add a task
def add_task():
    task = input("Enter new task: ")

    file = open(file_name, "a")  # append mode
    file.write(task + " | Pending\n")
    file.close()

    print("Task added successfully!")

# Function to mark task as done
def mark_done():
    try:
        file = open(file_name, "r")
        tasks = file.readlines()
        file.close()

        show_tasks()
        num = int(input("Enter task number to mark as done: "))

        if num <= len(tasks):
            tasks[num - 1] = tasks[num - 1].replace("Pending", "Done")

            file = open(file_name, "w")
            file.writelines(tasks)
            file.close()

            print("Task marked as done!")
        else:
            print("Invalid task number.")

    except:
        print("Error occurred.")

# Function to show only pending tasks
def show_pending():
    try:
        file = open(file_name, "r")
        tasks = file.readlines()
        file.close()

        print("\nPending Tasks:")
        for i in range(len(tasks)):
            if "Pending" in tasks[i]:
                print(i + 1, tasks[i].strip())

    except:
        print("No tasks found.")

# Main program loop
while True:
    print("\n--- TO-DO LIST MENU ---")
    print("1. View all tasks")
    print("2. Add new task")
    print("3. Mark task as done")
    print("4. View pending tasks")
    print("5. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        show_tasks()
    elif choice == "2":
        add_task()
    elif choice == "3":
        mark_done()
    elif choice == "4":
        show_pending()
    elif choice == "5":
        print("Goodbye!")
        break
    else:
        print("Invalid choice. Try again.")
