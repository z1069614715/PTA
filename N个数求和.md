# PTA
天梯练习

[N个数求和](https://pintia.cn/problem-sets/994805046380707840/problems/994805133597065216)

    import java.util.ArrayList;
    import java.util.Collections;
    import java.util.Scanner;

    public class L1_009 {
        public static long gcb(long x, long y) {
            long z = x % y;
            if (z == 0) return y;
            return gcb(y, z);
        }

        public static void main(String[] args) {
            Scanner input = new Scanner(System.in);
            ArrayList<Long> numerator = new ArrayList<>();
            ArrayList<Long> denominator = new ArrayList<>();
            int n = input.nextInt();
            for (int i = 0; i < n; i++) {
                String num[] = input.next().split("/");
                long gcbNum = gcb(Long.parseLong(num[0]), Long.parseLong(num[1]));
                numerator.add(Long.parseLong(num[0]) / gcbNum);
                denominator.add(Long.parseLong(num[1]) / gcbNum);
            }
            long x = numerator.get(0), y = denominator.get(0);
            for (int i = 1; i < n; i++) {
                long num = gcb(y, denominator.get(i));
                x = (y / num) * numerator.get(i) + (denominator.get(i) / num) * x;
                y *= (denominator.get(i) / num);
                num = gcb(x, y);
                x /= num;
                y /= num;
            }
            boolean isHavePreNum = false;
            if (x == 0) {
                System.out.println(0);
            } else {
                if (Math.abs(x) >= Math.abs(y)) {
                    System.out.print((int) (x / y));
                    if (y != 1) System.out.print(" ");
                    isHavePreNum = true;
                }
                if (y != 1) {
                    if (isHavePreNum) {
                        System.out.print(Math.abs(x - ((int) (x / y) * y)) + "/" + y);
                    } else {
                        System.out.print(x - ((int) (x / y) * y) + "/" + y);
                    }
                }
            }
        }
    }
