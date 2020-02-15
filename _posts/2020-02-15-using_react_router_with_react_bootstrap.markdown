---
layout: post
title:      "Using React/Router with React/Bootstrap"
date:       2020-02-15 06:36:31 +0000
permalink:  using_react_router_with_react_bootstrap
---


As I was trying to implement react-bootstrap with my project to speed up the design process while keeping with the Component theme of react I ran into a little bump in the road when I was creating the Nav. How was I going to implement bootstraps components with react-router? The answer was easy to find and cleverly named "react-router-bootstrap". There wasn't much information of how to apply this practically and the one article I did find I don't think implemented it correctly. 

The first step was to install the packages using npm using the following command...

```
npm install -S react-router-bootstrap
npm install react-bootstrap bootstrap

```
Then import the needed modules to the component using react-bootstrap and react-router-bootstrap

```
import Navbar from 'react-bootstrap/Navbar';
import Nav from 'react-bootstrap/Nav';
import { LinkContainer } from 'react-router-bootstrap';
```

I chose this react-bootstrap template to get my Navbar started, there are plenty of different styles to choose from within the react-bootstrap documentation. So this is what I started with. 

```
  <Navbar bg="dark" variant="dark">
    <Navbar.Brand href="#home">Navbar</Navbar.Brand>
    <Nav className="mr-auto">
      <Nav.Link href="#home">Home</Nav.Link>
      <Nav.Link href="#features">Features</Nav.Link>
      <Nav.Link href="#pricing">Pricing</Nav.Link>
    </Nav>
    <Form inline>
      <FormControl type="text" placeholder="Search" className="mr-sm-2" />
      <Button variant="outline-info">Search</Button>
    </Form>
  </Navbar>
```
The next step was to figure out how to make the links clickable, get them to go to the route you want, while also preventing the app from reloading. That's where react-router-boostrap comes to the rescue. The way I achieved this is removing the href completely from the Nav.Link component, and then wrapping the Nav.Link inside if LinkContainer provided by react-router-boostrap like so...

```
<Navbar bg='dark' variant='dark'>
	<LinkContainer to='/'>
		{' '}
		<Navbar.Brand>Navbar</Navbar.Brand>{' '}
	</LinkContainer>

	<Nav className='mr-auto'>
		<LinkContainer to='/home'>
			{' '}
			<Navbar.Link>Home</Navbar.Link>{' '}
		</LinkContainer>
		<LinkContainer to='/features'>
			{' '}
			<Navbar.Link>Features</Navbar.Link>{' '}
		</LinkContainer>
		<LinkContainer to='/pricing'>
			{' '}
			<Nav.Link>Pricing</Nav.Link>
		</LinkContainer>
	</Nav>
</Navbar>;
```

And that's it nice and simple!
