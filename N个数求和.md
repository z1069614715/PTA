# PTA
天梯练习

[N个数求和](https://pintia.cn/problem-sets/994805046380707840/problems/994805133597065216)

    import java.util.Scanner;

    public class L1_009 {
        public static long gcb(long x, long y) {
            long z = x % y;
            if (z == 0) return y;
            return gcb(y, z);
        }

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int n = input.nextInt();
        long x = 0, y = 0;
        for (int i = 0; i < n; i++) {
            String num[] = input.next().split("/");
            long gcbNum = gcb(Long.parseLong(num[0]), Long.parseLong(num[1]));
            if (i == 0) {
                x = Long.parseLong(num[0]) / gcbNum;
                y = Long.parseLong(num[1]) / gcbNum;
            } else {
                long x1 = Long.parseLong(num[0]) / gcbNum, y1 = Long.parseLong(num[1]) / gcbNum;
                gcbNum = gcb(y, y1);
                x = (y / gcbNum) * x1 + (y1 / gcbNum) * x;
                y *= (y1 / gcbNum);
                gcbNum = gcb(x, y);
                x /= gcbNum;
                y /= gcbNum;
            }
        }
        if (x == 0) {
            System.out.println(0);
        } else {
            boolean isHavePreNum = false;
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
