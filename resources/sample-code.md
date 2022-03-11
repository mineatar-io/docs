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
import React from 'react';
import PropTypes from 'prop-types';

export default function PlayerBody({ username }) {
    return (
        <img src={`https://api.mineatar.io/body/${username}?scale=4`} alt={`${username}'s Body`} />
    );
}

PlayerBody.propTypes = {
    username: PropTypes.string.isRequired
};
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
