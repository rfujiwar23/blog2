<template>
  <div class="container">
	<main class="main">
    <div class="blog">
		<h1 class="title-page">{{ title }}</h1>
		<p class="publishedAt">{{ publishedAt }}</p>
		<div class="post" v-html="body"></div>
	</div>
  </main>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://jjcproject.microcms.io/api/v1/blogme/${params.slug}`,
      {
        headers: { 'X-API-KEY': '78f8f871-a021-4bda-ad62-887f8a5d39fc' }
      }
    )
    return data
  }
}
</script>

<style scoped>

.container {
	background: rgb(223,252,184);
	background: linear-gradient(135deg, rgba(223,252,184,1) 0%, rgba(33,196,168,1) 100%);
}

.main {
	 width: 960px;
	 margin: 0 auto;
}

.blog {
	padding:20px;
}
 .title-page {
	 margin-bottom: 20px;
	 font-size:24px;
}
 .publishedAt {
	 margin-bottom: 40px;
}
 .post > h1 {
	 font-size: 24px;
	 font-weight: bold;
	 margin: 40px 0 20px;
	 background-color: #eee;
	 padding: 10px 20px;
	 border-radius: 5px;
}
 .post > h2 {
	 font-size: 24px;
	 font-weight: bold;
	 margin: 40px 0 16px;
	 border-bottom: 1px solid #ddd;
}
 .post > p {
	 line-height: 1.8;
	 letter-spacing: 0.2px;
}
 .post > ol {
	 list-style-type: decimal;
	 list-style-position: inside;
}
</style>