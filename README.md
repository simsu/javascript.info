# javascript.info
translation page


[원본 링크] (https://ko.javascript.info/custom-elements)

# Custom elements

우리는 우리의 클래스에 자기 자신의 메서드와 속성, 이벤트 등을 가지는 클래스 커스텀 HTML element를 만들 수 있습니다.

커스텀 element가 선언되면 우리는 그것을 내장 HTML element와 똑같이 사용할 수 있습니다.

HTML 사전은 충분히 많은 것을 제공하지만 무한하지는 않습니다. ```<easy-tabs>``` 라던가 ```<sliding-carousel>```, ```<beautiful-upload>``` 같은 태그들은 존재하지 않습니다. 그저 우리가 필요로 하는 다른 태그들을 생각해보세요.

우리는 특별한 클래스를 정의한 다음 그것들을 HTML의 일부분이었던 것처럼 사용할 수 있습니다.

커스텀 elements엔 두 가지가 있습니다:

<strong>Autonomous custom elements</strong> – 추상 ```HTMLElement``` 클래스를 확장한 “모든-새로운” elements.

<strong>Customized built-in elements</strong> – ```HTMLElement``` 등에 기반을 둔, 커스터마이징한 버튼같은 내장 elements를 확장한 elements.

먼저 우리는 autonomous elements에 대해 알아보고, 커스터마이징된 내장 element를 알아볼 것입니다.

맞춤 element를 만들기 위해서 우리는 브라우저에게 그것에 대한 몇가지 세부사항들을 알려주어야 합니다. 어떻게 보여지는지, element가 페이지에서 추가되거나 삭제되는 경우 무엇을 하는지 등.

그것은 특별한 메서드들을 클래스에 추가하면 됩니다. 그것은 메서드들은 거의 없고, 대부분 선택사항이기 때문에 매우 간단합니다.

다음은 전체 예시입니다:
