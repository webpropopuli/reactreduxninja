Last stop point: https://www.youtube.com/watch?v=5QwNCX3UbXc&index=10&list=PL4cUxeGkcC9ij8CfkAY2RAGb-tmkNwQHG

#Working through the React Tutorial
## Weds: create-react-app
    1) npx create-react-app todothing (5 minutes, go get coffee)

 public/ is where app served from to browser
 src/ is where we work
 app runs from index.html in public which defines 
    <div id="root"></div>
    The entire app runs in this div element. (SPA)

 Components are init'ed in app.js and the app runs from index.js
 App.js is the "root component". Other components are "nested" in it

 The flow:```
    [public/index.html]
        <body>
            <div id="root"></div>```

    [src/app.js]```
        class MyApp extends Component {
          render() {   // only required fn
            return (...
              <div className="App">  //NB: 'className' replaces HTML 'class' (hmmm, so what about 'id'?)
        then made available by
            export default MyApp;```

    [src.js]
        import ReactDOM from 'react-dom';
        import './index.css';
        import MyApp from './MyApp';

        ReactDOM.render(<MyApp />, document.getElementById('root'));

## PROPS
   Data flows down from parent to children. Watch the 'myTitle' string become a 'prop' ro 'Welcome':
```
   const myTitle = "The super awesome React Thing!!"

    class App extends Component {  //   also ....extends React.Component
      render() {       
        return (
          <div className="App">
            <header className="App-header">
              <Welcome text={myTitle}/>         // SEE? test is a prop of Welcome
            </header>
          </div>
        );  } }

class Welcome extends Component {   // Welcome is a child prop of App
  render() {
    return(
      <h1 className="App-title">{this.props.text}</h1>   // AND IT LIVES HERE
    )
  }
}
```

## STATE
Keep track of things. Allows dynamice components. Toggle is good example.
Not setting in constructor anymore

## LIFECYCLE METHODS
Phases that trigger events. constructor(), componentWillMount(), ..WillReceiveProps(), ..ShouldComponentUpdate(), ..WillUpdate(), ..DidUpdate(), ..WillUnmount(), ..ComponentDidCatch(), et al
  ```//LIFECYCLE parts
  constructor(props) {
    console.log('construct');
    super(props);
    //use props here, but we are going to set state as below, so unused.
  }

  componentWillMount() {        // PRE RENDER. State changes here don't trigger redraws
    console.log('Will mount')   }

  componentDidMount() {           // AFTER RENDER
    console.log('Did mount')   }
```
## REFS
Like a reference to a DOM element
