import java.io.*;
import java.util.ArrayList;
import java.util.Scanner;

public class Main {


    public static void main(String[] args) {

        try {

            long TimeZero = System.currentTimeMillis();
            FileReader fr = new FileReader("word.txt");
            Scanner scan = new Scanner(fr);
            ArrayList<String> library = new ArrayList<>();
            while (scan.hasNextLine()) {
                library.add(scan.nextLine().toUpperCase());
            }
            System.out.println(library.size() + " слов");
            System.out.println(System.currentTimeMillis() - TimeZero + " милисекунд загрузка словаря");
            menu(library);
        } catch (Exception ex) {
            ex.printStackTrace();
        }
    }

    static void menu(ArrayList<String> library) {
        System.out.println("\n[N]ew game or [E]xit");
        switch (readerKeyboard()) {
            case 'N':
                Game(library);
                break;

            case 'E':
                exit();
                break;

            default:
                menu(library);
                break;
        }
    }

    static char readerKeyboard() {

        Scanner sc = new Scanner(System.in);
        String a = sc.nextLine();
        if (a.isEmpty()) {
            System.out.println("Вы ничего не ввели \n Пожалуйста, введите команду");

            return readerKeyboard();
        } else {
            a = a.toUpperCase();
            char b[] = a.toCharArray();
            return b[0];
        }


    }

    static void Game(ArrayList<String> library) {
        int numberRandomWorld = (int) (Math.random() * library.size());
        String answerWord = library.get(numberRandomWorld);
        int errorCount = 0;
        ArrayList<Character> usedLetters = new ArrayList<Character>();
        String foundWord[] = new String[answerWord.length()];
        for (int i = 0; i < foundWord.length; i++) {
            foundWord[i] = "*";
            System.out.print(foundWord[i]);
        }


        char secretWord[] = answerWord.toCharArray();
        System.out.println();
        int foundSymbol = 0;
        letterCheck(answerWord, secretWord, foundWord, errorCount, usedLetters, foundSymbol);
    }


    static public void usedLetters(ArrayList<Character> usedLetters) {
        System.out.print("\n Вы использовали буквы:");

        for (int i = 0; i < usedLetters.size(); i++) {
            System.out.print(usedLetters.get(i)+" ");
        }
    }

    static void letterCheck(String answerWord, char[] secretWord, String[] foundWord, int errorCount, ArrayList<Character> usedLetters, int foundSymbol) {
        if (usedLetters.size() > 0) {
            usedLetters(usedLetters);
        }
        System.out.print("\nВвведите букву \n");
        char letter = readerKeyboard();

        if (letter == 0) {
            System.out.println("вы ничего не ввели");
            letterCheck(answerWord, secretWord, foundWord, errorCount, usedLetters, foundSymbol);
        }

        if (letter <= 'Z') {
            System.out.println("не корректный символ, попробуйте снова!");
            letterCheck(answerWord, secretWord, foundWord, errorCount, usedLetters, foundSymbol);
        }


        for (int count = 0; count < usedLetters.size(); count++) {
            if (letter == usedLetters.get(count)) {
                System.out.println("Вы уже вводили эту букву");
                letterCheck(answerWord, secretWord, foundWord, errorCount, usedLetters, foundSymbol);
            }
        }

        usedLetters.add(letter);

        int enumeration = 0;
        for (int count = 0; count < answerWord.length(); count++) { // Проверяем совпадает ли введённая буква с буквами из загаданного слова
            if (letter == secretWord[count]) {
                foundWord[count] = String.valueOf(letter);
                secretWord[count] = 0;
                foundSymbol++;
            } else {
                enumeration++;
                // если буква не совпала с № буквой добавляем счётчик "несовпадений"
            }
            System.out.print(foundWord[count]);
        }


        if (enumeration == secretWord.length) {
            errorCount++;
            System.out.println("\n Упс, такой бувы нет!");
// если буква прошла полный цикл и количество "несовпадений" равно длине слова - добавляем счётчик ошибок

            String errorDeclination = null;
            switch (6 - errorCount) {
                case 5:
                    errorDeclination = "ошибок";
                    break;
                case 4, 3, 2:
                    errorDeclination = " ошибки";
                    break;
                case 1:
                    errorDeclination = " ошибка";
                    printErrors(6 - errorCount);
                    break;
            }
            System.out.println("\n У вас осталось " + (6 - errorCount) + " "+errorDeclination);
            printErrors(6 - errorCount);
        }
        System.out.println();

        if (errorCount == 6) {
            System.out.println("Вы проиграли");// когда количество ошибок достигает 6 игра окончена

            System.out.print("Загаданное слово было " + answerWord + "\n");

        }
        letterCheck(answerWord, secretWord, foundWord, errorCount, usedLetters, foundSymbol);
    }


    static void printErrors(int errors) {
        switch (errors) {
            case 5:
                System.out.println
                        ("\n|   " +
                                "\n|   " +
                                "\n|   " +
                                "\n|   " +
                                "\n|   " +
                                "\n|    ");
                break;
            case 4:
                System.out.println
                        ("\n ___" +
                                "\n|/  | " +
                                "\n|   " +
                                "\n|   " +
                                "\n|   " +
                                "\n|   " +
                                "\n|    ");
                break;
            case 3:
                System.out.println
                        ("\n ___" +
                                "\n|/  | " +
                                "\n|   *" +
                                "\n|   " +
                                "\n|   " +
                                "\n|   " +
                                "\n|    ");
                break;
            case 2:
                System.out.println
                        ("\n ___" +
                                "\n|/  | " +
                                "\n|   *" +
                                "\n|  /|| " +
                                "\n|   " +
                                "\n|   " +
                                "\n|    ");
                break;
            case 1:
                System.out.println
                        ("\n ___" +
                                "\n|/  | " +
                                "\n|   *" +
                                "\n|  /|| " +
                                "\n|   |" +
                                "\n|   " +
                                "\n|    ");
                break;
            case 0:
                System.out.println
                        ("\n ___" +
                                "\n|/  | " +
                                "\n|   *" +
                                "\n|  /|| " +
                                "\n|   |" +
                                "\n|   ||" +
                                "\n|    ");
                break;
            default:
                break;

        }


    }

    static void exit() {
    }
}
