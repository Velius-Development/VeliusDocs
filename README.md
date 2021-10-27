<div align="center">
  <img src="https://api.netlify.com/api/v1/badges/42a0fbc4-0ffe-4a46-9b42-0571b700ae93/deploy-status"/>
</div>

# Velius Engine Documentation
This repository is public to enable all users to fix and expand the documentation.
<br>The main branch gets automatically deployed on [velius.dev](https://velius.dev/)

## How To Contribute

- **Clone** the master branch of this repository
- **Use `npm install`** to install all dependencies
- **Use `npm run dev`** to run local development server

### How to add a page

- **go into [guide](https://github.com/SpyrexDE/VeliusDocs/tree/master/guide)** directory

- **add your page as a ` .md`-file**

- **add the name of the file you added without .md-Extension to [/.vuepress/config.js](https://github.com/SpyrexDE/VeliusDocs/tree/master/.vuepress/config.js)**

  ```
  themeConfig: {
  	...,
      sidebar: {
        '/guide/': [
          {
            ...,
            children: [
            	...,
              'example-page', <- Add this line
  ```

### ***Thank you for contibuting!***
