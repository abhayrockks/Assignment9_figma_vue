<template>
  <div>
    <transition name="modal">
      <div class="modal-mask">
        <div class="modal-wrapper">
          <div class="modal-container">
            <div>
              <form>
                <label>Add Todo</label>
                <br />
                <textarea rows="10" v-model="todo" required></textarea>
                <br />
                <p id="cancel" @click="cancel">Cancel</p>
                <p id="done" @click.prevent="submit">Done</p>
              </form>
            </div>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "Form",
  data: function () {
    return {
      todo: "",
    };
  },

  methods: {
    submit() {
      if (this.todo == "") {
        return alert("Nothing to add");
      }
      this.$emit("submitItem", this.todo);
      this.$emit("close");
    },
    cancel() {
      this.$emit("close");
    },
  },
};
</script>

<style>
.heading {
  font-family: SFProText;
  font-size: 18px;
  line-height: 41px;
  letter-spacing: 0.01em;
  color: #000000;
}

#cancel {
  float: left;
  margin-top: 8px;
  margin-left: 10px;
  font-family: SF Pro Text;
  font-style: normal;
  font-weight: normal;
  font-size: 18px;
  line-height: 21px;
  letter-spacing: -0.434118px;
  color: #006cff;
}

#done {
  margin-top: 8px;
  margin-left: 92%;
  font-family: SF Pro Text;
  font-style: normal;
  font-weight: 600;
  font-size: 18px;
  line-height: 21px;
  letter-spacing: -0.434118px;
  color: #006cff;
}

textarea {
  border-radius: 10px;
  width: 100%;
  resize: none;
  border: 1px solid #ebeff5;
  box-sizing: border-box;
}

label {
  font-family: SFProText;
  font-size: 18px;
  line-height: 41px;
  letter-spacing: 0.01em;
  color: #000000;
}
@media screen and (max-width: 900px) {
  #done {
    margin-left: 90%;
  }
}

@media screen and (max-width: 710px) {
  #done {
    margin-left: 87%;
  }
}

@media screen and (max-width: 600px) {
  #done {
    margin-left: 85%;
  }
}

@media screen and (max-width: 450px) {
  #done {
    margin-left: 80%;
  }
}
</style>