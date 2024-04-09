#include <iostream>
#include <vector>
#include <string>

// A simple task structure
struct Task {
  std::string description;
  bool completed;
};

int main() {
  std::vector<Task> tasks;

  int choice;

  do {
    // Display menu
    std::cout << "\nTo-Do List Application\n";
    std::cout << "1. Add Task\n";
    std::cout << "2. Mark Task Completed\n";
    std::cout << "3. View All Tasks\n";
    std::cout << "4. Exit\n";
    std::cout << "Enter your choice: ";
    std::cin >> choice;

    switch (choice) {
      case 1: {
        // Add task
        std::string description;
        std::cout << "Enter task description: ";
        std::getline(std::cin, description); // Get entire line with spaces
        tasks.push_back({description, false});
        std::cout << "Task added successfully!\n";
        break;
      }
      case 2: {
        // Mark task completed
        if (tasks.empty()) {
          std::cout << "No tasks to mark completed.\n";
          break;
        }

        int taskNumber;
        std::cout << "Enter the number of the task to mark completed (1-" << tasks.size() << "): ";
        std::cin >> taskNumber;

        if (taskNumber > 0 && taskNumber <= tasks.size()) {
          tasks[taskNumber - 1].completed = true;
          std::cout << "Task marked completed.\n";
        } else {
          std::cout << "Invalid task number.\n";
        }
        break;
      }
      case 3: {
        // View all tasks
        if (tasks.empty()) {
          std::cout << "No tasks found.\n";
          break;
        }

        std::cout << "\nYour Tasks:\n";
        int i = 1;
        for (const Task& task : tasks) {
          std::cout << i << ". " << task.description;
          if (task.completed) {
            std::cout << " (Completed)";
          }
          std::cout << std::endl;
          i++;
        }
        break;
      }
      case 4:
        std::cout << "Exiting...\n";
        break;
      default:
        std::cout << "Invalid choice.\n";
    }

  } while (choice != 4);

  return 0;
}



