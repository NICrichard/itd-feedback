<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col mt-0 text-right">
        <button class="btn btn-default" data-dismiss="modal">x</button>
      </div>
    </div>

    <div class="card">
      <div class="card-header">Help us improve ITD online services</div>
      <div class="card-body">
        <h5
          class="card-title"
        >How would you prefer to do business with ITD (example, renew your license)?</h5>
        <div class="form-check">
          <input type="radio" name="itd-feedback" id="itd1" value="app" class="form-check input">
          <label for="itd1" class="form-check-label">Via an app downloaded to my device</label>
        </div>
        <div class="form-check">
          <input
            type="radio"
            name="itd-feedback"
            id="itd2"
            value="website"
            class="form-check input"
          >
          <label for="itd2" class="form-check-label">Online through a secure website</label>
        </div>
        <div class="form-check">
          <input type="radio" name="itd-feedback" id="itd3" value="person" class="form-check input">
          <label for="itd3" class="form-check-label">In person</label>
        </div>
        <div class="form-group">
          <label for="comments">Comment box, optional</label>
          <textarea
            name="itd-comment"
            id="comments"
            cols="30"
            rows="10"
            class="form-control"
            maxlength="300"
          ></textarea>
        </div>
        <div class="card-footer">
          <button class="btn btn-primary" data-dismiss="modal">Submit</button>
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
  name: "itd",
  data: function() {
    return {};
  }
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

.feedback {
  padding-top: 20px;
}

textarea {
  resize: none;
}
</style>
