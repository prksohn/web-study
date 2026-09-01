## 테이블 Table

### 1. `<table>` - 표 전체 감싸는 태그

표 형태의 데이터를 표현할 때 사용

```html
<table></table>
```

### 2. `<caption>` - 표 제목

표 자체의 제목

```html
<table>
  <caption>
    표 제목
  </caption>
</table>
```

### 3. `<thead>` - 표 머리

Colum, 표 안의 제목 부분을 감싸는 태그

```html
<table>
    <caption> 표 제목 </caption>
  <thead>

  <thead>
</table>
```

### 4. `<tbody>` - 표 본문

표 안의 내용, 실제 데이터 부분을 감싸는 태그

```html
<table>
  <caption> 표 제목 </caption>

  <thead>

  <thead>

  <tbody>

  <tbody>
</table>
```

### 5. `<tr>` - 한 줄

Table Row의 약자, 한 줄 (행) <br>
표의 방향은 좌->우

```html
<table>
  <caption> 표 제목 </caption>

  <thead>
    <tr>

    </tr>
  <thead>

  <tbody>
    <tr>

    </tr>
  <tbody>
</table>
```

### 6. `<th>` - 표 안의 제목

Table Header의 약자, 표 안의 제목 또는 헤더 셀

```html
<table>
  <caption> 표 제목 </caption>

  <thead>
    <tr>
      <th>제목</th>
    </tr>
  <thead>

  <tbody>
    <tr>

    </tr>
  <tbody>
</table>
```

### 7. `<td>` - 표 안의 내용

Table Data의 약자, 실제 데이터를 담는 셀

```html
<table>
  <caption> 표 제목 </caption>

  <thead>
    <tr>
      <th>제목</th>
    </tr>
  <thead>

  <tbody>
    <tr>
      <td>내용</td>
    </tr>
  <tbody>
</table>
```
