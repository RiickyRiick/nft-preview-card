# Frontend Mentor - Ricky's NFT preview card component solution

This is a solution to the [NFT preview card component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/nft-preview-card-component-SbdUL_w0U). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

**Note: Delete this note and update the table of contents based on what sections you keep.**

## Overview

This project was reviewed for me, but I don't overlook any of these simple projects since they are a good way to continue showing me how much I have improved, i.e., how long it takes me to code, whether I'm using good HTML semantics, whether I understand the basic fundamentals, etc. 

However, the process of hovering over the image and displaying a white background color, overlaying another image, and adding a smooth transition is still fairly new to me. This led me to learn more about how to use an image wrapper to execute this hover image overlay. 

### The challenge

Users should be able to:

- View the optimal layout depending on their device's screen size
- See hover states for interactive elements

### Screenshot

<img src="./design/desktop-design.jpg"/>
<img src="./design/mobile-design.jpg"/>


### Links

- Live Site URL: https://riickyriick.github.io/nft-preview-card/

## My process

I approached my HTML and CSS in a more "professional way." By this, I mean I focused more on readability and keeping my code organized in sections. I wanted to approach easier projects with a more presentable look. 

--I started by grouping all my tags and naming them accordingly

--Next, I added a bg-color, positioned, and sized my card

--I then proceeded to work on the hovering active state for my image

--Moved onto the NFT card design i.e., fonts, color, sizing, and positioning

--Desgined the .price-timer section

--Designed.creator-info section

--Lastly, finished off with the footer -- .attribution

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Desktop-first workflow

### What I learned

HTML:

--I learned how to be more clear when naming my classes. 
For example, this is my code before I rewrote it:

```html
<main class="container">
  <article class="card">
    <div class="card-content">

      <div class="img-container">
        <img class="img-equil" src="./images/image-equilibrium.jpg" alt="equilibrium image">
        <img class="img-view" src="./images/icon-view.svg" alt="icon view">
      </div>
      <div class="content-text">
        <a class="number" href="#">
          <h1>Equilibrium 3429</h1>
        </a>
        <p class="pro-des same-color">Our Equilibrium collection promotes balance and calm.</p>
        <section class="eth-days">
          <div class="price-container">
            <img class="img-eth" src="./images/icon-ethereum.svg" alt="ethereum">
            <p class="eth">0.041 ETH</p>
          </div>
          <div class="time-container">
            <img class="img-clock" src="./images/icon-clock.svg" alt="clock">
            <p class="time same-color">3 days left</p>
          </div>
        </section>
        <section class="jules">
          <img class="img-jules" src="./images/image-avatar.png" alt="avatar">
          <p><span class="same-color">Creation of</span><a class="name" href="#">Jules Wyvern</a></p>
      </div>
      </section>
    </div>
  </article>
</main>
```
...and this is my code after I revised it: 
```html
<main class="portfolio-container">
  <article class="nft-card">

    <div class="img-wrapper">
      <img class="nft-image" src="./images/image-equilibrium.jpg" alt="equilibrium image">
      <img class="view-icon" src="./images/icon-view.svg" alt="icon view">
    </div>

    <div class="cards-details">
      <a class="card-title" href="#">
        <p></p>
      </a>
      <p class="card-description same-color"></p>
      <section class="price-timer">
        <div class="price-info">
          <img class="ethereum-icon" src="./images/icon-ethereum.svg" alt="ethereum">
          <p class="eth-text">/p>
        </div>
        <div class="time-info">
          <img class="timer-icon" src="./images/icon-clock.svg" alt="clock">
          <p class="timer-text same-color"></p>
        </div>
      </section>
      <section class="creator-info">
        <img class="creator-avatar" src="./images/image-avatar.png" alt="avatar">
        <p><span class="creator-label same-color"></span> <a class="creator-name" href="#"></a></p>
    </div>
    </section>
  </article>
</main>
```
...as you can see, it is much more organized. I eliminated the redundancy 
and gave all the classes a more more precise and concise names. 

____________________________________________________________________________

Another thing I learned was how to overlay a background color and display an 
overlayed the image with the hover pseudo-class and maintained its position. 

I started by wrapping the images together to use .img-wrapper as a position: relative; this will help me add a position: absolute to the .view-icon image and make it easier to adjust it to the center. Also, another great reason for wrapping these images is that when you hover over the image wrapper, it will trigger the .view-icon, instead of only hovering over the .view-icon; more friendly user (more on this in the hovering section down below):
```html
 <article class="nft-card">

   <div class="img-wrapper">
     <img class="nft-image" src="./images/image-equilibrium.jpg" alt="equilibrium image">
     <img class="view-icon" src="./images/icon-view.svg" alt="icon view">
   </div>
      
</article>
```

I also used percentages for the top, bottom, and transform since pixels gave it a fixed size. This caused me problems when shrinking the viewport. When I used percentages in properties like transform: translate(-10%, -10%), the values were calculated relative to the size of the element itself (in this case, the .view-icon). 
As the size of the icon changes (for example, if it gets smaller due to a resizing viewport), the translation also scales accordingly. This maintains the intended visual position over the image.

For Example:

--Responsiveness with Percentages:

With percentages, if the icon’s size shrinks to maintain responsiveness (say from 45px down to 30px), using translate(-10%, -10%) means it will move 3px left and 3px up (because 10% of 30px = 3px). The centering effect remains visually intact.

Inconsistent with Pixels:
--In contrast, if you used a fixed translate(-10px, -10px) while the icon size decreased, the icon might not stay visually centered. It would have a constant movement and may result in the icon appearing further from the center than intended.


```css
.nft-card {
 background-color: hsl(215, 59%, 21%);
 width: 400px;
 border-radius: 15px;
 padding: 30px 30px 5px 30px;
}


.img-wrapper {
 position: relative;
}

.nft-image {
 display: block;
 width: 100%;
 border-radius: 10px;
 transition: opacity 0.3s ease-in-out;
}

.view-icon {
 position: absolute;
 left: 45%;
 top: 45%; 
 opacity: 0;
 width: 45px; 
 height: 45px; 
 transition: opacity 0.2s ease-in-out, transform 0.3s ease-in-out;
 transform: translate(-5%, -5%); 
}
```
...I also made the .nft-image width to 100% since the .nft-card width was 400px; decreasing the size being within the parent container.

I then moved on to the hover pseudo-class:
```css
.img-wrapper:hover {
 background-color: white;
 border-radius: 11px;
}

.img-wrapper:hover .nft-image {
 opacity: 0.8;
}

.img-wrapper:hover .view-icon {
 opacity: 1;
 transform: scale(1.2);
}
```
So, I first added a bg-color: white to give it a faded effect. I also added an 11px for the white background, not how from the corners, keeping it close to the same size as the .negt-image borders at 10px. I then needed to target the .nft-image and .view-icon; however, as I mentioned before since I wrapped them together within the. img-wrapper, I can then use .img-wrapper to trigger the hover effect.
In other words, the .nft-image and .view-icon image will only trigger their effect when you go over the .img-wrapper, which covers the full width of the parent container. 

### Continued development

I will continue to work with the transition and transform rules. This project was good 
review, and learn more about hover effects, transitioning, and transformation.

### Useful resources

<a href="https://stackoverflow.com/questions/7285058/css-percentages-or-pixels" target="_blank">Stackflow CSS Percentages or Pixels</a> 
<a href="https://www.w3schools.com/cssref/css_units.php
" target="_blank">W3schools CSS Units</a> 



## Author

-Website: (https://www.rarroyoharo.com)<a href="https://www.rarroyoharo.com" target="_blank">rarroyoharo.com</a> 
--Frontend Mentor - [@RiickyRiick]<a href="https://www.frontendmentor.io/profile/RiickyRiick" target="_blank">@RiickyRiick</a> 



