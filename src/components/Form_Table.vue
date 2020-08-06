<template>
  <div class="main">
    <header>Today</header>
    <button id="add_button" @click="showModal = true">
      <svg
        width="14"
        height="14"
        viewBox="0 0 18 18"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          fill-rule="evenodd"
          clip-rule="evenodd"
          d="M10 6C10 7.10457 10.8954 8 12 8H17C17.5523 8 18 8.44771 18 9C18 9.55229 17.5523 10 17 10H12C10.8954 10 10 10.8954 10 12V17C10 17.5523 9.55229 18 9 18C8.44771 18 8 17.5523 8 17V12C8 10.8954 7.10457 10 6 10H1C0.447715 10 0 9.55229 0 9C0 8.44771 0.447715 8 1 8H6C7.10457 8 8 7.10457 8 6V1C8 0.447715 8.44771 0 9 0C9.55229 0 10 0.447715 10 1V6Z"
          fill="#006CFF"
        />
      </svg>
    </button>
    <br />
    <br />
    <Form v-on:submitItem="submit" v-if="showModal" @close="showModal = false" />
    <div id="row" v-for="(item, index) in details" v-bind:key="index">
      <label class="container">
        <input type="checkbox" />
        <span class="checkmark"></span>
      </label>
      <div id="list">
        <span class="list_details">{{item.todo}}</span>
        <span
          class="dot"
          v-bind:style="{'background-color': colors[Math.floor(Math.random() * colors.length)]}"
        ></span>
      </div>
      <div class="smallicons" v-if="index == 1">
        <svg
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M20 13C20 17.4183 16.4183 21 12 21C7.58172 21 4 17.4183 4 13C4 8.58172 7.58172 5 12 5C16.4183 5 20 8.58172 20 13Z"
            stroke="#006CFF"
            stroke-width="2"
          />
          <path d="M12 9V13" stroke="#006CFF" stroke-width="2" stroke-linecap="round" />
          <path d="M15 13H12" stroke="#006CFF" stroke-width="2" stroke-linecap="round" />
          <path
            opacity="0.3"
            d="M21 6.5L18.7938 4.29383"
            stroke="#006CFF"
            stroke-width="2"
            stroke-linecap="round"
          />
          <path
            opacity="0.3"
            d="M3 6.5L5.20617 4.29383"
            stroke="#006CFF"
            stroke-width="2"
            stroke-linecap="round"
          />
        </svg>
        <span id="time">7:00pm</span>
      </div>
      <hr />
    </div>
  </div>
</template>


<script>
import Form from "./Form.vue";
export default {
  name: "Form_Table",
  components: {
    Form,
  },
  data() {
    return {
      showModal: false,
      colors: ["red", "yellow", "blue", "orange", "green", "coral"],
      details: [
        {
          todo: "Start making a presentation",
        },
        {
          todo: "Pay for rent",
        },
        {
          todo: "Buy a milk",
        },
        {
          todo: "Don’t forget to pick up Mickael from school",
        },
        {
          todo: "Buy a chocolate for Charlotte",
        },
      ],
    };
  },

  methods: {
    submit(value) {
      this.details.push({
        todo: value,
      });
    },
  },
};
</script>
<style>
hr {
  border-top: 1px;
  margin-top: 21px;
  margin-left: 50px;
}
header {
  float: left;
  font-family: SFProDisplay;
  font-size: 32px;
  line-height: 41px;
  letter-spacing: 0.01em;
  color: #252a31;
}
#add_button {
  float: right;
  background: white;
  width: 28px;
  height: 28px;
  border-radius: 100%;
  border: 1px solid #006cff;
  outline: none;
}

#row {
  margin-top: 20px;
  padding-top: 10px;
}
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.modal-wrapper {
  margin-top: 96px;
}
.modal-container {
  height: 250px;
  width: 78%;
  margin: auto;
  padding: 15px;
  background-color: #fff;
  border-radius: 10px;
  border: 1px solid #ebeff5;
  transition: all 0.3s ease;
}

.container {
  display: block;
  position: relative;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}
/* Create a custom checkbox */
.checkmark {
  text-align: center;
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  border: solid #dadada;
  border-radius: 15px;
}

/* When the checkbox is checked, add a blue background */
.container input:checked ~ .checkmark {
  background-color: #2196f3;
}

/* Create the tick (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the tick */
.container .checkmark:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
#list {
  display: flex;
  margin-top: 3px;
  margin-left: 50px;
}

.list_details {
  align-self: center;
  padding: 0;
  margin-top: 2px;
  display: inline-block;
  font-family: SFProText;
  font-size: 18px;
  line-height: 21px;
  letter-spacing: -0.02em;
  color: #252a31;
  max-width: 250px;
  word-wrap: break-word;
}

.dot {
  align-self: center;
  margin-left: auto;
  margin-right: 8px;
  height: 12px;
  width: 12px;
  border-radius: 50%;
}

.smallicons {
  display: flex;
  margin-left: 44px;
}

.smallicons svg {
  align-self: center;
  height: 17px;
  mix-blend-mode: normal;
  opacity: 0.3;
}

#time {
  align-self: center;
  font-family: SFProText;
  font-size: 14px;
  line-height: 16px;
  letter-spacing: -0.337647px;
  color: #252a31;
  mix-blend-mode: normal;
  opacity: 0.3;
}

.main {
  padding: 10px;
}
</style>