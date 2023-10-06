---
id: 33ylell56q96ksnbmds03df
title: 날짜 다루기
desc: ''
updated: 1696549528896
created: 1696548789488
---

## 현재 시각 가져오기
```javascript
const currentDate = new Date();
```

## Datetime을 Date 포맷으로 바꾸기
```javascript
// Format the date as 'YYYY-MM-DD'
const formattedDate = currentDate.toISOString().slice(0, 10);
```

## 날짜를 해당 주의 월요일 날짜로 변경
```javascript
function convertDate(dateString) {
  const date = new Date(dateString);
  const dayOfWeek = date.getDay();

  // If the date is already a Sunday, subtract 7 days
  if (dayOfWeek === 0) {
    date.setDate(date.getDate() - 7);
  } else {
    date.setDate(date.getDate() - dayOfWeek);
  }

  return date.toISOString().slice(0, 10);
}

// Example usage
const date1 = '2023-09-18';
const convertedDate1 = convertDate(date1);
console.log(convertedDate1); // Output: 2023-09-17

const date2 = '2023-09-25';
const convertedDate2 = convertDate(date2);
console.log(convertedDate2); // Output: 2023-09-24

const date3 = '2023-10-02';
const convertedDate3 = convertDate(date3);
console.log(convertedDate3); // Output: 2023-10-01
```