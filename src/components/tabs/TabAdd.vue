<template>
  <form class="form" @submit.prevent = "submitInput">
    <div class="form-filed">
      <input
        type="text"
        class="form-input"
        placeholder=" "
        ref="titleInput"
        id="title"
        name="title"
      />
      <label for="" class="form-label">Title</label>
      <label for="" class="label-name">Title</label>
    </div>
    <div class="form-filed">
      <textarea class="form-input" placeholder=" " ref="titleDesc"></textarea>
      <label for="" class="form-label">Description</label>
      <label for="" class="label-name">Description</label>
    </div>
    <div class="form-filed">
      <input type="url" class="form-input" placeholder=" " ref="titleUrl" />
      <label for="" class="form-label">Link</label>
      <label for="" class="label-name">Link</label>
    </div>
    <button class="form-btn" type="submit">add Resource</button>
  </form>
</template>
<script>
export default {
  name: "TabAdd",
  inject: ["addTask"],
  data() {
    return {};
  },
  methods: {
    submitInput() {
      const title = this.$refs.titleInput.value;
      const desc = this.$refs.titleDesc.value;
      const url = this.$refs.titleUrl.value;
      this.$refs.titleInput.value = "";
      this.$refs.titleDesc.value = "";
      this.$refs.titleUrl.value = "";
      if (title.trim() === "" || desc.trim() === "" || url.trim() === "") {
        alert("Vui lòng nhập đầy đủ thông tin");
      } else {
        alert("Thêm thành công")
        this.addTask(title, desc, url);
      }
    },
  },
};
</script>
<style>
input,
textarea {
  outline: none;
}
.form-filed:first-of-type {
  top: 45px;
}
.form-filed:nth-of-type(2) {
  top: 90px;
}
.form-filed:nth-of-type(3) {
  top: 130px;
}
.form-filed:nth-of-type(2) > textarea {
  height: 200px;
}
.form {
  width: 700px;
  box-shadow: 0 2px 8px rgb(0 0 0 / 26%);
  border-radius: 20px;
  height: 600px;
  margin: 0 auto;
  margin-top: 20px;
  padding: 30px 0;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.label-name {
  display: block;
  width: max-content;
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 10px;
  letter-spacing: 1px;
  color: black;
  margin-left: 15px;
  position: absolute;
  top: -30px;
  transition: all 0.25s linear;
  opacity: 1;
  visibility: visible;
}
.form-filed {
  position: relative;
  margin: 0 30px;
}
.form-input {
  width: 100%;
  padding: 10px 20px;
  height: 50px;
  border-radius: 10px;
  margin-left: 0;
  border: 2px solid #bbb;
  transition: all 0.25s linear;
}
.form-input:focus {
  border-color: #c9252c;
}

.form-label {
  position: absolute;
  top: 25px;
  left: 20px;
  transform: translateY(-50%);
  user-select: none;
  pointer-events: none;
  color: #ccc;
  font-size: 18px;
  transition: all 0.25s linear;
}
.form-input:not(:placeholder-shown) + .form-label,
.form-input:focus + .form-label {
  background-color: white;
  color: #c9252c;
  padding: 0 5px;
  top: 0px;
}
.form-input:not(:placeholder-shown) ~ .label-name,
.form-input:focus ~ .label-name {
  opacity: 0;
  visibility: hidden;
}
.form-btn {
  width: max-content;
  outline: none;
  border: none;
  padding: 15px 20px;
  color: white;
  background-color: #c9252c;
  display: block;
  margin: auto auto 0;
  cursor: pointer;
  font-size: 18px;
  border-radius: 10px;
}
</style>
