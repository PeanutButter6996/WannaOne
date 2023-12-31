# Crypto Homework #

## 1. Collider
- Bài này server sẽ nhận vào các document và MD5 hash nó. Chúng ta cần 2 document khác nhau nhưng có cùng MD5 hash để có thể thu về được flag. <br>
- Sau khi tìm kiếm thì em đã tìm được trang này ```https://www.mscs.dal.ca/~selinger/md5collision/```, sử dụng 2 stirng mà đã cho sẵn, ta sẽ nhận được flag.
![image](https://github.com/PeanutButter6996/WannaOne/assets/109911533/ac3493f0-edd4-48c1-91d9-bca72dfbecb3)

## 2. Jack's Birthday Hash
- Hàm băm ```JACK11``` trả về 1 chuỗi nhị phân dài 11 số, tham khảo công thức tại ```https://en.wikipedia.org/wiki/Birthday_problem#Probability_of_a_shared_birthday_(collision)```
- Hash collision xảy ra trong trường hợp này: $\frac{1}{2^{11}} = \frac{1}{2048}$
- Vậy xác suất tìm ra sẽ là $q(n) =1 - (\frac{2047}{2048})^n$

Ta cần tìm $n$ sao cho $q(n) \ge 0.5$. Thế n vào công thức, ta sẽ tìm được: $n = 1420$

## 3. Jack's Birthday Confusion
- Tham khảo công thức ở ```https://en.wikipedia.org/wiki/Birthday_problem#Arbitrary_number_of_days```
- Thay thế 0.5 bằng 0.75, và thế từng d vào công thức ta sẽ tìm được n=76

## 4. Hash Stuffing
```python
# 2^128 collision protection!
BLOCK_SIZE = 32

def pad(data):
    padding_len = (BLOCK_SIZE - len(data)) % BLOCK_SIZE
    return data + bytes([padding_len]*padding_len)
```
- Hàm sẽ thêm padding nếu ko đủ độ dài, nhưng nếu black đủ độ dài 32 thì lại không thêm gì.
- Vì thế ```pad(b'\x01'*31) == pad(b'\x01'*32)```
