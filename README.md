# 中文睡前故事生成器 (Chinese Bedtime Story Generator)

一個使用Google Gemini API生成個性化中文睡前故事的應用程序。

## 功能特點

- 🎯 個性化故事生成（根據年齡、性別、興趣等）
- 🇨🇳 繁體中文故事內容
- 📖 包含拼音和注音輔助
- 🎨 現代化UI設計
- 🔧 多種API調用方法以解決CORS問題

## 快速開始

### 方法1：直接使用（推薦Firefox瀏覽器）

1. 啟動HTTP服務器：
   ```bash
   python -m http.server 8000
   ```

2. 在瀏覽器中打開：
   ```
   http://localhost:8000/bedtime-story-app.html
   ```

3. 輸入您的Google Gemini API金鑰

### 方法2：使用本地代理服務器（解決CORS問題）

1. 安裝Node.js依賴：
   ```bash
   npm install
   ```

2. 啟動代理服務器：
   ```bash
   npm start
   ```
   或
   ```bash
   node proxy-server.js
   ```

3. 在另一個終端啟動HTTP服務器：
   ```bash
   python -m http.server 8000
   ```

4. 在瀏覽器中打開：
   ```
   http://localhost:8000/bedtime-story-app.html
   ```

## API金鑰獲取

1. 訪問 [Google AI Studio](https://aistudio.google.com/app/apikey)
2. 登錄您的Google帳戶
3. 點擊「Create API Key」
4. 選擇或創建一個Google Cloud項目
5. 複製生成的API金鑰
6. 確保API金鑰有足夠的配額並啟用Gemini API服務

## 故障排除

### CORS錯誤解決方案

如果遇到CORS錯誤，請嘗試以下方法：

#### 方法1：瀏覽器設置
- 安裝CORS瀏覽器擴展（Chrome: CORS Unblock）
- 使用Firefox瀏覽器（CORS限制較少）
- 禁用瀏覽器安全模式（僅限開發）

#### 方法2：本地代理服務器
- 運行本地代理服務器（見上方說明）
- 代理服務器會在 `http://localhost:3001` 運行

#### 方法3：檢查API設置
- 確認API金鑰有效且有足夠配額
- 檢查Google Cloud項目設置
- 確保Gemini API服務已啟用

### 常見問題

**Q: API調用失敗怎麼辦？**
A: 應用程序會自動嘗試三種不同的API調用方法：
1. 直接API調用
2. 使用公共CORS代理
3. 使用本地代理服務器

**Q: 故事生成很慢？**
A: 這是正常的，AI生成需要一些時間。請耐心等待。

**Q: 生成的故事格式不正確？**
A: 檢查控制台日誌，可能是API響應格式問題。

## 技術架構

- **前端**: React (通過CDN)
- **樣式**: Tailwind CSS
- **API**: Google Gemini 1.5 Flash
- **代理服務器**: Node.js + Express

## 文件結構

```
├── bedtime-story-app.html    # 主應用程序
├── proxy-server.js           # 本地代理服務器
├── package.json             # Node.js依賴配置
└── README.md               # 說明文檔
```

## 開發說明

應用程序使用多層錯誤處理和API調用策略：

1. **直接API調用**: 嘗試直接調用Google Gemini API
2. **公共代理**: 如果直接調用失敗，使用公共CORS代理
3. **本地代理**: 如果公共代理也失敗，嘗試本地代理服務器

這種設計確保了最大的兼容性和可靠性。