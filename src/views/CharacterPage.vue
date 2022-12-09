<template>
  <main class="character_page--background">
    <div class="character_page--background-filter">
      <div class="character_page">



        <div class="character_page--characterName">
          <h1>
            Black Panther
          </h1>
        </div>

        <div class="character_page--characterInfo">

          <img style="width: 65vw;" src="./BlackPanther.jpg" alt="imagem aqui" />

          <div class="character_page--characterControl">
            <div class="characterControl-control">
              <v-icon>mdi-star-plus</v-icon>
            </div>
            <div class="characterControl-control">
              <v-icon>mdi-share-variant-outline</v-icon>
            </div>
          </div>
        </div>

        <!-- TODO: preciso fazer os cards, inicialmente faço individualmente um por um, 
      talvez poderia ser automatizado, mas pode dar problemas por conta das PROPS -->
        <div>
          Comics
          Series
          Stories
          Events
        </div>
      </div>
    </div>
  </main>
</template>

<script>

export default {
  name: 'CharacterPage',

  data() {
    return {
      characterImage: './BlackPanther.jpg',

    }
  },
}
</script>

<style lang="scss" scoped>
// -----------------
$bg-filter-blur: blur(10px);
$bg-filter-color: rgba(31, 0, 0, 0.783);
$bg-min-size: 150vh;
// -----------------

.container {
  padding: 0;
}

.character_page--background {
  background: url('./BlackPanther.jpg');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  min-height: $bg-min-size;

  .character_page--background-filter {
    min-height: $bg-min-size;
  }

  @supports (-webkit-backdrop-filter: none) or (backdrop-filter: none) {
    .character_page--background-filter {
      -webkit-backdrop-filter: $bg-filter-blur;
      backdrop-filter: $bg-filter-blur;
      background-color: $bg-filter-color;
    }
  }

  .character_page{
    min-height: $bg-min-size;
  }

  .character_page--characterName {
    h1 {
      background-color: $color_main-darkest;
      font-size: 2.25rem;
      font-family: $font-family_titles;
      padding: 2.5rem 0;
      text-align: center;
    }
  }

  .character_page--characterInfo {
    display: flex;
    justify-content: space-around;
    margin-top: 5vh;

    img {
      box-shadow: 0px 2px 60px 17px $bg-filter-color inset;
      border-radius: .75rem;
      outline: .35rem white solid;
    }

    .character_page--characterControl {
      display: flex;
      flex-direction: column;
      justify-content: space-around;

      .characterControl-control {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 3.2rem;
        height: 3.2rem;
        background-color: $color_main-darkest;
        border-radius: 50%;
        transition: .25s ease-in-out;

        i {
          color: $color_main;
        }

        &:hover {
          cursor: pointer;
          background-color: $color_main;

          i {
            color: $color_main_darkest;
          }
        }
      }
    }


  }
}
</style>
