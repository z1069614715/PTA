# PTA
天梯练习

[Left-pad](https://pintia.cn/problem-sets/994805046380707840/problems/994805100684361728)

    //
    // Created by Admin on 2019/3/6.
    //

    using namespace std;

    #include <iostream>
    #include <stdio.h>
    #include <stdlib.h>
    #include <algorithm>

    int main() {
        int n;
        char a;
        cin >> n >> a;
        getchar();
        string str;
        getline(cin, str);
        if (n > str.size()) {
            for (int i = 0; i < n - str.size(); ++i) {
                cout << a;
            }
            cout << str;
        } else {
            for (int i = str.size() - n; i < str.size(); ++i) {
                cout << str[i];
            }
        }
    }
