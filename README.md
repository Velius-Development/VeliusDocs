<div align="center">
  <img src="https://api.netlify.com/api/v1/badges/42a0fbc4-0ffe-4a46-9b42-0571b700ae93/deploy-status"/>
</div>

# Velius Engine Documentation
This repository is public to enable all users to fix and expand the documentation.
<br>The main branch gets automatically deployed on [velius.dev](https://velius.dev/)

## How To Contribute

- **Clone** the master branch of this repository
- **cd into docs** directory
- **Use `npm install`** to install all dependencies

### How to add a page

- **go into [docs/guide](https://github.com/SpyrexDE/VeliusDocs/tree/master/docs/guide)** directory

- **add your page as a ` .md`-file**

- **add the name of the file you added without .md-Extension to [/docs/.vuepress/config.js](https://github.com/SpyrexDE/VeliusDocs/tree/master/docs/.vuepress/config.js)**

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

### **Thank you for contibuting!**
