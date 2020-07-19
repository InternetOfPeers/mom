# MOM

MOM (My Own Messages) is a cheap, easy and effective Ethereum standard to give voice to your smart contract, send messages to the world, create a certified blog with your ideas, and so on. ERC will be soon submitted.

![Node.js Package](https://github.com/InternetOfPeers/mom/workflows/Node.js%20Package/badge.svg)

## How to use MOM

Install the package with:

```bash
$ npm install @internetofpeers/mom
```
Then in your Javascript file use something like this:

```javascript
// example
const mom = require("@internetofpeers/mom");
const multihashes = require("multihashes");
//...
let senderAddress = "0x....";
let messageHash = "QmbHQieckNGj2KwBhpzkGSLDgezGnArL6eeuvb87YLX665";
let multihash = multihashes.fromB58String(messageHash);
let addTransacion = mom.createAddTransaction("0x", multihash);
//...
```

Check the MOM client example to develop your own _MOM-enabled_ ÐApp:

```bash
$ git clone https://github.com/InternetOfPeers/mom-client.git
$ cd mom-client
$ npm install
$ npm start
```
or see MOM client in action using GitHub servers
- https://internetofpeers.github.io/mom-client

## Project's rationales (WIP)

My Own Messages
"Just say it to MOM"

Create your Ethereum account dedicated to your personal messages
Spread your words to the world
Follow other

And do it all by yourself

How MOM can help me?

You can send messages to users of your ÐApp or Smart Contract, and they always know it is a voice reliable as the smart contract is.
Say once, show everywhere. Say something only once, it can be seen on every social platform (no more reply of the same post/opinion on dozens of sites like reddit, twitter, facebook, medium, disquis, and so on...)

Verificable and decentralized content

Small fee to be free: pay just few cents of dollar to notarize your messages, and distribute them with IPFS or Swarm.

Get tips for your words directly into your wallet.

MOM is already available on every Ethereum network (mainnet, rinkeby, kovan, ecc.): just choose one and you are there.
I don't like to use smart contract if they are not needed. And I want to spend less gas as possible, so MOM transactions acts like this:

- `from`: `MUST` be the tx signer
- `to`: `MUST` be the tx signer
- `value`: `MUST` be 0 wei
- `data`: `MUST` be at least 1 byte. First byte is the code for operation. Then it comes the content.

### MOM v.1.0 - List of standard message types

| OPERATION | CODE | PARAMETERS | MEANING 			|
|--------|:------------:|------------|-------------------|
| ADD | 00       | multihash  | Add a message. The parameter is the multihash of the content. Content default is Markdown text in UTF8 without BOM |
| DELETE | 01	   | multihash | Delete a message identified by the specified multihash |
| UPDATE | 02       | multihash, multihash | Update a message. The first parameter is the message to be updated. The second parameter is the multihash of the updated message |
| REPLY | 03       | multihash, multihash | Reply to a message. The first parameter is the message to reply to. The second parameter is the multihash of the message
| ENDORSE | 04	   | multihash | Endorse a message identified by the specified multihash. Think it as a "like", a "retwitt", etc. |
| DISAPPROVE | 05  | multihash | Disapprove a message identified by the specified multihash. Think it as a "I don't like it" |
| CUSTOM | FE	   | any | Custom MOM specifications
| RAW | FF	   | any | Raw content, no need to disclose the meaning. General client can ignore it.

**DELETE** command? Yeah, it's like: I changed my mind so please ÐApps don't show this anymore, unless expressly asked by the user of course, and if the content is still available, of course.

Why [multihash](https://github.com/multiformats/multihash)? Because it is flexible, future-proof and there are already a tons of library supporting it.

### Don't like default specifications, just choose yours
FE - Define your own specification. If you encounter FE again, you read the next byte to know the message type, and so on..
If you find FE it means user want to define it's own MOM specifications and meaning.

#### MOM Smart Contract - V1 specification, list of codes, ecc
If you don't like the standard code list, you need to deploy the specification that works for yourself. You can use the MOM Factory (WIP) if you prefer, but it's not mandatory.

### Dealing with line endings
https://help.github.com/en/articles/dealing-with-line-endings

## VSCode plugins
I develop with VSCode and in particular these plugins are used that affect source code formatting:
- Beautify ([hookyqr.beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify))
- ESLint ([dbaeumer.vscode-eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint))
- EditorConfig for VS Code ([editorconfig.editorconfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig))
