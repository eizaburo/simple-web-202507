# Simple Web

### API（GAS）コード

```
const doPost = (e) =>{

  //値の受取
  const title = e.parameter.title;
  const email = e.parameter.email;
  const message = e.parameter.message;

  //スプレッドシートの準備
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const sheet = ss.getSheetByName("シート1"); //シート名の数字は半角

  //シートの一番下の行に追加
  sheet.appendRow([title,email,message,new Date()]);

  //レスポンス
  return ContentService.createTextOutput("受け付けました");
}
```

curlで試すなら、以下の感じ。

```
curl -X POST \
  -H "Content-type: application/x-www-form-urlencoded" \
  -d "title=title&email=test@test.local&message=fogogufo" \
  "https://gas/api/path"
```