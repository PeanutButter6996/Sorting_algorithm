```cpp
#include <iostream>
#include <fstream>
#include <chrono>

using namespace std;

void heapify(double arr[], int n, int i) {
    int largest = i;  
    int left = 2 * i + 1;  
    int right = 2 * i + 2;  
 
    if (left < n && arr[left] > arr[largest])
        largest = left;
 

    if (right < n && arr[right] > arr[largest])
        largest = right;
 

    if (largest != i) {
        swap(arr[i], arr[largest]);
 
        heapify(arr, n, largest);
    }
}
 
void heapSort(double arr[], int n) {
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);
 
    for (int i = n - 1; i >= 0; i--) {

        swap(arr[0], arr[i]);

        heapify(arr, i, 0);
    }
}


double arr[1'000'000];


void input(const string& file){
    ifstream in(file);
    for(int i = 0; i < 1000000; ++i){
        in >> arr[i];
    }
    in.close();
}

int main(){
    auto start = chrono::high_resolution_clock::now(); // bắt đầu thời gian
    input("data_1.txt"); //ở đây thế từng file vào 2,3,...
    heapSort(arr, 1000000); // gọi hàm sắp xếp
      // xuất ra 1 file
    ofstream out("out_1.txt"); // xuất ra từng file 2,3,...
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
