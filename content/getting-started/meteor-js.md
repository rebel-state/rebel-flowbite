---
layout: home
title: Tailwind CSS Meteor.js - Flowbite
description: Learn how to install Tailwind CSS with Flowbite for your Meteor.js project to build full-stack JavaScript or TypeScript web, mobile, and desktop applications 
group: getting-started
toc: true
requires_meteorjs: true

previous: Remix
previousLink: getting-started/remix/
next: Gatsby
nextLink: getting-started/gatsby/
---

[Meteor.js](https://meteor.com/) is a full-stack JavaScript platform for developing modern web and mobile applications. Meteor includes a key set of technologies for building connected-client reactive applications, a build tool, and a curated set of packages from the Node.js and general JavaScript community.

- Meteor allows you to develop in one language, JavaScript, in all environments: application server, web browser, and mobile device.

- Meteor uses data on the wire, meaning the server sends data, not HTML, and the client renders it.

- Meteor embraces the ecosystem, bringing the best parts of the extremely active JavaScript community to you in a careful and considered way.

- Meteor provides full stack reactivity, allowing your UI to seamlessly reflect the true state of the world with minimal development effort.

Using both Meteor.js, Tailwind CSS and Flowbite can help you get started building modern UI web applications by leveraging the extensive framework features of Meteor.js, the utility-first approach of the Tailwind CSS framework and the open-source UI components from the Flowbite Library.

## Requirements

Make sure that you have [Node.js v14](https://nodejs.org/en/) installed on your computer to be able to install Meteor.js, Tailwind CSS and Flowbite using NPX and NPM.

For more information on how to install Meteor.js, check out the [official installation guide](https://docs.meteor.com/install.html#prereqs).

## Create a Meteor.js project

The easiest way to create a new Meteor.js project is by first installing the CLI globally:

```bash
npm install -g meteor
```

After you have `meteor` available in your terminal you can go ahead and create a new project:

```bash
meteor create flowbite-app --tailwind      
cd flowbite-app
```

This will create a new `meteor` project with `tailwindcss` support and no extra configuration is needed as we added the `--tailwind` flag when setting up the project.

Now that you have created a new Meteor.js project with Tailwind CSS configured automatically we can proceed with installing Flowbite and Flowbite React to start leveraging the open-source UI components.

## Install Flowbite

[Flowbite](https://flowbite.com/) is an open-source UI component library based on the Tailwind CSS utility-first framework featuring hundreds of components like dropdowns, modals, navbars, datepickers, and more that you can leverage to quickly build modern web applications.

1. The first step is to install Flowbite and Flowbite React via NPM:

```bash
npm install --save flowbite flowbite-react
```

2. Make sure that you set up the Flowbite plugin and template paths in your `tailwind.config.js` file:

```javascript
module.exports = {
  content: [
    "./imports/ui/**/*.{js,jsx,ts,tsx}",
    "./client/*.html",
    "node_modules/flowbite-react/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [require("flowbite/plugin")],
};

```

3. Now that you have installed the Flowbite packages you can start importing the UI components:

```javascript
import { Alert } from "flowbite-react";

export default function MyPage() {
  return <Alert color="info">Alert!</Alert>;
}
```

The code above will import the `<Alert>` component that you can use to send feedback messages.

## Flowbite UI components

To get you started you can check out the full collection of React components from the [Flowbite React repository](https://github.com/themesberg/flowbite-react) and [browse the documentation](https://www.flowbite-react.com/docs/getting-started/introduction) for the source code of each component.

Here's an example of how you can use the modal and button components by importing them from the Flowbite React package inside your Meteor.js project:

```javascript
import { Button, Modal } from 'flowbite-react';

export default function DefaultModal() {
  const [openModal, setOpenModal] = useState<string | undefined>();
  const props = { openModal, setOpenModal };

  return (
    <>
      <Button onClick={() => props.setOpenModal('default')}>Toggle modal</Button>
      <Modal show={props.openModal === 'default'} onClose={() => props.setOpenModal(undefined)}>
        <Modal.Header>Terms of Service</Modal.Header>
        <Modal.Body>
          <div className="space-y-6">
            <p className="text-base leading-relaxed text-gray-500 dark:text-gray-400">
              With less than a month to go before the European Union enacts new consumer privacy laws for its citizens,
              companies around the world are updating their terms of service agreements to comply.
            </p>
            <p className="text-base leading-relaxed text-gray-500 dark:text-gray-400">
              The European Union’s General Data Protection Regulation (G.D.P.R.) goes into effect on May 25 and is meant to
              ensure a common set of data rights in the European Union. It requires organizations to notify users as soon as
              possible of high-risk data breaches that could personally affect them.
            </p>
          </div>
        </Modal.Body>
        <Modal.Footer>
          <Button onClick={() => props.setOpenModal(undefined)}>I accept</Button>
          <Button color="gray" onClick={() => props.setOpenModal(undefined)}>
            Decline
          </Button>
        </Modal.Footer>
      </Modal>
    </>
  )
}
```

Here's another example of how you can use the dropdown component:

```javascript
import { Dropdown } from "flowbite-react";

<Dropdown label="Dropdown button">
  <Dropdown.Item>
    Dashboard
  </Dropdown.Item>
  <Dropdown.Item>
    Settings
  </Dropdown.Item>
  <Dropdown.Item>
    Earnings
  </Dropdown.Item>
  <Dropdown.Item>
    Sign out
  </Dropdown.Item>
</Dropdown>
```

Finally, another example on how you can use the navbar component:

```javascript
import { Navbar } from "flowbite-react";

<Navbar
  fluid={true}
  rounded={true}
>
  <Navbar.Brand href="https://flowbite.com/">
    <img
      src="https://flowbite.com/docs/images/logo.svg"
      className="mr-3 h-6 sm:h-9"
      alt="Flowbite Logo"
    />
    <span className="self-center whitespace-nowrap text-xl font-semibold dark:text-white">
      Flowbite
    </span>
  </Navbar.Brand>
  <Navbar.Toggle />
  <Navbar.Collapse>
    <Navbar.Link
      href="/navbars"
      active={true}
    >
      Home
    </Navbar.Link>
    <Navbar.Link href="/navbars">
      About
    </Navbar.Link>
    <Navbar.Link href="/navbars">
      Services
    </Navbar.Link>
    <Navbar.Link href="/navbars">
      Pricing
    </Navbar.Link>
    <Navbar.Link href="/navbars">
      Contact
    </Navbar.Link>
  </Navbar.Collapse>
</Navbar>
```

To learn more about Flowbite React make sure to check out to the [repository](https://github.com/themesberg/flowbite-react) and the [main website](https://flowbite-react.com/).

## Meteor.js starter project

The Flowbite and Meteor community has created an open-source Meteor.js starter project that has Tailwind CSS and Flowbite React set up beforehand and you can go ahead and clone it by checking out the official [repository on GitHub](https://github.com/meteor/flowbite-meteor-starter).