

## Explicação do Código

O código a seguir é um programa em C++ que organiza um conjunto de pessoas em times com base em suas pontuações e, em seguida, ordena os nomes dentro de cada time.

### Inclusão de Bibliotecas

```cpp
#include<bits/stdc++.h>
```
A linha acima inclui todas as bibliotecas padrão do C++. É uma prática comum em competições de programação, mas não é recomendada para produção devido ao aumento do tempo de compilação.

### Uso do Espaço de Nomes

```cpp
using namespace std;
```
Esta linha permite que usemos funções da biblioteca padrão sem precisar prefixá-las com `std::`.

### Função de Comparação

```cpp
bool comparaSegundo(const pair<string, int>& a, const pair<string, int>& b){
    return a.second > b.second;
}
```
A função `comparaSegundo` é usada para comparar dois pares. Ela retorna `true` se o segundo elemento do primeiro par for maior que o segundo elemento do segundo par.

### Função Principal

```cpp
int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
```
As duas linhas acima são otimizações de entrada/saída que sincronizam os fluxos de entrada/saída do C++ com os do C para tornar a leitura e escrita mais rápidas.

### Declaração de Variáveis

```cpp
    int n, t; cin >> n >> t;
```
Declaramos duas variáveis, `n` e `t`, e lemos seus valores. `n` é o número de pessoas e `t` é o número de times.

### Vetor de Pessoas

```cpp
    vector<pair<string, int>> pessoas(n);
```
Criamos um vetor de pares, onde cada par contém um `string` (nome da pessoa) e um `int` (pontuação da pessoa). O vetor é inicializado com tamanho `n`.

### Leitura dos Dados das Pessoas

```cpp
    for(int i = 0; i < n; i++){
        cin >> pessoas[i].first >> pessoas[i].second;
    }
```
Usamos um loop para ler os nomes e pontuações das pessoas e armazená-los no vetor `pessoas`.

### Ordenação das Pessoas

```cpp
    sort(pessoas.begin(), pessoas.end(), comparaSegundo);
```
Ordenamos o vetor `pessoas` usando a função `comparaSegundo`.

### Criação dos Times

```cpp
    vector<vector<string>> times(t);
```
Criamos um vetor de vetores de `string` para representar os times.

### Distribuição das Pessoas pelos Times

```cpp
    for(int i = 0; i < n; i++){
        int vez = i % t;
        times[vez].push_back(pessoas[i].first);
    }
```
Distribuímos as pessoas pelos times de forma circular usando o operador módulo.

### Ordenação dos Nomes dentro dos Times

```cpp
    for(int i = 0; i < t; i++){
        sort(times[i].begin(), times[i].end());
    }
```
Ordenamos os nomes dentro de cada time.

### Exibição dos Times

```cpp
    for(int i = 0; i < t; i++){
        cout << "TIME " << i + 1 << ":\n";
        for(string nome : times[i]){
            cout << nome << '\n';
        }
        cout << '\n';
    }
    return 0;
}
```
Exibimos os times e os nomes de cada pessoa em cada time.

---

## Código Completo

```cpp
#include<bits/stdc++.h>
using namespace std;

bool comparaSegundo(const pair<string, int>& a, const pair<string, int>& b){
    return a.second > b.second;
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int n, t; cin >> n >> t;
    
    vector<pair<string, int>> pessoas(n);
    
    for(int i = 0; i < n; i++){
        cin >> pessoas[i].first >> pessoas[i].second;
    }
    
    sort(pessoas.begin(), pessoas.end(), comparaSegundo);
    
    vector<vector<string>> times(t);
    
    for(int i = 0; i < n; i++){
        int vez = i % t;
        times[vez].push_back(pessoas[i].first);
    }
    
    for(int i = 0; i < t; i++){
        sort(times[i].begin(), times[i].end());
    }
    
    for(int i = 0; i < t; i++){
        cout << "TIME " << i + 1 << ":\n";
        for(string nome : times[i]){
            cout << nome << '\n';
        }
        cout << '\n';
    }
    return 0;
}
