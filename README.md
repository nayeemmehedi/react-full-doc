# redux basic page 1st 

    npm install redux react-redux
    
    
  ### app.reducer.js
  
  
  
    const initialState = { count: 0 };

    export function user_reducer(state = initialState, action) {
      switch (action.type) {
        case 'INCREMENT':
          return { count: state.count + 1 };
        case 'DECREMENT':
          return { count: state.count - 1 };
        default:
          return state;
      }
    }

    const initialStateAge = { name: '', age: null };

    export function userReducer(state = initialStateAge, action) {
      switch (action.type) {
        case 'SET_NAME':
          return { ...state, name: action.payload };
        case 'SET_AGE':
          return { ...state, age: action.payload };
        default:
          return state;
      }
    }
    
    
 ### app.rootUser.js
 
    import { combineReducers } from "redux";
    import { userReducer, user_reducer } from "./app.reducer";

    const rootReducer = combineReducers({
      user: user_reducer,
      counter : userReducer
    });

    export default rootReducer;
    
    
 ### app.store.js
 
 
    import { createStore } from "redux";
    import reducer from "./app.reducer";
    import rootReducer from "./app.rootReducer";

    const store = createStore(
      rootReducer,
      window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
    );

    export default store;
    
    
 ### index.js
  
     import React from "react";
    import ReactDOM from "react-dom/client";
    import "./index.css";
    import App from "./App";
    import reportWebVitals from "./reportWebVitals";
    import { BrowserRouter } from "react-router-dom";
    import { Provider } from "react-redux";
    import store from "./redux/app.store";

    const root = ReactDOM.createRoot(document.getElementById("root"));
    root.render(
      <BrowserRouter>
        <Provider store={store}>
          <App />
        </Provider>
      </BrowserRouter>
    );

    reportWebVitals();
    
    
  
 ### app.js
  
    import React from "react";
    import { useSelector, useDispatch } from "react-redux";

    function App() {
      const count = useSelector((state) => state.user.count);
      const user = useSelector(state => state.counter);
      const dispatch = useDispatch();

    console.log("jj",user)

    return (
      <div>
        <p>Count: {count}</p>
        <button onClick={() => dispatch({ type: "INCREMENT" })}>Increment</button>
        <button onClick={() => dispatch({ type: "DECREMENT" })}>Decrement</button>


        <br />
        <input type="text" placeholder="Name" value={user?.name} onChange={e => dispatch({ type: 'SET_NAME', payload: e.target.value })} />
        <input type="number" placeholder="Age" value={user?.age} onChange={e => dispatch({ type: 'SET_AGE', payload: parseInt(e.target.value) })} />
        <br />
        <p>Name: {user.name}</p>
        <p>Age: {user.age || '-'}</p>
      </div>
    );
  }

  export default App;








