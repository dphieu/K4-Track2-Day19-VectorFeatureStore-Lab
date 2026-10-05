# Reflection — Lab 19

**Tên:** Dương Phương Hiểu
**Cohort:** A20-K4
**Path đã chạy:** Lite

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Hybrid đạt trung bình cao nhất: 78,6%, so với BM25 77,8% và Semantic 73,2%. Ở nhóm `exact`, BM25 và Hybrid cùng đạt 96,7% vì từ khóa kỹ thuật xuất hiện trực tiếp. Ở nhóm `mixed`, Hybrid thắng với 100%: BM25 giữ độ chính xác từ vựng, còn vector bổ sung độ phủ ngữ nghĩa. Với `paraphrase`, kết quả Lite là BM25 33,3%, Hybrid 32,0% và Semantic 24,0%. Semantic không dẫn đầu vì `bge-small-en-v1.5` chủ yếu học tiếng Anh. Đây là giới hạn thực nghiệm cần ghi nhận; với BGE-M3 đa ngữ, pure vector có thể phù hợp hơn cho truy vấn diễn đạt lại không có ràng buộc từ khóa.

Tôi chọn pure BM25 cho mã sản phẩm, tên biến, lỗi hoặc định danh cần khớp chính xác và latency thấp. Tôi chọn pure vector để khám phá ngữ nghĩa trên corpus đa ngữ khi exact match không quan trọng. Tôi không dùng Hybrid nếu một retriever đã đủ tốt, vì Hybrid tăng chi phí embedding, độ trễ và độ phức tạp vận hành.


---

## Điều ngạc nhiên nhất khi làm lab này

Mô hình vector tiếng Anh không tự động thắng truy vấn paraphrase tiếng Việt; chất lượng embedding phải được đo trên đúng ngôn ngữ và corpus triển khai.


---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
