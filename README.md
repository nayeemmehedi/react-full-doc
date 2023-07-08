# react-router-6

## basic example

import { BrowserRouter, Routes, Route } from "react-router-dom";

function App() {
  return (
   
      <Routes>
        <Route path="/" element={<h1>Hello World</h1>}></Route>
      </Routes>
  
  );
}

export default App;


##### $index js 

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
   
   
   
   import { NavLink } from "react-router-dom";
             
                
       <NavLink to ="/app"  className={(info)=>info.isActive ? "text-danger":"text-light"}>App</NavLink>
  
  
  ## child router
  
 ######  rules 1 : 
  
  app.js 
  
            <Routes>
              
                <Route path="/hello/*" element={<Hello></Hello>}></Route>
              </Routes>
              
   Hello.js
   
              <Routes>
                <Route path="/child" element={ <p>Hello child</p>}></Route>
              </Routes>
              
    
######  rules 2 : 

        <Route path="/hello/*" element={<Hello></Hello>}>
                  <Route path="child" element={<p>Hello child</p>}></Route>
        </Route>
        
        import { Outlet } from "react-router-dom";
        
         <Outlet></Outlet>
         
         
## back Process 
import { useNavigate } from "react-router-dom";

    useHistory die now useNavigate
    
    const navigate = usenavigate()
    
    navigate("app")
    navigate(-1)
    
    
    
    
         


       
