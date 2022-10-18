<!-- eslint-disable vuejs-accessibility/form-control-has-label -->
<!-- eslint-disable vuejs-accessibility/click-events-have-key-events -->
<!-- eslint-disable max-len -->
<template>
  <div class="fixed z-2 inset-0 overflow-y-auto bg-black bg-opacity-50">
    <div
      class="flex items-start justify-center max-h-screen pt-20 text-center z-10 mx-10"
    >
      <div
        class="overflow-auto h-auto bg-black w-auto mt-20 mx-auto p-8 shadow-md rounded-2xl text-white"
      >
        <div class="pb-5">
          <p class="text-lg">
            Please select the timezone
          </p>
        </div>
        <select
          v-model="locationTimezone"
          class="p-2 text-black"
          @update="getTimeZone(locationTimezone)"
        >
          <option value="" disabled selected>select your a timezone</option>
          <option
            v-for="(location, index) in timezone"
            :key="index"
            class="text-black"
            :value="index"
          >
            {{ location }}
          </option>
        </select>
        <div class="py-5">
          <button
            @click="getTimezone(locationTimezone)"
            class="text-white w-32 h-10 bg-purple-500 rounded-md"
          >
            Send
          </button>
        </div>
        <div>
          <p class="font-bold text-white">{{currentHourTimezoned}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import timezones from 'google-timezones-json';

export default {
  name: 'ModalLocation',

  data() {
    return {
      timezone: timezones,
      locationTimezone: '',
      currentHourTimezoned: '',
    };
  },

  methods: {
    getTimezone(localTime) {
      console.log(localTime);
      const options = {
        timeZone: localTime,
        year: 'numeric',
        month: 'numeric',
        day: 'numeric',
        hour: 'numeric',
        minute: 'numeric',
        second: 'numeric',
      };
      const formatter = new Intl.DateTimeFormat([], options);
      this.currentHourTimezoned = formatter.format(new Date());

      console.log(formatter.format(new Date()));
    },
  },
};
</script>
