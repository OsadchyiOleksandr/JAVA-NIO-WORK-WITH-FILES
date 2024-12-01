За допомогою можливостей File NIO API необхідно створити файл та прочитати його.

Результат виведення має бути

Created files\\myfile.txt
Recorded in files\\myfile.txt
CONTENT: Super information.


(1) Cтворіть проект Text-Handler на локальній машині через IntelliJ IDEA (IDE). В кореневій папці проекту
створіть внутрішню директорію files , яка буде використовуватись для роботи з файлом.

Рекондація як створити цю директорію: Правий клік мишею на кореневу директорію проекту > New > Directory >
Лівий клік мишею на Directory > У віконці ввести files > Натиснути Enter

(2) Структура проекту має бути такою:

(3) Функціонал класу Main

package app;

import java.nio.file.Paths;

public class Main {

    private static final String BASE_PATH = "files/";

    public static void main(String[] args) {
        FileHandler handler = new FileHandler();
        String newFileName = "myfile";
        String content = "Super information.";
        String path = BASE_PATH + newFileName + ".txt";
        // Виклики методів маніпуляції з файлом
        getOutput(handler.createFile(path));
        getOutput(handler.writeToFile(Paths.get(path), content));
        getOutput("CONTENT: " + handler.readFromFile(path));
    }

    private static void getOutput(String output) {
        System.out.println(output);
    }
}


(4) Доопрацюйте функціонал класу FileHandler

package app;

import java.io.IOException;
import java.nio.file.FileAlreadyExistsException;
import java.nio.file.Files;
import java.nio.file.Path;

public class FileHandler {

    public String createFile() {
        Path newFile;
        try {
            newFile = Files(Path.of(path));
        } catch (FileAlreadyExistsException e) {
            return "File already exists!";
        } catch (IOException e) {
            return "Something wrong " +;
        }
        return "Created " + newFile;
    }

    public String writeToFile(Path  content) {
        try {
            Files.writeString(path, content);
        } catch (IOException e) {
            return e.getMessage();
        }
        return "Recorded in " + path;
    }

    public String readFromFile(String path) {
        try {
            return readString(Path(path));
        } catch (IOException e) {
            return "Something wrong " + e.getMessage();
        }
    }
}

(5) Залийте виконаний проект на свій GitHub репозиторій, посилання на який зазначте в LMS.
