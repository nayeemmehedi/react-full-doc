# react- private router

1st way to make Private Route

app.js


                <Route path="/*" element={<PrivateRouteMade></PrivateRouteMade>}>
                    <Route path="hello/*" element={<Hello></Hello>}>
                      <Route path="child" element={<ChildValue></ChildValue>}></Route>
                      <Route path="child1" element={<p>hello</p>}></Route>
                    </Route>

                    {/* <Route path="hello" element={<Hello></Hello>}> */}
                    {/* <Route path="child" element={<p>Hello child</p>}></Route> */}
                  </Route>


PrivateRouteMade.js

               import { Navigate, Outlet } from "react-router-dom"
               import useAuth from ".././hook/useAuth.js"
               import Login from "../value/Login.js"

               export default function PrivateRouteMade(){
                  const auth = useAuth()

                  return auth ? <Outlet></Outlet> : <Navigate to ="login"></Navigate>


              }
              
              
useAuth.js


               export default function useAuth(){

                  return false

              }
              
  #### 2nd way to make private router
