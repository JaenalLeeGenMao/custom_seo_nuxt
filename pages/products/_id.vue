<template>
  <div>
    <h1 class="title">{{title}}</h1>
    <h2 class="subtitle">Product {{id}} is name</h2>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      id: 'empty',
      description: 'empty desc',
      imageUrl: 'empty image url',
      title: 'empty title'
    }
  },
  created() {
    const { params } = this.$route
    console.log(this.$route)
    this.id = params.id
  },
  methods: {
    getProductInfo(id) {
      const promise1 = new Promise(function(resolve, reject) {
        setTimeout(function() {
          resolve({
            id,
            imageUrl:
              'https://playlistcuration.com/wp-content/uploads/formidable/6/Ambient-Encounters-600px.png',
            description: 'foo is the product description',
            title: `Product ${id}`
          })
        }, 1000)
      })
      return promise1.then((res) => res)
    }
  },
  async asyncData({ params, query, store }) {
    const { id } = params
    // Validate query params

    // fetch data from API
    try {
      const result = new Promise(function(resolve, reject) {
        resolve({
          id,
          imageUrl:
            'https://playlistcuration.com/wp-content/uploads/formidable/6/Ambient-Encounters-600px.png',
          description: 'foo is the product description',
          title: `Product ${id}`
        })
      })
      return await result
    } catch (error) {
      // Redirect to error page or 404 depending on server response
    }
  },
  head() {
    return {
      title: `Product ${this.id}`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.description
        },
        {
          hid: 'og:site_name',
          name: 'og:site_name',
          property: 'og:site_name',
          content: this.title
        },
        {
          hid: 'og:title',
          name: 'og:title',
          property: 'og:title',
          content: this.title
        },
        {
          hid: 'og:description',
          name: 'og:description',
          property: 'og:description',
          content: this.description
        },
        {
          hid: 'og:url',
          name: 'og:url',
          property: 'og:url',
          content: `https://synthetic-cargo-257303.appspot.com/products/${this.id}`
        },
        {
          hid: 'og:image',
          name: 'og:image',
          property: 'og:image',
          content: this.imageUrl
        },
        // <!-— twitter card tags additive with the og: tags -->
        {
          hid: 'twitter:card',
          name: 'twitter:card',
          property: 'twitter:card',
          content: 'summary'
        },
        {
          hid: 'twitter:domain',
          name: 'twitter:domain',
          property: 'twitter:domain',
          content: 'https://synthetic-cargo-257303.appspot.com'
        },
        {
          hid: 'twitter:text:title',
          name: 'twitter:text:title',
          property: 'twitter:text:title',
          content: this.title
        },
        {
          hid: 'twitter:image:src',
          name: 'twitter:image:src',
          property: 'twitter:image:src',
          content: this.imageUrl
        },
        {
          hid: 'twitter:url',
          name: 'twitter:url',
          property: 'twitter:url',
          content: `https://synthetic-cargo-257303.appspot.com/products/${this.id}`
        },
        {
          hid: 'twitter:label1',
          name: 'twitter:label1',
          property: 'twitter:label1',
          content: 'Opens in Theaters'
        },
        {
          hid: 'twitter:data1',
          name: 'twitter:data1',
          property: 'twitter:data1',
          content: 'October 28, 2019'
        },
        {
          hid: 'twitter:label2',
          name: 'twitter:label2',
          property: 'twitter:label2',
          content: 'On demand'
        },
        {
          hid: 'twitter:data2',
          name: 'twitter:data2',
          property: 'twitter:data2',
          content: 'at Mola.tv'
        }
      ]
    }
  }
}
</script>