<template>
  <div id="post">
    <li class="list-group-item">
      <i class="glyphicon glyphicon-chevron-up" @click="upvote" :class="{disabled: upvoted}"></i>
      <span class="label label-primary">{{ votes }}</span>
      <i class="glyphicon glyphicon-chevron-down" @click="downvote" :class="{disabled: downvoted}"></i>
      <a>{{ post.title }}</a>
    </li>
  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      upvoted: false,
      downvoted: false
    }
  },
  methods:{
    upvote(){
      this.upvoted =! this.upvoted;
      this.downvoted= false;
    },
    downvote(){
      this.downvoted =! this.downvoted;
      this.upvoted= false;
    }
  },
  computed: {
    votes(){
      if(this.upvoted){
        return this.post.votes + 1;
      } else if(this.downvoted){
        return this.post.votes - 1; 
      } else{
        return this.post.votes;
      }
    }
  }
  ,
  props:['post']
  
}

</script>


<style>
.disabled{
  color: orange
}
#post{
  text-align:left;
 

}

</style>