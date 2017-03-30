# TypeScript + AngularJS

In the last years AngularJS has stablished itself as the most popular Front-end framework due to features like Data Binding, HTML enhancement, AJAX, and built-in testability. Nevertheless, the open web has shortened the period in which new technologies appear.

Just as this entry is being written a new version of [Angular](http://angularjs.blogspot.mx/2017/03/angular-400-now-available.html) is being released, which adopted two unstoppable trends in the current year, components and TypeScript. The reason for adopting them is mostly scalability since JavaScript and DOM can get very complicated to manage in modern web applications. This is a list of TypeScript features that makes it a great tool for JavaScript development.

### IDE Autocompletion

In the past when it came to JavaScript the IDEs were not very helpful, autocompletion and suggestions were based on what you previously typed, not to talk about methods description or return type. A workaround to this was to install extra modules to the IDE or write references. With typescript you have extensive support for modules, libraries and DOM methods. 

![TypeScript autocompletion](https://github.com/alejandromdz/blog/raw/master/typescript-autocompletion.png "TypeScript autocompletion")

### Static Type checking

While the JavaScript language design originally considered loose typing JS itself was created as a simple scripting language for basic tasks in the web browser (like showing an [ASCII clock tracking your pointer](http://llizard.etherwork.net/cwc/amazing_clock.html)) but now it handles AJAX calls, effects, routing, virtual DOM, and that's only client-wise, with NodeJS the spectrum of JS applications reaches even the Internet of things, with all this in mind the original design just gets in the way with respect of managing a complex code base, ES2015 updated the language specification with many helpful features but it didn't considered variable types other than typed arrays and this is where TypeScript shines, it provides primitive types, access modifiers and interfaces which makes TypeScript a serious Object Oriented language just like Java or C# but with al the benefits of functional programming, (The best of both worlds!).

### ESNext support

Finally, by using TypeScript you have access to the most recent features of JS which can be then transpiled to older JS versions. ReactJS was probably the biggest recipient of ES2015's features such as arrow functions, class declarations and decorators.

```javascript
//ES5
var Button = React.createClass({
  clickHandler: function(e) {...},
  render: function() {...},
});
```
```javascript
//ES6
class Button extends React.Component {
  clickHandler(e) {...}
  render() {...}
}
```

As for AngularJS, ES6 classes were a relief valve to functions which were the commodity for controllers and directives, TypeScript adds more value to class declarations with interfaces which prodive a specification for arguments passed through dependency injection.

```typescript
interface IMainScope extends angular.IScope{
    setLang?(string):void;
}

class MainControl {
    static $inject = ['$scope', '$cookies'];
    constructor(private $scope: IMainScope,
        private $cookies: ng.cookies.ICookiesService) {
        $scope.setLang = (lang:string) => {
            $cookies.put('lang', lang, { path: '/' })
        }
    }
}
```