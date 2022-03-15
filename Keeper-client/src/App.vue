<template>
<Header/>
<AddNote @add-note="addNote"/>
<Note @delete-note="deleteNote" @update-note="updateNote" :data= "data"/>
</template>

<script>
import Note from './components/Note'
import Header from './components/Header'
import AddNote from './components/AddNote'
import getApi from './url'
export default {
  name: 'App',
  components: {
    Header,
    AddNote,
    Note
  },
  data () {
    return {
      data: []
    }
  },
  methods: {
    deleteNote (id) {
      console.log(id)

      getApi.put('deletenote', { id: id }).then((response) => console.log(response))
      this.data = this.data.filter((data) => data.id !== id)
    },
    addNote (note) {
      const len = this.data.length - 1
      const lastId = this.data[len]
      note.id = Number(lastId + 1)

      // axios.post('addnote', note)
      getApi.post('addnote', note).then((response) => console.log(response))
      console.log(note)
      this.data.push(note)
      //
    },
    updateNote (updatednote) {
      console.log(updatednote)
      getApi.put('updatenote', updatednote).then((response) => console.log(response))
      window.location.reload()
    }
  },
  created () {
    getApi.get('api/').then((response) => {
      this.data = response.data
      console.log(this.data)
    })
    // this.data = [jsonData]
    // [
    //   { id: 1, name: 'virat', message: 'be the best you can be ' },
    //   { id: 2, name: 'rohit', message: 'sun will rise again tommorrow' },
    //   { id: 3, name: 'Dhoni', message: "i don't see any in em" },
    //   { id: 4, name: 'kane Williamson', message: 'its me who should decide , whether i smile or cry . i prefer smile ' },
    //   { id: 5, name: 'Afridi', message: ' Age is just a number' },
    //   { id: 6, name: 'de villiers', message: ' ipl is harder than world cup' }

    // ]
  }
}
</script>

<style>
*{
  padding: 0;
  margin: 0;
}
body {
  background: #eee;
}
</style>
