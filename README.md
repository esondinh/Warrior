⚔️ JBV Warriors – Vòng 4: Thực chiến

Chào mừng chiến binh! Vòng này không có điểm thưởng.

Qua vòng = Bạn đủ năng lực nhận task kiếm tiền thật.
Không qua = Quay lại rèn luyện thêm.

📌 Task của bạn

Viết chương trình console C# (.NET 6/8) thực hiện:

Đọc file input.json (nằm trong cùng thư mục với file .exe)
Nội dung file: Là mảng số nguyên, ví dụ: [5, 2, 8, 2, 1, 9, 5]
Xuất ra file output.json: Mảng đã sắp xếp tăng dần và loại bỏ số trùng lặp

Kết quả mong đợi: [1, 2, 5, 8, 9]

[!CAUTION]
Không dùng Console.ReadLine(). Hệ thống CI/CD sẽ bị treo và không thể chấm điểm.

🚀 Hướng dẫn từng bước
1. Fork repo về tài khoản của bạn

Truy cập: https://github.com/esondinh/Warrior

→ Bấm nút Fork (góc trên bên phải)

2. Clone repo vừa fork về máy
git clone https://github.com/TEN_NGUOI_DUNG_CUA_BAN/Warrior.git
cd Warrior
3. Tạo branch mới để code
git checkout -b feature/giai-phap-cua-ban
4. Mở project
Visual Studio: Mở file Warrior.sln
VS Code:
code .
5. Code solution
Thư mục chính: src/WarriorTask/
File cần sửa: Program.cs

Gợi ý code mẫu:

using System.Text.Json;

string inputPath = "input.json";
string outputPath = "output.json";

if (File.Exists(inputPath))
{
    string jsonString = File.ReadAllText(inputPath);
    var numbers = JsonSerializer.Deserialize<int[]>(jsonString);

    if (numbers != null)
    {
        // Lọc trùng & Sắp xếp tăng dần
        var result = numbers.Distinct().OrderBy(x => x).ToArray();

        string outputJson = JsonSerializer.Serialize(result);
        File.WriteAllText(outputPath, outputJson);
    }
}

Console.WriteLine("Done!");
6. Chạy thử
dotnet run --project src/WarriorTask

👉 Kiểm tra file output.json để xác nhận kết quả

7. Commit và Push
git add .
git commit -m "Hoàn thành task vòng 4"
git push origin feature/giai-phap-cua-ban
8. Tạo Pull Request (PR)
Vào GitHub repo của bạn
Chọn Contribute → Open Pull Request
Kiểm tra đúng:
base: esondinh/Warrior
head: tài khoản của bạn
✅ Điều kiện PASS
Code chạy đúng logic (Unique + Sort)
Build thành công trên hệ thống tự động
Tuyệt đối không dùng Console.ReadLine()
❌ Lỗi thường gặp
Lỗi	Nguyên nhân	Cách sửa
dotnet command not found	Chưa cài .NET SDK	Tải tại https://dotnet.microsoft.com

Không thấy input.json	Sai thư mục thực thi	Đảm bảo file nằm cùng cấp với .exe
CI/CD báo đỏ	Lỗi môi trường Linux	Kiểm tra chữ hoa/thường (input.json ≠ Input.json)