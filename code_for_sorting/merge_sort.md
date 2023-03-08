```cpp
#include <iostream>
#include <fstream>
#include <vector>
using namespace std;

template <typename T>
void sort(T arr[], int left, int right){
    vector<T> MidArr(right - left + 1); //khởi tạo mảng trung gian để "trộn"
    if(right - left + 1 == 1) //mảng chỉ có 1 phần tử, không cần phải sắp xếp
        return;
    int mid = (left + right) / 2; //chọn phần giữa để chia mảng thành 2 phần

    //gọi hàm sắp xếp 2 nửa
    sort(arr, left, mid);
    sort(arr, mid + 1, right);

    //"trộn" 2 nửa đã sắp xếp
    int i = left, j = mid + 1; 
    int cur = 0;// chỉ số của mảng trung gian
    while(i <= mid || j <= right){
        if(i > mid) //bên trái không còn phần tử
            MidArr[cur++] = arr[j++];
        else if(j > right) //bên phải không còn phần tử
            MidArr[cur++] = arr[i++];
        else if(arr[i] < arr[j]) //phần tử bên trái nhỏ hơn, ta cho vào mảng trước
            MidArr[cur++] = arr[i++];
        else //phần tử bên trái nhỏ hơn, ta cho vào mảng trước
            MidArr[cur++] = arr[j++];
    }

    //đưa các giá trị ở mảng trung gian về mảng chính
    for(int i = 0; i < cur; ++i)
        arr[left + i] = MidArr[i];
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
    input("data_1.txt"); //ở đây thế từng test vào
    sort(arr, 0, 999999); // gọi hàm sắp xếp
      // write the sorted data to a file
    ofstream out("out_3.txt");
    for(int i = 0; i < 1000000; ++i){
        out << arr[i] << endl;
    }
    out.close();
    return 0;

}
```
