# GitHub example



## head



- og: Open Graph

```html
<meta property="og:type" content="website" />
    <meta property="og:site_name" content="GitHub" />
    <meta property="og:title" content="Build software better, together" />
    <meta property="og:description"
      content="GitHub clone coding / GitHub is where people build software. More than 31 million people use GitHub to discover, fork, and contribute to over 100 million projects."
    />
    <meta property="og:image" content="img/logo__github.png" />
    <meta property="og:url" content="https://github.com" />

    <!-- https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started.html -->
    <meta property="twitter:card" content="summary" />
    <meta property="twitter:site" content="GitHub" />
    <meta property="twitter:title" content="Build software better, together" />
    <meta
      property="twitter:description"
      content="GitHub clone coding / GitHub is where people build software. More than 31 million people use GitHub to discover, fork, and contribute to over 100 million projects."
    />
    <meta property="twitter:image" content="img/logo__github.png" />
    <meta property="twitter:url" content="https://github.com" />
```



- favicon

```html
<!-- <link rel="shortcut icon" type="image/x-icon" href="favicon.ico"> -->
    <link rel="icon" href="favicon.png" />
    <link rel="apple-touch-icon" href="favicon.png" />

```

- reset.css

```
 <link rel="stylesheet" href="css/reset.css" />
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.min.css"
    />
```

구글 resetcss cdn



## body

- BEM 

  css 작명 규칙(일반적- 회사마다 다름)

  `_ _` ~의 일부분

  `--` ~의 상태

  `-` 일반적인 작명



### header

- 가상선택자::before, ::after는 content: " "; 와 함께 사용. 

  ```css
  body::before {
  	content: "";
  	top: 0;
  	left: 0;
  }
  ```

- vendor prefix (브라우저별 접두사)

  ```css
  /*vendor prefix*/
  .input--text::-webkit-input-placeholder {
    color: #cacaca;
  }
  .input--text::-ms-input-placeholder {
    color: #cacaca;
  }
  .input--text::-moz-input-placeholder {
    color: #cacaca;
  }
  
  /*.input--text::-o-input-placeholder {
    color: #cacaca;
  }*/
  /* opera는 placeholder 지원 안함 */
  
  ```

- outline: none;

- box-shadow

  ```css
  .input--text {
    height: 34px;
    padding: 0 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    box-sizing: border-box;
    outline: none;
    box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.075);
    font-size: 16px;
  }
  .input--text:focus {
    border-color: #51a7e8;
    box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.075),
      0 0 5px rgba(81, 167, 232, 0.5);
  }
  ```

  inset으로 박스 안으로 그림자

  box-shadow는 이중 그림자가 가능하다.

- inner 

  가운데 정렬시 margin: 0 auto;를 사용하려면 width값이 정의되어 있어야 한다.

- logo

  ```html
  <div class="menu-group">
     <div class="logo">
     <a href="#">GitHub</a>
  </div>
  ```

  

  ```css
  header .logo a {
    background: url(../img/logo.svg);
    width: 32px;
    height: 32px;
    display: block;
    text-indent: -999px;
  }
  ```

  a 태그는 inline 요소이기 때문에 display: block;해야 한다.

  html에서 img 태그로 이미지를 넣을 경구 alt가 있지만

  css에서 background로 이미지를 넣을 경우 대체텍스트가 없으므로 html에 텍스트가 필요하다.

  text-indent로 화면에서 보이지 않게 처리한다.

- clearfix

  ```css
  /*float clearfix*/
  .clearfix::after {
    content: "";
    clear: both;
    display: block;
  }
  .float--left {
    float: left;
  }
  .float--right {
    float: right;
  }
  ```

  float속성을 사용하면 부모가 제대로 감싸주지 못하는 문제가 발생한다. 이를 해결하기 위해 부모에 clearfix속성을 사용한다.

- order

  ```css
  header .btn-group {
    order: 2;
  }
  #search-form {
    order: 1;
  }
  .sub-menu {
      /*default :0;*/
  }
  
  ```

  order속성을 통해 배치순서를 바꿀 수 있다.

- html에서 줄바꿈을 하면 화면상에 공간이 생긴다.

  ```html
  <div class="btn-group">
    <a href="#" class="btn sign-in">Sign in</a>
    <a href="#" class="btn btn--primary sign-up">Sign up</a>
  </div>
  ```

  ```css
  header .btn-group {
    display: flex;
  }
  ```



### visual

- padding이나 margin이 들어가서 보더 영역이 늘어나는 것을 방지하기 위해

  box-sizing: border-box;를 사용

- absolute가 걸리도록 하기 위해서 relative를 큼직큼직한 영역에 사용

- text-shadow: x y blur rgba(0,0,0,0);

- 배경 이미지 어둡게 blur처리

  기존에 있는 배경에 before속성을 이용해서 덮어버리는 방법

  ```css
  .section--visual::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.3);
  }
  ----------------------------------------
  .section--visual::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;  <---
    right: 0;   <---
    background: rgba(0, 0, 0, 0.3);
  }
  
  둘다 같은 효과
  ```

- 배경이미지가 비율이 변경되도 전체를 차지하게 설정

  ```css
  background-size: cover;
  ```

- form태그 안에 type="submit"인 버튼을 누르면 form태그안의 양식들이 action=""안의 특정한 페이지 주소로 전송된다.

  ```html
  <form id="sign-form" method="POST" action="">
    <button type="submit"></button>
  </form>
  ```

- 특정단어 연결

  ```html
  단어와 단어사이에 &nbsp;를 사용한다. 띄어쓰기 하지 않고 붙여써야한다.
  ```

- flex 

  flex-grow: 0  flex-shrink: 1 flex-basis: auto가 기본값

  flex-grow가 1이되면 flex-basis는 0이 된다.



### feature

- video

  화면의 비율 16:9

  ```html
  <div class="video">
    <div class="video-ratio">
    </div>
  </div>
  ```

  ```css
  video {
    max-width: 500px;
  }
  video-ratio {
      height: 0;
      padding-top: 56.25%
  }
  
  /*부모의 width값이 500px 500:x=16:9  --> 56.25%*/
  ```

  height에 값을 지정하면 고정이 되기 때문에 부모의 값에 따라 비율이 정해지도록 설정 

  ```css
  video {
    max-width: 500px;
  }
  video-ratio {
      height: 0;
      padding-top: 56.25%
      position: relative;
  }
  iframe {
    position:absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
  ```

  video영역 안에 iframe 비디오를 삽입

- tiles 정렬

  ```css
  .section--feature .tiles ul {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
  }
  
  /* 4개의 column 1:1:1:1비율 */
  ```

  구형브라우저의 경우

  ```html
  <ul class="clerfix">
  </ul>
  ```

  html의 부모태그에 clearfix 적용

  ```css
  .section--feature .tiles li {
  padding: 34px 24px;
  text-align: center;
  line-height: 1.5;
  border-right: 1px solid #e5e5e5;
  box-sizing: border-box;
  float: left;
  width: 25%
  }
  ```

  float: left; width: 25%;로 4개의 컬럼, padding이나 border가 있어서 요소가 커지는 경우가 생기기 때문에 box-sizing: border-box;가 있는지 확인

  

### 지도

```html
 <script>
      function iniMap() {
        const myLatLng = {
          lat: 37.782293,
          lng: -122.391240
        }
        const map = new google.maps.Map(
          document.getElementById('map'),
          {
            center: myLatLng,
            scrollwheel: false,
            zoom: 18
          }
        );
        const marker = new google.maps.Marker({
          position: myLatLng,
          map: map,
          title: 'GitHub'
        });
      }
    </script>
    <script src="https://maps.googleapis.com/maps/api/jskey=AIzaSyCTQIlxBn5AfKGvsfJiormAE1esN3fcCkg&callback=iniMap" async defer></script>
```

lat, lng : 위도, 경도

center: 지도의 센터

scrollwheel: 지도상에서 휠 방지

zoom: 18까지 허용

marker: 지도상에 포인트

position: 위치

mapAPI는 개발자등록을해서 구글에서 받아야함 

async: 비동기로 실행

defer: html의 구조가 전부 로드되면 실행





### Pricing card

- 배경색

  ```css
  .section--pricing {
    background: linear-gradient(#f5f5f5, #fff);
  }
  ```

- flex

  flex:1; 로 Sign for GitHub 버튼 영역 잡아줌



### Footer

- 가운데 배치

  ```css
  footer .logo {
    position: absolute;
    top:0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
    width: 24px;
    height: 24px;
  }
  ```

- 로고 hover

  ```css
  footer .logo:hover svg {
    fill: #4078c0;
  }
  ```

- underline

  ```css
  footer .site-links li a:hover {
    text-decoration: underline;
  }
  ```



### media

#### header

- 설정단위

  | 종류           | 디바이스         | 단위(px)    |
  | -------------- | ---------------- | ----------- |
  | Large Devices  | Desktops         | 1024px 이상 |
  | Medium Devices | Tablets          | 1024px 이하 |
  | Small Devices  | Tablets + Phones | 768px 이하  |

- 초기화

  ```css
  @media (max-width:1024px) {
    header.section .inner { /* header .inner이면 명시도값이 낮아서 덮어쓰기가 안됨 section붙여서 높여줌*/
      max-width: none;
      height: auto;
      padding: 0 20px;
    }
    header .menu-group,
    header .sign-group {
      float: none;
    }
  }
  ```

  max-width, height, float 초기화

  

  height값을 지정해버리면 나중에 만들 토글버튼의 높이가 정해져버리기 때문에 컨텐츠만큼 늘어나게 만들기위해

  auto로 지정

- toggle-btn

  ```css
  #toggle-btn {
      background: url("../img/toggle-btn.svg");
      width: 18px;
      height: 24px;
      position: absolute;
      top: 16px;
      right: 20px;
      cursor: pointer;
      text-indent: -9999px;
    }
  ```

  height값이 로고만큼 차지하기 때문에 padding으로 공간 만들어줌

  ```css
  header .logo {
      padding: 12px 0;
    }
  ```

  

  자바스크립트

  

  toggle 이벤트 적용

  ```javascript
  (function(window, document) {
      'use strict';
  
      const toggles = document.querySelectorAll('.toggle');
      const toggleBtn = document.getElementById('toggle-btn');
  
      toggleBtn.addEventListener('click', function(){
          toggleElements();
      });
  
      function toggleElements() {
          [].forEach.call(toggles, function(toggle) {
              toggle.classList.toggle('on');
          });
      }
  })(window, document);
  ```

  화면 사이즈가 변경되면(resize) 토클 remove 코드 추가

  ```javascript
  (function(window, document) {
      'use strict';
  
      const toggles = document.querySelectorAll('.toggle');
      const toggleBtn = document.getElementById('toggle-btn');
  
      toggleBtn.addEventListener('click', function(){
          toggleElements();
      });
  
      window.addEventListener('resize', function() {
          if(window.innerWidth > 1024) {
              offElements();
          }
      });
  
      function toggleElements() {
          [].forEach.call(toggles, function(toggle) {
              toggle.classList.toggle('on');
          });
      }
      function offElements() {
          [].forEach.call(toggles, function(toggle) {
              toggle.classList.remove('on');
          });
      }
  })(window, document);
  ```

  

#### visual

- 배경이미지변경

  ```css
  .section--visual {
      background-image: url(../img/bg-small.jpg);
    }
  ```



- small device 

  footer 정렬 

  ```css
  /* footer */
  footer .site-links {
      float: none;
      display: block;
      text-align: center;
  }
  footer .site-links:first-child {
      margin-bottom: 20px;
  }
  footer .site-links li {
      display: inline;
  }
  ```

  main.css에서 flex처리한 것을 부모(.site-links)에 block으로 수직 정렬시키고 자식(.site-links li)를 inline으로 수평정렬