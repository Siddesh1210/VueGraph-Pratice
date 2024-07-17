<template>
  <div class="container">
    <div class="cookieCard red">
      <p class="cookieHeading">Cookies.</p>
      <p class="cookieDescription">
        By using this website you automatically accept that we use cookies.
        <a href="#">What for?</a>
      </p>
      <button class="acceptButton">Understood</button>
    </div>

    <div class="cookieCard blue">
      <p class="cookieHeading">Privacy.</p>
      <p class="cookieDescription">
        We value your privacy and data security.
        <a href="#">Learn more</a>
      </p>
      <button class="acceptButton">Got it</button>
    </div>

    <div class="cookieCard green">
      <p class="cookieHeading">Notifications.</p>
      <p class="cookieDescription">
        We may send you notifications about updates.
        <a href="#">Read more</a>
      </p>
      <button class="acceptButton">Okay</button>
    </div>

    <div class="cookieCard yellow">
      <p class="cookieHeading">Updates.</p>
      <p class="cookieDescription">
        Keep updated with our latest features.
        <a href="#">Find out more</a>
      </p>
      <button class="acceptButton">Acknowledge</button>
    </div>
  </div>
</template>
<script>
export default{
  name: "CardsComponent",
}
</script>
<style scoped>
.container {
    display: flex;
    justify-content: space-around;
    align-items: center;
  }
  
  .cookieCard {
    width: 100%;
    height: 200px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    gap: 20px;
    padding: 20px;
    position: relative;
    overflow: hidden; /* This hides the overflow */
    border-radius: 15px; /* Optional: Add rounded corners */
    color: rgb(241, 241, 241);
    margin:0 20px;
  }
  
  .cookieCard::before {
    width: 150px;
    height: 150px;
    content: "";
    position: absolute;
    z-index: 1;
    border-radius: 50%;
    right: -25%;
    top: -25%;
  }
  
  .red {
    background: linear-gradient(to right, rgb(137, 104, 255), rgb(175, 152, 255));
  }
  
  .red::before {
    background: linear-gradient(to right, rgb(142, 110, 255), rgb(208, 195, 255));
  }
  
  .blue {
    background: linear-gradient(to right, rgb(80, 160, 255), rgb(155, 210, 255));
  }
  
  .blue::before {
    background: linear-gradient(to right, rgb(90, 140, 255), rgb(185, 225, 255));
  }
  
  .green {
    background: linear-gradient(to right, rgb(80, 255, 159), rgb(152, 255, 195));
  }
  
  .green::before {
    background: linear-gradient(to right, rgb(90, 255, 140), rgb(195, 255, 208));
  }
  
  .yellow {
    background: linear-gradient(to right, rgb(255, 230, 85), rgb(255, 240, 150));
  }
  
  .yellow::before {
    background: linear-gradient(to right, rgb(255, 220, 80), rgb(255, 240, 180));
  }
  
  .cookieHeading {
    font-size: 1.5em;
    font-weight: 600;
    z-index: 2;
  }
  
  .cookieDescription {
    font-size: 0.9em;
    z-index: 2;
  }
  
  .cookieDescription a {
    color: rgb(241, 241, 241);
  }
  
  .acceptButton {
    padding: 11px 20px;
    background-color: #7b57ff;
    transition-duration: 0.2s;
    border: none;
    color: rgb(241, 241, 241);
    cursor: pointer;
    font-weight: 600;
    z-index: 2;
    border-radius: 10px;
  }
  
  .acceptButton:hover {
    background-color: #714aff;
    transition-duration: 0.2s;
  }
</style>
