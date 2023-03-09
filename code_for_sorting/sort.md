```cpp
#include <iostream>
#include <fstream>
#include <chrono>
#include <algorithm>

using namespace std;

double arr[1'000'000];


void input(const string& file){
    ifstream in(file);
    for(int i = 0; i < 1000000; ++i){
        in >> arr[i];
    }
    in.close();
}

int main(){
    auto start = chrono::high_resolution_clock::now(); // start the timer
    input("data_10.txt");
    sort(arr, arr + 1000000); // gọi hàm sắp xếp
      // write the sorted data to a file
    ofstream out("out_10.txt");
    for(int i = 0; i < 1000000; ++i){
        out << arr[i] << endl;
    }
    out.close();
    auto end = chrono::high_resolution_clock::now(); // end the timer
    auto time_taken = chrono::duration_cast<chrono::milliseconds>(end - start); // calculate the time taken

    cout << "Time taken by code segment: " << time_taken.count() << " milliseconds." << endl;
    return 0;
}
```
