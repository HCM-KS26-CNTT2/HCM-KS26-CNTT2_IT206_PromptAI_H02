# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 07
- **Họ tên:**
- **Lớp:**
- **Link repository Pha2:**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):**

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt vé vào cổng ra JSON

**KET QUA AI**

```text
```json
[
  {
    "loai_ve": "VECH",
    "ngay_choi": "2026-12-20",
    "nguoi_lon": 2,
    "tre_em": 1,
    "loai_tu": "nho",
    "ghi_chu": null
  },
  {
    "loai_ve": "VECN",
    "ngay_choi": "2027-01-03",
    "nguoi_lon": 3,
    "tre_em": 0,
    "loai_tu": null,
    "ghi_chu": "Một người đang bó bột tay"
  },
  {
    "loai_ve": "VEVIP",
    "ngay_choi": null,
    "nguoi_lon": 4,
    "tre_em": 0,
    "loai_tu": "lon",
    "ghi_chu": "Một bạn đi xe lăn"
  }
]

```
```

**Link trò chuyện:**https://share.gemini.google/1mq85m1zBFcv

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**

```text
```python
adult_price = 250000
num_adults = 8
total_adult = adult_price * num_adults

child_price = int(adult_price * 0.6)
num_children_paid = 4 # 1.05m, 1.15m, 1.2m, 1.3m are all between 1m and 1.4m
num_children_free = 2 # under 1m
total_child = child_price * num_children_paid

total_tickets = total_adult + total_child

# 8 adults >= 8 -> 10% discount
discount = int(total_tickets * 0.1)

life_jacket_price = 40000
num_jackets = 6
total_surcharge = life_jacket_price * num_jackets

final_total = (total_tickets - discount) + total_surcharge

print(f"1. Adult: {total_adult:,}")
print(f"2. Child: {total_child:,} (unit: {child_price:,})")
print(f"3. Total tickets: {total_tickets:,}")
print(f"4. Discount: {discount:,}")
print(f"5. Surcharge: {total_surcharge:,}")
print(f"6. Final total: {final_total:,}")


```

```text
1. Adult: 2,000,000
2. Child: 600,000 (unit: 150,000)
3. Total tickets: 2,600,000
4. Discount: 260,000
5. Surcharge: 240,000
6. Final total: 2,580,000


```

1. **Tổng tiền vé người lớn:**
Đoàn mua vé cả ngày (VECN) có giá niêm yết là 250.000 đồng/vé người lớn.

$$8 \times 250.000 = 2.000.000\text{ (đồng)}$$


2. **Tổng tiền vé trẻ em:**

* Cả 4 trẻ em có chiều cao 1,05 m, 1,15 m, 1,2 m và 1,3 m đều nằm trong khoảng từ 1 m đến 1,4 m nên áp dụng mức giá bằng 60% giá vé người lớn:

$$250.000 \times 60\% = 150.000\text{ (đồng/vé)}$$


* 2 bé cao dưới 1 m được miễn phí (0 đồng).
* Tổng tiền vé trẻ em:

$$4 \times 150.000 + 2 \times 0 = 600.000\text{ (đồng)}$$



3. **Tổng tiền vé tất cả (của người lớn và trẻ em):**

$$2.000.000 + 600.000 = 2.600.000\text{ (đồng)}$$


4. **Tổng tiền giảm giá đoàn:**
Đoàn có 8 người lớn (đạt điều kiện từ 8 người lớn trở lên) nên được giảm 10% trên tổng tiền vé:

$$2.600.000 \times 10\% = 260.000\text{ (đồng)}$$


5. **Tổng tiền phụ thu:**
Đoàn thuê 6 áo phao với giá 40.000 đồng/chiếc (không áp dụng giảm giá):

$$6 \times 40.000 = 240.000\text{ (đồng)}$$


6. **Tổng tiền:**

$$\text{Tổng tiền} = (2.600.000 - 260.000) + 240.000 = 2.340.000 + 240.000 = 2.580.000\text{ (đồng)}$$



[RESULT: 2.580.000 đồng]
```

**Link trò chuyện:**https://share.gemini.google/JaxN1IxyMZrd

### b) Kiểm tra kết quả AI

AI chính xác

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
```json
{
  "loai_su_co": "dong_khu_choi",
  "so_khach": 4,
  "so_khu_bi_dong": 2,
  "tom_tat": "Khách phàn nàn khu trượt nước chính và khu sóng nhân tạo đóng cửa cả ngày không thông báo trước."
}

``````

**Link trò chuyện:**https://share.gemini.google/gVUvOXzGVCfG

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
## Tổng điểm: 0/10

---

### Bảng chấm điểm chi tiết

| Tiêu chí | Trọng số | Điểm đạt | Nhận xét |
| --- | --- | --- | --- |
| **Đúng thông tin** | 5 điểm | **0/5** | Sai cả giá vé lẫn chính sách thời tiết so với thông tin chuẩn. |
| **Đầy đủ** | 3 điểm | **0/3** | Thiếu thông tin/câu trả lời đầy đủ và chưa mời khách cung cấp ngày chơi, số vé để đặt vé. |
| **Giọng điệu** | 2 điểm | **0/2** | Dùng nhiều từ ngữ suồng sã, thiếu chuyên nghiệp (*"Hello chị!"*, *"mát rượi luôn"*, *"nha"*, *"ới"*). |

---

### Đánh giá & Góp ý cải thiện

* **Sai lệch thông tin nghiêm trọng:**
* Báo giá **150k** trong khi giá chuẩn của vé VECH là **180.000 đồng/vé người lớn**.
* Báo **hoàn tiền mặt 100%** khi đóng cửa do mưa, trái hoàn toàn với chính sách chuẩn (khách đã vào **dưới 2 giờ** được **tặng 1 vé cùng loại dùng trong 30 ngày, không hoàn tiền mặt**; **từ 2 giờ trở lên không được bù**).


* **Thiếu bước chốt/hỗ trợ đặt vé:** Chưa hỏi/mời khách cung cấp **ngày chơi** và **số lượng vé** để tiến hành đặt vé.
* **Cách xưng hô và ngôn ngữ:** Các từ như *"Hello chị!"*, *"mát rượi luôn"*, *"nha"*, *"ới"* tạo cảm giác quá suồng sã. Cần chuyển sang văn phong lịch sự, rõ ràng và chuẩn mực hơn.

### Câu trả lời mẫu gợi ý

> *"Dạ em chào chị. Giá vé VECH bên em là 180.000 đồng/vé người lớn ạ. Về chính sách khi đóng cửa do thời tiết: nếu chị đã vào cổng dưới 2 giờ, bên em sẽ tặng 1 vé cùng loại có thời hạn sử dụng trong 30 ngày (không áp dụng hoàn tiền mặt); trường hợp từ 2 giờ trở lên thì không được bù vé ạ. Để em hỗ trợ đặt vé cho chị, chị cho em xin ngày đi và số lượng vé mình cần nhé!"*
```

**Link trò chuyện:**https://share.gemini.google/Wgfndldcmnge
