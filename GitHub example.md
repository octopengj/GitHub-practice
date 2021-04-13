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

