Add the following to your code:
<ul>
  <li>replies</li>
  <li>pins</li>
  <li>reactions</li>
  <li>attachments</li>
  <li>message edits</li>
  <li>threads</li>
  <li>tts</li>
</ul>

**replies**
Use `message.reply(/*message*/)`

**pins**
Use `await message.pin`

**reactions**
Use `await message.react('/*emoji*/')`

**attachments**
Use `message.reply({content: "hi", files: ['./filename' /*use the repl sidebar*/]})`

**message edits**
```js
replymsg = await message.reply({content: "Hi"}) // saves the reply to a variable
await replymsg.edit({content: "This message has been edited."}) // edits the reply
```

**threads**
```js
message.startThread({
  name: "threadname",
  reason: "new thread"
})
```
https://old.discordjs.dev/#/docs/discord.js/main/typedef/StartThreadOptions

**tts**
message.reply({content: "hi", tts: true})
