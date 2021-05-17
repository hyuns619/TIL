# 나만의 커밋 메시지 가이드

> 올바른 커밋 메시지 작성을 위해서 나만의 컨벤션을 작성합니다.

# 작성법

모든 커밋 메시지는 아래와 같이 세 영역으로 구성된다.

```
제목 : Type : 본문에 대한 요약

본문 : 전체적인 내용

꼬리말
```

**제목**

- 제목은 대문자로 시작하며 50자 이내로 작성한다.
- 제목의 끝에 마침표(.)를 붙이지 않는다.
- 과거시제를 사용하지 않는다.

**본문**

- 제목과 구분되기 위해 한 칸을 띄워서 작성한다.
- 부연 설명이 필요할 때, 72자를 내에서 작성한다.
- 본문에 여러 줄을 작성할 땐, 문장부호(-)로 구분한다.

**꼬리말**

- 선택사항으로 이슈 트래커 ID를 작성한다.
- 꼬리말은 "유형 : #이슈번호" 형식으로 사용한다.
- 여러 개의 이슈 번호는 쉼표로 구분한다.

## 코드를 보지 않고도 변경 사항이 무엇을 하는지 알 수 있도록 하기

```
# 올바른 커밋 메시지

Credit 모델에 use 메서드 추가

Add : use method to Credit model
```

```
# 조금 아쉬운 커밋 메시지

Add use method
```

```
# 올바른 커밋 메시지

텍스트 상자와 레이아웃 프레임 사이 왼쪽 간결 늘림

Increase left padding between textbox and layout frame
```

```
# 나쁨

CSS 조정

style : Adjust css
```

커밋 히스토리를 보고 어떠한 작업을 하려고 했는지 알 수 있도록 커밋 단위를 나누는 연습과 의미 있는 커밋을 작성하려고 노력해야 한다.

## 커밋 타입

- **add** : 기능 추가
- **delete** : 기능 삭제
- **modify** : 기능 수정
- **fix** : 버그 수정
- **docs** : 문서 수정 (markdown) / 코드 수정 없음
- **style** : css, 정렬, 주석 변경, 세미콜론 추가 등
- **refactor** : 코드 리팩토링
- **test** : 테스트 코드와 관련된 모든 변경
- **etc** : 빌드 업무 수정, 패키지 매니저 수정 외 위에 해당하지 않는 모든 변경

## Reference

- [좋은 git 커밋 메시지를 작성하기 위한 7가지 약속](https://meetup.toast.com/posts/106)<br>
- [커밋 메시지 가이드](https://github.com/RomuloOliveira/commit-messages-guide/blob/master/README_ko-KR.md)<br>
- [Udacity 커밋 메시지 스타일 가이드](https://udacity.github.io/git-styleguide/)<br>
- [깃허브로 취업하기](https://sujinlee.me/professional-github/)
