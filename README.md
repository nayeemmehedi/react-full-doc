# Error Boundary React

ErrorBoundary.js

      import React, { useState } from 'react';

      function ErrorBoundary(props) {
        const [hasError, setHasError] = useState(false);

        function handleOnError(error, info) {
          // Log the error to an error reporting service
          console.error('Error Boundary caught an error:', error, info);

          // Set the hasError state to true
          setHasError(true);
        }

        if (hasError) {
          // Fallback UI when an error occurs
          return (
            <div>
              <h1>Something went wrong.</h1>
              <p>Please try again later.</p>
            </div>
          );
        }

        // Render children if no error occurred
        return (
          <React.Fragment>
            {props.children}
          </React.Fragment>
        );
      }

      export default ErrorBoundary;
      
 app.js
      
      
      import React from 'react';
import ErrorBoundary from './ErrorBoundary';
import MyComponent from './MyComponent';

function App() {
  return (
    <ErrorBoundary>
      <MyComponent />
    </ErrorBoundary>
  );
}

export default App;

