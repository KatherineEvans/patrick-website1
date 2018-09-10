<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style>
html {
  font-size: 10px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  /*resetting the browser settings */
}

body {
  font-family: "Lato", sans-serif;
  font-weight: 400;
/*  font-size: 16px;*/
  line-height: 1.7;
  color: #777;
  padding: 3rem;
}

.header {
  height: 95vh;
  /*95% of the viewport height */
  background-image: linear-gradient(
    to right bottom, 
    rgba(126, 213, 111, 0.7), 
    rgba(40, 180, 131, 0.7)), 
  url(http://1lipics.com/img/single/2018/03/24/1lipics.com_Photo_2b573624711c5778c47def26d06c74e3.jpg);
  background-size: cover;
  /* fit image into width of viewport */
  background-position: top;
  position: relative;

  clip-path: polygon(0% 0%, 100% 0%, 100% 55%, 0% 100%);

}

.logo-box {
  position: absolute;
  top: 4rem;
  left: 4rem;
}

.logo {
  height: 3.5rem;
}

.text-box {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  /*Transform/translate no longer looks at the box relative to the parent aka. the header. It looks at it relative to the object itself */
}

.heading-primary {
  color: #fff;
  text-transform: uppercase;

  backface-visibility: hidden;
  /*The backface ivsibility keeps what's behind the element hidden - fixes shaking in animation*/
  margin-bottom: 6rem;
}

.heading-primary-main {
  display: block;
  font-size: 6rem;
  /*font size*/
  font-weight: 400;
  /*font thickness(ish)*/
  letter-spacing: 3.5rem;
  /*Space between letter, i.e. spread out or smushed*/
  animation-name: moveInLeft;
  animation-duration: 2s;
  animation-timing-function: ease-out;
  /* the number of times an animation runs
  animation-iteration-count: 3;

  the lenght of time before an animation begins
  animation-delay: 0.5s;
  */
}

.heading-primary-sub {
  display: block;
  font-size: 2rem;
  font-weight: 700;
  letter-spacing: 1.75rem;
  animation: moveInRight 2s ease-out;
  /*short hand version of writing what's written in heading-primary-main */
  }

/* to use css animation, you must first specifiy *keyframes* for the animation */
@keyframes moveInLeft {
  0% {
    opacity: 0;
    /* start of animation */
    transform: translateX(-10rem);
    /* use translateX because the x axis is the horizontal axis */
  }

  80% {
    transform: translateX(1rem);
  }

  100% {
    opacity: 1;
    /* end of annimation */
    transform: translate(0);
    /*translating at 0 means it will look like it does form the start, with 0 animation */
  }
}

@keyframes moveInRight {
  0% {
    opacity: 0;
    /* start of animation */
    transform: translateX(10rem);
    /* use translateX because the x axis is the horizontal axis */
  }

  80% {
    transform: translateX(-1rem);
  }

  100% {
    opacity: 1;
    /* end of annimation */
    transform: translate(0);
    /*translating at 0 means it will look like it does form the start, with 0 animation */
  }
}

@keyframes moveInBottom {
  0% {
    opacity: 0;
    /* start of animation */
    transform: translateY(3rem);
    /* use translateY because the y axis is the verticle axis, positive travels up, negative travels down */
  }

  100% {
    opacity: 1;
    /* end of annimation */
    transform: translate(0);
    /*translating at 0 means it will look like it does form the start, with 0 animation */
  }
}

.btn:link, 
.btn:visited {
  text-transform: uppercase;
  text-decoration: none;
  padding: 1.5rem 4rem;
  display: inline-block;
  border-radius: 10rem;
  transition: all .2s;
  position: relative;
  font-size: 1.6rem;
} /* using the : followed by text (here "link") is the sudo class - used to style elements under a special condiiton. You can use the sudo class "visited" after a link has been clicked*/

.btn:hover {
  transform: translateY(-.3rem);
  box-shadow: 0 1rem 2rem rgba(0,0,0,.2);
  /*first value is X axis, second is Y axis, thrid is blur, fourth is color!*/
}

.btn:active {
  transform: translateY(-.1rem);
  box-shadow: 0 .5rem 1rem rgba(0,0,0,.2);
}

.btn-white {
  background-color: #fff;
  color: #777;
  animation: moveInBottom 1s ease-out .75s;
  animation-fill-mode: backwards; /*this will automatically apply the 0% before the animation starts*/
}

.btn::after {
  content: "";
  display: inline-block;
  /*Display is set to inline-block because our button is set to inline-block. You must always specify content too, even if blank */
  height: 100%;
  width: 100%;
  border-radius: 10rem;
  position: absolute;
  /*position is listed as absolute in relations to the closest position it can find which is the button's relative position*/
  top: 0;
  left: 0;
  z-index: -1;
  /* z-index defines positions of elements if they're stacked i.e. one on top of the other. AKA this goes behind, hence the -1!*/
  transition: all .4s;
}

.btn-white::after {
  background-color: #fff;
}

.btn:hover::after {
  transform: scaleX(1.4) scaleY(1.4); /*scale 2 makes it double the size it was before*/
  opacity: 0; /* fade out */
}
</style>
