<template>
  <div id="itd" class="container">
    <div class="row">
      <div class="panel panel-default">
        <div class="panel-heading">
          Help us improve ITD online services
          <div class="m-btn">
            <button class="btn btn-default" data-dismiss="modal">x</button>
          </div>
        </div>
        <div class="panel-title">
          How would you prefer to do business with ITD (example, renew your
          license)?
        </div>
        <div class="panel-body">
          <div class="form-check">
            <input
              type="radio"
              class="form-check-input"
              name="itd-feedback"
              value="app"
              id="itd1"
              v-model="answer"
            />&nbsp;
            <label for="itd1" class="form-check-label">
              Via an app downloaded to my device</label
            >
          </div>
          <div class="form-check">
            <input
              type="radio"
              class="form-check-input"
              name="itd-feedback"
              value="website"
              id="itd2"
              v-model="answer"
            />&nbsp;
            <label for="itd2" class="form-check-label">
              Online through a secure website</label
            >
          </div>
          <div class="form-check">
            <input
              type="radio"
              class="form-check-input"
              name="itd-feedback"
              value="in-person"
              id="itd3"
              v-model="answer"
            />&nbsp;
            <label for="itd3" class="form-check-label"> In person</label>
          </div>
        </div>
        <div class="form-group">
          <label for="comments">Comments, <em>optional</em></label>
          <textarea
            name="comments"
            id="comments"
            maxlength="300"
            cols="30"
            rows="3"
            class="form-control"
            v-model="msg"
          ></textarea>
        </div>
        <div class="panel-footer text-right">
          <button class="btn btn-primary" @click="submit">submit</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.min.css";
import "jquery/src/jquery.js";
import "bootstrap/dist/js/bootstrap.min.js";
import axios from "axios";
export default {
  name: "itd",
  data: function() {
    return {
      token: "",
      answer: "",
      msg: ""
    };
  },
  methods: {
    submit: function() {
      let self = this;
      var headers = {
        "Content-Type": "application/json;charset=UTF-8",
        "Access-Control-Allow-Origin": "*",
        "X-Content-Type-Options": "nosniff"
      };
      if (this.token !== "") {
        this.token = localStorage.getItem("ai-itd");
        axios
          .post(
            "https://y1dtrwmk40.execute-api.us-east-1.amazonaws.com/UAT/RateMyTater-test",
            {
              tater_id: this.token,
              rating: this.answer.toString(),
              text: this.msg.toString(),
              appName: window.appName
            },
            headers
          )
          .then(response => {
            // console.log(response);
            this.token = response.data.tater_id;
            localStorage.setItem("ai-itd", this.token);
          })
          .catch(e => {
            console.error(e);
          });
      } else {
        axios
          .post(
            "https://y1dtrwmk40.execute-api.us-east-1.amazonaws.com/UAT/RateMyTater-test",
            {
              rating: this.answer.toString(),
              text: this.msg.toString(),
              appName: window.appName
            },
            headers
          )
          .then(response => {
            // console.log(response);
            this.token = response.data.tater_id;
            localStorage.setItem("ai-itd", this.token);
          })
          .catch(e => {
            console.error(e);
          });
      }
    }
  },
  created: function() {
    if (localStorage.getItem("ai-itd")) {
      this.token = localStorage.getItem("ai-itd");
    }
  }
};
</script>

<style scoped>
#itd {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  max-width: 500px;
  height: auto;
  padding: 20px;
  margin: auto;
}

.m-btn {
  display: inline;
  float: right;
}

.panel-heading {
  font-weight: bold;
  font-size: 1.5em;
}

.panel-title {
  padding: 10px;
}

.form-group {
  margin-bottom: 0;
  padding: 10px;
}

label {
  font-weight: normal;
}

textarea {
  resize: none;
}
</style>
