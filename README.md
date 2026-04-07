Markdown

\# ⚔️ JBV Warriors – Vòng 4: Thực chiến



Chào mừng chiến binh! Vòng này \*\*không có điểm thưởng\*\*.  

\*\*Qua vòng\*\* = Bạn đủ năng lực nhận task kiếm tiền thật.  

\*\*Không qua\*\* = Quay lại rèn luyện thêm.



\---



\## 📌 Task của bạn



Viết chương trình console C# (.NET 6/8) thực hiện:



\- \*\*Đọc file\*\* `input.json` (nằm trong cùng thư mục với file `.exe`).

\- \*\*Nội dung file:\*\* Là mảng số nguyên, ví dụ: `\[5, 2, 8, 2, 1, 9, 5]`.

\- \*\*Xuất ra file\*\* `output.json`: Mảng đã \*\*sắp xếp tăng dần\*\* và \*\*loại bỏ số trùng lặp\*\*.



\*\*Kết quả mong đợi:\*\* `\[1, 2, 5, 8, 9]`



> \[!CAUTION]

> \*\*Không dùng `Console.ReadLine()`\*\*. Hệ thống CI/CD sẽ bị treo và không thể chấm điểm.



\---



\## 🚀 Hướng dẫn từng bước



\### 1. Fork repo về tài khoản của bạn

Truy cập \[esondinh/Warrior](https://github.com/esondinh/Warrior) → Bấm nút \*\*Fork\*\* (góc trên bên phải).



\### 2. Clone repo vừa fork về máy

Mở terminal và chạy lệnh:

```bash

git clone \[https://github.com/TEN\_NGUOI\_DUNG\_CUA\_BAN/Warrior.git](https://github.com/TEN\_NGUOI\_DUNG\_CUA\_BAN/Warrior.git)

cd Warrior

3\. Tạo branch mới để codeBashgit checkout -b feature/giai-phap-cua-ban

4\. Mở projectVisual Studio: Mở file Warrior.sln.VS Code: Gõ code . tại thư mục dự án.5. Code solutionThư mục chính: src/WarriorTask/. File cần sửa: Program.cs.Gợi ý code mẫu:C#using System.Text.Json;



string inputPath = "input.json";

string outputPath = "output.json";



if (File.Exists(inputPath))

{

&#x20;   string jsonString = File.ReadAllText(inputPath);

&#x20;   var numbers = JsonSerializer.Deserialize<int\[]>(jsonString);



&#x20;   if (numbers != null)

&#x20;   {

&#x20;       // Lọc trùng \& Sắp xếp tăng dần

&#x20;       var result = numbers.Distinct().OrderBy(x => x).ToArray();

&#x20;       

&#x20;       string outputJson = JsonSerializer.Serialize(result);

&#x20;       File.WriteAllText(outputPath, outputJson);

&#x20;   }

}



Console.WriteLine("Done!");

6\. Chạy thửBashdotnet run --project src/WarriorTask

Kiểm tra file output.json phát sinh để xác nhận kết quả.7. Commit và PushBashgit add .

git commit -m "Hoàn thành task vòng 4"

git push origin feature/giai-phap-cua-ban

8\. Tạo Pull Request (PR)Vào GitHub của bạn -> Contribute -> Open Pull Request.Kiểm tra đúng: base: esondinh/Warrior <- head: tài khoản của bạn.✅ Điều kiện PASSCode chạy đúng logic (Unique + Sort).Build thành công trên hệ thống tự động.Tuyệt đối không dùng Console.ReadLine().❌ Lỗi thường gặpLỗiNguyên nhânCách sửadotnet command not foundChưa cài .NET SDKTải tại dotnet.microsoft.comKhông thấy input.jsonSai thư mục thực thiĐảm bảo file nằm cùng cấp với file .exe khi chạyCI/CD báo đỏLỗi môi trường LinuxKiểm tra chữ hoa/thường của tên file (input.json khác Input.json)

