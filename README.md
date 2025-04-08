# 덕성여대 웹 폼 프로젝트 - Google Apps Script 연동

이 프로젝트는 구글 앱스 스크립트를 활용하여 웹 폼을 통해 사용자의 정보를 Google 스프레드시트로 전달하는 기능을 구현한 과제입니다.

## 📌 프로젝트 개요

- HTML/CSS로 구성된 웹 폼
- `<fieldset>`으로 구분된 입력 그룹
- 다양한 HTML5 폼 요소 활용
- Google Apps Script를 통한 스프레드시트 자동 연동
- 제출 정보: 이름, 이메일, 학과, 기술, 팀 여부, 만족도, 피드백 등

## 💻 사용 기술

- HTML5
- CSS3
- Google Apps Script (doPost 함수 활용)

## 📁 주요 파일

- `form.html`  
  → 사용자 입력 폼을 구현한 HTML 파일입니다. 다양한 입력 요소와 시멘틱 마크업을 포함하고 있습니다.

- `form.css`  
  → 웹 폼의 레이아웃과 스타일을 정의한 CSS 파일입니다. 가독성과 중앙정렬을 고려한 디자인이 적용되었습니다.

## 📤 연동 방식

사용자가 폼을 제출하면 `Google Apps Script Web App URL`로 정보가 POST 전송되어 Google 스프레드시트에 자동 저장됩니다.

Google Apps Script 예시:
```javascript
function doPost(e) {
  const sheet = SpreadsheetApp.openById("스프레드시트ID").getSheetByName("시트명");
  const data = [
    new Date(),
    e.parameter.name,
    e.parameter.email,
    e.parameter.department,
    e.parameter.tech,
    e.parameter.team,
    e.parameter.satisfaction,
    e.parameter.feedback
  ];
  sheet.appendRow(data);
  return ContentService.createTextOutput("Success");
}
