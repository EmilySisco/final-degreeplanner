<template>

  <div class="col-lg-6 semester-schedules">
            <h3>Semester Schedules</h3>

            <div
              v-for="schedule in schedules"
              v-bind:key="schedule.id"
              class="accordion my-4"
              id="schedule.id"
            >
              <div class="accordion-item">
                <h2
                  class="accordion-header"
                  id="fall2019heading"
                  v-b-toggle:[schedule.collapseId]
                >
                  <div class="">
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
    data() {
      return {

      }
    }
  }
</script>

<style>

.accordion {
    min-width: 40%;
}

</style>