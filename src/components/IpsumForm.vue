<template>
  <form @submit.prevent="onAdd(ipsum)">
    <label>
      <span>Title:</span>
      <input v-model="ipsum.title" required>
    </label>
    <label>
      <span>Author:</span>
      <input v-model="ipsum.author" required>
    </label>
    <label>
      <span>Author URL:</span>
      <input v-model="ipsum.authorUrl" required>
    </label>
    <label>
      <span>Body:</span>
      <input v-model="ipsum.body" required>
    </label>
    <label>
      <span></span>
      <button type="submit">{{ ipsumToUpdate ? 'Update' : 'Add'}}</button>
      <button type="button" @click="onCancel">Cancel</button>
    </label>
  </form>
</template>

<script>

export default {
  data() {
    const update = this.ipsumToUpdate || {};
    return {
      ipsum: {
        name: update.name,
        author: update.author,
        authorUrl: update.authorUrl,
        body: update.body
      }
    };
  },

  props: {
    onAdd: Function,
    onCancel: Function,
    ipsumToUpdate: Object
  },
};
</script>

<style>

 form {
    text-align: center;
    display: flex;
    justify-content: center;
  }
  button {
    border: 2px solid black;
    border-radius: 5px;
    margin: 5px;
    font-size: 0.75em;
  }
  .button {
    display: block;
  }
  span {
    display: inline-block;
  }
  input, textarea {
    height: 20px;
    width: 13vw;
  }
  label {
    display: flex;
    padding: 5px;
    font-size: 1.1em;
    font-weight: 500;
  }
  @media only screen and (max-width: 1160px) {
    form {
      text-align: center;
      display: flex;
      justify-content: center;
      flex-direction: column;
      margin-left: 5%;
    }
    span {
      width: 90px;
    }
    input, textarea {
    width: 60vw;
    height: 20px;
    }
  }
</style>
