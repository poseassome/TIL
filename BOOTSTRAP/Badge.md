# Bootstrap
## Badge
[Bootstrap> components> Badges](https://getbootstrap.com/docs/5.1/components/badge/)

```html
<h1>Example heading <span class="badge bg-secondary">New</span></h1>
<button type="button" class="btn btn-primary">
  Notifications <span class="badge bg-secondary">4</span>
</button>
<button type="button" class="btn btn-primary position-relative">
  Inbox
  <span class="position-absolute top-0 start-100 translate-middle badge rounded-pill bg-danger">
    99+
    <span class="visually-hidden">unread messages</span>
  </span>
</button>
```
Button에도 badge를 달 수 있다.
![badge](../images/bs_badge_1.jpg)

## Breadcrumb
이건 잘 사용하지 않지만 홈페이지 depth가 깊어질 수록 그 경로를 표시하기위해서 사용한다.

## Button group
```html
<div class="btn-toolbar" role="toolbar" aria-label="Toolbar with button groups">
  <div class="btn-group me-2" role="group" aria-label="First group">
    <button type="button" class="btn btn-primary">1</button>
    <button type="button" class="btn btn-primary">2</button>
    <button type="button" class="btn btn-primary">3</button>
    <button type="button" class="btn btn-primary">4</button>
  </div>
  <div class="btn-group me-2" role="group" aria-label="Second group">
    <button type="button" class="btn btn-secondary">5</button>
    <button type="button" class="btn btn-secondary">6</button>
    <button type="button" class="btn btn-secondary">7</button>
  </div>
  <div class="btn-group" role="group" aria-label="Third group">
    <button type="button" class="btn btn-info">8</button>
  </div>
</div>
```
![badge](../images/bs_badge_2.jpg)
***