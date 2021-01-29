<template>
  <Layout>
    <template slot="page-top">
        <h1><span class="outlinedText">Mystery</span> Maker</h1>
        <h6>Version {{ version }}</h6>
        <div id="container">
            <div class="button" id="button-1">
                <div id="slide"></div>
                <a id="downloadBtn" href="setup.exe">Download</a>
            </div>
        </div>
	<iframe id="iFrame1" src="https://velius.zapto.org/mysterymaker/changelog" width="100%" height="100%" style="border: none;"></iframe>
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
            version: ""
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

            function resizeIFrameToFitContent( iFrame ) {

                iFrame.height = iFrame.contentWindow.document.body.scrollHeight * 1.4;
            }

            window.addEventListener('DOMContentLoaded', function(e) {

                var iFrame = document.getElementById( 'iFrame1' );
                resizeIFrameToFitContent( iFrame );

            } );
    },
    destroyed: function () {
        document.getElementById("styles").remove();
    },
}
</script>

<style scoped>
@import url("https://mysterymaker.zap106456-1.plesk05.zap-webspace.com/css/styles.css");

h1 {
    border-bottom: none;
}
::-webkit-scrollbar {
    display: none;
}
</style>