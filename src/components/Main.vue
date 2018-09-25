<template>
  <div class="main">
    <div class="space">
      I am space
    </div>
      <h1>Start of The map</h1>
    <div class="hints-wrapper" :style="mapAnimation.steps[mapAnimation.step]">
      <!-- <div v-for="(item, index) in map.hints" :key="index" class="hint-box">
        <h5>{{ item.title }}</h5>
        {{ item.content }}
      </div> -->
      <!-- <img class="start-map" :src="map.img" alt=""> -->
    </div>
    
    <p>End of the Map</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      pageInfo: {
        screenHeight: 0
      },
      map: {
        img: require('@/assets/map.jpg'),
        offsetStart: 0,
        offsetEnd: 0,
        height: 0,
        hints: [
          {
            title: 'hint 1',
            content: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Blanditiis, nihil.'
          },
          {
            title: 'hint 2',
            content: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Blanditiis, nihil.'
          },
          {
            title: 'hint 3',
            content: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Blanditiis, nihil.'
          },
          {
            title: 'hint 4',
            content: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Blanditiis, nihil.'
          },
          {
            title: 'hint 5',
            content: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Blanditiis, nihil.'
          }
        ]
      },
      mapAnimation: {
        step: 0,
        steps: [
          {
            'background-attachment': 'scroll',
            'background-size': '100%'
          },
          {
            'background-attachment': 'fixed',
            'background-size': '100%',
            'background-position': '50% 50%'
          },
          {
            'background-attachment': 'fixed',
            'background-size': '400%',
            'background-position': '0 0'
          },
          {
            'background-attachment': 'fixed',
            'background-size': '400%',
            'background-position': '0 100%'
          },
          {
            'background-attachment': 'fixed',
            'background-size': '400%',
            'background-position': '100% 0'
          },
          {
            'background-attachment': 'fixed',
            'background-size': '400%',
            'background-position': '100% 100%'
          },
          {
            'background-attachment': 'fixed',
            'background-size': '400%',
            'background-position': '50% 50%'
          },
          {
            'background-attachment': 'scroll',
            'background-size': '100%'
          }
        ]
      }
    }
  }, 
  methods: {
    handleScroll () {
      let currentHieght = window.pageYOffset,
          wrapperSection = this.map.height/6
          console.log(wrapperSection)
      if ( this.map.offsetStart < currentHieght && currentHieght < this.map.offsetStart + wrapperSection ) {
        console.log("its work")
        this.mapAnimation.step = 1;
      } else if ( this.map.offsetStart + wrapperSection + 1 < currentHieght && currentHieght < this.map.offsetStart + wrapperSection * 2 ) {
        this.mapAnimation.step = 2;
      } else if ( this.map.offsetStart + wrapperSection * 2 + 1 < currentHieght && currentHieght < this.map.offsetStart + wrapperSection * 3 ) {
        this.mapAnimation.step = 3;
      } else if ( this.map.offsetStart + wrapperSection * 3 + 1 < currentHieght && currentHieght < this.map.offsetStart + wrapperSection * 4 ) {
        this.mapAnimation.step = 4;
      } else if ( this.map.offsetStart + wrapperSection * 4 + 1 < currentHieght && currentHieght < this.map.offsetStart + wrapperSection * 5 ) {
        this.mapAnimation.step = 5;
      } else if ( this.map.offsetStart + wrapperSection * 5 + 1 < currentHieght && currentHieght < this.map.offsetStart + wrapperSection * 6 ) {
        this.mapAnimation.step = 6;
      } else {
        this.mapAnimation.step = 0;
      }
    }
  },
  mounted () {
    let bodyRect   = document.body.getBoundingClientRect(),
        mapStartElement = document.querySelector('.hints-wrapper'),  
        mapStartRect  = mapStartElement.getBoundingClientRect(),
        mapHeight = mapStartRect.height,
        offsetStart   = mapStartRect.top - bodyRect.top

        this.map.height = mapHeight
        this.map.offsetStart = offsetStart

        console.log(mapHeight)
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
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
}
.hints-wrapper {
  @media only screen and (max-width: 600px) {
    width: 100vw;
    right: 0;
    height: 6000px;
  }
  transition: all 0.5s;
  background: url('../assets/map.jpg') no-repeat;
  background-position: center 0;
  position: relative;
  height: 8000px;
}
// .hints-wrapper > .hint-box1 {
//   @media only screen and (max-width: 600px) {
//     width: 100%;
//     right: 10;
//   }
//   position: absolute;
//   z-index: 2;
//   right: 100px;
//   top: 2.5%;
//   height: 200px;
//   width: 400px;
//   border: solid 1px	#00BFFF;
//   border-radius: 5px;
//   background-color: rgba($color: white, $alpha: 0.2)
// }
// .hints-wrapper > .hint-box2 {
//   @media only screen and (max-width: 600px) {
//     width: 100vw;
//     right: 0;
//   }
//   position: absolute;
//   z-index: 2;
//   right: 100px;
//   top: 22.5%;
//   height: 200px;
//   width: 400px;
//   border: solid 1px	#00BFFF;
//   border-radius: 5px;
//   background-color: rgba($color: white, $alpha: 0.2)
// }
// .hints-wrapper > .hint-box3 {
//   @media only screen and (max-width: 600px) {
//     width: 100vw;
//     right: 0;
//   }
//   position: absolute;
//   z-index: 2;
//   right: 100px;
//   top: 42.5%;
//   height: 200px;
//   width: 400px;
//   border: solid 1px	#00BFFF;
//   border-radius: 5px;
//   background-color: rgba($color: white, $alpha: 0.2)
// }
// .hints-wrapper > .hint-box4 {
//   @media only screen and (max-width: 600px) {
//     width: 100vw;
//     right: 0;
//   }
//   position: absolute;
//   z-index: 2;
//   right: 100px;
//   top: 62.5%;
//   height: 200px;
//   width: 400px;
//   border: solid 1px	#00BFFF;
//   border-radius: 5px;
//   background-color: rgba($color: white, $alpha: 0.2)
// }
// .hints-wrapper > .hint-box5 {
//   @media only screen and (max-width: 600px) {
//     width: 100vw;
//     right: 0;
//   }
//   position: absolute;
//   z-index: 2;
//   right: 100px;
//   top: 82.5%;
//   height: 200px;
//   width: 400px;
//   border: solid 1px	#00BFFF;
//   border-radius: 5px;
//   background-color: rgba($color: white, $alpha: 0.2)
// }
// .end-map {
//   position: absolute;
//   bottom: 0;
//   left: 50%;
//   transform: translateX(-50%);
// }
// .map-fixed {
//   position: fixed;
//   z-index: 1;
//   top: 0;
//   left: 0;
//   opacity: 1;
//   transform: scale(1);
//   transform-origin: 0 0;
//   height: auto;
//   transition: all 0.5s;
// }

</style>
