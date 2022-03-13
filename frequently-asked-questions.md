---
description: Questions and answers to frequently asked questions about the service.
---

# ❓ Frequently Asked Questions

### How does this service work?

When you make a request to the API either using a username or UUID as the user value, a request is made to Mojang's API (Yggdrasil) to retrieve the player's information. This includes their actual UUID, along with the skin information of the player. All of this information is cached for 24 hours to prevent repetitive fetches to Mojang on the same player. The skin is then passed along to the rendering method to draw the respective parts of the skin onto a larger image, either as a 2D or 3D image depending on what you are looking for.

### What is this service built with?

The entire back-end of the API is built using Go, a highly efficient compiled language built by Google in 2012. Go was chosen as the language of choice for the simple error handling, high speed capabilities, and easily understandable syntax. Although the libraries available for Go are not as large as something like Node.js, the speed benefits definitely outweigh something like Node.js or Python.

### I found an issue, how do I report it?

It depends on the vulnerability of the issue. If it is something that should be fixed with little to no urgency (like a rendering issue or caching issue), then either a [new issue](https://github.com/mineatar-io/api-server/issues/new) should be open on GitHub, or you can [create a pull request](https://github.com/mineatar-io/api-server/compare) to fix it yourself. Please note that pull requests will take some time to get reviewed and merged. If there is a security flaw or something that should be fixed silently regarding the site itself, please shoot an email to [contact@mineatar.io](mailto:contact@mineatar.io) with as much information as you can provide.

### Why did you choose GitBooks for the website?

Originally when the site was released, we used Next.js and self hosted the website. We soon realized that an automated hosting provider like GitBooks would be easiest for the community because it can easily allow people to modify page information by creating pull requests on GitHub. It also cleaned up the site design to allow better navigation and improved SEO.
