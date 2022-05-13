# Modifiers

## List
내용이 목록을 구성하고 있다면 각 목록에 대해서도 스타일 적용이 가능하다.
```tsx
<ul>
  {[1, 2, 3, 4].map((i) => (
    <div
      key={i}
      className="flex justify-between my-2 odd:bg-blue-50 even:bg-yellow-50 first:bg-teal-50 last:bg-amber-50"
    >
      <span className="text-gray-500">Grey Chair</span>
      <span className="font-semibold">$19</span>
    </div>
  ))}
</ul>
```
- `odd:` 홀수 요소에 적용
- `even:` 짝수 요소에 적용
- `first:` 첫 번째 요소에 적용
- `last:` 마지막 요소에 적용

```tsx
<ul>
  {["a", "b", "c", ""].map((c, i) => (
    <li className="bg-red-500 py-2 empty:hidden" key={i}>
      {c}
    </li>
  ))}
</ul>
```
- `empty:` 빈 요소에 대해서도 적용이 가능하다.