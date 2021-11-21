<template>
 <div class="wrapper">
    <button class="btn__submit" @click="changeTabStore()"> Stored Resources</button>
    <button class="btn__submit" @click="createCourse()"> Add Resources</button>
    <button class="btn__submit" @click="clearCourse()"> Delete All Resources</button>
 </div>
  
  <div class="tab__add" v-if="showTabAdd">
   <form action="">
       <div class="form__control">
           <label for="title">Title</label>
           <input v-model="currentCourse.title" type="text" name="title" id="title">
       </div>
       <div class="form__control">
           <label for="description">Description</label>
           <textarea v-model="currentCourse.description" type="text" name="description" id="description"></textarea>
       </div>
       <div class="form__control">
           <label for="link">Link</label>
           <input v-model="currentCourse.link" type="url" name="link" id="link">
       </div>
       <div class="form__control">
           <button @click.prevent="submitCourse(currentCourse.title, currentCourse.description, currentCourse.link)" type="submit">Add Resource</button>
       </div>
   </form>
   
   <div class="popup" v-if="showPopup" @click="hidePopup">
        <div class="popup__content" @click.stop="this.showPopup=true">
            <header>
                <h2 class="popup__title">Invalid Input</h2>
            </header>
            <div class="popup__para">
                    <p class="popup__des">Unfortunately, at least one input value is invalid.</p>
                    <p class="popup__des">Please check all inputs and make sure you enter at least a few characters into each input field.</p>
            </div>
            <div class="popup__btn">
                <button @click.stop="hidePopup">Okay</button>
            </div>
        </div>
    </div>

 </div>


    <div class="tab__store" v-if="showTabStore">
        <div class="main" v-if="!courses.length">
            <p>No courses added</p>
        </div>
        <ul class="main" v-else>
            <li v-for="(course, index) in courses" :key="index">
                <div>
                    <header class="title">
                        <h2>{{ course.title }}</h2>
                        <button @click="handleDelete(index)">Delete</button>
                    </header>
                    <p class="description">
                        {{ course.description }}
                    </p>
                    <nav class="link">
                        <a v-bind:href="course.link" target="_blank" class="link">View Resource</a>
                    </nav>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>


export default {
  name: 'Button',
  components: {

  },
  data() {
      return {
         courses: [],
         currentCourse: null,
         showTabStore: true,
         showTabAdd: false,
         showPopup: false,
         showDelete: false,
         
      }
  },
  methods: {
    createCourse() {
        const newCourse = {title: '', description: '', link: ''};
        this.currentCourse = newCourse;
        this.changeTabAdd();
    },
    changeTabAdd() {
        this.showTabStore = false;
        this.showTabAdd = true;
    },
    changeTabStore() {
        this.showTabStore = true;
        this.showTabAdd = false;
    },
    submitCourse(title, description, link) {
       if(this.currentCourse.title == '' || this.currentCourse.description == '' || this.currentCourse.link == '') {
           this.showPopup = true;
       }
       else {
           let regex = new RegExp ('^(https?:\\/\\/)?'+ '((([a-z\\d]([a-z\\d-]*[a-z\\d])*)\\.)+[a-z]{2,}|'+ '((\\d{1,3}\\.){3}\\d{1,3}))'+ '(\\:\\d+)?(\\/[-a-z\\d%_.~+]*)*'+ 
                '(\\?[;&a-z\\d%_.~+=-]*)?'+ '(\\#[-a-z\\d_]*)?$','i');
           if (!regex.test(this.currentCourse.link)) {
               alert('Enter the wrong URL');
           }
           else {
            const newCourse = {title: title, description: description, link: link};
            this.courses.push(newCourse);
            this.showTabAdd = false;
            this.showTabStore = true;
           }
       }
    },
    clearCourse() {
       if(this.courses.length) {
            this.courses = JSON.parse(localStorage.courses);
            this.courses.splice(0, this.courses.length);
            // localStorage.courses = JSON.stringify(localStorage.courses);
       }
       else {
           alert('Please add course first!')
       }
    },
    hidePopup() {
        this.showPopup = false;
    },
    handleDelete(index) {
        this.courses = JSON.parse(localStorage.courses);
        this.courses.splice(index, 1);
        // localStorage.courses = JSON.stringify(localStorage.courses);
    }
  },
  watch: {
      courses: {
          handler(newCourses) {
              localStorage.courses = JSON.stringify(newCourses);
          },
          deep: true
      }
  },
  mounted() {
       if(localStorage.courses) {
            this.courses = JSON.parse(localStorage.courses);
        }   
  }
}
</script>

<style scoped>
@import "./button.css";
</style>
