<template>
  <main>
    <section id="home">
<nav>
  <img src="../assets/logo.svg" alt="">
  <div class="links">
    <a href="">About</a>
    <a href="">Discover</a>
    <a href="">Get Started</a>
  </div>
</nav>
    </section>
    <section id="crowdfund">
      <div class="panel-div">
        <div class="top panel">
          <img src="../assets/logo-mastercraft.svg" alt="">
          <h1>Mastercraft Bamboo Monitor Riser</h1>
          <p>A beautiful & handcrafted monitor stand to reduce neck and eye strain.</p>
          <div class="btn-group">
            <button>Back this project</button>
          <button>Bookmark</button>
          </div>
          <progress min="0" max="100" value="60"></progress>
        </div>
        <div class="mid panel">
<div>
  <div><h2>$89,914</h2>
    <p>of $100,000 backed</p>
  </div>
  <div>
    <h2>
      5,007
    </h2>
    <p>total backers</p>
  </div>
  <div>
    <h2>56</h2>
    <p>days left</p>
  </div>
 <!-- slider -->
</div>
        </div>
        <div class="bottom panel">
<h6>About this project</h6>
<div class="para">
<p>The Mastercraft Bamboo Monitor Riser is a sturdy and stylish platform that elevates your screen to a more comfortable viewing height. Placing your monitor at eye level has the potential to improve your posture and make you more comfortable while at work, helping you stay focused on the task at hand.</p>
        <p>Featuring artisan craftmanship, the simplicity of design creates extra desk space below your computer to allow notepads, pens, and USB sticks to be stores under the stand.</p>
</div>
<div class="container">
  <div class="item">
    <div class="item-top">
    <h4>Bamboo Stand</h4>
    <p>Pledge $25 or more</p>
  </div>
  <p>You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campaign, and you'll still be added to the special backer list</p>
  <div class="item-bottom">
    <h6>101</h6>
    <button>Select Reward</button>
  </div>
</div>
</div>
</div>
      </div>
    </section>
  </main>
</template>

<script>
export default {

}
</script>
<style>
#home{
  height: 40vh;
  width: 100%;
  background-image: linear-gradient(to top, rgba(255, 0, 0, 0) 10%, rgba(128, 0, 128, 0) 45%, rgba(0, 0, 0, 0.577) 99%), url(../assets/image-hero-desktop.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  display: flex;
  justify-content: center;
}
nav{
  width: 80%;
  height: fit-content;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 3rem;
}
nav .links{
  display: flex;
  column-gap: 3rem;
}
.links a{
  color: white;
  text-decoration: none;
  font-weight: 500;
}
#crowdfund{
  height: fit-content;
  width: 100%;
  background: #FAFAFA;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-bottom: 2rem;
}
.panel-div{
  width: 40vw;
  height: fit-content;
  background:inherit;
  margin-top: 0;
  border-radius: 20px;
  display: flex;
  flex-direction: column;
  row-gap: 2rem;
  margin-top: -5rem;
}
.panel{
  width: 100%;
  background:white;
  border-radius: 12px;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.131);
}
.top{
  height: 20rem;
}
.mid{
  height: 15rem;
}
.bottom{
  height: 40rem;
}
</style>
