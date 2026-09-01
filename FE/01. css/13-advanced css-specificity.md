## Advanced CSS (6) - Specificity

### Specificity란? - 명시도

이 선택자가 얼마나 구체적으로 특정 요소를 가리키고 있는지?

```html
<p class="text">Hello</p>
```

```css
p {
  color: blue;
}

.text {
  color: red;
}
```

- 둘 다 `<p>` 에 적용되는데 결론적으로 red가 적용
- `.class` > `element` = Specificity가 높다.
- `Inline style` > `ID selector` > `Class selector`, `Attribute`, `Pseudo-class` > `Element`, `Pseudo-element`
- `* {}` : Specificity 0

### Specificity 계산

```css
(A, B, C)

0 = Inline
A = ID
B = Class / Attribute / Pseudo-class
C = Element / Pseudo-element
```

```css
#title -> (1, 0, 0)
.title -> (0, 1, 0)
p -> (0, 0, 1)
```

- 일 경우 단순히 숫자를 전부 더해서 비교하는 것이 아니라,
- 각 자리의 중요도로 비교

#### Inline style

```html
<p style="color: green;" class="text">Hello</p>
```

- `style=""` 은 일반적인 Specificity 계산을 하지 않고, 별도의 매우 높은 우선순위 영역
- `!important`, `@layer` ≄ Specificity
