<template>
  <div class="Discover">
    <!-- Header -->
    <div class="header">
      <h1 class="header__label">Discover</h1>
    </div>
    <!-- Navigation -->
    <nav class="genres">
      <ul class="genres__list">
        <li
          @click="getGenre(genre.playlistId, genre.id)"
          v-for="genre in genres"
          :key="genre.id"
          class="genres__list__item"
          :class="{ active: genreId == genre.id }"
        >
          <span class="genres__list__link">{{ genre.name }}</span>
        </li>
      </ul>
    </nav>
    <!-- feed -->
    <Feed :genreId="genreId" />
  </div>
</template>

<script>
import Feed from './Feed'
import genres from '../static/GenresMap'

export default {
  name: 'discover',
  components: {
    Feed
  },
  data() {
    return {
      genres,
      genreId: '132',
      playlistId: '2098157264'
    }
  },
  methods: {
    getGenre(pId, gId) {
      this.playlistId = pId
      this.genreId = gId
    }
  }
}
</script>

<style lang="scss" scoped>
.genres {
  margin: 30px -8px;
  &__list {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    align-items: flex-start;

    &__item {
      font-size: 15px;
      font-weight: 700;
      text-transform: capitalize;
      color: #8f8f8f;
      margin: 0 10px;
      transition: all 0.2s;
      &:hover {
        color: white;
      }
    }

    &__link {
      cursor: pointer;
    }
  }
}

.active {
  color: #db1d40;
  font-weight: 700;
  &:hover {
    color: #db1d40;
  }
}
</style>