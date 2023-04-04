# Custom hook React

useAuth.js

      export default function useAuth() {
          {your work }
        return false;
      }
      
      
private route {where we use useAuth hook}

        import { Navigate, Outlet } from "react-router-dom";
        import useAuth from ".././hook/useAuth.js";
        import Login from "../value/Login.js";

        export default function PrivateRouteMade({ children }) {
          const auth = useAuth();

          return auth ? children : <Navigate to="/login"></Navigate>;
        }


