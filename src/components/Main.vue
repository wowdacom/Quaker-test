<template>
  <div class="main">
    <div class="space">
      I am space
    </div>
    <h1 :style="steps[step]">Hello I am Your Main</h1>
    <img class="start-map" :src="map.img" alt="">
    <div class="hints-wrapper">
      <div class="hint-box1">hint1</div>
      <div class="hint-box2">hint2</div>
      <div class="hint-box3">hint3</div>
      <div class="hint-box4">hint4</div>
      <div class="hint-box5">hint5</div>
      <img class="end-map" :src="map.img" alt="">
    </div>
    <img class="map-fixed" :src="map.img" :style="steps[step]" alt="">
    
    <p>1234</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      map: {
        img: require('@/assets/map.jpg'),
        offsetStart: 0,
        offsetEnd: 0
      },
      step: 0,
      screenHeight: 0,
      steps: [
        {
          position: 'fixed',
          top: '0',
          left: '0',
          opacity: '0',
          transform: 'scale(1)',
          'transform-origin': '0 0'
        },
        {
          position: 'fixed',
          top: '0',
          left: '0',
          opacity: '1',
          transform: 'scale(2)',
          'transform-origin': '0 0'
        }
        // {
        //   position: 'fixed',
        //   top: '0',
        //   left: '0',
        //   transform: 'scale(2)',
        //   opacity: '1',
        //   'transform-origin': '50% 50%'
        // },
        // {
        //   position: 'fixed',
        //   top: '0',
        //   left: '0',
        //   transform: 'scale(2)',
        //   opacity: '1',
        //   'transform-origin': '100% 0'
        // },
        // {
        //   position: 'fixed',
        //   top: '0',
        //   left: '0',
        //   transform: 'scale(2)',
        //   opacity: '1',
        //   'transform-origin': '100% 100%'
        // },
        // {
        //   position: 'fixed',
        //   top: '0',
        //   left: '0',
        //   transform: 'scale(1)',
        //   opacity: '1',
        //   'transform-origin': '0 100%'
        // },
        // {
        //   position: 'fixed',
        //   top: '0',
        //   left: '0',
        //   transform: 'scale(1)',
        //   opacity: '1',
        //   'transform-origin': '0 0'
        // }
      ]
    }
  }, 
  methods: {
    handleScroll () {
      let currentHieght = window.pageYOffset

      if ( this.map.offsetStart < currentHieght && currentHieght < this.map.offsetEnd ) {
        this.step = 1;
      } else {
        this.step = 0;
      }
      // if (this.map.offset < currentHieght && currentHieght < this.map.offset + 1000 ) {
      //   this.step = 1;
      // } else if ( this.map.offset + 1001 < currentHieght && currentHieght < this.map.offset + 2000 ) {
      //   this.step = 2;
      // } else if ( this.map.offset + 2001 < currentHieght && currentHieght < this.map.offset + 3000 ) {
      //   this.step = 3;
      // } else if ( this.map.offset + 3001 < currentHieght && currentHieght < this.map.offset + 4000 ) {
      //   this.step = 4;
      // } else if ( this.map.offset + 4001 < currentHieght && currentHieght < this.map.offset + 5000 ) {
      //   this.step = 5;
      // } else {
      //   this.step = 0;
      // }
    }
  },
  mounted () {
    // let bodyRect   = document.body.getBoundingClientRect(),
    //     mapStartElement = document.querySelector('.page-start'),  
    //     mapStartRect   = mapStartElement.getBoundingClientRect(),
    //     mapEndElement = document.querySelector('.page-end'),  
    //     mapEndRect   = mapEndElement.getBoundingClientRect(),
    //     offsetStart     = mapStartRect.top - bodyRect.top,
    //     offsetEnd       = mapEndRect.top - bodyRect.top ;

    //     this.map.start = offsetStart;
    //     this.map.end = offsetEnd;


    //     console.log(offsetStart);
    //     console.log(offsetEnd);
    let bodyRect   = document.body.getBoundingClientRect(),
        mapStartElement = document.querySelector('.start-map'),  
        mapStartRect  = mapStartElement.getBoundingClientRect(),
        offsetStart   = mapStartRect.top - bodyRect.top,
        mapEndElement = document.querySelector('.end-map'),  
        mapEndRect    = mapEndElement.getBoundingClientRect(),
        offsetEnd     = mapEndRect.top - bodyRect.top
        // wrapper       = document.querySelector('.hints-wrapper')
        // wrapper.style.height = document.body.clientHeight * 5

        this.screenHeight = document.body.clientHeight
        this.map.offsetStart = offsetStart
        this.map.offsetEnd = offsetEnd

        console.log(this.screenHeight)
        console.log(this.map.offsetStart)
        console.log(this.map.offsetEnd)

        window.addEventListener('scroll', this.handleScroll)

  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.main {
  height: 100000px;
}
.space {
  height: 3000px;
}
h1 {
  cursor: pointer;
}
.start-map {
  position: static;
}
.hints-wrapper {
  @media only screen and (max-width: 600px) {
    width: 100vw;
    right: 0;
    height: 6000px;
  }
  position: relative;
  height: 8000px;
}
.hints-wrapper > .hint-box1 {
  @media only screen and (max-width: 600px) {
    width: 100%;
    right: 10;
  }
  position: absolute;
  z-index: 2;
  right: 100px;
  top: 0%;
  height: 200px;
  width: 400px;
  border: solid 1px	#00BFFF;
  border-radius: 5px;
  background-color: rgba($color: white, $alpha: 0.2)
}
.hints-wrapper > .hint-box2 {
  @media only screen and (max-width: 600px) {
    width: 100vw;
    right: 0;
  }
  position: absolute;
  z-index: 2;
  right: 100px;
  top: 20%;
  height: 200px;
  width: 400px;
  border: solid 1px	#00BFFF;
  border-radius: 5px;
  background-color: rgba($color: white, $alpha: 0.2)
}
.hints-wrapper > .hint-box3 {
  @media only screen and (max-width: 600px) {
    width: 100vw;
    right: 0;
  }
  position: absolute;
  z-index: 2;
  right: 100px;
  top: 40%;
  height: 200px;
  width: 400px;
  border: solid 1px	#00BFFF;
  border-radius: 5px;
  background-color: rgba($color: white, $alpha: 0.2)
}
.hints-wrapper > .hint-box4 {
  @media only screen and (max-width: 600px) {
    width: 100vw;
    right: 0;
  }
  position: absolute;
  z-index: 2;
  right: 100px;
  top: 60%;
  height: 200px;
  width: 400px;
  border: solid 1px	#00BFFF;
  border-radius: 5px;
  background-color: rgba($color: white, $alpha: 0.2)
}
.hints-wrapper > .hint-box5 {
  @media only screen and (max-width: 600px) {
    width: 100vw;
    right: 0;
  }
  position: absolute;
  z-index: 2;
  right: 100px;
  top: 80%;
  height: 200px;
  width: 400px;
  border: solid 1px	#00BFFF;
  border-radius: 5px;
  background-color: rgba($color: white, $alpha: 0.2)
}
.end-map {
  position: absolute;
  bottom: 0;
  left: 0;
}
.map-fixed {
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  opacity: 1;
  transform: scale(1);
  transform-origin: 0 0;
  height: auto;
  transition: all 0.5s;
}

</style>
