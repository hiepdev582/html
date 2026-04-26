# HTML

## HTML syntax

### I. Web Browsers

Always check web browser support:

1. Chrome
2. Edge
3. Firefox
4. Safari

### II. Semantics

1. **Structuring documents**:
    - `<header>`
    - `<nav>`
    - `<main>` _(unique)_: `<article>`, `<section>`
    - `<aside>`
    - `<footer>`
2. **No Script**:
    ```html
    <noscript>Nội dung hiển thị khi trình duyệt không hỗ trợ JavaScript</noscript>
    ```
3. Dùng thẻ **heading** h1 - h6 hợp lý. Mỗi page phải có thẻ h1 và không nên quá 3 cấp heading
    - Dùng kèm thẻ `<hgroup>`
    ```html
    <hgroup>
        <h1>Tiêu đề chính</h1>
        <p>Mô tả ngắn gọn</p>
    </hgroup>
    ```
4. **Emphasis tag**: em (tông giọng), strong (mức độ quan trọng), mark (đánh dấu)
5. **Abbreviations**:
    - `<abbr title="Viết tắt">Viết tắt</abbr>`
6. **Table**:
    - scope attribute
7. **Picture**:

    ```html
    <picture>
        <source media="(max-width: 599px)" srcset="https://picsum.photos/id/10/400/600" />
        <source media="(min-width: 600px)" srcset="https://picsum.photos/id/10/1200/675" />
        <img
            src="https://picsum.photos/id/10/1200/675"
            alt="Ảnh minh họa"
            style="width: 100%; height: auto; border-radius: 8px"
        />
    </picture>
    ```

8. **Blockquote**:
    - Block: `<blockquote cite="Nguồn trích dẫn">Nội dung trích dẫn</blockquote>`
    - Inline: `<q cite="Nguồn trích dẫn">Nội dung trích dẫn</q>`
    - Link: `<a href="Nguồn trích dẫn"><cite>Nội dung trích dẫn</cite></a>`
9. **Address**:
    - `<address>Địa chỉ</address>`
10. **Time**:
    - `<time datetime="2022-01-01">2022-01-01</time>`
11. **Code**:
    - `<code>Mã code</code>`
    - `<var>Biến</var>`
    - `<kbd>Phím</kbd>`
    - `<samp>Kết quả</samp>`
12. **Figure and caption**:
    - `<figure>`
    - `<figcaption>`
      `<figure><img src="" alt=""><figcaption></figcaption></figure>`
13. **Video**:
    ```html
    <video controls width="400" height="400" autoplay loop muted preload="auto" poster="poster.png">
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
14. **Audio**:
    ```html
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
15. **Template**:

    ```html
    <template id="project-card">
        <div class="card">
            <p class="title"></p>
            <p class="price"></p>
        </div>
    </template>

    <div id="container"></div>
    <script>
        const template = document.querySelector('#project-card');
        const container = document.querySelector('#container');

        // Giả sử nhận dữ liệu từ API
        const projects = [
            { name: 'NHS Trung Văn', price: '19.5tr' },
            { name: 'UDIC EcoTower', price: '20tr' },
        ];

        projects.forEach((p) => {
            // Sao chép nội dung từ template
            const clone = template.content.cloneNode(true);
            clone.querySelector('.title').textContent = p.name;
            clone.querySelector('.price').textContent = p.price;
            container.appendChild(clone);
        });
    </script>
    ```

16. **Slot**:

    ```html
    <template id="user-card-template">
        <style>
            .card {
                border: 1px solid #ccc;
                padding: 15px;
                border-radius: 8px;
                font-family: sans-serif;
            }
            .card-title {
                color: #007bff;
                border-bottom: 1px solid #eee;
            }
        </style>

        <div class="card">
            <div class="card-title">
                <slot name="title">Tiêu đề mặc định</slot>
            </div>
            <div class="card-content">
                <slot>Nội dung mặc định nếu bên ngoài không truyền gì vào.</slot>
            </div>
        </div>
    </template>

    <user-card>
        <h2 slot="title">Dự án NHS Trung Văn</h2>
        <p>Đây là thông tin chi tiết về căn hộ tại Nam Từ Liêm mà bạn đang quan tâm.</p>
        <button>Xem chi tiết</button>
    </user-card>

    <script>
        customElements.define(
            'user-card',
            class extends HTMLElement {
                constructor() {
                    super();
                    const template = document.getElementById('user-card-template');
                    const shadowRoot = this.attachShadow({ mode: 'open' });
                    shadowRoot.appendChild(template.content.cloneNode(true));
                }
            },
        );
    </script>
    ```

17. **Search**:
    ```html
    <search>
        <form action="/search">
            <label for="search">Tìm kiếm:</label>
            <input type="search" id="search" name="search" />
            <button type="submit">Tìm kiếm</button>
        </form>
    </search>
    ```
18. **Menu**:

```html
<menu>
    <button>Button 1</button>
    <button>Button 2</button>
    <button>Button 3</button>
</menu>
```

19. **Details and summary**:
    ```html
    <details>
        <summary>Title</summary>
        <p>Content</p>
    </details>
    ```
20. **Dialog**:

    ```html
    <dialog>
        <p>Content</p>
    </dialog>
    ```

    - Phương thức: `show()`, `showModal()`, `close(value)` (`returnValue`)
    - Pseudo-element: `::backdrop` (dùng cho `showModal()`)
    - Kết hợp với `form` bằng cách dùng `method="dialog"`. Submit tự đóng form và trả ra value

21. **Progress**:
    ```html
    <progress value="50" max="100"></progress>
    ```
22. **Meter**:
    ```html
    <meter value="50" max="100"></meter>
    ```
23. **Definition**:
    ```html
    <dfn>Định nghĩa</dfn>
    ```
24. **Insert and delete**:
    ```html
    <ins>Nội dung</ins> <del>Nội dung</del>
    ```
25. **Math**: Dùng để nhúng các công thức toán học bằng ngôn ngữ MathML
    ```html
    <math>
        <msup>
            <mi>x</mi>
            <mn>2</mn>
        </msup>
        <mo>+</mo>
        <msup>
            <mi>y</mi>
            <mn>2</mn>
        </msup>
        <mo>=</mo>
        <msup>
            <mi>z</mi>
            <mn>2</mn>
        </msup>
    </math>
    ```
26. **Object**:
    ```html
    <object data="file.pdf" type="application/pdf" width="100%" height="500px">
        <p>
            Trình duyệt của bạn không hỗ trợ xem PDF.
            <a href="file.pdf">Nhấn vào đây để tải về.</a>
        </p>
    </object>
    ```
27. **Microdata: itemscope + itemprops + itemtype**
    ```html
    <div itemscope itemtype="https://schema.org/Person">
        <span itemprop="name">John Doe</span>
        <span itemprop="jobTitle">Software Engineer</span>
        <span itemprop="email">[EMAIL_ADDRESS]</span>
    </div>
    ```
28. **Microformats**

**Class:**

- h-\* (Root/Object): Dùng để xác định "Gốc" của một đối tượng (h = hierarchy)
- p-\* (Plain text): Dùng cho dữ liệu dạng văn bản thuần túy
- u-\* (URL): Dùng cho các liên kết hoặc tài nguyên đa phương tiện
- dt-\* (Date/Time): Dùng cho ngày tháng và thời gian
- e-\* (Embedded HTML): Dùng cho các khối nội dung lớn chứa cả mã HTML bên trong

**Rel attribute:**

### III. Data attributes

```html
<div data-id="1" data-name="John">John Doe</div>
```

- Truy cập qua JS: `element.dataset.id` và `element.dataset.name`
- Truy cập qua CSS: `element[data-id="1"]`

### IV. HTML Entities - Character References

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
| ⇒         | Right arrow double    | &rArr;   |
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
| ♥         | Heart                 | &hearts; |
| ♦         | Diamond               | &diams;  |
| ♣         | Clubs                 | &clubs;  |
| ♠         | Spades                | &spades; |

### V. Constraint validation

1. pattern
2. min
3. max
4. required
5. step
6. minLength
7. maxLength

=> **HTMLFormElement**: checkValidity(), reportValidity(), setCustomValidity()

### VI. HTML attributes

1. `fetchpriority`: img, link, script - Value - auto / high / low
2. `tabindex`
3. `accept`: server, input
4. `autocomplete`: Value - on / off / name / email / current-password / new-password / tel / one-time-code
5. `draggable`:
    - Event `dragover`: Trình duyệt mặc định sẽ ngăn cản việc thả dữ liệu vào các phần tử khác. Phải gọi `event.preventDefault()`. trong sự kiện `ondragover` thì sự kiện `ondrop` mới có thể xảy ra
    - Object `dataTransfer`: Nơi chứa dữ liệu đang được kéo. Có thể dùng nó để truyền thông tin (như ID, chuỗi văn bản, hoặc file).
    - UX: Nên thay đổi con trỏ chuột trong CSS (`cursor: move;`) để người dùng biết phần tử đó có thể tương tác được.
6. `translate`: Mặc định là yes
7. `hidden`
8. `is`
9. `list`: input
10. `role`
11. `accesskey`: Alt + Phím
12. `contenteditable`
13. `autocapitalize`: Chỉ dành cho thiết bị di động (Value - sentences / words / characters / off)
14. `spellcheck`

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
9. application-name
   `<meta name="application-name" content="">`

### II. Applying JS to HTML

- **Mặc định**: Khi trình duyệt đọc đến thẻ script, nó sẽ dừng việc dựng HTML (block parsing) để tải file script về và thực thi nó ngay lập tức. Sau khi xong mới tiếp tục dựng nốt HTML. Điều này khiến trang web bị "đứng" nếu file JS nặng.
  `<script src="my-js-file.js"></script>`
- **async**: Trình duyệt tải file JS trong khi vẫn tiếp tục dựng HTML. Tuy nhiên, ngay khi file JS tải xong, nó sẽ tạm dừng HTML để thực thi JS. Không đảm bảo thứ tự thực thi. File nào tải xong trước sẽ chạy trước.
  `<script src="my-js-file.js" async></script>`
- **defer**: Trình duyệt tải file JS song song với việc dựng HTML nhưng chỉ thực thi JS sau khi HTML đã được dựng xong hoàn toàn (ngay trước sự kiện DOMContentLoaded).
  `<script src="my-js-file.js" defer></script>`

---

## Web Optimization

### I. Fast loading HTML pages

1. Giảm thiểu độ sâu của DOM
2. Luôn sử dụng responsive images
3. Luôn set width và height cho image
4. Dùng `loading="lazy"` cho những hình ảnh không nằm trong vùng nhìn thấy ban đầu
5. Dùng Pre-loading với `rel="preload"` và Pre-fetching `rel="prefetch"`
6. Giảm số lượng HTTP Requests
7. Luôn minify file HTML, CSS, JS
8. Sử dụng CDN
9. Caching

### II. Image Optimization

1. Media assets and licensing
2. Responsive images: `<picture>`, `srcset`, `sizes`
    - `srcset` & `sizes`: Khi chỉ muốn cung cấp các phiên bản to/nhỏ khác nhau của cùng một nội dung ảnh
    - `<picture>`: Khi muốn thay đổi bố cục ảnh (Art Direction) hoặc hỗ trợ nhiều định dạng file khác nhau (WebP, AVIF, JPG)

### III. Media Optimization

1. **Ảnh**: Ưu tiên WebP hoặc AVIF (cho tốc độ load nhanh nhất), dự phòng JPG/PNG
2. **Video**: Ưu tiên WebM cho web hiện đại, dự phòng MP4
3. **Audio**: Ưu tiên Opus (chất lượng cao ở bitrate thấp), dự phòng MP3
