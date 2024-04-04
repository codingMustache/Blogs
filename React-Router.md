# What is React Router

React router is a one of the greatest tool for using react, also one of the intuitive tools for react to use. React Router is a tool to mark your components to endpoints without using your server do that for you. React Router is a sense acts like a server itself, you can pass things down like you could with a request parameter or in a request body in a AJAX request. This can do really nice things to make your webapp do things like building a navigation bar or build components that can be linked through other elements on your page. Another great use is building a 404 page that can catch a user trying to reach your page with a bad endpoint as to not lead them to an bad request page given from the browser. I expect the reader of this blog top understand React basics and I wont get deep into building a react app.


# Setting Up Routes

Setting up pretty straight forward, you will need to set up the routes in your root component. For the sake of explaining I will refer to the root component as `App.jsx` but the same applies for `.tsx` and whatever you might want to call your parent component. You will also need a component to show your navigation bar that I will refer as `Nav-bar.jsx`. `App.jsx` will hold your routes and render your `Nav-bar.jsx`, and your `Nav-bar.jsx` will render the links of your components and the child components that the user has clicked. You will want to also add routes that will also not be in your `Nav-bar.jsx` but wish to render through another component. You will have to install react router into your `package.json` with this command:
```
npm install react-router-dom
```
After installing this package and setting up your `index.jsx`, you can start building out your route. `App.jsx` will look similar to this:
```js
// Required dependencies
import { BrowserRouter, Routes, Route } from "react-router-dom";
// Component that you want to build routes to
import Nav-bar from "./pages/Nav-bar";
import Home from "./pages/Home";
import Page1 from "./pages/Page1";
import Page2 from "./pages/Page2";
import 404Page from "./pages/404Page";

const App = () => (
     <BrowserRouter>
    <!--Renders nav bar -->
          <Nav-bar />
          <Routes>
               <!-- This is the route to your main page-->
               <Route path="/" element={<Home />}>
               <Route path="page1" element={<Page1 />} />
               <!--Path with a id will act as a query param-->
               <Route path="page2:id" element={<Page2 />} />
               <!--This is a catch all route-->
               <Route path="*" element={<404Page />} />
          </Routes>
    </BrowserRouter>
)
```
Next thing to do is setup your navigation or `Nav-bar.jsx`:
```js
import { Outlet, Link } from "react-router-dom";

const Nav-Bar = () => (
  <>
    <nav>
      <ul>
        <!--Sets up links to components-->
        <li>
          <Link to="/">Home</Link>
        </li>
        <li>
          <Link to="/pothole">page1</Link>
        </li>
      </ul>
    </nav>
    <!--This render clicked component-->
    <Outlet />
  </>
)
```
`App.jsx` will render the `Nav-bar.jsx` as an `ul`. As you clicked through the `li` it will render clicked component. `404Page` and `Page2` are not on the `Nav-bar` for different reasons. The `404Page` will render is the user tries to goto a endpoint that does not exist. `Page2` has a `:id` in its route path and this can be used on page one to pass down props into from another route.




# Pass down Props and State

Passing down props can be really useful tool in your react tool belt. You may want to pass down something like a string that user might have inputted in a form. Lets setup `Page1` to pass down a prop down to `Page2`.
`Page1.jsx`:
```js
import { Link } from "react-router-dom";

const Page1 = () =>{
     const [user, setUser] = useState(
          {
               id: 123,
               userName: 'Jane Smith'
          }
     );
     return (
          <Link to={'/page2:' + user.id } >
               <button>Submit</button>
          </Link>
     )
}
```
This is taking the state object and passing down the `id` value to the `Page2` component. To receive the prop in `Page2`:
```js
import {useLocation} from 'react-router-dom';

const Page2 = () =>{
     const id = useLocation().pathname.split(':')[1];
     return(
          <>
               { id }
          </>
     )
}
```
`Page2` will render 123 on the page that is passed down from `Page1`. Using the `useLocation` object at the key of `pathname` will give you what component was passed down from and the prop that was passed down with it. By splitting it at the colon and taking the `1` index will give you the prop that was passed down. Alternatively you can pass down state this can be useful if you plan on passing down a larger object than just a string. If you change the `<Link>` on `Page1` to this:
```js
<Link to="/page2" state={user}>
     <button>Location</Button>
</Link>
```
To receive the state from `Page2`:
```js
import { useLocation } from 'react-router-dom';

const Page2 = () =>{
     const location = useLocation();
     const user = location.state;
     return(
          <p>
               { user.id }
               { user.name }
          </p>
     )
}
```
This will pass down the whole user object down from `Page1` down to `Page2`. This is really useful if you want pass down larger objects than just a string. Both methods have their own use cases depending on what you are doing and what you need done.



React Router is a great and need to use piece of technology that is essential to understand how to use in order to build a good react app. Not only is it great to add endpoints to your pages on your react app but it is one of the most intuitive tools to use. There are so many other great things that you can use React Router can do, I would suggest looking at the helpful links to take a deeper dive and feel free to reach out to me through any of my social links, if you find something that you learned about React Router that you love.


# Helpful Links

[W3 Schools](https://www.w3schools.com/react/react_router.asp)

[React Router Docs](https://reactrouterdotcom.fly.dev/docs/en/v6)

[Tyler McGinnis's Blog](https://ui.dev/react-router-tutorial)

[GeeksforGeeks Blog](https://www.geeksforgeeks.org/what-is-react-router-dom/)
