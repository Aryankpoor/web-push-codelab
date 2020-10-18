# octo-notifications
This repo provides the info and structure for creating notifications for web apps made in ionic and javascript frameworks such as react, vue, angular etc.


<hr>

# 1. Overview
Push messaging provides a simple and effective way to re-engage with your users. In this repo, you'll learn how to add push notifications to your web app.

## What you'll learn
- How to subscribe and unsubscribe a user for push messaging
- How to handle incoming push messages
- How to display a notification
- How to respond to notification clicks

## What you'll need
- Chrome 52 or above
- Web Server for Chrome, or your own web server of choice
- A text editor
- Basic knowledge of HTML, CSS, JavaScript, and Chrome DevTools
- The sample code (See Get set up.)

<hr>

<!-- Please dont make any changes in readme.md -->

# 2. Get Set Up

### Download the samle code

You have two options for getting the sample code this codelab:

**1. Clone the Git repository:**
<code>
  git clone https://github.com/GoogleChrome/push-notifications.git
  </code>
  
  you can even clone this repo itself
  
**2. [Download the zip file](https://github.com/googlechrome/push-notifications/archive/master.zip)**

If you download the source as a ZIP file, unpacking it gives you a root folder push-notifications-master

### Install and verify the web server

Though you're free to use your own web server, this codelab is designed to work well with the Web Server for Chrome app. If you don't have that app installed yet, you can get it from the Chrome Web Store:
[Install web server for chrome](https://chrome.google.com/webstore/detail/web-server-for-chrome/ofhbbkphhbklhfoeikjpcbhemlocgigb)

After installing the Web Server for Chrome app, click on the Apps shortcut on the bookmarks bar:

![Apps shortcut](https://developers.google.com/codelabs/push-notifications/img/a80b29d5e878df22.png)

In the Apps window, click the Web Server icon:

![The web server icon](https://developers.google.com/codelabs/push-notifications/img/dc07bbc9fcfe7c5b.png)

You'll see this dialog next, which allows you to configure your local web server:

![configure local web server image](https://developers.google.com/codelabs/push-notifications/img/433870360ad308d4.png)

Click the <strong>Choose folder</strong> button, and select the <code>app</code> folder in the <code>push-notifications</code> folder you downloaded. This enables you to serve your work in progress via the URL shown in the <strong>Web Server URL(s)</strong> section of the dialog.

Under **Options**, check the box next to **Automatically show index.html**, as shown below

![Automatically show index.htmls respective image](https://developers.google.com/codelabs/push-notifications/img/39b4e0371e9703e6.png)

Then stop and restart the server by sliding the **Web Server: STARTED** toggle to the left and then back to the right

![web server: started toggle image](https://developers.google.com/codelabs/push-notifications/img/daefd30e8a290df5.png)

Click the Web Server URL to visit your site in your web browser. You should see a page that looks like this — though your version might show 127.0.0.1:8887 as the address:

![localhost example image](https://developers.google.com/codelabs/push-notifications/img/4525ec369fc2ae47.png)

## Always update the service worker

During development, it's helpful to ensure that your service worker is always up to date and has the latest changes.

To set this up in Chrome:

- Go to the Push Codelab tab.
- Open DevTools: Ctrl-Shift-I on Windows and Linux, Cmd-Option-I on macOS.
- Select the Application panel, click the Service Workers tab, and check the Update on Reload checkbox. When this checkbox is enabled, the service worker is forcibly updated every time the page reloads.

![setup image](https://developers.google.com/codelabs/push-notifications/img/6b698d7c7bbf1bc0.png)

<hr>

# 3. Register a service worker

[completed code](https://github.com/GoogleChromeLabs/web-push-codelab/tree/master/completed/01-register-sw)

In your <code>app</code> directory, notice that you have an empty file named <code>sw.js.</code> This file will be your service worker. For now, it can stay empty. You'll add code to it later.

First, you need to register this file as your service worker.

Your <code>app/index.html</code> page loads <Code>scripts/main.js.</code> You register your service worker in this JavaScript file.

Add the following code to <code>scripts/main.js</code>:


`    if ('serviceWorker' in navigator && 'PushManager' in window) {`   <br>
  `console.log('Service Worker and Push are supported');`<br>
  `navigator.serviceWorker.register('sw.js') `   <br>
  `.then(function(swReg) {`<br>
    `console.log('Service Worker is registered', swReg);`<br>
    `swRegistration = swReg;`<br>
  `})`<br>
  `.catch(function(error) {`<br>
    `console.error('Service Worker Error', error);`<br>
  `});`<br>
`} else {`<br>
  `console.warn('Push messaging is not supported');`<br>
  `pushButton.textContent = 'Push Not Supported';`<br>
`}`<br>

This code checks whether service workers and push messaging are supported by your browser. If they are supported, the code registers your `sw.js` file.

**Try it out**

Check your changes by refreshing the **Push Codelab** tab in the browser.

Check the console in Chrome DevTools for a `Service Worker is registered message`, like so:

![Service worker registered message](https://developers.google.com/codelabs/push-notifications/img/de3ceca91043d278.png)

## Get application server keys

To work with this codelab, you need to generate application server keys. You can do this on the companion site: [To work with this codelab, you need to generate application server keys. You can do this on the companion site: web-push-codelab.glitch.me](To work with this codelab, you need to generate application server keys. You can do this on the companion site: web-push-codelab.glitch.me)

Here you can generate a public and private key pair.

![image](https://developers.google.com/codelabs/push-notifications/img/a1304b99e7b981dd.png)

Copy your public key into `scripts/main.js` replacing the `<Your Public Key>` value:

`const applicationServerPublicKey = '<Your Public Key>';`

Important: You should never put your private key in your web app!

The readme cannot go any longer, it will be hard to read for the users. Visit the ![google codelab of this project](https://developers.google.com/codelabs/push-notifications?return=%2Ftopics%2Fweb&hl=en#0)

All the instructions provided have been given by google team and I did nnot create any of this.
