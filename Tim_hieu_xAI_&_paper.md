## xAI là gì? Tại sao cần xAI?
- xAI: kỹ thuật/ phương pháp giúp giải thích các mô hình DL được xem là blackbox
- Nó thường quan trọng và rất cần thiết khi ứng dụng mô hình cho các lĩnh vực y tế, giáo dục, tài chính... cần tính giải thích và trách nhiệm cao.
- Giúp ta biết mô hình đang tập trung vào features nào, cái nào ảnh hưởng đến việc ra quyết định.
- Biết được model có hoạt động đúng như mong muốn không, vd: bias, overfit
- Việc giải thích giúp ta có thể trace lại nguyên nhân, đôi khi nó có giá trị hơn kết quả cuối.

## Có những loại xAI nào?
- Theo tìm hiểu thì xAI được phân loại dựa trên phạm vi giải thích và ứng dụng.
    - Local Explanation: Tập trung vào 1 điểm dữ liệu duy nhất trong feature space. Ý tưởng của nó là đi xấp xỉ hàm f(x) bằng 1 hàm tuyến tính đơn giản hơn. Kết quả đầu ra sẽ là 1 vector trọng số thể hiện sự đóng góp của từng đặc trưng cho 1 đối tượng.
    - Global Explanation: Đánh giá hành vi model trên toàn bộ phân phối dữ liệu. Hệ thống sẽ tính toán giá trị kỳ vọng hoặc mức độ ảnh hưởng trung bình của các đặc trưng lên kết quả dự đoán và một tập mẫu thử. Kết quả: hệ thống cung cấp 1 bảng xếp hạng tầm quan trọng của các đặc trưng.

## Nhược điểm của từng loại???
 - Local Explanation:
    + Thiếu góc nhìn mang tính hệ thống, chi tiết cho 1 điểm dữ liệu nhưng k thể giúp phát hiện ra mô hình có bị bias không.
    + Thiếu ổn định, nhạy cảm với noise.
    + Chi phí tính toán cao do phải tính từng điểm dữ liệu.
- Global Explanation: 
    + Có thể bị sai lệch khi dùng để giải thích cho một đối tượng có các đặc trưng phức tạp hoặc nằm ở vùng biên của tập dữ liệu.
    + Làm lu mờ các đặc trưng chỉ nổi bậc khi đi kèm các đặc trưng khác trong feature space.

## Mô hình tiêu biểu của xAI?
- LIME: thuộc loại cục bộ và đôc lập cho từng mô hình.
    + Cách hoạt động: Tạo nhiễu, xấp xỉ mô hình huấn luyện bằng mô hình tuyến tính để xấp xỉ kết quả.
    + Mạnh: Nhanh, dễ giải thích, áp dụng rộng rãi cho các mô hình blackbox.
    + Yếu: Thiếu ổn định, việc random noise và xấp xỉ mô hình phi tuyến bằng mô hình tuyến tính có thể dẫn đến sai sót nếu thử chạy nhiều lần
- ANCHOR: sinh ra để khắc phục hạn chế của LIME bằng việc đưa ra các luật dẫn. Nhưng lại có chi phí tính toán lớn khi duyệt quả không gian tổ hợp luật này.
- SHAP: cục bộ hoặc toàn cục đều được.
    + Ứng dụng Game Theory giúp model xem xét mỗi đặc đóng gọp bao nhiêu vào kết quả.
    + Mạnh: nhất quán dựa trên nền tảng toán.
    + Yếu: Chi phí tính toán cao khí lượng features tăng
- Grad-CAM: Cục bộ, và đặc thù cho mô hình, ứng dụng trong CNNs
    + Cách hoạt động: Tính đạo hàm của nhãn dự đoán đối với feature map ở lớp tích chập cuối cùng để tạo bản đồ nhiệt (heatmap).
    + Mạnh: trực quan, k cần huấn luyện lại mô hình.
    + Yếu: Chỉ ứng dụng đc cho CNN
- Attention-based: cục bộ và đặc thù cho các mô hình dùng Attention
    + Cách hoạt động: Dựa trên Attention weights.
    + Mạnh: Nhanh do attention weights đã được tính toán, nó cũng phản ánh chính xác nhưng thông tin model dùng để dự đoán kết quả thay vì xấp xỉ.
    + Yếu: Bài báo "Attention is not Explanation" chỉ ra việc có thể thay đổi các trọng số attention bên trong mô hình bằng nhiễu, nhưng kết quả dự đoán vẫn không đổi -> giảm độ tin cậy.

## Paper 