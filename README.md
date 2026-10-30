# SESSION15 – HYBRID WORKFLOW & CLOUD SYNC
## 1. Thiết kế mô hình Hybrid Workflow
Kết hợp SSD Local và OneDrive Cloud:
- SSD Local: Chạy dự án, chỉnh sửa code với tốc độ cao.
- OneDrive: Tự động đồng bộ và bảo vệ source code.
- Files On-Demand: Chỉ tải file về máy khi cần, tiết kiệm dung lượng ổ cứng.
## 2. Phân tích luồng dữ liệu (I/O)
Quá trình từ khi nhấn Ctrl + S đến khi xuất hiện tích xanh:
1. Ctrl + S: Lưu code vào SSD Local.
2. OneDrive phát hiện: Nhận diện file vừa thay đổi.
3. Đồng bộ: Tải nội dung file lên Cloud.
4. Hoàn tất: OneDrive hiển thị dấu tích xanh, báo file đã đồng bộ thành công.
# 3. Xử lý bẫy dữ liệu Node_modules
- Không đồng bộ thư mục node_modules vì chứa hàng nghìn file thư viện, gây tốn dung lượng và làm chậm quá trình Sync.
- Sử dụng .gitignore để loại trừ node_modules khỏi GitHub.
- Chỉ đồng bộ source code, file cấu hình và tài liệu cần thiết lên Cloud.
- Khi cần cài lại thư viện, sử dụng:
npm install


Lưu ý: .gitignore chỉ loại trừ file khỏi Git, không tự động loại trừ khỏi OneDrive. Cần đặt thư mục dự án ngoài vùng OneDrive hoặc cấu hình đồng bộ phù hợp để tránh tải node_modules lên Cloud.
## 4. Sơ đồ tổ chức thư mục Cloud
```OneDrive/
└── SmartFood/
    │
    ├── Code/
    │   ├── src/
    │   ├── public/
    │   ├── package.json
    │   └── .gitignore
    │
    ├── Docs/
    │   ├── README.md
    │   └── Documentation.docx
    │
    └── Assets/
        ├── Images/
        ├── Videos/
        └── Icons/
```


5. Sử dụng Files On-Demand
- Chọn Free up space để chuyển file sang trạng thái chỉ lưu trên Cloud.
- Khi mở file, OneDrive tự tải file về máy.
- Chọn Always keep on this device nếu muốn giữ file trên máy để sử dụng ngoại tuyến.
Kết luận: Hybrid Workflow giúp lập trình viên tận dụng tốc độ SSD Local, bảo vệ source code trên Cloud và tiết kiệm dung lượng nhờ Files On-Demand.
