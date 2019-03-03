# PTA
天梯练习

[输出GPLT](https://pintia.cn/problem-sets/994805046380707840/problems/994805113036587008)

_java_

    import java.util.HashMap;
    import java.util.Scanner;

    public class L1_023 {
        public static void main(String[] args) {
            Scanner input = new Scanner(System.in);
            String str = input.nextLine().toUpperCase();
            HashMap<Character, Integer> map = new HashMap<>();
            Character arr[] = {'G', 'P', 'L', 'T'};
            for (int i = 0; i < arr.length; i++) {
                map.put(arr[i],0);
            }
            for (int i = 0; i < str.length(); i++) {
                if (map.containsKey(str.charAt(i))){
                    map.put(str.charAt(i),map.get(str.charAt(i)) + 1);
                }
            }
            while (true){
                boolean isPrint = false;
                for (int i = 0; i < arr.length; i++) {
                    if (map.get(arr[i]) != 0){
                        System.out.print(arr[i]);
                        map.put(arr[i],map.get(arr[i]) - 1);
                        isPrint = true;
                    }
                }
                if (!isPrint) break;
            }
        }
    }

_python_

    line = input().upper()
    CountDict = {i: line.count(i) for i in ['G', 'P', 'L', 'T']}
    while True:
        IsPrint = False
        for i in ['G', 'P', 'L', 'T']:
            if CountDict[i] != 0:
                print(i,end='')
                IsPrint = True
                CountDict[i] -= 1
        if not IsPrint:
            break
