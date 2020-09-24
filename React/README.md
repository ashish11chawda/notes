# React

*A JavaScript Library for building user interfaces.*
**React is not a framework but because of its applications it is considered one.**
> Developed by facebook in 2011.

*In a React application, we make bunch of reusable, independent and isolated components*

*Components are a piece of UI which are composed together to make complex user interfaces*

```javascript
//a UI component
<x>

</x>
```
*Every React application has a root component which is usually termed as "App" - this component contains entire application and also other child components*

*Every React application can be said a tree of components with root element on top*

```javascript
    class Component{
        state ={}; /*state is data we want to display
        when the component is rendered on webpage*/
        render() {  
            /*Output of render is a React Element*/
        }
    }
```

*React Element creates a Virtual DOM which maps to DOM Element, which on change of state in virtual DOM, it makes changes in DOM Element which is mapped by Element in virtual DOM*

> "React" is called react because when state changes it reacts and makes changes on DOM.

```bash
npm i -g create-react-app
```
| npm | i | -g | create-react-app |
| :--:  | :-: | :-: | :--------------: |
| command | install | Global | option |
