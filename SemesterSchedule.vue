<template>

  <div class="col-lg-6 semester-schedules">
            <h3>Semester Schedules</h3>

            <div
              v-for="schedule in schedules"
              v-bind:key="schedule.id"
              class="accordion"
              id="schedule.id"
            >
              <div class="accordion-item">
                <h2
                  class="accordion-header"
                  id="fall2019heading"
                  v-b-toggle:[schedule.collapseId]
                >
                  <div class="schedules">
                    <h4 class="my-0">{{ schedule.name }}</h4>
                  </div>
                </h2>
                <b-collapse :id="schedule.collapseId">
                  <div class="accordion-body">
                    <table class="table table-hover">
                      <thead>
                        <th>Course</th>
                        <td></td>
                        <td></td>
                        <th>Credits</th>
                      </thead>
                      <tr
                        v-for="classes in schedule.classes"
                        v-bind:key="classes.id" >

                        <td> {{classes["Course ID"]}}</td>
                        <td> {{classes["Course Name"]}}</td>
                        <td> {{classes["Credit Hours"]}}</td>
                        <td> <p class="btn" id = "remove" @click="remove(classes, schedule)" > <b>Remove</b> </p></td>
                      </tr>
                    </table>
                  </div>
                </b-collapse>
              </div>
            </div>
          </div>
</template>

<script>



  export default {
    name: "SemesterSchedule.vue",
    props: {
      title: String,
      schedules: Object
    },
    methods: {

      remove(classes, schedule) {
        
            classes.semester = schedule.id;
            this.$emit("remove", classes);
      }
    }
  }
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500;1,600;1,700&display=swap');

.accordion-header {
    background-color: 	rgb(173, 216, 230);
    margin: auto;
    border-top: 2px solid white;
    font-family: 'leapis';
    padding-left:100%;
    padding-right:100%;
    padding-top: 5px;
}

.schedules h4 {
     writing-mode: horizontal-tb;
     text-align: justify;
     padding: 100%;
     display: inline-block;
}
.accordion-body {
  text-align: justify;
  margin-left: auto;
  margin-right: auto;
  display: block;
  justify-content: center;
  float: center;
}

#remove {
  color: darkred;
  text-decoration: underline;
}

</style>