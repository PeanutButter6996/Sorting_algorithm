```py
import random

n=1000000
arrays = [round(random.uniform(1, 1000000), 2) for i in range(n)]

arrays.sort() # Ở đây dãy 1 là dãy đc sort bé đến lớn nên sẽ chỉ chạy sort. Đối với data 2 thì cần set .sort(reverse=True) để sắp xếp từ lớn đến bé, còn các data còn lại thì bỏ sort

# Write the arrays to a file
with open("data_1.txt", "w") as f: #đổi các tên khác nhau 2,3,... để tạo 10 dãy khác nhau
    for array in arrays:
        f.write(str(array) + " ")
 ```
