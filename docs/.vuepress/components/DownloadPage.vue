<template>
  <Layout>
    <template slot="page-top">
        <h1><span class="outlinedText">Mystery</span> Maker</h1>
        <h6>Version {{ version }}</h6>
        <div id="container">
            <div class="button" id="button-1">
                <div id="slide"></div>
                <a id="downloadBtn" href="https://mysterymaker.zap106456-1.plesk05.zap-webspace.com/setup.exe">Download</a>
            </div>
        </div>
        <iframe id="iFrame1" @load="onLoad()" src="/custom_pages/changelog.html" width="100%" height="100%" style="border: none;"></iframe>
    </template>
  </Layout>
</template>

<script>
import Layout from "@theme/layouts/Layout.vue";
export default {
    name: "DownloadPage",
    components: { Layout },
    data() {
        return {
            version: "LOADING..."
        };
    },
    mounted: function(){
            const style = document.createElement('style');
            style.setAttribute("id", "styles");
            style.textContent = "html, body, #app, .theme-container, .page{height: 100%; width: 100%; padding: 0;} .theme-default-content, .page-edit {display: none;}";
            document.head.append(style);
            axios.get("https://mysterymaker.zap106456-1.plesk05.zap-webspace.com/php/getVersion.php").then(response => {
                this.version = response.data
            });

    },
    created() {
        window.addEventListener("resize", this.onResize);
    },
    destroyed() {
      document.getElementById("styles").remove();
      window.removeEventListener("resize", this.onResize);
    },
    methods: {
      onResize(e) {
        var iFrame = document.getElementById( 'iFrame1' );
        iFrame.height = iFrame.contentWindow.document.body.scrollHeight * 1.2;
      },
      onLoad() {
        this.onResize();
        document.getElementById( 'iFrame1' ).style.opacity = 1;
      }
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Raleway:300,400');

#iFrame1{
    opacity: 0;
    transition: opacity 0.5s;
    -webkit-transition: opacity 0.5s; /* Safari */
    transition-timing-function: ease-out;
}

body {
  background: #2D3142;
  font-family: 'Raleway', sans-serif;
  font-size: xx-large;
}


/* Heading */

h1 {
  font-size: 5em;
  text-align: center;
  padding: 70px 0 0 0;
  color: #EF8354;
  font-weight: 300;
  letter-spacing: 1px;
  margin-bottom: 15px;
  border: none;
}

h6 {
    font-family: Consolas;
    font-size: 2em;
    text-align: center;
    color: #ffffffb4;
    font-weight: 300;
    letter-spacing: 3px;
    margin: 0;
}

.outlinedText {
  border: 2px solid #4F5D75;
  padding: 10px;
  padding-top: 0;
}


/* Layout Styling */

#container {
  width: 100%;
  margin: 0 auto;
  padding: 80px 0 60px 0;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}


/* Button Styles */

.button {
  display: inline-flex;
  height: 60px;
  width: 250px;
  border: 2px solid #BFC0C0;
  margin: 20px 20px 20px 20px;
  color: #BFC0C0;
  text-transform: uppercase;
  text-decoration: none;
  font-size: .8em;
  letter-spacing: 1.5px;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

a {
  color: #BFC0C0;
  text-decoration: none;
  letter-spacing: 1px;
}
/* First Button */

#button-1 {
  position: relative;
  overflow: hidden;
  cursor: pointer;
}
#button-1 a {
    position: relative;
    transition: all .35s ease-Out;
}

#slide {
    width: 100%;
    height: 100%;
    left: -250px;
    background: #BFC0C0;
    position: absolute;
    transition: all .35s ease-Out;
    bottom: 0;
}

#button-1:hover #slide {
    left: 0;
}

#button-1:hover a {
    color: #2D3142;
}

#downloadBtn {
    font-family: 'Raleway', sans-serif;
    font-size: 2rem;
}

::-webkit-scrollbar {
    display: none;
}
</style>