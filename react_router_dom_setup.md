# React Router Dom, is only for React Application

I am setting this up in a react app, which was created through vite.

install react router dom
npm i react-router-dom

now, go to main.tsx
import {BrowserRouter} from 'react-router-dom'

now, wrap your <App /> component with BrowserRouter

now, go to App.tsx file
import {Routes, Route} from 'react-router-dom'

to create a router
first, all your routes should be wrapped with Routes Component, that we imported from react-router-dom

to create a single route
<Route path="/" element={<Home />} />

to navigate btw screens, use Link component, import it from react-router-dom
import {Link} from 'react-router-dom'

to use Link Component

<Link to="/login">Login</Link>

## Dynamic Route

to create a dynamic route,
<Route path="book/:id" element={<Some />} />

to get the id, there is an hook, useParams()
import {useParams} from react-router-dom

const {id} = useParams()

## Nesting of Routes

React Router dom allows to nest routes
Company
New Company
Edit Company

<Route path="/company">
    <Route index element={<Company />} />
    <Route path="new" element={<NewCompany />} />
    <Route path="edit" element={<EditCompany />} />
    <Route path=":id" element={<EditCompany />} />
</Route>

you can add element to the parent route, to kind of define same layouts for the child Routes
make sure in the element of parent, a Component called Outlet should be used, to render the current Route Element

import {Outlet} from 'react-router-dom'
