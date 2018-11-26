<template>
  <div id="itd" class="container">
    <div class="row">
      <div class="col mt-0 text-right">
        <button class="btn btn-default" data-dismiss="modal">x</button>
      </div>
    </div>
    <div class="row">
      <div class="card">
        <div class="card-header">Help us improve ITD online services</div>
        <div class="card-body">
          <div
            class="card-title"
          >How would you prefer to do business with ITD (example, renew your license)?</div>
          <div class="card-text">
            <div class="form-check">
              <input
                type="radio"
                class="form-check-input"
                name="itd-feedback"
                value="app"
                id="itd1"
              >
              <label for="itd1" class="form-check-label">Via an app downloaded to my device</label>
            </div>
            <div class="form-check">
              <input
                type="radio"
                class="form-check-input"
                name="itd-feedback"
                value="website"
                id="itd2"
              >
              <label for="itd2" class="form-check-label">Online through a secure website</label>
            </div>
            <div class="form-check">
              <input
                type="radio"
                class="form-check-input"
                name="itd-feedback"
                value="in-person"
                id="itd3"
              >
              <label for="itd3" class="form-check-label">In person</label>
            </div>
          </div>
          <div class="form-group">
            <label for="comments">Comments, optional</label>
            <textarea
              name="comments"
              id="comments"
              maxlength="300"
              cols="30"
              rows="10"
              class="form-control"
            ></textarea>
          </div>
        </div>
        <div class="card-footer">
          <button class="btn btn-primary">submit</button>
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
var $ = jQuery;
export default {
  name: "itd"
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  max-width: 500px;
  height: auto;
  border: 3px solid black;
  background-color: azure;
  padding: 20px;
  margin: auto;
  text-align: center;
}

textarea {
  resize: none;
}
</style>
