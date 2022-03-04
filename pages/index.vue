<template>
  <v-row>
    <v-col class="d-flex flex-column align-center">
      <v-row>
        <v-col cols="12" class="d-flex justify-center">
          <div class="search-container d-flex mt-3">
            <v-text-field
              v-model="searchText"
              outlined
              placeholder="Type here"
              dense
              rounded
              @keydown.enter="search"
              @focusin="searchFocus = true"
              @focusout="searchFocus = false"
            />
            <v-btn
              fab
              dark
              small
              outlined
              :color="searchFocus ? 'primary' : 'rgba(0,0,0,0.38)'"
              elevation="0"
              class="ml-2"
              @click="search"
            >
              <v-icon dark>
                mdi-magnify
              </v-icon>
            </v-btn>
          </div>
        </v-col>
      </v-row>
      <v-row class="site-width">
        <v-col v-for="(item, index) in fakeBoxesData" :key="index" :cols="item.type === 'image' ? 3 : 6">
          <v-hover>
            <template v-slot:default="{ hover }">
              <v-card
                :elevation="hover ? item.link ? 12 : 0 : 0"
                :color="item.color"
                class="card-rounded transition-swing"
                :to="item.link"
                height="130px"
              >
                <v-img
                  v-if="item.type === 'image'"
                  :src="item.src"
                  class="align-end"
                  height="100px"
                />
                <v-card-text
                  v-if="item.type === 'image'"
                  class="card-title"
                  :style="{ color: item.fontColor }"
                  v-text="item.text"
                />
                <div class="text-card" :style="{ color: item.fontColor }">
                  {{ item.text }}
                </div>
              </v-card>
            </template>
          </v-hover>
        </v-col>
        <v-col cols="7">

        </v-col>
        <v-col cols="5">
          <v-card
            elevation="0"
            color="#B2DFDB"
            class="card-rounded px-4 py-3 news-container"
            height="340px"
          >
            <div class="news-box-title">
              Latest News
            </div>
            <v-hover v-for="(item, index) in fakeLatestNews" :key="index">
              <template v-slot:default="{ hover }">
                <div class="news transition-swing" :class="`elevation-${hover ? 12 : 0}`" v-ripple>
                  <nuxt-link :to="item.link" style="text-decoration: none">
                    <div class="news-date">{{ item.date }}</div>
                    <div class="news-title">{{ item.title }}</div>
                  </nuxt-link>
                </div>
              </template>
            </v-hover>
          </v-card>
        </v-col>
      </v-row>
    </v-col>
  </v-row>

</template>

<script>
export default {
  name: 'IndexPage',
  data () {
    return {
      searchText: null,
      searchFocus: false,
      fakeBoxesData: [
        {
          type: 'image',
          color: '#F44336',
          text: 'Tissue',
          src: 'https://www.proteinatlas.org/images_static/tissue_atlas.jpg',
          link: '#',
          fontColor: '#fff'
        },
        {
          type: 'image',
          color: '#E91E63',
          text: 'Brain',
          src: 'https://www.proteinatlas.org/images_static/brain_atlas.jpg',
          link: '#',
          fontColor: '#fff'
        },
        {
          type: 'image',
          color: '#9C27B0',
          text: 'Tissue',
          src: 'https://www.proteinatlas.org/images_static/tissue_atlas.jpg',
          link: '#',
          fontColor: '#fff'
        },
        {
          type: 'image',
          color: '#673AB7',
          text: 'Cell Line',
          src: 'https://www.proteinatlas.org/images_static/cell_line_atlas.jpg',
          link: '#',
          fontColor: '#fff'
        },
        {
          type: 'image',
          color: '#3F51B5',
          text: 'Single Cell Type',
          src: 'https://www.proteinatlas.org/images_static/tissue_cell_type.jpg',
          link: '#',
          fontColor: '#fff'
        },
        {
          type: 'text',
          color: '#eee',
          text: 'The open access resource for human proteins\n' +
            'Search for specific genes/proteins or\n' +
            'explore the 10 different sections',
          link: '',
          fontColor: '#000'
        },
        {
          type: 'image',
          color: '#2196F3',
          text: 'Tissue',
          src: 'https://www.proteinatlas.org/images_static/tissue_atlas.jpg',
          link: '#',
          fontColor: '#fff'
        },
        {
          type: 'image',
          color: '#00BCD4',
          text: 'Blood Protein',
          src: 'https://www.proteinatlas.org/images_static/blood_protein_section.jpg',
          link: '#',
          fontColor: '#fff'
        },
        {
          type: 'image',
          color: '#009688',
          text: 'Brain',
          src: 'https://www.proteinatlas.org/images_static/brain_atlas.jpg',
          link: '#',
          fontColor: '#fff'
        },
        {
          type: 'image',
          color: '#4CAF50',
          text: 'Single Cell Type',
          src: 'https://www.proteinatlas.org/images_static/tissue_cell_type.jpg',
          link: '#',
          fontColor: '#fff'
        },
        {
          type: 'image',
          color: '#8BC34A',
          text: 'Metabolic',
          src: 'https://www.proteinatlas.org/images_static/metabolic_atlas.png',
          link: '#',
          fontColor: '#fff'
        },
      ],
      fakeLatestNews: [
        {
          date: 'Fri, 4 Mar 2022',
          title: 'Podcast: mapping the Human Proteome',
          link: '#'
        },
        {
          date: 'Fri, 4 Mar 2022',
          title: 'Podcast: mapping the Human Proteome',
          link: '#'
        },
        {
          date: 'Fri, 4 Mar 2022',
          title: 'Genome-wide annotation of protein-coding genes in pig',
          link: '#'
        }
      ]
    }
  },
  methods: {
    search () {
      console.log('search', this.searchText)
    }
  }
}
</script>

<style scoped lang="scss">

.search-container {
  width: 776px;
  background: #eee;
  box-sizing: border-box;
  padding: 43px 100px;
  border-radius: 20px;
}

.news-box-title {
  font-weight: 500;
  font-size: 20px;
  color: #494949;
}

.news-container {
  overflow-y: auto;

  .news {
    background: #fff;
    margin: 12px 0;
    padding: 8px 12px;
    border-radius: 8px;

    .news-date {
      font-size: 10px;
      color: #2d2d2d;
    }

    .news-title {
      font-size: 16px;
      color: #000;
    }
  }
}



</style>

<style lang="scss">
.search-container {

  .v-text-field__details {
    display: none;
  }

  .v-input__slot,
  .v-btn {
    background: #fff !important;
  }
}

.container {
  max-width: 1185px;
}

.site-width {
  width: 800px;
}

.card-title {
  padding: 4px 16px !important;
  text-align: center;
}

.card-rounded {
  border-radius: 10px !important;
  overflow: hidden;
}

.text-card {
  padding: 12px 16px;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  text-align: center;
}
</style>
