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

