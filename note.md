# HTML

## HTML syntax

### I. Web Browsers

Always check web browser support:

1. Chrome
2. Edge
3. Firefox
4. Safari

### II. Semantics

1. Dùng thẻ **heading** h1 - h6 hợp lý. Mỗi page phải có thẻ h1 và không nên quá 3 cấp heading
2. **Emphasis tag**: em (tông giọng), strong (mức độ quan trọng), mark (đánh dấu)
3. **Blockquote**:
    - Block: `<blockquote cite="Nguồn trích dẫn">Nội dung trích dẫn</blockquote>`
    - Inline: `<q cite="Nguồn trích dẫn">Nội dung trích dẫn</q>`
    - Link: `<a href="Nguồn trích dẫn"><cite>Nội dung trích dẫn</cite></a>`
4. **Abbreviations**:
    - `<abbr title="Viết tắt">Viết tắt</abbr>`
5. **Address**:
    - `<address>Địa chỉ</address>`
6. **Code**:
    - `<code>Mã code</code>`
    - `<var>Biến</var>`
    - `<kbd>Phím</kbd>`
    - `<samp>Kết quả</samp>`
7. **Time**:
    - `<time datetime="2022-01-01">2022-01-01</time>`
8. **Structuring documents**:
    - `<header>`
    - `<nav>`
    - `<main>` _(unique)_: `<article>`, `<section>`
    - `<aside>`
    - `<footer>`
9. **Figure and caption**:
    - `<figure>`
    - `<figcaption>`
      `<figure><img src="" alt=""><figcaption></figcaption></figure>`
10. **Video**:
    - ```html
      <video
          controls
          width="400"
          height="400"
          autoplay
          loop
          muted
          preload="auto"
          poster="poster.png"
      >
          <source src="video1.mp4" type="video/mp4" />
          <source src="video2.webm" type="video/webm" />
          <track kind="subtitles" src="subtitles_vi.vtt" srclang="vi" label="Vietnamese" />
          <track kind="captions" src="captions_vi.vtt" srclang="vi" label="Vietnamese" />
          <track kind="descriptions" src="descriptions_vi.vtt" srclang="vi" label="Vietnamese" />
          <track kind="chapters" src="chapters.vtt" srclang="vi" label="Vietnamese" />
          <p>
              Your browser doesn't support this video. Here is a
              <a href="video1.mp4">link to the video</a> instead.
          </p>
      </video>
      ```
11. **Audio**:
    - ```html
      <audio controls autoplay loop muted preload="auto">
          <source src="audio1.mp3" type="audio/mpeg" />
          <source src="audio2.ogg" type="audio/ogg" />
          <track kind="subtitles" src="subtitles_vi.vtt" srclang="vi" label="Vietnamese" />
          <track kind="captions" src="captions_vi.vtt" srclang="vi" label="Vietnamese" />
          <track kind="descriptions" src="descriptions_vi.vtt" srclang="vi" label="Vietnamese" />
          <track kind="chapters" src="chapters.vtt" srclang="vi" label="Vietnamese" />
          <p>
              Your browser doesn't support this audio file. Here is a
              <a href="audio1.mp3">link to the audio</a> instead.
          </p>
      </audio>
      ```
12. **Table**:
    - scope attribute

### III. HTML Entities - Character References

| Character | Description           | Code     |
| --------- | --------------------- | -------- |
| <         | Less than             | &lt;     |
| ≤         | Less than or equal    | &le;     |
| >         | Greater than          | &gt;     |
| ≥         | Greater than or equal | &ge;     |
| ≠         | Not equal             | &ne;     |
| ≡         | Identical to          | &equiv;  |
| ≈         | Approximately equal   | &asymp;  |
| ⊂         | Subset of             | &sub;    |
| ⊃         | Superset of           | &sup;    |
| ⊄         | Not subset of         | &nsub;   |
| ⊅         | Not superset of       | &nsup;   |
| ←         | Left arrow            | &larr;   |
| →         | Right arrow           | &rarr;   |
| ↑         | Up arrow              | &uarr;   |
| ↓         | Down arrow            | &darr;   |
| "         | Double quote          | &quot;   |
| '         | Single quote          | &apos;   |
| °         | Degree                | &deg;    |
| $         | Dollar                | &dollar; |
| ©         | Copyright             | &copy;   |
| ®         | Registered            | &reg;    |
| ™         | Trademark             | &trade;  |
| &         | Ampersand             | &amp;    |
| ±         | Plus-minus            | &plusmn; |
| ×         | Multiplication        | &times;  |
| ÷         | Division              | &divide; |
|           | Space                 | &nbsp;   |

---

## Web page metadata

### I. Meta tags

1. viewport
   `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
2. charset
   `<meta charset="UTF-8">`
3. Đảm bảo Internet Explorer sử dụng engine mới nhất
   `<meta http-equiv="X-UA-Compatible" content="ie=edge">`
4. description
   `<meta name="description" content="">`
5. author
   `<meta name="author" content="">`
6. robots
   `<meta name="robots" content="index, follow">`
7. Open Graph
   `<meta property="og:title" content="">`
   `<meta property="og:description" content="">`
   `<meta property="og:image" content="">`
   `<meta property="og:url" content="">`
   `<meta property="og:type" content="website">`
8. Đổi màu thanh địa chỉ trên trình duyệt di động
   `<meta name="theme-color" content="">`

### II. Applying JS to HTML

- **Mặc định**: Khi trình duyệt đọc đến thẻ script, nó sẽ dừng việc dựng HTML (block parsing) để tải file script về và thực thi nó ngay lập tức. Sau khi xong mới tiếp tục dựng nốt HTML. Điều này khiến trang web bị "đứng" nếu file JS nặng.
  `<script src="my-js-file.js"></script>`
- **async**: Trình duyệt tải file JS trong khi vẫn tiếp tục dựng HTML. Tuy nhiên, ngay khi file JS tải xong, nó sẽ tạm dừng HTML để thực thi JS. Không đảm bảo thứ tự thực thi. File nào tải xong trước sẽ chạy trước.
  `<script src="my-js-file.js" async></script>`
- **defer**: Trình duyệt tải file JS song song với việc dựng HTML nhưng chỉ thực thi JS sau khi HTML đã được dựng xong hoàn toàn (ngay trước sự kiện DOMContentLoaded).
  `<script src="my-js-file.js" defer></script>`

---

## Web Optimization

### I. Image Optimization

1. Luôn set width hoặc / và height cho image
2. Media assets and licensing
