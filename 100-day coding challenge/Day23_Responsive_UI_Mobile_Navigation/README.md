
## 1. 미디어 쿼리 실전
본 과정에서는 완성된 데스크톱 디자인에서 시작했으므로, `max-width`를 사용
```CSS
@media (max-width: 768px) { ... }
```
의미 브라우저 너비가 최대 768px일때까지 이 규칙을 적용할것

주의할것
CSS는 종속(Cascade)되는 성질을 가지기때문에 미디어쿼리는 항상 기본스타일 아래에 위치해야함

```CSS
@media (max-width: 48rem) {
  main h1 {
    font-size: 1.5rem;
  }
  #main-header nav {
    display: none;
  }
  #latest-products ul {
    grid-template-columns: 100%;
  }
}
```
1. 타이포그래피 최적화: h1(제목) 크기조정 
2. 래이아웃 단순화: nav(가로형 메뉴) 숨기기
nav의 기본 display속성은 block이기떄문에 none으로 수정
3. 브레이크포인트의 유연성: px ->rem 변환
## 2. Hamburger Icon & Side Drawer 

### 자바스크립트 없는 메뉴의 작동 원리
hamburger icon구조: 햄버거 아이컨제작 보통 `<a>` 태그)안에 세개의 `<span>` 요소를 넣음
1. 내부링크
보통 a를 다른 페이지로 이동할때 쓰지만, 현재 페이지 내의 특정 위치로 이동할때도 사용함
2. 가상 선택자 :target
 - **원리**: URL 끝의 ID와 일치하는 요소를 찾아 스타일을 적용합니다.
- **예시**: 주소창이 `...#side-drawer`가 되는 순간, CSS의 `#side-drawer:target` 규칙이 활성화됩니다. 이때 `display: block;`이나 `left: 0;` 같은 속성을 주면 숨겨져 있던 메뉴가 화면에 나타남

| **동작**        | **브라우저 상태**                       | **CSS 반응**                          |
| ------------- | --------------------------------- | ----------------------------------- |
| **햄버거 버튼 클릭** | URL이 `#side-drawer`로 변경           | `:target` 활성화 $\rightarrow$ 메뉴 나타남  |
| **닫기 버튼 클릭**  | URL에서 `#` 이후 내용이 사라짐 (예: `#`만 남음) | `:target` 비활성화 $\rightarrow$ 메뉴 사라짐 |
```HTMl
<a href="#" class="menu-btn"> 
	<span></span> 
	<span></span>
	<span></span> 
</a>
```

```css
.menu-btn {
  width: 3rem;
  height: 3rem;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
.menu-btn span {
  width: 100%;
  height: 3px; /
  background-color: white;
}
```
이미지 파일을 불러올필요가 없어 로딩속도가 빠름
rem 단위를 사용하여 사용자가 브라우저 폰트크리를 키우면 버튼도 함께 커지는 반응형구조
### SideDrawer 제작
#### 1. 의미 있는 HTML: `<aside>` 요소
sidebar 는 메인 콘텐츠가 아니기때문에, 부수적인 정보를 담는 `<aside>` 태그 사용 헤더와 메인 사이에 배치하여 구조적으로도 중간지점임을 명시함
#### 2. 레이아웃의 마법: `position: fixed`
드로워가 화면 전체를 차지하게 만드는 비결
- **`fixed`**: 요소를 일반적인 문서 흐름에서 완전히 제외하고, **브라우저의 보이는 영역(Viewport)**을 기준으로 고정합니다.
- **`top: 0`, `left: 0`**: 화면 왼쪽 맨 위에서 시작.
- **`width: 100%`, `height: 100%`**: 화면을 꽉 채우도록 설정.

#### 3. 내부 정렬: Flexbox
SideDrawer 내부의 메뉴들을 정렬할때 다시한번 플렉스 박스를 사용함
- **`flex-direction: column`**: 메뉴들을 세로로 쌓음.
- **`align-items: center`**: 가로축(교차축) 중앙 정렬.
- **`padding: 4rem`**: 메뉴들이 화면 위쪽에 너무 붙지 않도록 여백 확보.

## 3. HTML Fragments의 이해 
보통 링크를 다른 페이지로 이동할 때 사용하지만 현재 페이지 내의 특정 지점으로 이동하는 '내부 링크'기능을 활용함

### 1. URL 프래그먼트(`#`)의 마법
URL 끝에 붙는 `#contact`나 `#side-drawer` 같은 부분을 **프래그먼트(Fragment)**라고 부릅니다.
- **작동 원리**: 브라우저는 URL에 `#ID`가 추가되면, 해당 ID를 가진 요소를 찾아 그곳으로 화면을 스크롤합니다.
- **실습 내용**: 햄버거 버튼(`<a>`)의 `href` 속성에 `#side-drawer`를 입력하여, 클릭 시 페이지 내의 `side-drawer` ID를 가진 요소로 이동하게 만들었습니다.
### 2. 상태(State)의 변화로서의 URL
 URL이 변한다는 것은 브라우저에게 "사용자가 특정 섹션을 보고 싶어 한다"는 신호를 주는 것과 같습니다.
 
- **현재 상태**: 햄버거 버튼을 누르면 주소창이 `.../index.html#side-drawer`로 변하며 사이드바 위치로 이동합니다.
- **남은 과제**: 단순히 위치만 이동하는 것이 아니라, 이 URL의 변화를 감지해 **숨겨져 있던 사이드바를 화면에 나타나게(display: block)** 만드는 것입니다.
### 3. 구조적 실험
사이드바의 위치 이동을 명확히 확인하기 위해 잠시 `position: fixed`를 해제하고 HTML 하단으로 옮겨보는 실험을 진행했습니다. 이를 통해 클릭과 이동의 상관관계를 시각적으로 확인.

- **내부 링크 설정**: `<a href="#side-drawer">`
- **대상 요소 설정**: `<aside id="side-drawer">`
- **브라우저 행위**: 주소창에 `#side-drawer` 추가 + 해당 요소로 포커스 이동
