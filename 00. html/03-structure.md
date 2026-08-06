## 구조 Structure

페이지가 어떤 구조로 되어있는지 표현

### 전체 구조 예시

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <title>페이지 구조</title>
  </head>

  <body>
    <header>
      <nav>
        <a href="/">홈</a>
        <a href="/about">소개</a>
        <a href="/contact">문의</a>
      </nav>
    </header>

    <main>
      <section>
        <article>
          <h2>첫 번째 게시글</h2>
          <p>첫 번째 게시글 내용</p>
        </article>

        <article>
          <h2>두 번째 게시글</h2>
          <p>두 번째 게시글 내용</p>
        </article>

        <article>
          <h2>세 번째 게시글</h2>
          <p>세 번째 게시글 내용</p>
        </article>
      </section>

      <aside>
        <h2>관련 콘텐츠</h2>
        <p>추천 게시글이나 관련 링크</p>
      </aside>
    </main>

    <footer>
      <p>Copyright 2026</p>
    </footer>

    <div>
      <p>일반적인 영역을 묶는 div</p>
    </div>

    <p>
      문장 안에서
      <span>특정 부분을 묶을 때 span</span>
      을 사용
    </p>
  </body>
</html>
```

### 1. `<header>` - 페이지 머리말

페이지나 특정 영역의 시작 부분, 웹사이트의 로고와 메뉴를 만들 때 사용

```html
<header>
  <h1>My Blog</h1>

  <nav>
    <a href="/">홈</a>
    <a href="/posts">게시글</a>
    <a href="/about">소개</a>
  </nav>
</header>
```

- 웹 페이지 전체의 맨 위에만 사용되는 게 아니라,
- 특정 `article` 제목이나 작성자 정보 담는 `header` 도 가능

### 2. `<nav>` - 네비게이션

주요 이동 메뉴

```html
<nav>
  <a href="/">홈</a>
  <a href="/products">상품</a>
  <a href="/about">소개</a>
  <a href="/contact">문의</a>
</nav>
```

### 3. `<main>` - 핵심 콘텐츠

페이지의 주요 콘텐츠, 일반적으로 콘텐츠 하나당 `main` 1개로 구성

```html
<main>
  <h1>상품 목록</h1>

  <!-- 상품 목록 -->
</main>
```

### 4. `<section>` - 주제별 영역

하나의 주제를 가진 콘텐츠 영역

```html
<section>
  <h2>인기 게시글</h2>

  <p>많이 읽은 게시글입니다.</p>
</section>

<section>
  <h2>최근 게시글</h2>

  <p>최근 읽은 게시글입니다.</p>
</section>
```

### 5. `<article>` - 독립적인 콘텐츠

하나의 독립적인 콘텐츠

#### 대표적인 예

- 블로그 게시글
- 뉴스 기사
- 커뮤니티 게시글
- 댓글
- 상품 정보

```html
<section>
  <h2>최신 게시글</h2>

  <article>
    <h3>HTML 공부하기</h3>
    <p>HTML 기본 구조 공부</p>
  </article>

  <article>
    <h3>CSS 공부하기</h3>
    <p>CSS 기본 문법 공부</p>
  </article>
</section>
```

### 6. `<aside>` - 부가적인 콘텐츠

주요 콘텐츠와 관련은 있지만 중심 내용은 아닌 콘텐츠

#### 대표적인 예

- 추천 게시글
- 관련 링크
- 광고
- 사이드 메뉴
- 작성자 정보

```html
<main>
  <section>
    <h1>HTML 공부하기</h1>
    <p>HTML에 대한 내용</p>
  </section>

  <aside>
    <h2>추천 게시글</h2>
    <a href="/css">CSS 공부하기</a>
  </aside>
</main>
```

### 7. `<footer>` - 페이지 또는 영역의 하단

페이지나 특정 영역의 하단 정보 <br>
페이지 전체뿐만 아니라 `article` 같은 특정 영역의 하단에서도 사용

#### 대표적인 예

- 저작권 정보
- 회사 정보
- 연락처
- 관련 링크

```html
<footer>
  <p>Copyright 2026</p>
</footer>
```

### 8. `<div>` - 의미 없는 일반적인 영역

특별한 의미 없는 컨테이너지만 큰 영역을 묶을 때

```html
<div>
  <h2>제목</h2>
  <p>내용</p>
</div>
```

### 9. `<span>` - 인라인 영역

특별한 의미 없는 요소지만 문장 안에서 특정 부분을 묶을 때 <br>
추후 해당 부분만 css로 디자인 변경 가능하기 때문

```html
<p>
  현재 가격은
  <span>10,000원</span>
  입니다.
</p>
```

### 10. `<hr>` - 주제 구분

Horizontal Rule의 약자로, 콘텐츠 사이의 주제 전환이나 구분을 나타낼 때 <br>
화면 출력 : 구분선

```html
<hr />
```
