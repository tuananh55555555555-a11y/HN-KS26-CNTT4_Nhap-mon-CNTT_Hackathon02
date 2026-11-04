# BÀI LÀM – HACKATHON 02

- **Mã đề:** 02
- **Họ tên: Trần Tuấn Anh**
- **Lớp:CNTT4**
- **Link repository:**
- **Hệ điều hành (Windows/macOS):Windows**

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
pwd
ls
Move-Item .\huong_dan_van_hanh.txt .\docs\
mkdir backup
Copy-Item .\data\luot_gui_xe_thang_2.xlsx .\backup\
rm .\temp_202.tmp
cd .\logs\
ls
cd ..
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
    Directory: D:\starter-kit\bai_xe_website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         11/4/2026   7:47 AM                backup
d-----         11/4/2026   7:44 AM                data
d-----         11/4/2026   7:47 AM                docs
d-----         11/4/2026   7:43 AM                evidence
d-----         11/4/2026   7:44 AM                logs
d-----         11/4/2026   7:33 AM                web
-a----         11/4/2026   7:45 AM           2414 bai_lam.md


```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
Get-Content .\logs\gate.log | Select-String "status=500" >> .\logs\loi_500.txt.

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
2026-02-28 08:08:39 POST /api/cho-trong status=500
2026-02-28 08:23:23 POST /api/cho-trong status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(Get-Content .\logs\gate.log | Select-String "status=404").count
```

```text
4
```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
notepad tong_hop.ps1
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
# Script: tong_hop.ps1
# Tac gia: Tran Tuan Anh
# Ngay tao: 11/04/2026
Write-Host "Dang tao bao cao ... '
" === BAO CAO SU CO WEBSITE === " > logs/tong_hop.txt
Get-Content logs\gate.log | Select-String "status=404" >> logs/tong_hop.txt
Get-Content logs\gate.log | Select-String "status=500" | Measure-Object >>
logs/tong_hop.txt
Write-Host "Hoan thanh!"
.\tong_hop.ps1
Get-Content .\logs\tong_hop.txt
```

### Nội dung file logs/tong_hop.txt

```text
Dang tao bao cao...
Hoan thanh!
=== BAO CAO SU CO WEBSITE ===

2026-02-28 08:12:50 GET /tin-tuc status=404
2026-02-28 08:31:56 GET /images/so-do-bai.jpg status=404
2026-02-28 08:36:18 GET /images/so-do-bai.jpg status=404
2026-02-28 08:47:02 GET /tin-tuc status=404




Count    : 6
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [X] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [X] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | Network |images/logo.jpg| sửa thành images/logo-parkeasy.png |
| 2 | Console | Uncaught ReferenceError: hienThiGiaGui is not defined | sửa hienThiGiaGui thành hienThiBangGiaGui |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context: Một trang wed ParkEasy - Bãi giữ xe thông
  minh logo không
  hiển thị và bảng giá không có dữ liệu.** 
- **Expected: Trang wed chạy không hiển thị lỗi logo và hiển thị bảng giá** 
- **Actual: Lỗi logo và bảng giá không có dữ liệu** 
- **Log: Uncaught ReferenceError: hienThiGiaGui is not defined**

### Câu tìm kiếm Google

```text
site:stackoverflow.com "Uncaught ReferenceError: hienThiGiaGui is not defined"
```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/luot_gui_xe_thang_2.xlsx`, không cần ghi vào đây.
