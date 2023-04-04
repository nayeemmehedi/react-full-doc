# react-doc

basic synchronous

      import React, { createContext, useContext } from 'react';

      const MyContext = createContext();

      function MyProvider(props) {
        return <MyContext.Provider value={{ data: 'Hello World' }}>{props.children}</MyContext.Provider>;
      }

      function MyComponent() {
        const { data } = useContext(MyContext);

        return <div>{data}</div>;
      }

      function App() {
        return (
          <MyProvider>
            <MyComponent />
          </MyProvider>
        );
      }

      export default App;
      
      
  basic asynchronous
  

      import React, { createContext, useState, useEffect } from 'react';

    const MyContext = createContext();

    function MyProvider(props) {
      const [data, setData] = useState([]);

      useEffect(() => {
        // Fetch data from the backend
        fetch('/api/data')
          .then((response) => response.json())
          .then((data) => setData(data));
      }, []);

      return <MyContext.Provider value={{ data }}>{props.children}</MyContext.Provider>;
    }

    function MyComponent() {
      const { data } = useContext(MyContext);

      return (
        <div>
          {data.map((item) => (
            <div key={item.id}>{item.name}</div>
          ))}
        </div>
      );
    }

    function App() {
      return (
        <MyProvider>
          <MyComponent />
        </MyProvider>
      );
    }

    export default App;


