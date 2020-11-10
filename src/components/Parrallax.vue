<template>
  <div class='root'>
    <img class='background' ref='background' src='@/assets/img/bg.jpg'/>
    <img class='foreground' ref='foreground' src='@/assets/img/t2.png'/>
    <img class='slide' ref='foreground2' src='@/assets/img/foreground2.png'/>
    <div class='section section-1' ref='first'>
      <div>
        <h1 ref="h1name">Rang</h1>
        <h3>Yooradet Khamon</h3>
      </div>
    </div>
    <div class="section header-edu" ref="eduHeader">
        <div ref="eduSpan">
            <span>Education</span>
        </div>
    </div>
    <div class='section section-2' ref='second'>
      <div>
        <h2>Montfort College</h2>
        <p>2010 - 2016</p>
      </div>
    </div>
    <div class='section section-3' ref='third'>
      <div>
        <h2>Chiang Mai</h2>
        <h4>University</h4>
        <p ref='tagPstrike'><span>CPE</span> 2016 - 2019</p>
        <p ref="tagPapper" style="opacity: 0;"><span>ISNE</span> 2020 - Now</p>
      </div>
    </div>
    <div class='section section-4' ref="forth">
    <img class='background' style="filter: opacity(80%);" src='@/assets/img/bg2.jpg'/>
      <div>
        <div class="loader"></div>
      </div>
    </div>
    <div class="section header-skill" ref="skillHeader">
        <div ref="skillSpan">
            <span>Skills</span>
        </div>
    </div>
    <div class='section section-5' ref="fifth"> 
      <div>
        <h2>Javascipt</h2>
        <div>
            <FontAwesome name="js"/>
            <FontAwesome name="vuejs"/>
        </div>
        
      </div>
    </div>

    <div class='section section-6' ref="six"> 
      <div>
        <div>
        <FontAwesome name="css3-alt"/>
        <FontAwesome name="tailwindcss-icon"/>
        </div>
        <h2>CSS</h2>
      </div>
    </div>

    <div class='section section-7' ref="seven"> 
      <div>
        <h2>Adobe</h2>
        <div>
        <FontAwesome name="adobe-illustrator"/>
        <FontAwesome name="adobe-photoshop"/>
        </div>
      </div>
    </div>

    <div class='section section-8' ref="eight"> 
      <div>
        <img src="@/assets/img/IMG_2080.png" alt="">
        <h2>Contact</h2>
        <p>Email <a href="mailto: yooradet.jobs@gmail.com">yooradet.jobs@gmail.com</a></p>
        <p>Phone <a href="tel:+66987476212">+66987476212</a></p>
        <div>
        <span><a href="https://goo.gl/maps/NvLhSBZD5mDhAfNA7">Building 4/24 Flat CMU, Road 24, Suthep, Mueang Chiang Mai District, Chiang Mai 50200</a></span>
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d944.2862782684531!2d98.96745682922767!3d18.79168526882185!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMTjCsDQ3JzMwLjEiTiA5OMKwNTgnMDQuOCJF!5e0!3m2!1sth!2sth!4v1605038577939!5m2!1sth!2sth" frameborder="0" allowfullscreen="" aria-hidden="false" tabindex="0"></iframe>
        </div>
        <p style="color:white; font-size: 16px">Inspire By https://playvalorant.com/en-us/ And https://www.apple.com/th/ipad-air/</p>
      </div>
    </div>
    
    <!-- <img src="@/assets/img/logo.png" alt="" id="logo"> -->
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from 'vue'
import FontAwesome from '@/components/FontAwesome.vue' 

export default {
    components: {
    FontAwesome
    },
    setup () {
    const h1name = ref(null)
    const foreground = ref(null)
    const foreground2 = ref(null)
    const background = ref(null)
    const first = ref(null)
    const second = ref(null)
    const third = ref(null)
    const eduHeader = ref(null)
    const tagPstrike = ref(null)
    const tagPapper = ref(null)
    const forth = ref(null)
    const skillHeader = ref(null)
    const fifth = ref(null)
    const six = ref(null)
    const seven = ref(null)
    const eight = ref(null)
    const background2 = ref(null)
    const skillSpan = ref(null)
    const eduSpan = ref(null)
    let bg1 = true
    let bg2 = false
    let skillTextMove = false
    let eduTextMove = false

    const handleScroll = () => {
      const scrollY = window.scrollY 
      const offSet = 0;


      //Section 1
      if(scrollY > first.value.offsetHeight) first.value.style.opacity = 0
      else first.value.style.opacity = 100
      h1name.value.style.transform = `translate(-${scrollY / 10}px,0)`

      //Section 2 if apper Heder Edu ill apper too
      if(scrollY < second.value.offsetTop - offSet) {
          second.value.style.opacity = 0
          eduHeader.value.style.opacity = 0
      }
      else if(scrollY > second.value.offsetHeight - offSet) {
          eduTextMove = true
          second.value.style.opacity = 100
          eduHeader.value.style.opacity = 100
      }
      else second.value.style.opacity = 0

      //Section 3
      if(scrollY < third.value.offsetTop - offSet * 2 ) third.value.style.opacity = 0
      else if(scrollY > third.value.offsetHeight - offSet * 2) {
          third.value.style.opacity = 100
          //Show CPE TO ISNE
          tagPapper.value.style.transform = `translate(0,-60px)`
          if(scrollY > third.value.offsetTop + third.value.offsetHeight*3/5) {
              tagPapper.value.style.opacity = 100
              tagPstrike.value.style.color = '#0f1922';
          }
          else {
              tagPapper.value.style.opacity = 0
              tagPstrike.value.style.color = 'white';
          }
          // to here
      }
      else third.value.style.opacity = 0
        

      //Section 4 loading
      if(scrollY < forth.value.offsetTop - offSet) {
          forth.value.style.opacity = 0
          bg1 = true;
          
          foreground2.value.style.opacity = 0
      }
      else if(scrollY > forth.value.offsetHeight - offSet) {
          eduTextMove = false
          forth.value.style.opacity = 100
          bg1 = false;
      }

      //Section 5(SKILLS) and Header 
      if(scrollY < fifth.value.offsetTop - offSet) {
          fifth.value.style.opacity = 0
          skillHeader.value.style.opacity = 0
          skillTextMove = false
          bg2 = false;
          foreground2.value.style.opacity = 0
      }
      else if(scrollY > fifth.value.offsetHeight - offSet) {
          eduHeader.value.style.opacity = 0
          second.value.style.opacity = 0
          third.value.style.opacity = 0
          forth.value.style.opacity = 0

          skillTextMove = true
          bg2 = true;
          foreground2.value.style.opacity = 100
          skillHeader.value.style.opacity = 100
          fifth.value.style.opacity = 100
      } 
      
      //Section 6(CSS)
      if(scrollY < six.value.offsetTop - offSet) {
          six.value.style.opacity = 0
      }
      else if(scrollY > six.value.offsetHeight - offSet) {
          six.value.style.opacity = 100
      }

      //Section 7(Adobe)
      if(scrollY < seven.value.offsetTop - offSet) {
          seven.value.style.opacity = 0
      }
      else if(scrollY > seven.value.offsetHeight - offSet) {
          seven.value.style.opacity = 100
      }
      else {
          seven.value.style.opacity = 0
      }

      if(scrollY < eight.value.offsetTop - offSet) {
          eight.value.style.opacity = 0
      }
      else if(scrollY > six.value.offsetHeight - offSet) {
          fifth.value.style.opacity = 0
          six.value.style.opacity = 0
          seven.value.style.opacity = 0
          skillHeader.value.style.opacity = 0
          skillTextMove = false

          eight.value.style.opacity = 100
      }
      else {
          eight.value.style.opacity = 0
      }
    
       
      
      //Skills Text Move
      if(skillTextMove) {
          skillSpan.value.style.transform = `translate(${-120+(scrollY/600)}%,-20%)`
      }

      if(eduTextMove) {
          eduSpan.value.style.transform = `translate(-65%, ${-110-(scrollY/300)}%)`
      }
      //if Scroll more then Section 3 disapper Background 1
      if(bg1){
          background.value.style.opacity = 100
        const maxBackgroundSize = 110;
        const backgroundSize = ((scrollY) / (maxBackgroundSize - 100)) // increases as user scrolls
        // zoom the background at a slower rate
        background.value.style.transform = 'scale(' + (100 + backgroundSize * .4) / 100 + ')'
      }else background.value.style.opacity = 0

      if(bg2) {
        foreground2.value.style.transform = `translate(${30-(scrollY/150)}%,1%)`
        foreground2.value.style.top = 0
      }else background2.value.style.opacity = 0
      
    //   console.log(skillHeader.value.style.transform)
    }

    onMounted(() => {
      document.addEventListener('scroll', handleScroll)
    }),

    onUnmounted(() => {
        document.removeEventListener('scroll', handleScroll)
    })

    return {
      h1name,foreground,background,first,second,third,skillHeader,seven,eight,foreground2,
      eduHeader,tagPstrike,tagPapper,forth,handleScroll,skillSpan,eduSpan,
      background2,fifth,six
    }
  }
}
</script>

<style lang="scss">
$primary: #ff4457;
    #logo {
        position: fixed;
        width: auto;
        height: 100px;
        padding: 15px;
        display: none;
        
    }

    .slide {
        position: fixed;
        height: auto;
        opacity: 0;
        object-fit: cover;
    }

    img.background, img.foreground {
        /* Fill background */
        min-height: 100%;
        min-width: 1024px;
        
        /* Scale proportionately */
        width: 100%;
        height: auto;
        overflow-x: hidden;
        position: absolute; 
    }

    img.background {
        /* Positioning */
        position: fixed;
        top: 0;
        left: 0;
    }

    .section {
        min-height: 100vh;
        position: relative;
        transition: all ease-out .3s; 
        div {
            position: fixed;
            color: white;
            /* centers this div */ 
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
        }       

        h2 {
            font-family: 'VALORANT-Regular';
            font-size: 6em;
            margin-bottom: 40px;
            color: $primary;
        }
        p {
            margin-top:-45px;
            font-size: 3em;
        }
    }
    
    .header-edu {
        opacity: 0;
        div {
            position: fixed;
            left: 50%;
            top: 50%;
            transform: translate(-65%, -110%);
        }    
        div span{
            position: relative;
            font-size: 12em;
            font-family: 'VALORANT-Regular';
            -webkit-text-stroke-width: 1.5px;
            -webkit-text-stroke-color: white;
            color: transparent;
        }
    }

    .header-skill {
        opacity: 0;
        div {
            position: fixed;
            left: 50%;
            top: 50%;
            transform: translate(-120%, 25%);
        }    
        div span{
            position: relative;
            font-size: 12em;
            font-family: 'VALORANT-Regular';
            -webkit-text-stroke-width: 3px;
            -webkit-text-stroke-color: white;
            color: transparent;
        }
    }

  .section-1 {
      h1 {
        font-family: 'VALORANT-Regular';
        font-size: 3em;
      }
    margin-bottom: 100px; /* determines the gap between our two sections */
    font-size: 2em;
  }

  .section-2 {
    opacity: 0;
    div{
        color: white;
        text-align: center;
        padding: 50px;
        width: 80vw;
        transform: translate(-35%, -75%);
    }
  }

  .section-3 {
    opacity: 0; 
    min-height: 140vh;
    div{
        color: white;
        text-align: center;
        padding: 50px;
        width: 40vw;
        transform: translate(-100%, -15%);
    }
    h4{
        font-family: 'VALORANT-Regular';
        color: $primary;
        font-size: 5em;
        margin-top: -0.6em;
    }
    p {
        span {
            font-family: 'VALORANT-Regular';
        }
        margin-top: 0;
        font-size: 3em;
        transition: all ease-in .5s; 
    }
  }
  
  .section-4 {
    opacity: 0;
    div {
        position: fixed;
        color: white;
        /* centers this div */ 
        left: 45%;
        top: 45%;
        transform: translate(-50%, -50%);
        }       
  }

  .section-5 {
    opacity: 0;
    div{
        width: 500px;
        position: fixed;
        color: white;
        left: 45%;
        top: 45%;
        transform: translate(30%, -70%);
        div {
            position: relative;
            font-size: 6em;
            color: $primary;
            text-align: center;
            font-family: 'VALORANT-Regular';
            transform: translate(-40%, -20%);
        }
    }
  }

  .section-6 {
    opacity: 0;
    div{
        width: 500px;
        position: fixed;
        color: white;
        left: 0%;
        top: 0%;
        transform: translate(90%, 20%);
        div {
            position: relative;
            font-size: 6em;
            color: $primary;
            text-align: center;
            font-family: 'VALORANT-Regular';
            transform: translate(-25%, 10%);
        }
        h2 {
            font-size: 8em;
        }
    }
  }

  .section-7 {
    opacity: 0;
    div{
        width: 500px;
        position: fixed;
        color: white;
        left: 45%;
        top: 45%;
        transform: translate(5%, 20%);
        div {
            position: relative;
            font-size: 6em;
            color: $primary;
            text-align: center;
            font-family: 'VALORANT-Regular';
            transform: translate(-75%, -20%);
        }
    }
  }

  .section-8 {
    opacity: 0;
    min-height: 100vh;
    height: 100vh;
    transform: translate(-20%,20%);
    h2 {
        margin-bottom: -10px;
    }

    p {
        padding: 0;
        margin: 0;
        font-size: 2em;
    }

    a {
        color: white;
    }

    span {
        padding-top: 20px;
    }
    
    div {
        color: #ff4457;
        width: 40%;
    }

    div div {
        position: relative;
        padding-top: 250px;
        width: 100%;
        iframe {
            padding-top: 20px;
            width: 100%;
            height: 200px;
        }
    }

    div img {
        width: 80%;
        height: auto;
        position: absolute;
        left: 110%;
        top: -10%;
    }
  }

    .loader {
    border: 8px solid #0d0b0d; /* Ring */
    border-top: 8px solid #ff4654; /* Progress */
    border-radius: 50%;
    width: 120px;
    height: 120px;
    animation: spin .9s ease-out infinite;
    }

    @keyframes spin {
    0% { transform: rotate(0deg); }
    90% { transform: rotate(350deg); }
    95% { transform: rotate(355deg); }
    100% { transform: rotate(360deg); }
    }
</style>