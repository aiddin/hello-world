<template>
  <div>
    <date-dropdown
      default="1993.02.27"
      min="1940"
      max="2020"
      :months-names="months"
      :format="'MM.DD.YYYY'"
      v-model="date_of_birth"
      id="dateDropdownDesign"
    >
    </date-dropdown>
    /** i tried to use :format date option , but it did not work **/
  </div>
</template>

<script>
import DateDropdown from "vue-date-dropdown";
import moment from "moment";

export default {
  components: {
    DateDropdown,
  },
  data() {
    return {
      date_of_birth: "",
      new_date_of_birth: "",
      months: "",
    };
  },
  watch: {
    date_of_birth() {
      this.new_date_of_birth = moment(this.date_of_birth, "DD.MM.YYYY").format("MM.DD.YYYY");
      console.log(this.date_of_birth);
      console.log(this.new_date_of_birth);
    },
    months() {
      console.log(this.months);
    },
  },
};
</script>