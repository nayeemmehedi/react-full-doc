# redux thunk 

    npm install redux react-redux redux-thunk
    
    
 action.js 
 

        export const fetchData = () => {
        return (dispatch) => {
          dispatch({ type: 'FETCH_DATA_START' });
          fetch('https://jsonplaceholder.typicode.com/todos/1')
            .then(response => response.json())
            .then(data => {
              dispatch({ type: 'FETCH_DATA_SUCCESS', payload: data });
            })
            .catch(error => {
              dispatch({ type: 'FETCH_DATA_FAILURE', payload: error });
            });
        };
      };


reducer.js

      const initialState = { loading: false, data: null, error: null };

      function reducer(state = initialState, action) {
        switch (action.type) {
          case 'FETCH_DATA_START':
            return { ...state, loading: true };
          case 'FETCH_DATA_SUCCESS':
            return { ...state, loading: false, data: action.payload };
          case 'FETCH_DATA_FAILURE':
            return { ...state, loading: false, error: action.payload };
          default:
            return state;
        }
      }

      export default reducer;
      
  store.js
  
  
       import { createStore, applyMiddleware } from 'redux';
      import thunk from 'redux-thunk';
      import reducer from './reducer';

      const store = createStore(reducer, applyMiddleware(thunk));

      export default store;


app.js


      import React, { useEffect } from 'react';
      import { useDispatch, useSelector } from 'react-redux';
      import { fetchData } from './actions';

      function App() {
        const dispatch = useDispatch();
        const loading = useSelector(state => state.loading);
        const data = useSelector(state => state.data);
        const error = useSelector(state => state.error);

        useEffect(() => {
          dispatch(fetchData());
        }, [dispatch]);

        if (loading) {
          return <p>Loading...</p>;
        }

        if (error) {
          return <p>Error: {error.message}</p>;
        }

        return (
          <div>
            <p>Data: {data && JSON.stringify(data)}</p>
          </div>
        );
      }

      export default App;


