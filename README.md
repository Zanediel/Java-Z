# Java-Z
import java.util.ArrayList;
import java.util.Scanner;

class User {
    String username;
    String password;

    User(String username, String password) {
        this.username = username;
        this.password = password;
    }
}

class GradingSystem {
    private ArrayList<User> users;
    private String[] students = {"Aldrin", "Kisha", "Malong", "Jefferson", "Theressa"};
    private String[] subjects = {"Science", "Math", "English"};
    private int[][][] scores = new int[5][3][3];

    public GradingSystem() {
        users = new ArrayList<>();
        users.add(new User("Aldrin", "pass123"));
        users.add(new User("Kisha", "kisha321"));
        users.add(new User("Malong", "malong444"));
        users.add(new User("Jefferson", "jeff123"));
        users.add(new User("Theressa", "theressa567"));
    }

    public boolean register(String username, String password) {
        for (User user : users) {
            if (user.username.equals(username)) {
                return false;
            }
        }
        users.add(new User(username, password));
        return true;
    }

    public boolean login(String username, String password) {
        for (User user : users) {
            if (user.username.equals(username) && user.password.equals(password)) {
                return true;
            }
        }
        return false;
    }

    public String[] getStudents() {
        return students;
    }

    public String[] getSubjects() {
        return subjects;
    }

    public void inputScores(Scanner sc) {
        boolean[] completed = new boolean[students.length];

        while (true) {
            System.out.println("Choose a student to assign scores:");
            for (int i = 0; i < students.length; i++) {
                System.out.println((i + 1) + ". " + students[i] + " - " + 
                                  String.join(" - ", subjects) + 
                                  (completed[i] ? " > Completed" : ""));
            }
            System.out.println("6. Exit");

            int studentChoice = -1;
            while (true) {
                System.out.print("Enter your choice: ");
                if (sc.hasNextInt()) {
                    studentChoice = sc.nextInt() - 1;
                    sc.nextLine();
                    if (studentChoice >= 0 && studentChoice <= 5) {
                        break;
                    }
                } else {
                    sc.next();
                }
                System.out.println("Invalid input. Please enter a number between 1 and 6.");
            }

            if (studentChoice == 5) break;

            if (completed[studentChoice]) {
                System.out.println("Re-assign the recently assigned score? 1.Yes 2.No");
                int reassignChoice = -1;
                while (true) {
                    System.out.print("Enter your choice: ");
                    if (sc.hasNextInt()) {
                        reassignChoice = sc.nextInt();
                        sc.nextLine();
                        if (reassignChoice == 1 || reassignChoice == 2) {
                            break;
                        }
                    } else {
                        sc.next();
                    }
                    System.out.println("Invalid input. Please enter 1 for Yes or 2 for No.");
                }
                if (reassignChoice == 2) {
                    continue;
                }
            }

            for (int subj = 0; subj < subjects.length; subj++) {
                System.out.println("Assigning Score for " + subjects[subj] + ":");
                int quiz, task, exam;

                while (true) {
                    System.out.print("Quiz: ");
                    String input = sc.nextLine();
                    try {
                        quiz = Integer.parseInt(input);
                        if (input.startsWith("-") || quiz < 0 || quiz > 30) {
                            continue;
                        }
                        break;
                    } catch (NumberFormatException e) {
                        // Invalid input, continue loop
                    }
                }

                while (true) {
                    System.out.print("Performance Task: ");
                    String input = sc.nextLine();
                    try {
                        task = Integer.parseInt(input);
                        if (input.startsWith("-") || task < 0 || task > 50) {
                            continue;
                        }
                        break;
                    } catch (NumberFormatException e) {
                        // Invalid input, continue loop
                    }
                }

                while (true) {
                    System.out.print("Exam: ");
                    String input = sc.nextLine();
                    try {
                        exam = Integer.parseInt(input);
                        if (input.startsWith("-") || ex
