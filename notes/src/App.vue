<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section class="container">
        <h1>{{title}}</h1>
        <message v-if="message" :message="message" />

        <div>
          <input type="text" v-model="note.title" placeholder="Input title note"><br>
          <textarea v-model="note.descr" placeholder="Input description note"></textarea><br>
          <button type="submit" @click="addNote">Submit</button><br>
        </div>
        <div class="notes">
          <div class="note" v-for="(note, index) in notes" :key="index">
            <h2>{{ note.title }}</h2>
            <p>{{ note.descr }}</p>
            <p>{{ note.date }}</p>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import message from '@/components/Message'
export default {
  components: {
    message
  },
  data() {
    return {
      message: null,
      title: 'Notes App',
      notes: [
        {
          title: 'Some 1 note',
          descr: 'Description note',
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: 'Some 2 note',
          descr: 'Description note',
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: 'Some 3 note',
          descr: 'Description note',
          date: new Date(Date.now()).toLocaleString(),
        }
      ],
      note: {
        title: '',
        descr: '',
        date: ''
      }
    }
  },
  methods: {
    addNote() {
      let { title, descr } = this.note;

      if(title.trim() === '') {
        this.message = `title can't be blank!`;
        return false
      }

      this.notes.push({
        title,
        descr,
        date: new Date(Date.now()).toLocaleString()
      });
      this.message = null;
      this.note.title = '';
      this.note.descr = '';
    }
  }
}
</script>
