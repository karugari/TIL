## 1. Flexbox 실전 적용 (L:121 - 122)
flexboxsms 부모(Conrainer)에게 명령을 내릴 때 시작됨
justify-content에서 flex-end 와 end의 차이는 무엇일까에대한 답
- **`flex-end`**: 거의 모든 브라우저(아주 오래된 버전 포함)에서 완벽하게 지원
- **`end`**: 최신 브라우저에서는 잘 작동하지만, 몇 년 된 구형 브라우저에서는 인식을 못 할 수도 있음.

```css
header {

  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 60px;

}
```
- **`display: flex`**: 헤더 내부의 로고(`div`)와 메뉴(`nav`)를 가로로 나란히 세웁니다.
- **`justify-content: space-between`**: 로고는 왼쪽 끝, 메뉴는 오른쪽 끝으로 밀어내어 가운데 빈 공간을 만듭니다.
- **`align-items: center`**: 로고의 높이와 메뉴의 높이가 달라도 수직 중앙에 딱 맞게 정렬합니다.
## 2. 배경 이미지와 히어로 섹션 (L:123 - 124)
### 1. HTML 구조 정의: 의미 있는 ID 부여
`<secion id ="hero">` : 페이지 상단의 대형 이미지와 메인 문구가 들어가는 '주인공' 섹션
**`<section id="highlights">`**: 추천 여행지 카드가 들어갈 섹션입니다.
### CSS 배경이미지의 특징
HTML의 `<img>` 태그는 문서 흐름(Flow)을 차지하여 다른 요소를 옆이나 아래로 밀어내지만, **CSS 배경 이미지**는 요소의 '바닥'에 깔립니다. 덕분에 그 위에 글자나 버튼을 자유롭게 올릴 수 있습니다.
```css
#hero { height: 800px; /* 이미지를 보여줄 충분한 공간 확보 */ 
background-image: url("images/places/ocean.jpg"); /* 이미지 경로 설정 */ }
```

| 속성 | 값 | 설명 |
|---|---|---|
|height|800px|섹션 자체의 높이를 지정해야 배경 이미지가 노출될 공간이 생깁니다.|
|background-position|center|이미지의 중심부를 컨테이너 중앙에 맞춥니다. (서퍼가 중앙에 오게 함)|
|background-size|cover|이미지가 잘리더라도 **요소 전체를 빈틈없이 덮도록** 크기를 조절합니다.|
```css
#hero-content {
    width: 900px;
    background-color: rgba(51, 47, 47, 0.8);
    box-shadow: 2px 4px 8px rgb(68, 67, 67);
    border-radius: 8px;
    text-align: center;
    padding: 50px 0;
    margin: 0 auto;

}
```
박스 중앙 정렬의 두 가지 방법
1. 텍스트 및 인라인 요소 정렬
**`text-align: center`**: 컨테이너 내부의 글자들과 링크(인라인 요소)를 가로 중앙으로 정렬합니다.
2. 블록요소(박스 자체)정렬
margin: 0 auto 박스 모델의 원리를 이용한 기법 상하는 0 좌우는 auto 로 설정해 브라우저가 남은 공간을 절반으로 나누어 좌우에 배분함으로 박스 자체가 중앙으로 이동됨

