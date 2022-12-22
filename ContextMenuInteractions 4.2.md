# test

`bot.on('ready', () => {/* code here */})` is an emitter that runs when your bot logs in. This is useful for many things, but in this case, we can use it to push our context menu command.

For this tutorial, please follow along accurately to make a kick command with the same functionality. You can make your own commands later using this information.

---

**4.2-1**

Add the following code to make a kick-user select menu command
```js
bot.on('ready', async () => {
  guild = await bot.guilds.fetch('766057533911466024') // your TEST SERVER here. fetches a **guild object** based on its ID
  guild.commands.create({
    name: 'Kick User >:O', // the command name
    type: Discord.ApplicationCommandType.User // there are multiple types of commands, this is a user command
  })
})
```

After rebooting the bot, it should appear when you right click on a member and go to apps.
*comment your code out now so it doesn't try making a new user-command every time you reboot your bot. there are heavy ratelimits so your bot may not work if you don't*

---

**4.2-2**

This is another type of interaction, so add this in your current `interactionCreate` emitter.
```js
if (int.isUserContextMenuCommand() == true) {
  if (int.commandName == "Kick User >:O") {
    console.log(int.targetMember.displayName) // int.targetMember - the member that the command is being run on
  }
}
 ```
 Now if you test out your command, it shouldn't respond but it should log the target member's displayName.
 
 ---
 
 **4.2-3**
 
 Now, using what you know make the bot respond with a modal containing a field asking for the *reason* of the kick.
 (it doesn't have to be required)
 
 ---

Now add something like this to your code modal receiver
 
 ```js
 if (int.customId.startsWith('kickmodal.')) {
  targetid = int.customId.slice(10)
  // replace kickmodal with your modal ID
  reason = int.fields.getTextInputValue("reason")
  member = await int.guild.members.fetch(targetid)
  if (int.member.permissions.has("KICK_MEMBERS")) {
    if (member.kickable) {
      member.kick(reason)
      int.reply("That member was successfully kicked.")
    } else {
      int.reply("That member cannot be kicked from the server by the bot.")
    }
  } else {
    int.reply('Sorry, you don\'t have access to do that.')
  }
}
```
