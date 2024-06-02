---
aliases:
  - Linkly
tags:
  - "#open-source"
  - "#developer-tools"
  - "#software-development"

  - "#link-management"
  - "#react"
  - "#nextjs"
---
<div align="center">
  <a href="https://linkly.nersent.com">
    <img src="https://github.com/woywro/Linkly/blob/main/screenshots/main.png" alt="Logo">
  </a>

  <p align="center">
    <a href="docs">Explore Docs »</a>
    ·
    <a href="https://linkly.nersent.com">Open the app »</a>
    ·
    <a href="https://github.com/woywro/linkly/issues">Report an Issue »</a>
   </p>
</div>

 <p align="center">
Linkly is an open source tool for managing your website urls like in file manager. As a logged user you can save links and create collections of them. Each collection can be shared with other users. If somebody wants to share collection with you you can accept the request or decline it. You can also access your links history.
  </p>
</div>

## About The Project

  <div align="center">
    <img src="https://github.com/woywro/Linkly/blob/main/screenshots/mockupLight.png" alt="Mockup" width="100%">
    <img src="https://github.com/woywro/Linkly/blob/main/screenshots/mockupDark.png" alt="Mockup" width="100%">
  </div>

This project enables you to manage your links just like in file manager. Most functions and interactions work as in any file manager. Each link keeps it's last modification timestamp, so you can sort your links alphabetically, by owner or by last modification. You can create collections of your links and share them with other users. If at least one of your share requests is accepted, your friend's email should appear on the list when sharing. Each collection can be tagged with color (e.g. all programming related collections). Collections are sorted by last opened by default, however you can set sorting to your own custom order by toggling edit mode and dragging them.

## Built With

- React
- Typescript
- Next.js
- NextAuth
- PostgreSQL
- Prisma
- Redux
- Redux thunk
- Styled Components

## Live version

https://linkly.nersent.com/ <br/>
If you don't want to authenticate with google/github you can use your email for passwordless login. Simply type in your email, click login button and check your inbox for login token.

## Installation

1. Clone the repo
   ```sh
   git clone https://github.com/woywro/Linkly.git
   ```
2. Install NPM packages
   ```sh
   npm install
   ```
3. Set environmental variables in /.env.local
   ```sh
   GOOGLE_CLIENT_ID=...
   GOOGLE_CLIENT_SECRET=...
   GITHUB_CLIENT_ID=...
   GITHUB_CLIENT_SECRET=...
   ```
4. Add PostgreSQL connection string in prisma/.env
   ```sh
   DATABASE_URL=...
   ```
5. Run
   ```sh
   npx prisma migrate dev --name "example"
   npx prisma generate
   ```
6. Run the dev server
   ```sh
   npm run dev
   ```

## Docs

<a href="docs"><strong>Explore the docs »</strong></a>

## License

Distributed under the MIT License. See `LICENSE` file for more information.

## Contact

Wojtek Wrotek - woywro@gmail.com

## Acknowledgments

Helpful libraries used to make this project:

- [Framer Motion](https://www.framer.com/motion/)
- [Axios](https://axios-http.com/docs/intro)
- [Formik](https://formik.org/)
- [Yup](https://github.com/jquense/yup)
- [MomentJs](https://momentjs.com/)
- [React Icons](https://react-icons.github.io/react-icons/)
- [React Custom Scrollbars 2](https://github.com/RobPethick/react-custom-scrollbars-2)
- [Next SEO](https://github.com/garmeeh/next-seo)
- [Nodemailer](https://nodemailer.com/about/)
- [react-social-login-buttons](https://github.com/MichalSzorad/react-social-login-buttons)
