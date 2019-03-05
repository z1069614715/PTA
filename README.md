# PTA
天梯练习

[凑零钱](https://pintia.cn/problem-sets/994805046380707840/problems/994805054207279104)

    import java.util.*;

    public class L3_001 {
        public static void main(String[] args) {
            Scanner input = new Scanner(System.in);
            int n = input.nextInt();
            int m = input.nextInt();
            Integer coin[] = new Integer[n];
            for (int i = 0; i < coin.length; i++) {
                coin[i] = input.nextInt();
            }
            Comparator<Integer> cmp = new Comparator<Integer>() {
                @Override
                public int compare(Integer o1, Integer o2) {
                    return o2 - o1;
                }
            };
            Arrays.sort(coin,cmp);
            int dp[] = new int[m + 1];
            boolean ischoicn[][] = new boolean[n + 1][m + 1];
            for (int i = 0; i < n; i++) {
                for (int j = m; j >= coin[i]; j--) {
                    if (dp[j] <= dp[j - coin[i]] + coin[i]){
                        ischoicn[i][j] = true;
                        dp[j] = dp[j - coin[i]] + coin[i];
                    }
                }
            }

            if (dp[m] != m) System.out.println("No Solution");
            else {
                ArrayList<Integer> list = new ArrayList<>();
                int index = n - 1, money = m;
                while (money > 0){
                    if (ischoicn[index][money]){
                        if (index != n - 1) System.out.print(" ");
                        System.out.print(coin[index]);
                        money -= coin[index];
                    }
                    index--;
                }
            }
        }
    }
