# things-alarm

## 알람 count를 badge 형태로 출력하고, 알람 리스트를 화면에 드롭다운으로 표시한다.

### 외부에서 badge count만 설정하여 사용한다.
Example:

```html
    <things-alarm-badge
      count="10">
    </things-alarm-badge>
```

*****
</br></br>
### 외부에서 message를 통해 알람을 제공한다.
Example:

``` html
    <template is="dom-bind" id ="bind1">
      <things-alarm-badge align="center" id="alarm" messages="[[messages]]"></things-alarm-badge>
      <script type="text/javascript">
        document.getElementById('alarm').messages = [{
            title: 'message1',
            created_at: '2017-03-26 12:00:00',
            content: 'Test'
        }];
        document.getElementById('bind1').set('messages', [{
            title: 'message1',
            created_at: '2017-03-26 12:00:00',
            content: 'Test'
        }]);
      </script>
    </template>
```

*****
</br></br>
### iron-signal을 통해 메시지를 제공한다.</br>
iron-signal을 통한 subscribe event listener

```js
        this.fire('iron-signal',{name:'subscribed', data: message})
```

message의 오브젝트 구조는 아래와 같다.

```js
        {
            type: String, //badge,popup
            title: String,
            message: String
        }
```

[See iron-signals documentation](https://www.webcomponents.org/element/PolymerElements/iron-signals/)

Example:

```html
    <template is="dom-bind" id ="bind2">
      <paper-button onclick="onAddMessage()" raised> add messages</paper-button>
      <script type="text/javascript">
        function onAddMessage() {
            var msg = {
                type: 'badge',
                title: 'message1',
                created_at: '2017-03-26 12:00:00',
                content: 'Test'
            };
            document.getElementById('bind2').fire('iron-signal', {
                name: 'subscribed',
                data: {
                    message: msg
                }
            })
        }
      </script>
    </template>
```

## Dependencies

element의 종속성은 [Bower](http://bower.io/)를 통해 관리되며, 아래의 방법을 통해 설치할 수 있다.

    npm install -g bower

다음, element의 종속성을 다운로드한다.

    bower install

## Playing With Your Element

element를 독립적으로 처리하려면 [Polyserve](https://github.com/PolymerLabs/polyserve)를 사용하여 element의 bower 의존성을 유지하도록 하며, 이는 아래의 방법을 통해 설치할 수 있다.

    npm install -g polymer-cli

그리고, 아래의 방법을 통해 실행할 수 있다.

    polymer serve

element를 실행한 경우, `things-alarm`이 디렉토리 이름으로 포함되어 있는 `http://localhost:8080/components/things-alarm/`을 통해 이를 미리 확인할 수 있다. 
