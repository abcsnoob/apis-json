
# APIS-JSON
Nơi cung cấp các file JSON luôn luôn chất lượng để sử dụng cho kiểm duyệt và quản lý dữ liệu.
Bạn có thể fork về và edit sao cho hợp lí rồi liên hệ với mình qua [abcsspprt@gmail.com](mailto:abcsspprt@gmail.com) hoặc là [+84 772554682](tel:+84772554682). Đừng liên hệ vào số này trừ khi cần ngay!
## Các API khả dụng

1. **Kiểm duyệt từ chung**  
   URL: [bad-words.json](https://raw.githubusercontent.com/abcsnoob/apis-json/refs/heads/main/bad-words.json)  
   - Dành cho việc kiểm duyệt từ ngữ phổ biến trên nhiều nền tảng (Facebook, Discord, TikTok, Instagram,…).

2. **Kiểm duyệt từ dành riêng cho Roblox**  
   URL: [badword-roblox.json](https://raw.githubusercontent.com/abcsnoob/apis-json/refs/heads/main/badword-roblox.json)  
   - Tối ưu cho bộ lọc Roblox, bao gồm từ ngữ tục tĩu, vi phạm chính sách, và nội dung không phù hợp trẻ em.

---

## Hướng dẫn sử dụng JSON kiểm duyệt từ

### 1. JavaScript (Node.js)

```js
import fetch from "node-fetch";

async function loadBadWords(url) {
    const res = await fetch(url);
    const data = await res.json();
    return data.map(item => item.word.toLowerCase());
}

async function checkText(text, url) {
    const badWords = await loadBadWords(url);
    const found = badWords.filter(word => text.toLowerCase().includes(word));
    if (found.length > 0) {
        console.log("Phát hiện từ cấm:", found);
    } else {
        console.log("Không có từ cấm nào");
    }
}

// Ví dụ sử dụng
const textToCheck = "This is a fuck example";
const url = "https://raw.githubusercontent.com/abcsnoob/apis-json/refs/heads/main/bad-words.json";
checkText(textToCheck, url);
````

---

### 2. JavaScript (Browser)

```html
<script>
async function loadBadWords(url) {
    const res = await fetch(url);
    const data = await res.json();
    return data.map(item => item.word.toLowerCase());
}

async function checkText(text, url) {
    const badWords = await loadBadWords(url);
    const found = badWords.filter(word => text.toLowerCase().includes(word));
    if (found.length > 0) {
        console.log("Phát hiện từ cấm:", found);
    } else {
        console.log("Không có từ cấm nào");
    }
}

// Ví dụ sử dụng
checkText("This is a fuck example", "https://raw.githubusercontent.com/abcsnoob/apis-json/refs/heads/main/bad-words.json");
</script>
```

---

### 3. Python

```python
import requests

def load_bad_words(url):
    res = requests.get(url)
    data = res.json()
    return [item["word"].lower() for item in data]

def check_text(text, url):
    bad_words = load_bad_words(url)
    text_lower = text.lower()
    found = [word for word in bad_words if word in text_lower]
    if found:
        print("Phát hiện từ cấm:", found)
    else:
        print("Không có từ cấm nào")

# Ví dụ sử dụng
text_to_check = "This is a fuck example"
url = "https://raw.githubusercontent.com/abcsnoob/apis-json/refs/heads/main/bad-words.json"
check_text(text_to_check, url)
```

