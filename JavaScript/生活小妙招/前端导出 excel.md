
- npm install exceljs
- npm install file-saver
- https://www.npmjs.com/package/exceljs

```html
<template>
  <button @click="download('Andy测试文件.xlsx')">download</button>
</template>
 
<script setup>
import { ref, computed } from 'vue'
import ExcelJS from "exceljs";

async function download(filename) {
  const workbook = new ExcelJS.Workbook();
  const worksheet = workbook.addWorksheet("Sheet1");

  // 表头
  worksheet.columns = [
    { header: "序号", key: "id", width: 10 },
    { header: "姓名", key: "name", width: 10 },
    { header: "年龄", key: "age", width: 10 },
  ];

  // 数据
  const data = [
    { id: "1", name: "艾伦", age: "20" },
    { id: "2", name: "柏然", age: "25" },
  ];

  data.forEach(item => worksheet.addRow(item));

  // 合并单元格
  // worksheet.mergeCells("B1:C1");

  // 设置行高
  worksheet.getRow(2).height = 30;

  // 自定义样式
  const B1 = worksheet.getCell('B1')
  B1.font = { size: 20, color: { argb: 'FF8B008B' }, bold: true }
  B1.alignment = { horizontal: 'center', vertical: 'middle' }

  const buffer = await workbook.xlsx.writeBuffer();
  let fileURL = window.URL.createObjectURL(new Blob([buffer]));
  let fileLink = document.createElement("a");
  fileLink.href = fileURL;
  fileLink.setAttribute("download", filename);
  document.body.appendChild(fileLink);
  fileLink.click();
}

</script>
```
