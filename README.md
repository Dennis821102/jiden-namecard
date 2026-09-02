# 傑登隔熱紙 電子名片（LIFF）

黃偉哲｜傑登汽車大樓隔熱紙 的 LINE 電子名片。點「分享我的電子名片」會叫出 LINE 的分享清單，
送出一則 3 張卡片的 Flex Message（個人名片／品牌服務／門市社群），每張卡片底下都是可點的按鈕。

與 `king-namecard`（依燃軟體）完全獨立，兩者不共用 repo、不共用 LIFF ID。

## 檔案

| 檔案 | 用途 |
|---|---|
| `index.html` | 名片頁 + Flex Message 定義 + LIFF 分享邏輯，全部在這一支 |
| `img/logo.png` | 傑登 logo（黑底金字），用在頁首與第一張卡片 |
| `img/hero-work.jpg` | 施工照，第二張卡片主視覺 |
| `img/hero-building.jpg` | 大樓玻璃，第三張卡片主視覺 |

## 上線三步驟

### 1. 推上 GitHub 並開 Pages

```bash
cd ~/Desktop/jiden-namecard
git remote add origin git@github.com:Dennis821102/jiden-namecard.git
git push -u origin main
```

到 repo 的 Settings → Pages → Source 選 `main` / `root`，
網址會是 `https://dennis821102.github.io/jiden-namecard/`。

> Flex Message 的圖片一定要是 https 絕對網址，所以 Pages 沒開起來之前，
> 卡片上的圖會是空的。網址若不同，改 `index.html` 的 `const BASE` 那一行即可。

### 2. 建立 LIFF App

LINE Developers → 選一個 LINE Login channel → LIFF → Add：

| 欄位 | 值 |
|---|---|
| Endpoint URL | `https://dennis821102.github.io/jiden-namecard/` |
| Size | Full |
| Scope | `profile`、`chat_message.write` |
| Share target picker | **開啟** |

一個 channel 最多可以建 30 支 LIFF App，所以不必為了這張名片另開帳號，
但登入同意畫面會顯示該 channel 的名稱——要以傑登的名義出現，就用傑登自己的 channel 建。

### 3. 填 LIFF ID

把拿到的 ID 填進 `index.html`：

```js
const LIFF_ID = 'YOUR_LIFF_ID';   // ← 換成實際的 LIFF ID
```

推上去就完成，分享網址是 `https://liff.line.me/{LIFF_ID}`。

## 待補資料

- 人像照片：目前第一張卡片用「黃」字金框頭像頂著，拿到照片後
  放進 `img/portrait.jpg`，把 `index.html` 的 `<div id="portrait">黃</div>`
  換成 `<img src="img/portrait.jpg" alt="黃偉哲">`，Flex 第一張也可加 hero 圖。
- 職稱：現在只寫公司名，確認是負責人／店長／業務經理再補。
- 英文名：若有（像 Oliver 那樣）可加在姓名下方。

## 資料來源

電話、地址、官網、粉專、LINE ID 取自傑登官網 <https://www.jiden.com.tw/> 與
Google 商家頁；TikTok 由本人提供。
