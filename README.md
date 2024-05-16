# auto-CVC
### Here is your JavaScript code converted into a bookmarklet format in auto-CVC.js
```javascript
javascript:(function(){var queryString=prompt("Enter query string:");if(!queryString)return;function parseUrlEncoded(data){return data.split('&').map(function(param){return param.split('=')[0];}).filter(Boolean);}function parseMultipartFormData(data){var fieldNames=[];var parts=data.split(/-----------------------------\d+/);parts.forEach(part=>{var match=part.match(/name="([^"]+)"/);if(match){fieldNames.push(match[1]);}});return fieldNames;}function extractKeys(data){if(data.includes('Content-Disposition: form-data;')){return parseMultipartFormData(data);}else{return parseUrlEncoded(data);}}var keysList=extractKeys(queryString);kintone.events.on('app.record.edit.show',function(event){var record=event.record;var subtableFieldCode='パラメーター';var date=new Date();var today=date.getFullYear()+'-'+(date.getMonth()+1)+'-'+date.getDate();if(record[subtableFieldCode]&&record[subtableFieldCode].value){record[subtableFieldCode].value.forEach(function(subtableRow,index){var fieldCodeToUpdate='文字列__1行__2';var dateFieldCode='試験実施日_パラメーター_';var dropdownFieldCode='ドロップダウン_3';if(subtableRow.value[fieldCodeToUpdate]&&index<keysList.length){subtableRow.value[fieldCodeToUpdate].value=keysList[index];}if(subtableRow.value[dateFieldCode]){subtableRow.value[dateFieldCode].value=today;}if(subtableRow.value[dropdownFieldCode]){subtableRow.value[dropdownFieldCode].value="POST parameter";}});}return event;});})();

```
### Instructions for Use:
- Copy the entire JavaScript code above.
- Create a new bookmark in your browser: right-click the bookmarks bar > Add page.
- Paste the JavaScript code into the URL or Location field.
- Name the bookmark as desired.
- Click the bookmark when on a Kintone app page where you want to execute this script.
