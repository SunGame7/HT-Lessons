A message command is a command that runs when a message is sent in a server.

Ex:
User: "!ping" 
Bot: "Pong!"

There are **three** parts of objects in node.js One of them is an **emitter**

An **emitter** is a function that is called when something happens.

Add this code in between your bot variable being made and the bot logging in:
```js
  bot.on('messageCreate', async (message) => {
    // code here
  })
```

**on** indicates that we are looking for an emitter<br>
**messageCreate** is the name of the emitter<br>
**message** is the variable that is being passed through the emitter

**message** and **bot** are both examples of **objects**<br>
Each of them can have their own **emitters**, **methods** and **properties**

Now add the following code to the "code here" section
```js
  if (message.content == '!ping') {
    message.reply({content: "Pong!"})
   }
```

**message.content** is a property, that the bot is reading<br>
**message.reply()** is a method/function, that the bot is running
