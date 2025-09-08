tasks = []

def add_task():
    """Добавляет новую задачу"""
    task_name = input("Введите название задачи: ")
    tasks.append({"name": task_name, "completed": False})
    print(f"Задача '{task_name}' успешно добавлена в список.")

def show_tasks():
    """Выводит список задач с состоянием выполнения"""
    if not tasks:
        print("Список задач пуст.")
    else:
        print("Список задач:")
        for i, task in enumerate(tasks):
            status = "✔️ Выполнена" if task["completed"] else "🔴 Не выполнена"
            print(f"{i + 1}. {task['name']} | {status}")

def mark_task_completed():
    """Отмечает задачу как выполненную"""
    show_tasks()
    try:
        index = int(input("Введите номер задачи для пометки как выполненной: ")) - 1
        if 0 <= index < len(tasks):
            tasks[index]["completed"] = True
            print("Задача отмечена как выполненная.")
        else:
            print("Неверный номер задачи.")
    except ValueError:
        print("Ошибка: введен неправильный номер задачи.")

def delete_task():
    """Удаляет задачу из списка"""
    show_tasks()
    try:
        index = int(input("Введите номер задачи для удаления: ")) - 1
        if 0 <= index < len(tasks):
            deleted_task = tasks.pop(index)["name"]
            print(f"Задача '{deleted_task}' удалена из списка.")
        else:
            print("Неверный номер задачи.")
    except ValueError:
        print("Ошибка: введен неправильный номер задачи.")

def main():
    while True:
        print("\nМенеджер задач:")
        print("1. Добавить новую задачу")
        print("2. Просмотреть список задач")
        print("3. Отметить задачу как выполненную")
        print("4. Удалить задачу")
        print("5. Выход")
        
        choice = input("Выберите пункт меню (1-5): ")
        
        if choice == "1":
            add_task()
        elif choice == "2":
            show_tasks()
        elif choice == "3":
            mark_task_completed()
        elif choice == "4":
            delete_task()
        elif choice == "5":
            print("До свидания!")
            break
        else:
            print("Неправильный выбор. Попробуйте снова.")

if __name__ == "__main__":
    main()
