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
  - Thiếu góc nhìn mang tính hệ thống, chi tiết cho 1 điểm dữ liệu nhưng k thể giúp phát hiện ra mô hình có bị bias không.
  - Thiếu ổn định, nhạy cảm với noise.
  - Chi phí tính toán cao do phải tính từng điểm dữ liệu.
- Global Explanation:
  - Có thể bị sai lệch khi dùng để giải thích cho một đối tượng có các đặc trưng phức tạp hoặc nằm ở vùng biên của tập dữ liệu.
  - Làm lu mờ các đặc trưng chỉ nổi bậc khi đi kèm các đặc trưng khác trong feature space.

## Mô hình tiêu biểu của xAI?

- LIME: thuộc loại cục bộ và đôc lập cho từng mô hình.
  - Cách hoạt động: Tạo nhiễu, xấp xỉ mô hình huấn luyện bằng mô hình tuyến tính để xấp xỉ kết quả.
  - Mạnh: Nhanh, dễ giải thích, áp dụng rộng rãi cho các mô hình blackbox.
  - Yếu: Thiếu ổn định, việc random noise và xấp xỉ mô hình phi tuyến bằng mô hình tuyến tính có thể dẫn đến sai sót nếu thử chạy nhiều lần
- ANCHOR: sinh ra để khắc phục hạn chế của LIME bằng việc đưa ra các luật dẫn. Nhưng lại có chi phí tính toán lớn khi duyệt quả không gian tổ hợp luật này.
- SHAP: cục bộ hoặc toàn cục đều được.
  - Ứng dụng Game Theory giúp model xem xét mỗi đặc đóng gọp bao nhiêu vào kết quả.
  - Mạnh: nhất quán dựa trên nền tảng toán.
  - Yếu: Chi phí tính toán cao khí lượng features tăng
- Grad-CAM: Cục bộ, và đặc thù cho mô hình, ứng dụng trong CNNs
  - Cách hoạt động: Tính đạo hàm của nhãn dự đoán đối với feature map ở lớp tích chập cuối cùng để tạo bản đồ nhiệt (heatmap).
  - Mạnh: trực quan, k cần huấn luyện lại mô hình.
  - Yếu: Chỉ ứng dụng đc cho CNN
- Attention-based: cục bộ và đặc thù cho các mô hình dùng Attention
  - Cách hoạt động: Dựa trên Attention weights.
  - Mạnh: Nhanh do attention weights đã được tính toán, nó cũng phản ánh chính xác nhưng thông tin model dùng để dự đoán kết quả thay vì xấp xỉ.
  - Yếu: Bài báo "Attention is not Explanation" chỉ ra việc có thể thay đổi các trọng số attention bên trong mô hình bằng nhiễu, nhưng kết quả dự đoán vẫn không đổi -> giảm độ tin cậy.

## Paper "An explainable AI-driven deep neural network for accurate breast cancer detection from histopathological and ultrasound images'"

- Sơ lược: Paper đề cập đến việc sử dụng deep learning model do nhóm phát triển dựa trên Densenet121 bằng phương pháp transfer learning. Cải tiến của nhóm nghiên cứu nằm ở việc vận dụng các phương pháp tiền xử lý dữ liệu để giúp model có thể học tốt hơn. Đồng thời cũng ứng ựng xAI Grad-CAM để giải thích và trực quan hoá vùng ảnh hưởng quyết định đưa ra kết quả của model -> xAI là phần team cần tập trung tìm hiểu và chạy thực nghiệm lại.
- Dataset thực nghiệm:
  - Breakhis-400x (B-400x): Gồm 1.820 ảnh vi thể mô bệnh học (histopathological) của 82 bệnh nhân ở độ phóng đại 400x, phân loại thành 2 nhóm: lành tính (Benign) và ác tính (Malignant)
  - BUSI: Gồm 1.578 ảnh siêu âm tuyến vú (ultrasound images) từ 600 bệnh nhân nữ, phân loại thành 3 nhóm: bình thường (Normal), lành tính (Benign), và ác tính (Malignant)
- Lý do bài báo sử dụng xAI cho bài báo này??
  - Model DL blackbox về lĩnh vực y tế -> Cần lý do để các bác sỹ xem xét và đưa ra quyết định, với độ tin cậy cao.
  - Bên cạnh kết quả dự đoán ung thư hay không ung thư thì việc chỉ ra vùng có dấu hiệu bệnh sẽ minh bạch, hỗ trợ bác sỹ chuẩn lâm sàng chính xác hơn để đưa ra phác đồ điều trị phù hợp. Nếu không có giải thích thì chắc chắn bác sỹ sẽ không thể sử dụng.
- Tại sao dùng Grad-CAM ??
  - Được đánh giá là tốt cho các mô hình CNN bằng việc tận dụng feature map lớp Conv cuối cùng.
  - Nhóm nghiên cứu đánh giá Grad-CAM đặc biệt hiệu quả trong việc định vị chính xác các khu vực không gian trên ảnh có sức ảnh hưởng lớn nhất đến quyết định phân loại của mô hình.
  - Nhờ sử dụng hàm kích hoạt ReLU trong thuật toán, Grad-CAM đảm bảo chỉ có các kích hoạt mang giá trị dương mới được giữ lại, từ đó giúp bản đồ nhiệt tập trung cao độ vào các vùng bệnh lý có liên quan thay vì lan man sang các vùng nhiễu.
  - Bản đồ nhiệt khá hiệu quả trong trường hợp ảnh y tế, hỗ trợ bác sỹ trong việc đối chiếu chéo kết quả và kinh nghiệm chuyên môn.
- Cách đọc kết quả heatmap:
  - Màu nóng (Đỏ và Vàng): Biểu thị các khu vực có mức độ ảnh hưởng cao nhất đến quyết định của mô hình (ví dụ: vị trí nghi ngờ là khối u)
  - Màu lạnh (Xanh dương): Biểu thị các vùng mô không ảnh hưởng đến việc phân loại
  - Vòng tròn đen: Được thuật toán tự động vẽ thêm (bán kính 20 pixel) bao quanh điểm có cường độ ảnh hưởng cao nhất, giúp khoanh vùng chính xác tâm điểm của bệnh lý
- xAI giúp phân tích lỗi sai của mô hình (Error Analysis)
  - Bên cạnh việc giải thích khi mô hình đoán đúng, xAI còn giúp phân tích lý do khi mô hình dự đoán sai. Ví dụ: Trong bài, có một trường hợp ảnh siêu âm mô tuyến vú là Bình thường (Normal), nhưng mô hình lại dự đoán sai thành Lành tính (Benign)
  - XAI chỉ ra nguyên nhân: Khi nhìn vào bản đồ nhiệt Grad-CAM của ca bệnh này, các nhà nghiên cứu phát hiện ra khu vực có màu đỏ rực (nơi AI chú ý nhất) lại trùng khớp với một dải/đường màu trắng nổi bật trên ảnh gốc. Đường màu trắng này thực chất chỉ là một nhiễu ảnh chứ không phải khối u, nhưng vì nó có hình thù giống đặc điểm của mô lành tính nên đã đánh lừa mô hình

- Paper có đánh giá xAI không??
  - Theo tìm hiểu thì paper không đánh giá Grad-CAM trên tập dataset, nhóm chỉ tập trung vào cải tiến độ chính xác dự đoán của model và dùng xAI như một phương pháp bổ sung nhằm cũng cố kết quả, nhưng đây là một thiếu sót của paper vì thiếu độ tin cậy. Nếu Grad-CAM highlight sai thì sao?

  - Hướng bổ sung: Tận dụng dataset có sẵn, nhóm đề xuất 2 phương pháp để đánh giá Grad-CAM.
    - Pointing Game kiểm tra tính phù hợp (Plausibility): dùng có dataset BUSI có ground truth sẵn
    - Deletion AUC kiểm tra tính đúng đắn, k nguỵ tạo kết quả (Faithfulness): Không cần annotation nên dùng cho cả BUSI và B-400x dataset

  - Tìm hiểu sâu hơn về Deletion AUC:
    + Tại sao chọn? 
    -> Nó kiểm tra được metric faithfulness, và phù hợp với dataset B-400x không có ground truth. Nó giải quyết câu hỏi: làm sao để biêt heatmap có phản ảnh đúng cơ chế của model không?
    -> Grad-CAM chỉ là một approximation — nó tính weighted sum của feature maps dựa trên gradient. Không đảm bảo rằng vùng được highlight là vùng model thực sự chú ý cao khi ra quyết định. Deletion AUC kiểm tra điều này một cách trực tiếp: nếu heatmap đúng, xóa những pixel được highlight phải làm confidence drop mạnh.
    + Phương pháp thực hiện: 
        + B1 — Rank pixel: Lấy heatmap Grad-CAM, sort toàn bộ pixel theo activation value từ cao xuống thấp. Pixel nào có activation cao = model cho là quan trọng nhất.
        + B2 — Iterative deletion: Lần lượt xóa 1%, 2%, ..., 100% pixel theo thứ tự đó. Sau mỗi lần xóa, cho ảnh đã chỉnh sửa vào model, ghi lại confidence của predicted class.
        + B3 — Tính AUC: Vẽ curve confidence vs. % pixel bị xóa, tính AUC. AUC thấp = explanation tốt, vì nếu heatmap đúng thì chỉ cần xóa một ít pixel quan trọng là confidence đã drop mạnh.
    + Xoá pixel xong thì thay nó bằng value gì???
        + Mean fill: mean của cả anh -> Đơn giản, nhanh, nhưng tạo ra các pixel quá khác biệt, xoá gần như hoàn toàn thông tin điểm ảnh -> Có thể thử
        + Blur fill: Dùng Gaussian filter làm mở -> Hơi phức tạp, nhưng nếu làm đúng thì kết quả đánh giá khách quan hơn. -> Có vẻ tốt hơn, nhưng thử sau Mean fill.

    + Nếu class predicted sai thì sao?
        + PP này chỉ ứng dụng để giải thích cho model khi dự đoán đúng. AUC trong TH này sẽ trả lời câu hỏi: model tin tưởng vào quyết định sai như thế nào?
    
    + Ý nghĩa kết quả mong muốn: Nếu DNBCD cho AUC thấp hơn T_Mobilenet và T_VGG19 trên cùng dataset -> kết luận explanation của DNBCD faithfulness hơn -> Vừa chính xác lại còn đáng tin cậy hơn.

    + Vấn đề chưa giải quyết được: 
        + TH dự đoán sai, cần giải thích được Tại sao model dự đoán sai.
        + Đề xuất method Counterfactual Analysis, ý tưởng là so sánh heatmap của predicted class sai với true class -> Phần mở rộng.