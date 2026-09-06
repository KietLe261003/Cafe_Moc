Tôi cần bạn triển khai module "Học Từ Vựng" cho ứng dụng học tiếng Anh AuraSyncEnglish. 
Dự án đã setup sẵn (monorepo Next.js frontend + NestJS backend). Chỉ cần code feature này, 
cài thêm thư viện nếu cần thiết và giải thích lý do chọn.

## BỐI CẢNH DỰ ÁN
- Monorepo: Next.js (frontend) + NestJS (backend)
- Hãy tự kiểm tra cấu trúc thư mục hiện tại, package manager (npm/pnpm/yarn), 
  database/ORM đang dùng (Prisma/TypeORM...) trước khi code, để code khớp convention có sẵn.
- Nếu thiếu thông tin quan trọng (vd: chưa rõ dùng ORM nào), hãy hỏi tôi trước khi code.

## MỤC TIÊU MODULE
Module giúp người dùng học và ghi nhớ từ vựng tiếng Anh lâu dài thông qua flashcard, 
ôn tập ngắt quãng (spaced repetition), quiz và theo dõi tiến độ.

## TÍNH NĂNG CẦN CÓ

### 1. Quản lý từ vựng
- CRUD từ vựng (admin): từ, nghĩa, phiên âm (IPA), audio phát âm, hình ảnh minh họa, 
  ví dụ câu, từ đồng nghĩa/trái nghĩa, chủ đề (topic), cấp độ (level: beginner/intermediate/advanced)
- Phân loại theo chủ đề và cấp độ, hỗ trợ filter/search

### 2. Flashcard học từ mới
- Hiển thị flashcard 2 mặt (từ + nghĩa/hình ảnh/ví dụ), swipe hoặc click để lật
- Đánh dấu "đã biết" / "chưa biết" / "cần ôn thêm" sau mỗi thẻ
- Phát âm bằng audio (text-to-speech nếu chưa có file audio sẵn)

### 3. Ôn tập bằng Spaced Repetition (SRS)
- Áp dụng thuật toán SM-2 (SuperMemo 2) hoặc tương tự để tính lịch ôn tập tiếp theo 
  dựa trên độ khó người dùng tự đánh giá (again/hard/good/easy)
- Lưu trạng thái ghi nhớ từng từ theo từng user: easeFactor, interval, repetitions, nextReviewDate
- Endpoint trả về danh sách từ "đến hạn ôn tập hôm nay"

### 4. Quiz / Mini-game ôn tập
- Trắc nghiệm chọn nghĩa đúng
- Điền từ vào chỗ trống
- Nối từ với nghĩa (matching)
- Nghe audio và chọn từ đúng
- Chấm điểm, lưu kết quả để cập nhật SRS

### 5. Từ vựng cá nhân (My Wordlist)
- Người dùng lưu từ vào danh sách riêng để ôn tập tùy chỉnh
- Xem/xóa từ trong danh sách cá nhân

### 6. Theo dõi tiến độ
- Số từ đã học, tỷ lệ nhớ (%), streak học tập theo ngày
- Biểu đồ tiến độ theo tuần/tháng

## YÊU CẦU KỸ THUẬT
- Backend (NestJS): thiết kế module riêng (VocabularyModule), tách rõ Controller/Service/DTO, 
  validate input bằng class-validator, viết entity/schema phù hợp ORM hiện có
- Frontend (Next.js): component tái sử dụng được, quản lý state hợp lý (React Query/SWR nếu phù hợp 
  với pattern đã dùng trong dự án), UI responsive
- Nếu cần cài thư viện mới (vd: thư viện SRS, text-to-speech, chart), liệt kê rõ tên và lý do trước khi cài
- Viết API theo REST, có Swagger doc nếu dự án đã dùng Swagger
- Đảm bảo có xử lý lỗi, loading state, empty state ở frontend


Hãy làm từng phần một, không dồn hết vào 1 lần code — bắt đầu từ backend (entity + API) 
trước, sau đó mới tới frontend.