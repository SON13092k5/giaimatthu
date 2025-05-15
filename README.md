<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Giải Mật Thư - Chạy Tất Cả Trường Hợp A=*</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 40px;
      background-color: #f0f2f5;
    }
    h1 {
      text-align: center;
      color: #333;
    }
    textarea, input {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      font-size: 16px;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      margin-top: 15px;
      cursor: pointer;
    }
    .result {
      background-color: #fff;
      border: 1px solid #ccc;
      padding: 15px;
      margin-top: 20px;
      font-size: 18px;
      white-space: pre-wrap;
    }
    .result-entry {
      margin-bottom: 10px;
      padding: 8px;
      background: #eef;
      border-left: 5px solid #88f;
    }
  </style>
</head>
<body>
  <h1>🔐 Giải Mật Thư - Thử Tất Cả Trường Hợp A=*</h1>

  <label>Mật thư gốc:</label>
  <textarea id="inputText" rows="4" placeholder="Nhập đoạn văn bản mã hóa..."></textarea>

  <button onclick="tryAllSubstitutions()">🚀 Chạy tất cả trường hợp A=*</button>
  <button onclick="resetForm()">🧹 Xóa hết</button>

  <div class="result" id="output"></div>

  <script>
    function tryAllSubstitutions() {
      const input = document.getElementById('inputText').value.toUpperCase();
      const original = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
      let outputHTML = "";

      for (let shift = 0; shift < 26; shift++) {
        let substitution = "";
        for (let i = 0; i < 26; i++) {
          substitution += original[(shift + i) % 26];
        }

        let result = '';
        for (let i = 0; i < input.length; i++) {
          const char = input[i];
          const index = substitution.indexOf(char);
          if (index !== -1) {
            result += original[index];
          } else {
            result += char;
          }
        }

        outputHTML += `<div class="result-entry"><strong>A=${substitution[0]}</strong>: ${result}</div>`;
      }

      document.getElementById('output').innerHTML = outputHTML;
    }

    function resetForm() {
      document.getElementById('inputText').value = '';
      document.getElementById('output').innerHTML = '';
    }
  </script>
</body>
</html>

