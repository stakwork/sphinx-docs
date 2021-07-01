# Sphinx Bots!

The Sphinx bot framework is inspired by Discord's bot creation library. So far we have only implemented simple Message creation, but there are exciting times ahead for bot developers on Sphinx!

### Creating a bot

Bots can be created on your sphinx-relay instance. By creating a bot, you are generating a bridge from the Lightning Network to the regular web (http). Bots are secured with a secret key that is generated when a bot is created.

**connect your bot**

```js
const client = new Sphinx.Client()
client.login(process.env.SPHINX_TOKEN)
```

**create a bot Message**
```js
const embed = new Sphinx.MessageEmbed()
    .setAuthor('TestBot')
    .setDescription('Welcome to TestBot!')
```

**respond to a "bot install" message**
```js
client.on(msg_types.INSTALL, async (message) => {
    const embed = new Sphinx.MessageEmbed()
        .setAuthor('TestBot')
        .setDescription('Welcome to TestBot!')
        .setThumbnail('<svg></svg>')
    message.channel.send({ embed })
})
```

**respond to a chat message**
```js
client.on(msg_types.MESSAGE, async (message) => {
    // do something here!
    const embed = new Sphinx.MessageEmbed()
        .setAuthor('TestBot')
        .setTitle('TestBot Message:')
        .addFields([
            { name: 'Item #1:', value: 'hello', inline: true },
            { name: 'Item #2:', value: 'hello again', inline: true, color: '#00FF00' }
        ])
        .setThumbnail('<svg></svg>')
    message.channel.send({ embed })
})
```