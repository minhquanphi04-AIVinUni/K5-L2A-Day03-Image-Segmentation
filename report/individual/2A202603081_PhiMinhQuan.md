# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202603081
- Ngày / CVAT local: 12/11
- Công cụ đã dùng: sam-vit-h

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | --- | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | chưa có | 0 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | chưa có | 0 / 1 | 3 |
| cp6_coverage | chưa có | 0 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Ảnh 000000181542.jpg; Vị trí: Dưới cùng bên trái; Tên object: Motorcycle 2 (manual)
- Class và quy tắc tôi dùng để chọn biên: Class Motorcycle; Quy tắc chọn biên: bao phủ vật thể, không lem sang pixel không phải vật thể đó.
- Không dùng gợi ý; Lý do: Object nhỏ, dễ vẽ, ở gần biên, không cần dùng đến công cụ hỗ trợ.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: medium_instance/000000373353.jpg/Chính giữa phía dưới
- Lỗi thuộc loại: Sai lớp
- Bằng chứng tôi nhìn thấy: Khi công cụ mask Person đứng đằng trước ô tô, ô tô cũng bị lem vào và tính là Person.
- Quy tắc và hành động sửa: Chỉnh mask bằng tay, xoá phần ô tô được mask là Person đi.
- Sau sửa đã Save và export lại chưa? Đã Save và export.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): Kết quả tự đánh giá: medium_instance đạt metric 0.679 (19.8 / 32 điểm, IoU: 0.803, Recall: 0.85); hard_panoptic tăng từ 3.3 lên 6.4 / 30 điểm (PQ tăng lên 0.296, nhận đúng 24 xe ô tô); easy_semantic đạt mIoU 0.813 (18.3 / 20 điểm). Tổng điểm 3 tier tự đánh giá đạt 44.5 / 82 điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

- Em dùng sam-vit-h
- Em dùng AI tool, chọn class/label, rồi khoanh vùng để AI mask; Sau đó chỉnh sửa nếu cần thiết.
