# react-router-6

//index js 

        import { BrowserRouter } from "react-router-dom";

        const root = ReactDOM.createRoot(document.getElementById("root"));
        root.render(
          <BrowserRouter>
            <App />
          </BrowserRouter>
        );

        reportWebVitals();





import {BrowserRouter as Router , Routes , Route} from "react-router-dom"

       
        <Routes>
        <Route path ="/" element = {<p>Hello world</p>}>
        <Route>
        </Routes>

import { Navigate } from "react-router-dom";

<Navigate to="/dashboard" replace={true} />


<Routes>
        <Route path="/" element={<Navigate to="/app" replace={true} />}></Route>
        <Route path="/app" element={<p className="text-light">app</p>}></Route>
</Routes>


       
