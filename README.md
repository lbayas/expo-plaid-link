### [](#expo-plaid-link)Expo Plaid Link

Plaid Link is a quick and secure way to integrate with the Plaid API. Here is an Expo component which can be easily drop into your Expo project.

To get started you need to sign up at [https://plaid.com/](https://plaid.com/) for free Palid API keys. This front end component need you put your PUBLIC_KEY in place, and your private key is used at backend to futhur call to get Transactions etc.

Client uses this front end component Plaid Link to establish link with bank and Plaid return a public_token, you send the public_token back to your server to use the public_token with your private key to get an access_token and item_id which you use for access transactions etc.

![expo-plaid-link](https://raw.githubusercontent.com/chentong1966/expo-plaid-link/master/assets/link-example-img.png)

### [](#usage)Usage

    npm i expo-plaid-link

#### [](#api)API

<table>

<thead>

<tr>

<th>Prop</th>

<th>Type</th>

<th>defaultValue</th>

</tr>

</thead>

<tbody>

<tr>

<td>**publicKey** (required)</td>

<td>`string`</td>

<td></td>

</tr>

<tr>

<td>**env** (required)</td>

<td>`string`</td>

<td></td>

</tr>

<tr>

<td>**product** (required)</td>

<td>`string`</td>

<td></td>

</tr>

<tr>

<td>clientName</td>

<td>`string`</td>

<td></td>

</tr>

<tr>

<td>selectAccount</td>

<td>`boolean`</td>

<td>false</td>

</tr>

<tr>

<td>PlaidLinkUri</td>

<td>`string`</td>

<td>'https://cdn.plaid.com/link/v2/stable/link.html'</td>

</tr>

<tr>

<td>webhook</td>

<td>`string`</td>

<td>`'https://requestb.in'`</td>

</tr>

<tr>

<td>onMessage</td>

<td>`function`</td>

<td></td>

</tr>

<tr>

<td>onLoad</td>

<td>`function`</td>

<td></td>

</tr>

<tr>

<td>onReady</td>

<td>`function`</td>

<td></td>

</tr>

<tr>

<td>onAcknowledged</td>

<td>`function`</td>

<td></td>

</tr>

<tr>

<td>onEvent</td>

<td>`function`</td>

<td></td>

</tr>

<tr>

<td>onConnected</td>

<td>`function`</td>

<td></td>

</tr>

<tr>

<td>onExit</td>

<td>`function`</td>

<td></td>

</tr>

</tbody>

</table>

    //******************** Code Smaple *****************************

        import React from 'react';
        import { StyleSheet, Text, View } from 'react-native';
        import PlaidClient from 'expo-plaid-link';

        export default function App() {
          return (
            <View style={{flex: 1}}>
            <Text>Plaid Client</Text>

            <PlaidClient 
              selectAccount="false" 
              env="sandbox" 
              PublicKey="[PUBLIC_KEY]" 
              origin='localhost'
              product="auth,transactions" 
              clientName="Plaid Link" 
              webhook="https://requestb.in"
              PlaidLinkUri='https://cdn.plaid.com/link/v2/stable/link.html' 
              onLoad={onLoad} 
              onEvent={onEvent}
              onConnected={onConnected} 
              onExit={onExit} 
              onReady={onReady} 
              onAcknowledged={onAcknowledged} 
              onMessage={onMessage}
              onPlaidRef={onPlaidRef} 
            />

            </View>
          );
        }

        function onLoad(obj){console.log('call back onLoad:',obj)}
        function onReady(obj){console.log('call back onReady:',obj)}
        function onAcknowledged(obj){console.log('call back onAcknowledged:',obj)}
        function onConnected(obj){console.log('call back onConnected:',obj);}
        function onExit(obj){console.log('call back onExit:',obj)}
        function onEvent(obj){console.log('call back onEvent:',obj)}
        function onMessage(obj){console.log('call back onMessage:',obj)};
        function onPlaidRef(obj){console.log('call back onPlaidRef:',obj)};

    //******************************************************

##### [](#returned-data-object)Returned **data** object

<div class="highlight json">

<pre>    `{
          "action": "plaid_link-undefined::connected",
          "metadata": {
            "account": {
              "id": null,
              "name": null
            },
            "account_id": null,
            "public_token": "public-sandbox-e697e666-9ac2-4538-b152-7e56a4e58888",
            "institution": {
              "name": "Chase",
              "institution_id": "ins_3"
            }
          }
        }` 
  </pre>

</div>

For more information please read [their docs](https://plaid.com/docs/quickstart/#creating-items-with-link-and-the-api)

For test in `Sandbox mode` the credentials are:

        username: user_good
        password: pass_good