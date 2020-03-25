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

