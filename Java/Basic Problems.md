### 주기율표에서 문자열 찾기

```java
public class Main {
    public static void main(String[] args) {
       String dna = "GATCCGCCCGCCTCGGCCTCCCAAAGTGCTGGGATTACAGGTGTGAGCCA"
                + "CCACGCCCGGCTAATTTTTATTTATTTATTTAAAGACAGAGTCTCACTCT"
                + "GTCACTCAGGCTAGAGTGCAGTGGCACCATCTCAGCTCACTGCAGCCTTG"
                + "ACCTCCCTGGGCTCCGGTGATTTCACCCTCCCAAGTAGCTAGGACTACAG"
                + "GCACATGCCACGACACCCAGCTAATTTTTTATTTTCTGTGAAGTCAAGGT"
                + "CTTGCTACGTTGCCCATGCTGGTATCAAACCCCTGGGCTCAATCAATCCT"
                + "TCCACCTCAGCCTCCCCAAGTATTGGGGTTACAGGCATGAGCTACCACAC"
                + "TCAGCCCTAGCCTACTTGAAACGTGTTCAGAGCATTTAAGTTACCCTACA"
                + "GTTGGGCAAAGTCATCTAACACAAAGCCCTTTTTATAGTAATAAAATGTT"
                + "GTATATCTCATGTGATTTATTGAATATTGTTACTGAAAGTGAGAAACAGC"
                + "ATGGTTGCATGAAAGGAGGCACAGTCGAGCCAGGCACAGCCTGGGCGCAG"
                + "AGCGAGACTCAAAAAAAGAAAAGGCCAGGCGCACTGGCTCACGCCTGTAA"
                + "TCCCAGCATTTCGGGAGGCTGAGGCGGGTGGATCACCTGAGGTCAGGAGT"
                + "TCAAGACCAGCCTAGCCAACATGGTGAAACCCCGTCTCTACTAAAATACA"
                + "AAAATTAACCGGGCGTGATGGCAGGTGCCTGTAATCCCAGCTACTTGGGA"
                + "GGCTGAGGCAGGAGAATCGCTTGAACCAGGAGGCGGAGGTTGCAGGGAGC"
                + "CAAGATGGCGCCACTGCACTCCAGCCTGGGCGATAGAGTGAGACTCCGTC"
                + "TCAGAAAAAAAAGAAAAGAAACGAGGCACAGTCGCATGCACATGTAGTCC"
                + "CAGTTACTTGAGAGGCTAAGGCAGGAGGATCTCTTGAGCCCAAGAGTTTG"
                + "AGTCCAGCCTGAACAACATAGCAAGACATCATCTCTAAAATTTAAAAAAG"
                + "GGCCGGGCACAGTGGCTCACACCTGTAATCCCAGCACTTTGGGAGGTGGA"
                + "GGTGGGTAGATCACCTGACGTCAGGAGTTGGAAACCAGCCTGGCTAACAT";
        char[] charArray = dna.toCharArray();

        int numOne = 0;
        int numTwo = 0;
        int numThree = 0;

        for(int i = 0; i < charArray.length - 3; i++){
            char [] word = new char[4];
            word[0] = charArray[i];
            word[1] = charArray[i+1];
            word[2] = charArray[i+2];
            word[3] = charArray[i+3];
            String realWord = new String(word);

            if(realWord.equals("TAGG")){
                numOne += 1;
            }
            if(realWord.equals("CCAG")){
                numTwo += 1;
            }
            if(realWord.equals("AGCC")){
                numThree += 1;
            }
        }
        System.out.println("TAGG: " + numOne);
        System.out.println("CCAG: " + numTwo);
        System.out.println("AGCC: " + numThree);
    }
}
```

### 두 원소의 차 중 최댓값 구하기

GreastDifferenceFinder.java

```java
public class GreatestDifferenceFinder {
    int greatestDifference(int[] intArray) {
        // 코드를 입력하세요.
        if (intArray.length < 2){
            return 0;
        }
        int max = intArray[0];
        int min = intArray[0];
        for(int i = 0; i < intArray.length; i++){
            if(max < intArray[i]){
                max = intArray[i];
            }
            if(min > intArray[i]){
                min = intArray[i];
            }

        }
            return max - min;
    }
}
```

Main.java

```java
public class Main {
    public static void main(String[] args) {
        GreatestDifferenceFinder finder = new GreatestDifferenceFinder();

        // 테스트 1
        int[] testArray1 = {-2, 7, 3};
        System.out.println(finder.greatestDifference(testArray1));

        // 테스트 2
        int[] testArray2 = {8, 3, 14, 1};
        System.out.println(finder.greatestDifference(testArray2));

        // 테스트 3
        int[] testArray3 = {4, 2, 3, 1};
        System.out.println(finder.greatestDifference(testArray3));

        // 테스트 4
        int[] testArray4 = {};
        System.out.println(finder.greatestDifference(testArray4));

        // 테스트 5
        int[] testArray5 = {1, 2, -3, 4, 5};
        System.out.println(finder.greatestDifference(testArray5));

        // 테스트 6
        int[] testArray6 = {1};
        System.out.println(finder.greatestDifference(testArray6));
    }
}
```

### 삼각형 그리기

ShapePrinter.java

```java
public class ShapePrinter {
    public void printTriangle(int height) {
        // 코드를 입력하세요.
        for(int i = 1; i <= height; i++){
            for(int j = 1; j <= i; j++){
            System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

Main.java

```java
public class Main {
    public static void main(String[] args) {
        ShapePrinter printer = new ShapePrinter();

        // 테스트
        printer.printTriangle(3);
        System.out.println("----------");
        printer.printTriangle(5);
        System.out.println("----------");
        printer.printTriangle(10);
    }
}
```

### 피라미드 그리기

ShapePrinter.java

```java
public class ShapePrinter {
    public void printPyramid(int height) {
        // 코드를 입력하세요.
        for(int i = 1; i <= height; i++){
            for(int j = 1; j <= 2 * height - 1; j++){
                if ((height - i < j) && (height + i > j)){
                    System.out.print("*");
                }else {
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
    }
}
```

Main.java

```java
public class Main {
    public static void main(String[] args) {
        ShapePrinter printer = new ShapePrinter();

        // 테스트
        printer.printPyramid(3);
        System.out.println("----------");
        printer.printPyramid(5);
        System.out.println("----------");
        printer.printPyramid(10);
    }
}
```

### 플로이드의 삼각형

ShapePrinter.java

```java
public class ShapePrinter {
    public void printFloydsPyramid(int height) {
        // 코드를 입력하세요.
        int max = height * (height + 1) / 2;
        String maxString = Integer.toString(max);
        int maxStringLength = maxString.length();
        int sum = 0;
        for (int i = 1; i <= height; i++){
            for(int j = 1; j <= i; j++){
                sum ++;
                String sumString = Integer.toString(sum);
                int sumStringLength = sumString.length();
                for(int k = 0; k < maxStringLength - sumStringLength; k++){
                    System.out.print(" ");
                }
                System.out.print(sum);
                System.out.print(" ");
            }
            System.out.println();
        }
    }
}
```

Main.java

```java
public class Main {
    public static void main(String[] args) {
        ShapePrinter printer = new ShapePrinter();

        // 테스트
        printer.printFloydsPyramid(3);
        System.out.println("----------");
        printer.printFloydsPyramid(5);
        System.out.println("----------");
        printer.printFloydsPyramid(15);
    }
}
```

### 소개 프로그램

Main.java

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args){
      while(true){
          System.out.println("(I)ntro (C)ourse (E)xit");
          Scanner scanner = new Scanner(System.in);
          String menu = scanner.next();

          if (menu.equals("e") || menu.equals("E") ){
              System.out.println("안녕히 가세요.");
              break;
          }
          if(menu.equals("i") || menu.equals("I")){
              System.out.println("안녕하세요! 우리는 코드잇입니다.");
              System.out.println("함께 공부합시다!");
              continue;
          }
          if(menu.equals("c") || menu.equals("C")){
              while(true){
                  System.out.println("코드잇 수업을 소개합니다.");
                  System.out.println("(P)ython (J)ava (i)OS (B)ack");
                  String language = scanner.next();
                  if(language.equals("p") || language.equals("P")){
                      System.out.println("Python 언어를 통해 컴퓨터 사이언스의 기초를 배웁니다.");
                      System.out.println("강사: 강영훈");
                      System.out.println("추천 선수과목: 없음");
                      continue;
                  }
                  if(language.equals("j")|| language.equals("J")){
                      System.out.println("Java의 기본 문법과 객체지향적 프로그래밍을 배웁니다.");
                      System.out.println("강사: 김신의");
                      System.out.println("추천 선수과목: Python");
                      continue;
                  }
                  if(language.equals("i") || language.equals("I")){
                      System.out.println("최신 Swift 언어를 통해 iOS 개발을 시작할 수 있습니다.");
                      System.out.println("강사: 성태호");
                      System.out.println("추천 선수과목: Python, Java");
                      continue;
                  }
                  if(language.equals("b") || language.equals("B")){
                      break;
                  }
              }
          }
      }
    }
}
```

