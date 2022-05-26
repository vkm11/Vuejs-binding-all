<template>

<!-- Text Binding there are two way to bind -->
 <!-- <div>Hello {{name}}</div> -->
 <div>{{greet}} {{name}}</div>
 <!-- <div v-text="channel"></div> -->

 <!-- Html binding -->
 <!-- <div>{{channel}}</div> -->
<div v-html="channel"></div>
<div v-html="hack"></div>

<!-- Binding to Attribute -->
<h2 v-bind:id="headingId">Heading</h2>
<button v-bind:disabled="isDisabled">Bind</button>

<!-- bindig class -->
<!-- static class -->
<h2 class="underline">Underlined text</h2>
<h2 class="underline" :class="status">Status</h2>

<!-- V-BIND Shorthand (ex:- :class="isPromoted") -->
<h2 :class="isPromoted && 'promoted'">Promoted movie</h2>
<h2 :class="isSoldout? 'sold-out': 'new'">Soldout? movie</h2>
<h2 :class="['new','promoted']" >Newly promoted movie</h2>
<h2 :class="[isPromoted && 'promoted',isSoldout ? 'sold-out' : 'new']" >Array conditional movie</h2>

<h4 :class="{
  promoted: isPromoted,
  new:isSoldout,
  'sold-out':isSoldout
  }">Object conditional movie</h4>

  <!-- Binding style there are two way to bind:- 
  1) object syntax and 2) array syntax -->
<!-- 1.OBJECT SYNTAX -->
<h2 :style="{
  color: highligthColor,
  fontSize: headerSize + 'px',
  padding:'20px'
}">Inline Style</h2>

<h2 :style="headerStyleObject">Style Object</h2>

<!-- 2.ARRAY SYNTAX -->
<div :style="[ baseStyleObject, successStyleObject]">Success style</div>
<div :style="[ baseStyleObject, dangerStyleObject]">Danger style</div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{ 
      greet: 'Hello',
      name:"Vijay",
      channel:'<b>Codevolution<b>',
      hack: `<a href="#" onclick ="alert('you have been hacked!')">Win a prize!<a/>`,
      headingId: 'heading',
      isDisabled:true,
      status: 'success',
      isPromoted: true,
      isSoldout: true,
      highligthColor: 'orange',
      headerSize: 50,
      headerStyleObject: {
        color:'orange',
        fontSize: '50px',
        padding: '20px'
      },
      // array syntax
      baseStyleObject:{ 
        fontSize: '50px',
        padding:'10px',
      },
      successStyleObject: {
        color: 'green',
        backgroundColor:'lightgreen',
        border: '1px solid green',
        padding:'20px'
      },
      dangerStyleObject: { 
        color: 'darkred',
        backgroundColor:'red',
        border:'1px solid darkred',
      }

     }
  },

};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.underline{ 
  text-decoration:underline;
}
.promoted{ 
  font-style:italic;
}
.new{ 
  color: olivedrab
}
.sold-out{ 
  color: red;
}
</style>
