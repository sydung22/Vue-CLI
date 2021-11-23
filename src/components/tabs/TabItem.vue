<template>
    <div class="tab-item">
        <div class="title">
      <h2>{{title}}</h2>
      <button @click="deleteTask(title)" >Delete</button>
    </div>
    <p>{{desc}}</p>
    <div class="link-view"><a :href="link" target= "_blank">View Resource</a></div>
    </div>
</template>
<script>
export default {
    name:"TabItem",
    props: ["title", "desc", "link"],
    inject:["deleteTask"],

}
</script>
<style scoped>
.tab-item {
  border-radius: 12px;
  box-shadow: 0 2px 8px rgb(0 0 0 / 26%);
  padding: 1rem;
  margin: 2rem auto;
  max-width: 43.5rem;
}
.tab-item .title {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.tab-item .title button {
  outline: none;
  border: none;
  padding: 10px 20px;
  color: #c9252c;
  background-color: unset;
  display: block;
  cursor: pointer;
  font-size: 18px;
  border-radius: 10px;
  transition: 0.3s;
}
.tab-item .title button:hover {
  background-color: #c9252c;
  color: #fff;
}
.tab-item p,
.link-view {
  text-align: left;
  margin-top: 13px;
}
.tab-item p{
    text-align: justify;
}
.link-view a {
  text-decoration: none;
  color: #c9252c;
  position: relative;
}
.link-view a::before{
    content: '';
    position: absolute;
    left: 0;
    bottom: -3px;
    height: 2px;
    width: 100%;
    background-color: #c54c52;
    color: #c54c52;
    transform: scale(0);
    transition: 0.4s linear;
}
.link-view a:hover {
  color: #c54c52;
}
.link-view a:hover::before{
    transform: scale(1);

}
</style>