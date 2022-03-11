---
description: Sample code for how to implement in your website.
---

# 🖥 Sample Code

## HTML

```html
<img src="https://api.mineatar.io/body/MHF_Steve?scale=4" alt="Steve's Body" />
```

## React

```jsx
const username = 'MHF_Steve';

<img src={`https://api.mineatar.io/body/${username}?scale=4`} alt={`${username}'s Body`} />
```

## Discord.js Embed

```javascript
const { MessageEmbed } = require('discord.js');

// The following code will need to be placed within your message create
// event handler. This will send the embed to the channel within the
// `channel` variable.

const exampleEmbed = new MessageEmbed()
    .setTitle('Steve\'s Skin')
    .setColor(3066993)
    .setImage('https://api.mineatar.io/body/MHF_Steve?scale=4');

channel.send({ embeds: [exampleEmbed] });
```
