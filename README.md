# things-alarm

## 알람 count를 badge형태로 출력하고 드롭다운으로 알람 리스트를 화면에 출력

### 외부에서 벳지 카운트만 셋업하여사용
Example:

    <things-alarm-badge
      count="10">
    </things-alarm-badge>

*****
</br></br>
### 외부에서 messages을 통한 알람 제공
Example:

    <template is="dom-bind" id ="bind1">
      <things-alarm-badge align="center" id="alarm" messages="[[messages]]"></things-alarm-badge>
      <script type="text/javascript">
        document.getElementById('alarm').messages =[{title : 'message1', created_at : '2017-03-26 12:00:00', content : 'Test'}];
        document.getElementById('bind1').set('messages',[{title : 'message1', created_at : '2017-03-26 12:00:00', content : 'Test'}]);
      </script>
    </template>

*****
</br></br>
### iron-signal을 통한 메시지 제공</br>
iron-signal을 통한 subscribe event listener

        this.fire('iron-signal',{name:'subscribed', data: message})

message는 오브젝트 구조는 아래와 같음

        {
            type: String (badge,popup),
            title: String,
            message: String
        }

[See iron-signals documentation](https://www.webcomponents.org/element/PolymerElements/iron-signals/)

Example:

    <template is="dom-bind" id ="bind2">
      <paper-button onclick="onAddMessage()" raised> add messages</paper-button>
      <script type="text/javascript">
        function onAddMessage(){
          var msg = {title : 'message1', created_at : '2017-03-26 12:00:00', content : 'Test'};
          document.getElementById('bind2').fire('iron-signal',{name:'subscribed',data:{type:'badge', message: msg}})
        }
      </script>
    </template>

## Dependencies

Element dependencies are managed via [Bower](http://bower.io/). You can
install that via:

    npm install -g bower

Then, go ahead and download the element's dependencies:

    bower install

## Playing With Your Element

If you wish to work on your element in isolation, we recommend that you use
[Polyserve](https://github.com/PolymerLabs/polyserve) to keep your element's
bower dependencies in line. You can install it via:

    npm install -g polymer-cli

And you can run it via:

    polymer serve

Once running, you can preview your element at
`http://localhost:8080/components/things-alarm/`, where `things-alarm` is the name of the directory containing it.

things-alarm-badge:
count 횟수를 badge 형태로 출력하고 toggleAlarm()을 통해 count를 초기화 하는 컴퍼넌트

Example:

<template is="dom-bind" id="bind1">
    <things-alarm-badge align="center" id="alarm" messages="[[messages]]"></things-alarm-badge>
    <script type="text/javascript">
    document.getElementById('alarm').messages =['1','2'];
    document.getElementById('bind1').set('messages',['5','6','7'])
    </script>
</template>
