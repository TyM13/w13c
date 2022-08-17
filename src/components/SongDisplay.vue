<template>
  <div>
    <section class="picked_song">
      <h1 ref="playing_song">pick a song</h1>
    </section>

    <section
      class="songs_container"
      v-for="(song, index) in songs"
      :key="index"
    >
      <h2 class="song_class" @click="play_song">
        {{ song[`title`] }}
      </h2>
      <h1 class="song_class">
        {{ song[`artist`] }}
      </h1>
      <img :src="song[`img_url`]" />
    </section>
  </div>
</template>

<script>                           //^^ have a for loop that displays the songs [title][artist][img] on the page, when a song title is clicked it will call the function play_song ^^//
export default {                  //vv Below when the play_song function is called it will inject text into the ref[playing_song](section) and it will change the text to be the name of the song that was clicked vv
  methods: {
    play_song(details) {
      this.$refs[`playing_song`][`innerText`] = details[`target`][`innerText`];
    },
  },

  data() {                                //vv An Array of Objects that contains keys and value's for the songs vv
    return {
      songs: [
        {
          title: `It aint me`,
          artist: `Kygo, Selena Gomez`,
          song_id: 1,
          img_url: `https://upload.wikimedia.org/wikipedia/en/d/d3/It_Ain%27t_Me_%28Official_Single_Cover%29_by_Kygo_%26_Selena_Gomez.png`,
        },
        {
          title: `Over The Edge `,
          artist: `Tristam`,
          song_id: 2,
          img_url: `https://i1.sndcdn.com/artworks-OYEcCTq3XCtl-0-t500x500.jpg`,
        },
        {
          title: `Time Of Your Life`,
          artist: `Green Day`,
          song_id: 3,
          img_url: `https://upload.wikimedia.org/wikipedia/en/1/13/Green_Day_-_Good_Riddance_%28Time_of_Your_Life%29_cover.jpg`,
        },
      ],
    };
  },
};
</script>

<style scoped>  
img {
  width: 30%;
  height: 80%;
}

.song_class {
  margin-top: 20px;
  margin-bottom: 20px;
  display: grid;
}

.songs_container {
  display: grid;
  grid-auto-flow: row;
  place-items: center;
}

.picked_song {
  text-align: center;
  margin-top: 30px;
}
</style>