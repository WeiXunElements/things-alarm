# things-alarm

An element providing a starting point for your own reusable Polymer elements.

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
