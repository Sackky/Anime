<template>
  <div id="sup">
    <div>
      <b-navbar toggleable="lg" type="dark" variant="danger">
        <b-navbar-brand>Anime & Manga Online</b-navbar-brand>
      </b-navbar>
    </div>
    <br />

    <b-container class="bv-example-row bv-example-row-flex-cols">
      <b-row>
        <b-col></b-col>
        <b-col>
          <b-navbar-nav class="ml-auto">
            <b-nav-form>
              <b-form-input size="sm" class="mr-sm-2" v-model="textSearch"></b-form-input>
              <b-button
                variant="success"
                size="sm"
                class="my-2 my-sm-0"
                @click="searchData()"
              >Search</b-button>
            </b-nav-form>
          </b-navbar-nav>
        </b-col>
        <b-col></b-col>
      </b-row>
    </b-container>
    <br />

    <b-container class="bv-example-row bv-example-row-flex-cols">
      <div class="row">
        <div class="col">
          <b-row align-v="stretch">
            <b-card-group columns>
              <b-card
                class="card text-white bg-secondary mb-3"
                v-for="data in List"
                :key="data.mal_id"
                :title="data.title"
                :img-src="data.image_url"
                :img-alt="url"
                img-top
                tag="article"
                style="max-width: 25rem;"
              >
                <b-card-text>
                  Synopsis : {{data.synopsis}}
                  <br />
                  Score : {{data.score}}
                  <br />
                  Episodes : {{data.episodes}}
                  <br />
                  Rated : {{data.rated}}
                </b-card-text>
              </b-card>
            </b-card-group>
          </b-row>
        </div>
      </div>
    </b-container>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      List: null,
      textSearch: "",
    };
  },
  methods: {
    searchData() {
      axios
        .get(
          "https://api.jikan.moe/v3/search/anime?q=" +
            this.textSearch +
            "&limit=10"
        )
        .then((response) => {
          this.List = response.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>