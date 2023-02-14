<script>
export default {
  data() {
    return {
      characters: [
        { name: "Badaru", element: ["Military", "Father", "Husband"] },
        { name: "Buba", element: ["Military"] },
        { name: "Dantani", element: ["Husband"] },
        { name: "Nata'ala", element: ["Scholar"] },
      ],
      newChar: {
        name: "",
      },
      favCharacters: [],
    };
  },
  computed: {
    actorStat() {
      const players = ["Scholar", "Military", "Husband", "Father"];
      const statistics = {
        Military: 0,
        Scholar: 0,
        Husband: 0,
        Father: 0,
      }
      this.characters.forEach(ch => {
        players.forEach((player) => {
          if (ch.element.indexOf(player) > -1) {
            statistics[player] += 1;
          }
        });
      });
      return statistics;
    },
    militaryList() {
      return this.characters.filter(
        (character) => character.element.indexOf("Military") > -1
      );
    },
  },

  methods: {
    addCharacter() {
      this.characters.push(this.newChar);
      this.newChar = {
        name: "",
      };
    },
    addFavCharacter(fav) {
      this.favCharacters.push(fav);
    },
  },
};
</script>

<template>
  <h1>Statistics</h1>
  <ul>
    <li v-for="(stat, role) in actorStat" :key="`stat-${role}`">
      {{ role }}: {{ stat }}
    </li>
  </ul>
  <h1>Characters in Dadin Kowa</h1>
  <label for="">Name</label>
  <input type="text" v-model="newChar.name" @keyup.enter="addCharacter" />

  <ul v-if="characters.length > 0">
    <li v-for="(character, index) in characters" :key="`character-${index}`">
      {{ character.name }}
      <button @click="addFavCharacter(character)">Favorite</button>
    </li>
  </ul>
  <p v-else>No character</p>

  <p>
    <span v-for="(character, index) in characters" :key="`character-${index}`"
      >{{ character.name
      }}{{ index === characters.length - 1 ? "" : "," }}</span
    >
  </p>

  <h2>Favorite Characters</h2>
  <ul v-if="favCharacters.length > 0">
    <li v-for="(fav, index) in favCharacters" :key="`fav-${index}`">
      {{ fav.name }}
    </li>
  </ul>
  <p v-else>No favorite characters</p>

  <table>
    <tr>
      <th>Name</th>
      <th>Height</th>
      <th>Average</th>
    </tr>
    <tr v-for="character in characters">
      <td>{{ character.name }}</td>
      <td>{{ character.height }}</td>
    </tr>
  </table>
</template>
