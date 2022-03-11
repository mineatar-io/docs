---
description: Sample code for how to implement in your website.
---

# 🖥 Sample Code

## HTML

{% code title="index.html" %}
```html
<img src="https://api.mineatar.io/body/MHF_Steve?scale=4" alt="Steve's Body" />
```
{% endcode %}

## React

{% code title="components/PlayerBody.js" %}
```jsx
import React from 'react';
import PropTypes from 'prop-types';

export default function PlayerBody({ username, scale }) {
    return (
        <img src={`https://api.mineatar.io/body/${username}?scale=${scale}`} alt={`${username}'s Body`} />
    );
}

PlayerBody.propTypes = {
    username: PropTypes.string.isRequired,
    scale: PropTypes.number
};

PlayerBody.defaultProps = {
    scale: 4
};
```
{% endcode %}

## Discord.js Embed

{% code title="commands/body.js" %}
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
{% endcode %}
