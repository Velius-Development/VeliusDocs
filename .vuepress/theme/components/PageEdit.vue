<template>
  <footer class="page-edit">
    <div
      v-if="editLink"
      class="edit-link"
    >
      <a
        :href="editLink"
        target="_blank"
        rel="noopener noreferrer"
      >{{ editLinkText }}</a>
      <OutboundLink />
    </div>
    
    <div
      v-if="lastUpdated"
      class="last-updated"
    >
      <span class="prefix">{{ lastUpdatedText }}:</span>
      <span class="time">{{ lastUpdated }}</span>
      <br>
      <div @mouseover="expanded = true" @mouseleave="expanded = false" v-bind:class="[expanded ? 'expanded' : 'collapsed']" style="float: right; margin-top: 10px">
        <span class="prefix" v-html="authorsText">{{ authorsText }}</span>
        <span class="time" v-html="authors">{{ authors }}</span>
      </div>
    </div>
  </footer>
</template>

<script>
import isNil from 'lodash/isNil'
import { endingSlashRE, outboundRE } from '../util'

export default {
  name: 'PageEdit',

  data: function() {
    return {
      authors: "",
      expanded: false
    }
  },

  mounted: async function () {
    this.authors = await this.getAuthors()
  },

  computed: {
    lastUpdated () {
      return this.$page.lastUpdated
    },

    lastUpdatedText () {
      if (typeof this.$themeLocaleConfig.lastUpdated === 'string') {
        return this.$themeLocaleConfig.lastUpdated
      }
      if (typeof this.$site.themeConfig.lastUpdated === 'string') {
        return this.$site.themeConfig.lastUpdated
      }
      return 'Last Updated'
    },

    authorsText () {
      if (typeof this.$themeLocaleConfig.authors === 'string') {
        return this.$themeLocaleConfig.authors
      }
      if (typeof this.$site.themeConfig.authors === 'string') {
        return this.$site.themeConfig.authors
      }
      return 'Authors: '
    },

    editLink () {
      const showEditLink = isNil(this.$page.frontmatter.editLink)
        ? this.$site.themeConfig.editLinks
        : this.$page.frontmatter.editLink

      const {
        repo,
        docsDir = '',
        docsBranch = 'master',
        docsRepo = repo
      } = this.$site.themeConfig

      if (showEditLink && docsRepo && this.$page.relativePath) {
        return this.createEditLink(
          repo,
          docsRepo,
          docsDir,
          docsBranch,
          this.$page.relativePath
        )
      }
      return null
    },

    editLinkText () {
      return (
        this.$themeLocaleConfig.editLinkText
        || this.$site.themeConfig.editLinkText
        || `Edit this page`
      )
    }
  },

  methods: {
    createEditLink (repo, docsRepo, docsDir, docsBranch, path) {
      const bitbucket = /bitbucket.org/
      if (bitbucket.test(docsRepo)) {
        const base = docsRepo
        return (
          base.replace(endingSlashRE, '')
          + `/src`
          + `/${docsBranch}/`
          + (docsDir ? docsDir.replace(endingSlashRE, '') + '/' : '')
          + path
          + `?mode=edit&spa=0&at=${docsBranch}&fileviewer=file-view-default`
        )
      }

      const gitlab = /gitlab.com/
      if (gitlab.test(docsRepo)) {
        const base = docsRepo
        return (
          base.replace(endingSlashRE, '')
          + `/-/edit`
          + `/${docsBranch}/`
          + (docsDir ? docsDir.replace(endingSlashRE, '') + '/' : '')
          + path
        )
      }

      const base = outboundRE.test(docsRepo)
        ? docsRepo
        : `https://github.com/${docsRepo}`
      return (
        base.replace(endingSlashRE, '')
        + '/edit'
        + `/${docsBranch}/`
        + (docsDir ? docsDir.replace(endingSlashRE, '') + '/' : '')
        + path
      )
    },

    async getAuthors () {
      let authors = []
      this.$page.authors.forEach((entry, index) => {
        var name = ""
        if(entry.email.includes("users.noreply.github.com")) {
          name = entry.email
          name = name.split(/\+|@/)[1]
        } else {
          name = entry.username
        }
        authors.push(name)
      })

      let results = []

      //Check if valid contribution
      let response = await axios.get('https://api.github.com/repos/Velius-Development/VeliusDocs/contributors')

      authors.forEach((entry, index) => {

        response.data.forEach((item, key) => {
            if (item.login == entry) {
              results.push("<a href='https://github.com/" + entry + "'>" + entry + "</a>")
              return
            }
        })
      })

      return results.join(", ")
    }
  }
}
</script>

<style lang="stylus">
@require '../styles/wrapper.styl'

.page-edit
  @extend $wrapper
  padding-top 1rem
  padding-bottom 1rem
  overflow auto

  .edit-link
    display inline-block
    a
      color lighten($textColor, 25%)
      margin-right 0.25rem
  .last-updated
    max-width 40%
    float right
    font-size 0.9em
    .prefix
      font-weight 500
      color lighten($textColor, 25%)
    .time
      font-weight 400
      color #767676
      a
        font-weight 350

.expanded
    overflow: visible;
.collapsed
    display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;  
    overflow: hidden;

@media (max-width: $MQMobile)
  .page-edit
    .edit-link
      margin-bottom 0.5rem
    .last-updated
      font-size 0.8em
      float none
      text-align left

</style>
