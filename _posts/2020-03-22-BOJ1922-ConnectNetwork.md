---
layout: default
title: "BOJ 1922 : "네트워크 연결"
tags: 정보과학
---

문제에서 모든 컴퓨터를 최소 비용으로 연결하라고 했으니 트리를 만들되, 최소비용으로 트리를 만들라는 문제이다.

그렇다면 이 문제는 최소 스페닝 트리로 풀 수 있다

    #include <bits/stdc++.h>
    #define MEM 100001
    #define sanic ios_base::sync_with_stdio(0)
    using namespace std;
    typedef unsigned long long ull;
    typedef pair<int, int> pi;
    typedef pair<int, pair<int, int>> pii;
    int par[MEM], a, b, ans;
    vector<pii> g;
    int find(int x) {
        if (x == par[x])return x;
        return par[x] = find(par[x]);
    }
    void uni(int x, int y){
        x = find(x);
        y = find(y);
        par[y] = x;
    }
    int chk(int x, int y){
        x = find(x);
        y = find(y);
        if(x==y) return 1;
        return 0;
    }
    int main()
    {
        sanic;
        cin >> a >> b;
        for(int i=0; i<b; i++){
            int q1, q2, c;
            cin >> q1 >> q2 >> c;
            g.push_back({c, {q1, q2}});
        }
        sort(g.begin(), g.end());
        for(int i=1; i<=a; i++)
            par[i] = i;
        for(int i=0; i<b; i++){
            int c=g[i].first;
            int u=g[i].second.first;
            int v=g[i].second.second;
            if(!chk(u,v)){
                uni(u,v);
                ans += c;
            }
        }
        cout << ans;
    }
