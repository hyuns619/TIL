# DOCTYPE

Document Type의 약자로, **HTML이 어떤 버전으로 작성되었는지 미리 선언하여 웹 브라우저가 해당 버전에 맞는 방법으로 해석할 수 있도록 해주는 것이다.** `<!DOCTYPE>` 으로 선언하는데 선언을 하지 않으면 **호환 모드(quirks mode)** 로 동작한다. 호환 모드로 동작할 경우 각 브라우저마다 문서를 나타내는 방식이 다르기 때문에 크로스 브라우징 이슈가 나타날 수 있다.

# DTD(Document Type Definition)

DTD(Document Type Definition)란 문서 형식을 정의해놓은 것으로 DOCTYPE을 명시할 때 사용한다. 즉, HTML 문서가 어떤 문서 형식을 따르는지 DOCTYPE에서 DTD를 지정하는 것이다.

예시로 아래와 같은 것들이 있고 [W3C Recommended list of Doctype declarations](https://www.w3.org/QA/2002/04/valid-dtd-list.html) 에서 더 자세하게 확인할 수 있다.

- XHTML 1.1
- XHTML 1.0
  - Strict DTD
  - Transitional DTD
  - Frameset DTD
- HTML 4.01
  - Strict DTD
  - Transitional DTD
  - Frameset DTD
- HTML 5

현 시점에서 HTML 5의 DTD로 DOCTYPE을 명시하는 것이 제일 바람직하다.

```html
<!DOCTYPE html>
```

## 참고

- [Wikipedia, Quirks mode](https://en.wikipedia.org/wiki/Quirks_mode#Comparison_of_document_types)
- [DOCTYPE(문서형 정의) 선언](https://webdir.tistory.com/40)
- [비표준 모드 quirks mode, 표준 모드 standards mode 차이와 DOCTYPE ](https://aboooks.tistory.com/169)
