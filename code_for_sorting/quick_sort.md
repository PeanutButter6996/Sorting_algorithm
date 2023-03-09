```cpp
#include <iostream>
#include <fstream>
#include <chrono>

using namespace std;

void quickSort(double a[], int l, int r)
{
    double p = a[(l + r) / 2]; // Choose the pivot
    int i = l, j = r;
    while (i < j)
    {
        while (a[i] < p) // Ignore elements smaller than pivot and on the left
            i++;
        while (a[j] > p) // Ignore elements bigger than pivot and on the right
            j--;
        if (i <= j)
        {
            swap(a[i], a[j]); // Change position of 2 elements different side of pivot
            i++;
            j--;
        }
    }
    // Divide into 2 parts to sort
    if (i < r)
        quickSort(a, i, r);
    if (l < j)
        quickSort(a, l, j);
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
    auto start = chrono::high_resolution_clock::now(); // start the timer
    input("data_10.txt");
    quickSort(arr, 0, 999999); // gọi hàm sắp xếp
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
