<template>
  <div class="home flex-grow-1 d-flex flex-column align-items-center justify-content-center">
    <transition appear @before-enter="beforeEnter" @enter="enter" @after-enter="afterEnter">
      <h1>Hello</h1>
    </transition>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Labore rem sunt amet mollitia ratione, est esse. Totam nobis facere sed, aperiam consectetur illum ea ratione, suscipit alias ab cupiditate possimus.</p>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quis sunt quia illum assumenda laboriosam veritatis necessitatibus tenetur repellat maiores ipsa hic libero voluptates ad, id quam earum qui repellendus ratione!</p>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Asperiores ab ipsa placeat ut itaque, debitis voluptatibus harum rem natus eum voluptatem, perferendis mollitia esse neque sed quibusdam? Nisi, consequuntur. Illo.</p>
  </div>
</template>

<script>
import { ref } from 'vue'
import gsap from 'gsap'
export default {
  name: 'Home',
  setup() {
    const beforeEnter = (el) => {
      console.log('before enter - set initial state')
      el.style.transform = 'translateY(-60px)'
      el.style.opacity = 0
    }
    const enter = (el, done) => {
      console.log('starting to enter - make transition')
      gsap.to(el, {
        duration: 3,
        y: 0,
        opacity: 1,
        ease: 'bounce.out',
        onComplete: done
      })
    }
    const afterEnter = () => {
      console.log('after enter')
    }
    return { beforeEnter, enter, afterEnter }
  }
}
</script>

<style scoped lang="scss">
.home{
  text-align: center;
  user-select: none;
  > img{
    height: 200px;
    width: 200px;
  }
}
</style>
