+++
title = 'Union Find (C++)'
date = 2024-07-07T02:49:18+09:00
tags = ['C++']
ShowToc = true
+++

## Union Find
- **Union Find**: 그래프에서 두 노드가 같은 집합에 속하는지 판별하는 알고리즘
    - 노드를 합치는 union 연산
    - 노드가 같은 집합인지 판별하는 find 연산

## 구조
- **unionfind[i]**: i번 노드의 부모 노드 정보를 담는다.
- **unify(x, y)**: x번 노드와 y번 노드를 합친다. 이때 unify 이후 둘은 같은 부모 노드를 가리키게 된다.
- **same(x, y)**: x번 노드와 y번 노드가 같은 집합에 있는 지 반환한다.
- **find(x)**: x번 노드의 부모 노드 정보를 반환한다.
    - 이때 unionfind[x]를 단순히 반환하는 것이 아닌, unionfind[x]를 업데이트하는 과정을 거침
    - 재귀함수를 통해 구현하여 찾음과 동시에 부모 노드가 업데이트되도록 함

### 전체 코드
```C++
#include <iostream>
#define MAX 100
using namespace std;
using ll = long long;

ll unionfind[MAX];

ll find(ll x){
    if(unionfind[x]==x){    
        return x;
    }
    return unionfind[x]=find(unionfind[x]);
}

void unify(ll x, ll y){
    ll n1=find(x), n2=find(y);
    if(n1<n2){
        unionfind[n2]=n1;
    }
    else{
        unionfind[n1]=n2;
    }
}

bool same(ll x, ll y){
    return (find(x)==find(y));
}

int main(){
    
}
```