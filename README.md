---
description: An incredibly fast Minecraft avatar API.
---

# 🏠 Home

mineatar.io is an incredibly simple and fast Minecraft skin API. You can render the skin of any Minecraft player as a 2D or 3D image. As long as you know the username or UUID of the player, you can get their raw skin, isometric head, body, etc. Read more about how our service differs from others.

## Features

### Incredibly fast

This service is incredibly fast, rendering skins in only a couple milliseconds. The initial player lookup and skin fetching may take about a quarter second, but the render times after these are fetched are incredibly fast. The back-end API is built using [Go](https://go.dev) and our servers are hosted in central United States so load times will never be an issue.

### Efficient caching

Once a player has been looked up, their UUID and skin are cached for up to 24 hours. This is to prevent abuse and repetitive unnecessary requests to Mojang's API. Rendered images are also cached up to 24 hours to reduce load on the server.

### Username support

Usernames and UUIDs are both supported as means for retrieving a player's skin. If you don't have the player's UUID, and only their username, you can still retrieve their skin. No unnecessary redirects to the proper URL with the UUID, which may cause issues with older browsers or non-standard request clients.

### Overlay toggling

Each render route supports toggling the overlay (or 2nd layer) of the skin on and off. If you want the base layer of a player's skin but don't want to see their overlay, simply set the `overlay` query parameter to `false`.

### Regular and slim models

Our service provides support for both regular ("Steve") and slim ("Alex") models, and will render accordingly. The dimensions of the resulting image will be the same for either one, so you do not have to account for the change on your end.

## Open Source

The entire source code for our service is available under our [GitHub organization](https://github.com/mineatar-io). If you have any issues with our service, want to create a pull request, or just inspect how our service work, you can do so by GitHub.

## Self Hosting

Since our service is entirely open source, you are free to host your own player skin rendering service for your next project. Please make sure to credit us appropriately in your about page or footer.

## Contact

If you feel that you need to contact us privately, you can shoot an email to [contact@mineatar.io](mailto:contact@mineatar.io). If you have a general question about the service, you should instead open a discussion post on GitHub.

###
