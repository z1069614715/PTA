# PTA
天梯练习

[个位数统计](https://pintia.cn/problem-sets/994805046380707840/problems/994805143738892288)

    import java.util.Scanner;

    public class L1_003 {
        public static void main(String[] args) {
            Scanner input = new Scanner(System.in);
            String str = input.next();
            int arr[] = new int[10];
            for (int i = 0; i < str.length(); i++) {
                arr[Integer.parseInt(Character.toString(str.charAt(i)))] += 1;
            }
            for (int i = 0; i < arr.length; i++) {
                if (arr[i] != 0){
                    System.out.println(i + ":" + arr[i]);
                }
            }
        }
    }
