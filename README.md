# 0415

[社群網路爬蟲工作坊 講義資料](https://drive.google.com/drive/folders/1Rpre8mqEX55tO6mSovindJQ3_l9pmzz4?usp=sharing)

### 安裝 Python
- [Python 3.14.4 下載](https://www.python.org/downloads/)

### 安裝 VSCode
- [下載 Visual Studio Code](https://vscode.com.tw/download)
### VSCode 套件列表
- Python
- Codex
- Live Server

---
補充資源
- [Trafilatura: Discover and Extract Text Data on the Web](https://github.com/adbar/trafilatura?tab=readme-ov-file)

# Python 爬蟲最合適搭配的套件列表

基於網路來源的研究，以下是 **Python 爬蟲** 最常用且合適的套件組合。我挑選了五個熱門套件（**Requests**、**BeautifulSoup**、**Scrapy**、**Selenium** 和 **Playwright**），適合從簡單靜態頁面到複雜動態網站。每個套件會簡單說明**優點**和**缺點**，就像對完全新手解釋一樣。這些套件常互相搭配，例如用 **Requests** 抓網頁，再用 **BeautifulSoup** 解析。[^1][^2][^3]

## 1. 常用套件優缺點表格

| 套件名稱 | 主要功能 | **優點** | **缺點** | **適合情境** |
| :-- | :-- | :-- | :-- | :-- |
| **Requests** | 發送 HTTP 請求抓網頁 | 超簡單上手、速度快、支援 cookies/headers | 無法處理 **JavaScript** 動態內容、無解析功能需搭配其他 | 新手抓靜態頁面或 **API** |
| **BeautifulSoup** | 解析 **HTML/XML** | 容易學、處理不完美 HTML、快速找標籤/文字 | 解析慢、不抓網頁、不處理 **JS** | 從靜態 HTML 提取資料如標題/連結 |
| **Scrapy** | 完整爬蟲框架 | 速度極快（多執行緒）、內建去重/儲存、適合大規模 | 學習曲線陡、小任務麻煩 | 大量爬取如電商商品清單 |
| **Selenium** | 模擬瀏覽器操作 | 執行 **JS**、點擊/填表單、多瀏覽器支援 | 速度慢、吃資源、易被偵測為機器人 | 需要登入或 **JS** 載入的網站 |
| **Playwright** | 現代瀏覽器自動化 | 速度快、穩定、自動等元素、多瀏覽器/網路攔截 | 仍吃資源、學習需時間 | 複雜 **SPA**（單頁應用）網站 |

## 2. Trafilatura 的搭配性

**是的，Trafilatura 非常適合搭配以上套件！**

- **功能**：專門提取網頁主要文字內容（如文章主體），保留格式，輸出 **TXT** 或 **XML**，避免雜訊。
- **常見搭配**：
    - **Requests + Trafilatura**：抓網頁後直接提取乾淨文字。
    - **Scrapy/Selenium/Playwright**：後處理抓到的內容。
- **優點**：特別適合新聞、部落格爬取，簡單高效。[^4][^5]

**範例程式碼**（新手版）：

```python
import requests
from trafilatura import fetch_url, extract

url = 'https://example.com'
downloaded = fetch_url(url)  # 內建抓取
text = extract(downloaded)   # 提取主文字
print(text)
```

## 關鍵要點

- **新手黃金組合**：**Requests + BeautifulSoup**（靜態頁）。[^2]
- **大規模專用**：**Scrapy**。[^6]
- **動態頁首選**：**Selenium** 或 **Playwright**。[^3]
- **文字提取神器**：加 **Trafilatura** 提升品質。[^4]

希望這個 **Markdown** 表格清楚易懂，對你的研究有幫助！有其他問題歡迎再問哦！[^1][^2]

[^1]: https://thunderbit.com/zh-Hant/blog/top-python-web-scraping-libraries
[^2]: https://www.capsolver.com/blog/web-scraping/best-python-web-scraping-libraries
[^3]: https://www.learncodewithmike.com/2020/11/beautifulsoup-vs-selenium-vs-scrapy-for-python-web-scraping.html
[^4]: https://github.com/LukasBBAW/trafilatura-1
[^5]: https://webscraping.fyi/lib/python/trafilatura/
[^6]: https://thunderbit.com/zh-Hant/blog/python-web-crawler-explained
