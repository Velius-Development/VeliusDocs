# Velius Engine Documentation
This repository is public to enable all users to fix and expand the documentation.

## How To Contribute

- **Clone** the master branch of this repository
- **cd into docs** directory
- **Use `npm install`** to install all dependencies

### How to add a page

- **cd into [docs/guide](https://github.com/SpyrexDE/VeliusDocs/tree/master/docs/guide)** directory

- **add your page as a ` .md`-file**

- **add the name of the file you added without .md-Extension to [/docs/.vuepress/config.js](https://github.com/SpyrexDE/VeliusDocs/tree/master/docs/guide)**

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