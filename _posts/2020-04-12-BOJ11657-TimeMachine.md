---
layout: default
title: "BOJ 11657 : 타임머신"
tags: 정보과학
---

여기서 주어지는 그래프는 가중치가 음수인 간선이 있다.

그러므로 다익스트라를 이용하지 말고, 벨만 포드를 이용하자.

    #include <bits/stdc++.h>
    #define MEM 505
    #define sanic ios_base::sync_with_stdio(0)
    #define f first
    #define s second
    using namespace std;
    typedef long long ll;
    typedef pair<ll, ll> pi;
    const ll INF = 1e9+7;
    ll d[MEM];
    int n,m;
    int main()
    {
        sanic;
        cin >> n >> m;
        vector<pi> a[MEM];
        for(int i=0,x,y,z; i<m; i++){
            cin >> x >> y >> z;
            a[x].push_back({y,z});
        }
        fill(d, d+n+1, INF);
        d[1] = 0;
        bool cy=0;
        for(int i=1; i<=n; i++)
            for(int j=1; j<=n; j++)
                for(auto &p : a[j]){
                    int x=p.f, c=p.s;
                    if(d[j]!=INF && d[x]>d[j]+c){
                        d[x] = d[j]+c;
                        if(i==n) cy = 1;
                    }
                }
        if(cy) cout << -1;
        else{
            for(int i=2; i<=n; i++){
                if(d[i]==INF) cout << -1 << '\n';
                else cout << d[i] << '\n';
            }
        }
    }
