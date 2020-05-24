---
layout: default
title: "BOJ 8394 : 악수"
tags: 정보과학
---

피보나치 수열이다.

안 믿긴다면 직접 손으로 노가다를 하면 찾을 수 있다.

DP를 이용하여 피보나치를 구할 수 있다.

    #include <bits/stdc++.h>
    #define MEM 10000004
    #define sanic ios_base::sync_with_stdio(0)
    #define MOD 1000000007
    using namespace std;
    typedef long long lld;
    int n;
    int dp[MEM];
    main() {
        sanic;
        cin >> n;
        dp[1] = 1;
        dp[2] = 2;
        for(int i=3; i<=n; i++)
            dp[i] = (dp[i-1]+dp[i-2])%10;
        cout << dp[n]%10;
    }
 
