[WIP]
## DEMO

```
yarn install
yarn start
```

## NOTE: 
after making changes in the **Create React APP** to show case SDK config changes, always do a browser ***empty cache and hard reload***

this hot reloading fix is WIP.


## Usage Guide when doing from scratch in an APP
For using the `EmbedSDK` in your app, you can 

USING AS AN NPM PACKAGE
------------------------
First

    yarn add @epnsproject/frontend-sdk-staging

then


    import { EmbedSDK } from "@epnsproject/frontend-sdk-staging";

then

In `App.js` of your App entry point
add in HTML/JSX the below HTML tag -


    <button id="sdk-trigger-id">trigger button</button>

or any component with the ID ***sdk-trigger-id*** or any ***ID*** but it has to be the same as that passed to the
***targetID*** passed to the `init()` (see below)

After the wallet connect happens in your app flow trigger this. 
**Note:** you have to have wallet connected and the account value to execute the below code because internally the SDK calls the EPNS get_feeds which needs the account address.

```
  useEffect(() => {
    if (account) { // 'your connected wallet address'
      EmbedSDK.init({
        headerText: 'Hello DeFi', // optional
        targetID: 'sdk-trigger-id', // mandatory
        appName: 'consumerApp', // mandatory
        user: account, // mandatory
        viewOptions: {
            type: 'sidebar', // optional [default: 'sidebar', 'modal']
            showUnreadIndicator: true, // optional
            unreadIndicatorColor: '#cc1919',
            unreadIndicatorPosition: 'bottom-right',
        },
        theme: 'light',
      });
    }
  }, []);
```

--

**OR**

--

USING "script" file
-------------------
First,

    <script type="text/javascript" src="./embedsdk.umd.js" defer="defer"></script>

Add in HTML/JSX the below HTML tag-

    <button id="sdk-trigger-id">trigger button</button>```

or any component with the ID ***sdk-trigger-id*** or any ***ID*** but it has to be the same as that passed to the
***targetID*** passed to the `init()` (see below)

After the wallet connect happens in your app flow trigger below code snippet.

**Note:** you have to have wallet connected and the account value to execute the below code because internally the SDK calls the EPNS get_feeds which needs the account address.

```
  useEffect(() => {
    if (account) { // 'your connected wallet address'
      window.EmbedSDK.init({
        headerText: 'Hello DeFi', // optional
        targetID: 'sdk-trigger-id', // mandatory
        appName: 'consumerApp', // mandatory
        user: account, // mandatory
        viewOptions: {
            type: 'sidebar', // optional [default: 'sidebar', 'modal']
            showUnreadIndicator: true, // optional
            unreadIndicatorColor: '#cc1919',
            unreadIndicatorPosition: 'bottom-right',
        },
        theme: 'light',
      });
    }
  }, []);
```

