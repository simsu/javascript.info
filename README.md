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


...(중략)


# Rendering order

HTML 파서가 DOM을 생성할 때, element들은 하나씩, 부모부터 자식순으로 실행된다. 예를 들어 ```<outer><inner></inner></outer>```라는 태그가 있다면, ```<outer>``` element가 DOM에 처음으로 생성되고 연결된다. 그리고 그 다음 ```<inner>```가 그 뒤를 따른다.

그것은 custom elements들을 중요한 결과로 이끈다.

예를 들어, custom element가 ```connectedCallback``` 때에 ```innerHTML``` 안으로 접근하려고 한다면, 그것은 아무것도 얻지 못할것이다 :

만약 당신이 그것을 실행한다면, ```alert``` 는 비어있을 것이다.

그것은 DOM이 완성되지 않은 그 시점에서 어떠한 자식도 없기 때문이다. HTML 파서는 custom element인 ```<user-info>```에 연결되고 그것의 자식 element를 만들것이지만, 아직은 아니다.

우리가 custom element에 대한 정보를 넘겨주고 싶다면, 우리는 어트리뷰트를 이용할 수 있다. 그것들은 즉시 사용가능하다.

Or, if we really need the children, we can defer access to them with zero-delay setTimeout.

또는, 우리가 정말로 자식 element를 쓰길 원한다면, 우리는 제로 딜레이를 가진 `setTimeout` 을 defer access할 수 있다.

This works:
 
그것은 효과를 가진다 :
 
 


...(중략)



# Customized built-in elements

우리가 만든 `<time-formmatted>` 같은 새로운 엘리먼트는, 어떠한 semantics와도 연관되어 있지 않다. 그들은 unknown이다. 그들은 검색엔진에 알려지지 않았고, 접근 장치는 그것들을 처리할 수 없다.

하지만 그러한 것들은 중요하다. 예를 들어, 검색 엔진은 우리가 실제로 시간을 보여준다는 사실에 흥미가 있을 수 있다. 그리고 만약 우리가 특별한 어떤 버튼을 만든다면, 왜 존재하는 <button>의 기능을 재사용하지 않겠는가?

우리는 내장된 HTML 엘리먼트들을 커스터마이징하고 상속할 수 있다.
 
 예를 들어, 버튼은 `HTMLButtonElement`의 인스턴스이다. 이를 이용해서 작성해보자.
