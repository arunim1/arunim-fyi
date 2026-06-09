---
id: note_01fbawzg00ebwbnv2mr6j7pkr6
title: "Alto Clef: Palo Alto Public Piano"
public: true
updated: "August 15, 2022"
start: "July 24, 2021"
---

> [!note] Archived project
> This page is copied from a standalone site I made in 2021. The piano project is complete and the piano was donated to the City of Mountain View.

<div class="piano-page">

<style>
.piano-page {
  max-width: 720px;
  margin: 0 auto;
}
.piano-page .slideshow {
  position: relative;
  width: 100%;
  overflow: hidden;
  border-radius: 8px;
  background: #111;
  margin: 1.5rem 0;
}
.piano-page .slideshow img {
  width: 100%;
  display: none;
  border-radius: 8px;
}
.piano-page .slideshow img.active {
  display: block;
}
.piano-page .slide-counter {
  position: absolute;
  top: 12px;
  right: 16px;
  background: rgba(0,0,0,0.55);
  color: #fff;
  padding: 4px 10px;
  border-radius: 4px;
  font-size: 0.85rem;
  font-variant-numeric: tabular-nums;
}
.piano-page .slide-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0,0,0,0.45);
  color: #fff;
  border: none;
  font-size: 1.5rem;
  padding: 12px 14px;
  cursor: pointer;
  border-radius: 4px;
  line-height: 1;
  transition: background 0.2s;
  z-index: 1;
}
.piano-page .slide-btn:hover {
  background: rgba(0,0,0,0.7);
}
.piano-page .slide-btn.prev { left: 8px; }
.piano-page .slide-btn.next { right: 8px; }
.piano-page .piano-description {
  line-height: 1.7;
  margin: 1rem 0;
}
.piano-page .piano-links {
  display: flex;
  gap: 1.5rem;
  flex-wrap: wrap;
  margin: 1rem 0;
  list-style: none;
  padding: 0;
}
.piano-page .piano-links a {
  text-decoration: none;
}
</style>

<div class="slideshow" id="piano-slideshow">
  <span class="slide-counter" id="piano-counter">1 / 5</span>
  <button class="slide-btn prev" onclick="pianoSlide(-1)">&#10094;</button>
  <button class="slide-btn next" onclick="pianoSlide(1)">&#10095;</button>
  <img src="/assets/piano/pic01.jpg" alt="The piano at Mitchell Park" class="active" />
  <img src="/assets/piano/DSC_0004-min.jpg" alt="Piano restoration in progress" />
  <img src="/assets/piano/DSC_0010-min.jpg" alt="Piano restoration" />
  <img src="/assets/piano/DSC_0027-min.jpg" alt="Piano detail" />
  <img src="/assets/piano/DSC_0008-min.jpg" alt="Piano installed outdoors" />
</div>

<script>
(function() {
  let idx = 0;
  const imgs = document.querySelectorAll('#piano-slideshow img');
  const counter = document.getElementById('piano-counter');
  window.pianoSlide = function(d) {
    imgs[idx].classList.remove('active');
    idx = (idx + d + imgs.length) % imgs.length;
    imgs[idx].classList.add('active');
    counter.textContent = (idx + 1) + ' / ' + imgs.length;
  };
})();
</script>

<p class="piano-description">
Originally, we found this piano about to be thrown away in the Cubberley dumpster.
A couple of us MakeX mentors hauled it back in on a rather unstable cart and got to work fixing it up.
I applied for a grant from PA Public Art, and worked with my talented friends (shoutout to Daniel Pei, Faustine Wang, Sarah Sanders, Vivian Becker, Yash Nasikkar) to clean up, fix, and repaint the entirety of the piano piece by piece.
The installation in Mitchell Park ended in September 2021, and the piano has since been donated to the City of Mountain View.
</p>

<ul class="piano-links">
  <li><a href="https://www.instagram.com/pa_public_piano/" target="_blank">@pa_public_piano</a></li>
  <li><a href="https://www.instagram.com/makexpaloalto/" target="_blank">@makexpaloalto</a></li>
</ul>

</div>
