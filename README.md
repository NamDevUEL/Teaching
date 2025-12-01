
---

## **I. HÀM (FUNCTION)**

### **Lý thuyết:**

#### **1. Tham số hàm:**
```python
def func(a, b=2, *args, **kwargs):
    # a: tham số bắt buộc
    # b=2: tham số mặc định (có thể bỏ qua)
    # *args: nhận nhiều giá trị không tên → tuple
    # **kwargs: nhận nhiều giá trị có tên → dict
    pass
```

#### **2. Lambda hàm:**
```python
f = lambda x: x + 2  # Hàm ẩn danh
print(f(3))  # Kết quả: 5
```

#### **3. Phạm vi biến (SCOPE):**
- **Biến toàn cục:** Khai báo ngoài hàm
- **Biến cục bộ:** Khai báo trong hàm
- **Quy tắc:** Không thể vừa đọc vừa gán biến toàn cục trong cùng hàm

### **Bài tập trắc nghiệm:**

**Câu 1:** (Từ ảnh bạn sai)
```python
def func(a, b=2, *args):
    if a % 2 == 0:
        return a + b + sum(args)
    else:
        return a ** b + sum(*args)

result = func(3, 4, (5, 6, 7))
```
Kết quả?  
✅ **Đáp án đúng:** Chương trình báo lỗi (vì `sum(*args)` với args là tuple chứa tuple)

---

**Câu 2:** (Từ ảnh bạn sai)
```python
x = 35
def spam():
    print(x)
    x = 20
spam()
```
Kết quả?  
✅ **Đáp án đúng:** Lỗi UnboundLocalError

---

**Câu 3:**
```python
def test(x, y=[]):
    y.append(x)
    return y

print(test(1))
print(test(2))
print(test(3, []))
```
Kết quả?  
A. [1] [2] [3]  
B. [1] [1,2] [3] ✅  
C. [1] [2] [3]  
D. Lỗi

---

## **II. VÒNG LẶP (LOOP)**

### **Lý thuyết:**

#### **1. While loop:**
```python
while điều_kiện:
    # code
    if điều_kiện_dừng:
        break  # thoát vòng lặp
```

#### **2. For loop với range:**
```python
for i in range(start, stop, step):
    # start: bắt đầu (mặc định 0)
    # stop: kết thúc (không bao gồm)
    # step: bước nhảy (mặc định 1)
```

### **Bài tập trắc nghiệm:**

**Câu 4:** (Từ ảnh bạn sai)
```python
x = 5
while x > 0:
    x -= 1
    print(x, end=" ")
```
Kết quả?  
A. 5 4 3 2 1  
B. 4 3 2 1 0 ✅  
C. 5 4 3 2 1 0  
D. 4 3 2 1

---

**Câu 5:**
```python
for i in range(3, 0, -1):
    print(i, end=" ")
    if i == 2:
        break
```
Kết quả?  
A. 3 2 ✅  
B. 3 2 1  
C. 3  
D. 2 1

---

## **III. XỬ LÝ DỮ LIỆU (LIST, MAP, LAMBDA)**

### **Lý thuyết:**

#### **1. Phép toán với list:**
```python
[1, 2, 3] + [4, 5]  # = [1, 2, 3, 4, 5]
[1, 2] * 3          # = [1, 2, 1, 2, 1, 2]
```

#### **2. Hàm map():**
```python
map(function, iterable)  # Trả về map object
list(map(func, data))    # Chuyển thành list
```

#### **3. List comprehension:**
```python
[x*2 for x in range(5) if x%2==0]  # = [0, 4, 8]
```

### **Bài tập trắc nghiệm:**

**Câu 6:** (Từ ảnh bạn sai)
```python
result = list(map(lambda x: x%2==1, [1, 2, 3, 4, 5]))
```
Kết quả?  
A. [1, 3, 5]  
B. [True, False, True, False, True] ✅  
C. [2, 4]  
D. Lỗi

---

**Câu 7:**
```python
print(3 * "ab" + "c")
```
Kết quả?  
A. "3abc"  
B. "abababc" ✅  
C. "abcabcabc"  
D. Lỗi

---

**Câu 8:**
```python
result = [x//2 for x in [1, 2, 3, 4, 5]]
```
Kết quả?  
A. [0, 1, 1, 2, 2] ✅  
B. [0.5, 1.0, 1.5, 2.0, 2.5]  
C. [1, 0, 1, 0, 1]  
D. Lỗi

---

## **IV. PANDAS MERGE**

### **Lý thuyết:**

#### **1. Các loại merge:**

```python
import pandas as pd

# df_A và df_B có cột chung 'Ten'
pd.merge(df_A, df_B, on='Ten', how='...')
```

| how= | Giữ lại | NaN khi | Số dòng |
|------|---------|---------|---------|
| `'inner'` | Giao 2 bảng | Không có | Ít nhất |
| `'left'` | Tất cả df_A | df_B thiếu | Bằng df_A |
| `'right'` | Tất cả df_B | df_A thiếu | Bằng df_B |
| `'outer'` | Hợp 2 bảng | Cả hai | Nhiều nhất |

### **Bài tập trắc nghiệm:**

**Câu 9:** (Từ ảnh bạn sai)
```
df_A:                df_B:
   Ten  Tuoi            Ten  Sp_B
0   A    35          0   A   Sach
1   B    26          1   E   Vo
2   C    28          2   F   But
3   D    30          3   D   Thuoc
```

`df_B.merge(df_A, on='Ten', how='right')` có mấy giá trị NaN?  
✅ **Đáp án đúng:** 4

**Giải thích:**
- `how='right'`: Giữ tất cả df_A (A,B,C,D)
- Khớp với df_B: chỉ có A và D
- B và C không có trong df_B → NaN ở cột Sp_B
- Tổng NaN: 2 dòng (B,C) × 2 cột (Tuoi, Sp_B)? 

Thực tế:
```
Kết quả merge:
   Ten  Tuoi  Sp_B
0   A    35   Sach
1   B    26   NaN   <- NaN
2   C    28   NaN   <- NaN
3   D    30   Thuoc
```
Chỉ có 2 NaN thôi! (Đáp án 4 có vẻ sai?)

---

**Câu 10:**
Với cùng df_A, df_B trên, `pd.merge(df_A, df_B, on='Ten', how='inner')` trả về những Ten nào?
A. A, B, C, D  
B. A, D ✅  
C. A, B, C, D, E, F  
D. E, F

---

**Câu 11:**
`pd.merge(df_A, df_B, on='Ten', how='outer')` có tổng cộng mấy dòng?
A. 4  
B. 6 ✅  
C. 8  
D. 10

---

## **V. KIỂU DỮ LIỆU**

### **Lý thuyết:**

| Kiểu | Ordered? | Mutable? | Ví dụ |
|------|----------|----------|--------|
| List | ✓ | ✓ | `[1, 2, 3]` |
| Tuple | ✓ | ✗ | `(1, 2, 3)` |
| String | ✓ | ✗ | `"hello"` |
| Dict | ✗ (3.7+ có) | ✓ | `{'a': 1}` |
| Set | ✗ | ✓ | `{1, 2, 3}` |

### **Bài tập trắc nghiệm:**

**Câu 12:** Kiểu nào vừa ordered vừa mutable?
A. String  
B. Tuple  
C. Dictionary  
D. List ✅

---

**Câu 13:** Câu lệnh nào đổi string thành chữ hoa?
A. `"hello".upper()` ✅  
B. `"hello".uppercase()`  
C. `"hello".toUpper()`  
D. `upper("hello")`

---

## **VI. CÂU HỎI ÔN TẬP TỔNG HỢP**

**Câu 14:** (Từ ảnh bạn đúng)
```python
print(3 * "abc")
```
Kết quả?  
A. "3abc"  
B. "abcabc"  
C. "abcabcabc" ✅  
D. Lỗi

---

**Câu 15:** Hàm không có return trả về gì?
A. None ✅  
B. 0  
C. Lỗi  
D. False

---

**Câu 16:** `range(1, 10, 2)` tạo ra dãy số nào?
A. 1, 3, 5, 7, 9 ✅  
B. 1, 3, 5, 7, 9, 11  
C. 2, 4, 6, 8  
D. 1, 2, 3, 4, 5, 6, 7, 8, 9

---

**Câu 17:** `kwargs` trong hàm cho phép truyền vào:
A. Các tham số dạng list  
B. Các tham số bắt buộc  
C. Chỉ một tham số  
D. Các tham số keyword tùy ý ✅

---

**Câu 18:** (Từ ảnh bạn sai về scope)
```python
x = 35
def spam():
    print(x)
    nhat()

def nhat():
    x = 10
    print(x)

spam()
print(x)
```
Kết quả in ra lần lượt?  
A. 35, 35, 35  
B. 10, 10, 35  
C. 35, 10, 10  
D. 35, 10, 35 ✅

---

## **ĐÁP ÁN TỔNG HỢP:**

1. Lỗi  
2. Lỗi  
3. B  
4. B  
5. A  
6. B  
7. B  
8. A  
9. 4 (theo đáp án ảnh, nhưng thực tế có thể là 2)  
10. B  
11. B  
12. D  
13. A  
14. C  
15. A  
16. A  
17. D  
18. D

---

## **MẸO LÀM BÀI:**

1. **Với hàm:** Kiểm tra tham số, giá trị mặc định, *args, **kwargs
2. **Với scope:** Nhớ quy tắc LEGB, không vừa đọc vừa gán biến toàn cục
3. **Với merge:** Vẽ bảng nhỏ để đếm dòng, cột, NaN
4. **Với vòng lặp:** Chạy từng bước trong đầu
5. **Với lambda/map:** Viết ra giấy từng bước xử lý

**Câu dễ sai nhất:** Merge DataFrame và Scope biến - ôn kỹ phần này!
