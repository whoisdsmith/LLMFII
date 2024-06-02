---
tags:
  - "#developer-tools"
  - "#software-development"
  - "#api"

  - "#bookmark-management"
  - "#productivity-tool"
  - "#oauth-setup"
---
![pika-1678357198604-1x](https://user-images.githubusercontent.com/73278151/224000294-63f915d0-ff04-4604-9327-775135e5a72b.png)

# Mark

# What is mark?

Mark helps you streamline your productivity by organizing your bookmarks for you. We noticed that there is no easy way to store good articles, blogs, podcasts, or other useful resources that you come across while surfing the web. Mark is a one-stop solution for you to manage your knowledge base in a simple and efficient manner.

Import your existing bookmarks from Chrome/Firefox/Safari in a single click.

# Top features

- Categorize, tag, and star your bookmarks
- Find exactly what you're looking for with the powerful search and filter feature
- Support for nested bookmark collections
- Dark mode support
- One click bookmark imports

## Getting Started

First, run the development server:

```bash
npm install
# or
yarn 
```
### Setup google oauth
head over to https://console.developers.google.com/ > credentials > create credentials > oauth client id create an application, and then copy the client_id and client_secret

Authorized JavaScript origins - eg: http://localhost:3000

Authorized redirect URIs - (the same URL as used above with /api/auth/callback/google) eg: http://localhost:3000/api/auth/callback/google

create a `.env.local` file and add these to it
```bash
NEXTAUTH_URL = http:localhost:3000
MONGO_URI = <your_mongo_uri>
NEXTAUTH_SECRET=<anything_that_you_want_to_add>
GOOGLE_CLIENT_SECRET=
GOOGLE_CLIENT_ID=
```


```bash
npm run dev
# or
yarn dev
```
