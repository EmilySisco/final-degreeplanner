<template>
  <div class="card my-2">
    <div class="card-body">
      <div class="row">
        <h5 class="col-9">
          <b name = "name">{{ course["Course Name"] }}</b>
        </h5>
        <p class="col-3 text-right" name = "credit"> {{  course["Credit Hours"] }} hours</p>
      </div>

      <div class="row">
        <div class="col-8">
          <p class="card-subtitle" name = "code">{{ course["Course ID"] }}</p>
        </div>
        <div class="col-4 text-right">
          <span class="text-muted">{{ course["Semester Offered"] }}</span>
        </div>
      </div>
      <div class="row">
        <b-form-select v-model="selected" :options="options">

        </b-form-select>

        <b-button block variant="outline-secondary" class="my-2" @click = "AddCourses">Add</b-button>

      </div>

      <div class="row">
        <div class="col">
          <a :href="'#' + shortID" class="card-link fw-light" v-b-toggle:shortID>Course description ›</a>
        </div>
      </div>

      <b-collapse class="course-description collapse card-text" :id="shortID">
        <p class="text-muted card-text">
            {{course["Course Description"]}}
            <b>Prerequisites: </b> {{ course["Prerequisite"]}}
        </p>
      </b-collapse>
    </div>
  </div>
</template>

<script>
export default {
  name: "CourseInfoCard",
  props: {
    course: Object,
  },
  data() {
    return {

      options: [
        { value: null, text: "Please select an option" },
        { value: "fall2019", text: "Fall 2019" },
        { value: "spring2020", text: "Spring 2020" },
        { value: "fall2020", text: "Fall 2020" },
        { value: "spring2021", text: "Spring 2021" },
        { value: "fall2021", text: "Fall 2021" },
        { value: "spring2022", text: "Spring 2022" },
        { value: "fall2022", text: "Fall 2022" },
        { value: "spring2023", text: "Spring 2023" },
      ],
      selected: null,
      disabled: false
      
    }
  },
  methods: {
    convertID(courseID) {
      return courseID.replace(" ", "").replace("/", "-").toLowerCase();
    },
    AddCourses() {
      this.course.semester = this.selected;

      this.$emit("add-course", this.course)
    }
  },
  computed: {
    shortID() {
      return this.course['Course ID'].replace(" ", "").replace("/", "-").toLowerCase();
    }
  }


};
</script>

<style>
* {
  font-family: 'leapis';
}
</style>
