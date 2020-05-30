CSS Keyframe Animation with Pause between Keyframes
witter:Davecar Grave


Earth travels around the Sun with pause between keyframes
Have you ever wonder about how we can pause the animation when it starts?
We can use animation-delay property but it will only delay the start of the animation, once the animation starts it will continuously animate. Once the CSS keyframe animation starts, we cannot pause it unless we will use javascript. So how can we make the animation to pause between keyframes?
The solution will be making the keyframes with the same value and some math. (what!? math!? 😢) yep in order to accurately timing our keyframes.

Layout Animation
For example the image above, it animates for 1s and pauses for 2s and iterates 4 times.
First we need to get the total time of the animation.
total time = (animation time + animation pause) * number of iteration
total time = (animation time + animation pause) * number of iteration
total time = ( 1s + 2s ) * 4
total time = 12s
Calculate the percentage (%) of the animation keyframes
animation time (%) = (animation time / total time) * 100 animation pause (%) = (animation pause / total time) * 100
animation time (%) = (animation time / total time) * 100
animation time (%) = ( 1 / 12 ) * 100
animation time (%) = 8.33% (8.33% = 1s of the time)
animation pause (%) = (animation pause / total time) * 100
animation pause (%) = ( 2 / 12 ) * 100
animation pause (%) = 16.67% (16.67% = 2s of the time)
Initialize the value of percentage (%) of the animation keyframes
We will now initialize the value of percentage by adding the animation time and animation pause percentage then increment it until the 4th iteration.
0%(0s) + 8.33%(1s animate) = 8.33%(1s)
8.33%(1s) + 16.67%(2s pause) = 25%(3s) [1st iteration]
25%(3s) + 8.33%(1s animate) = 33.33%(4s)
33.33%(4s) + 16.67%(2s pause) = 50%(6s) [2nd iteration]
50%(6s) + 8.33%(1s animate) = 58.33%(7s)
58.33%(7s) + 16.67%(2s pause) = 75%(9s) [3rd iteration]
75%(9s) + 8.33%(1s animate) = 83.33%(10s)
83.33%(10s) + 16.67%(2s pause) = 100%(12s) [4th iteration]
Now we have,
0%→ 8.33%→ 25%→ 33.33%→ 50%→ 58.33%→75%→ 83.33%→ 100%

Initialize the value of percentage (%) of the animation keyframes
Lezz do this in action
total time = 12s
animation time (%) = 8.33% (8.33% = 1s of the time)
animation pause (%) = 16.67% (16.67% = 2s of the time)
percentage of the animation keyframe
0%→ 8.33%→ 25%→ 33.33%→ 50%→ 58.33%→75%→ 83.33%→ 100%
Since the animation rotates for 360deg and we have 4 iterations.
keyframe value = 360 / 4 = 90deg
We have 90deg per iteration, to get the deg in each iteration then we will increment it by 90deg.
0deg + 90deg = 90deg [1st iteration]
90deg + 90deg = 180deg [2nd iteration]
180deg + 90deg = 270deg [3rd iteration]
260deg + 90deg = 360deg [4th iteration]
Now we have,
0deg → 90deg → 180deg → 270deg → 360deg [deg in each iteration]
Now that we have all the values that we need, let’s add this to our code.
.planet{
   animation: rotateEarth 12s infinite
}
@keyframes rotateEarth {
  0% {
    transform: rotate(0deg)
  }
  8.33% {
    transform: rotate(90deg)
  }
  25% {
    transform: rotate(90deg)
  }
  33.33% {
    transform: rotate(180deg)
  }
  50% {
    transform: rotate(180deg)
  }
  58.33% {
    transform: rotate(270deg)
  }
  75% {
    transform: rotate(270deg)
  }
  83.33% {
    transform: rotate(360deg)
  }
  100% {
    transform: rotate(360deg)
  }
}
As you can see in the above code, there are some keyframes that have the same value. We can write less code by comma separate the keyframes that have the same value.
@keyframes rotateEarth {
  0% {
    transform: rotate(0deg)
  }
  8.33%, 25% {
    transform: rotate(90deg)
  }
  33.33%, 50% {
    transform: rotate(180deg)
  }
  58.33%, 75% {
    transform: rotate(270deg)
  }
  83.33%, 100% {
    transform: rotate(360deg)
  }
}
That’s all of it. Hope that you can be able to create your animation with pause between keyframes. Looking forward to see your animation.
