# 🎄 Cây Thông Noel 3D Tương Tác Sang Trọng

> Một ứng dụng web 3D cây thông Noel độ trung thực cao dựa trên **React**, **Three.js (R3F)** và **Nhận diện cử chỉ AI**.

Dự án này không chỉ là một cái cây, mà là một phòng trưng bày tương tác chứa đựng những ký ức. Hàng trăm nghìn hạt phát sáng, đèn màu rực rỡ và những tấm ảnh polaroid lơ lửng cùng nhau tạo nên một cây thông Noel lộng lẫy. Người dùng có thể điều khiển hình dạng cây (tập hợp/phân tán) và góc nhìn thông qua cử chỉ tay, trải nghiệm bữa tiệc hình ảnh đẳng cấp điện ảnh.

![Project Preview](public/preview.png)
*(Lưu ý: Nên tải lên một ảnh chụp màn hình khi chạy dự án)*

## ✨ Tính Năng Chính

* **Trải nghiệm hình ảnh tuyệt vời**: Thân cây được tạo từ hơn 45,000 hạt phát sáng, kết hợp với hiệu ứng Bloom và ánh sáng động, tạo nên bầu không khí mơ màng.
* **Phòng trưng bày ký ức**: Ảnh lơ lửng trên cây theo phong cách "polaroid", mỗi tấm đều là một nguồn sáng riêng biệt, hỗ trợ render hai mặt.
* **Điều khiển cử chỉ AI**: Không cần chuột, chỉ cần dùng camera thu nhận cử chỉ để điều khiển hình dạng cây (tập hợp/phân tán) và xoay góc nhìn.
* **Chi tiết phong phú**: Bao gồm đèn màu nhấp nháy động, tuyết vàng bạc rơi, cùng hộp quà và kẹo Giáng sinh phân bố ngẫu nhiên.
* **Tùy chỉnh cao**: **Hỗ trợ người dùng dễ dàng thay thế bằng ảnh của riêng mình và tự do điều chỉnh số lượng ảnh.**

## 🛠️ Công Nghệ Sử Dụng

* **Framework**: React 18, Vite
* **Engine 3D**: React Three Fiber (Three.js)
* **Thư viện công cụ**: @react-three/drei, Maath
* **Hậu xử lý**: @react-three/postprocessing
* **AI Vision**: MediaPipe Tasks Vision (Google)

## 🚀 Bắt Đầu Nhanh

### 1. Chuẩn bị môi trường
Đảm bảo máy tính của bạn đã cài đặt [Node.js](https://nodejs.org/) (khuyến nghị v18 trở lên).

### 2. Cài đặt dependencies
Mở terminal tại thư mục gốc của dự án, chạy:

```bash
npm install
```

### 3. Khởi chạy dự án

```bash
npm run dev
```

## 🖼️ Tùy Chỉnh Ảnh

### 1. Chuẩn bị ảnh
Tìm thư mục `public/photos/` trong thư mục dự án.

- **Ảnh lớn trên đỉnh/Ảnh bìa**: Đặt tên là `top.jpg` (sẽ hiển thị trên ngôi sao 3D ở đỉnh cây).
- **Ảnh trên thân cây**: Đặt tên lần lượt là `1.jpg`, `2.jpg`, `3.jpg`... 

> 💡 **Khuyến nghị**: Sử dụng ảnh vuông hoặc tỷ lệ 4:3, kích thước file không nên quá lớn (khuyến nghị dưới 500kb mỗi ảnh để đảm bảo mượt mà)

### 2. Thay thế ảnh
Chỉ cần copy ảnh của bạn vào thư mục `public/photos/`, ghi đè lên các ảnh gốc. Hãy giữ nguyên định dạng tên file (`1.jpg`, `2.jpg`, v.v.).

### 3. Thay đổi số lượng ảnh (thêm hoặc bớt)
Nếu bạn đặt nhiều ảnh hơn (ví dụ từ 31 ảnh mặc định tăng lên 100 ảnh), cần sửa code để thông báo cho chương trình tải chúng.

Mở file: `src/App.tsx`

Tìm dòng code khoảng **dòng 19**:

```typescript
// --- Tự động tạo danh sách ảnh (top.jpg + 1.jpg đến 31.jpg) ---
const TOTAL_NUMBERED_PHOTOS = 31; // <--- Sửa số này!
```

## 🖐️ Hướng Dẫn Điều Khiển Cử Chỉ

Dự án này tích hợp hệ thống nhận diện cử chỉ AI, hãy đứng trước camera để thao tác (có nút DEBUG ở góc dưới bên phải màn hình để xem hình ảnh camera):

| Cử chỉ | Hành động | Mô tả |
|--------|-----------|-------|
| 🖐 Xòe bàn tay (Open Palm) | Phân tán (Disperse) | Cây thông nổ tung thành các hạt và ảnh bay khắp nơi |
| ✊ Nắm chặt tay (Closed Fist) | Tập hợp (Assemble) | Tất cả các thành phần ngay lập tức tập hợp thành cây thông hoàn hảo |
| 👋 Di chuyển tay trái/phải | Xoay góc nhìn | Tay di sang trái, cây quay trái; tay di sang phải, cây quay phải |
| 👋 Di chuyển tay lên/xuống | Góc nhìn nghiêng | Tay di lên, góc nhìn nâng cao; tay di xuống, góc nhìn hạ thấp |

## ⚙️ Cấu Hình Nâng Cao

Nếu bạn quen thuộc với code, có thể điều chỉnh thêm các thông số hình ảnh trong object `CONFIG` ở file `src/App.tsx`:

```typescript
const CONFIG = {
  colors: { ... }, // Thay đổi màu cây, đèn, viền
  counts: {
    foliage: 15000,   // Thay đổi số lượng hạt lá cây (cấu hình thấp có thể bị lag)
    ornaments: 300,   // Thay đổi số lượng ảnh/polaroid treo
    lights: 400       // Thay đổi số lượng đèn màu
  },
  tree: { height: 22, radius: 9 }, // Thay đổi kích thước cây
  // ...
};
```

## 📄 Giấy Phép

MIT License. Thoải mái sử dụng và chỉnh sửa cho những dịp lễ của riêng bạn!

## 🎄✨ Chúc Mừng Giáng Sinh!
