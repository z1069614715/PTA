# PTA
天梯练习

[A-B](https://pintia.cn/problem-sets/994805046380707840/problems/994805130426171392)

_java_

    import java.util.Scanner;

    public class L1_011 {
        public static void main(String[] args) {
            Scanner input = new Scanner(System.in);
            String A = input.nextLine();
            String B = input.nextLine();
            int arr[] = new int[256];
            for (int i = 0; i < B.length(); i++) {
                arr[B.charAt(i)] = 1;
            }
            for (int i = 0; i < A.length(); i++) {
                if (arr[A.charAt(i)] == 0) System.out.print(A.charAt(i));
            }
        }
    }

_python_

    import re
    def Transform(match):
        return '\\' + match.group('value')
    A = input()
    B = input()
    B = '[' + re.sub('(?P<value>[\[\]])',Transform,B) + ']'
    A = re.sub(B,"",A)
    print(A)
