import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;
public class Main {
    public static void generateBinaryStrings(String str, int index, List<String> result) {
        if (index == str.length()) {
            result.add(str);
            return;
        }
        if (str.charAt(index) == '?') {
            generateBinaryStrings(str.substring(0, index) + '0' + str.substring(index + 1), index + 1, result);
            generateBinaryStrings(str.substring(0, index) + '1' + str.substring(index + 1), index + 1, result);
        } else {
            generateBinaryStrings(str, index + 1, result);
        }
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int T = scanner.nextInt();
        scanner.nextLine(); 
        for (int t = 0; t < T; t++) {
            String S = scanner.nextLine();
            List<String> result = new ArrayList<>();
            generateBinaryStrings(S, 0, result);
            for (String binaryString : result) {
                System.out.print(binaryString + " ");
            }
            System.out.println();
        }
    }
}

