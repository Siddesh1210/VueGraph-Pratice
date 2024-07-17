<template>
  <div class="container">
    <div class="cookieCard red">
      <p class="cookieHeading">Cookies.</p>
      <p class="cookieDescription">
        By using this website you automatically
        <a href="#">What for?</a>
      </p>
      <h3>25000</h3>
    </div>

    <div class="cookieCard blue">
      <p class="cookieHeading">Privacy.</p>
      <p class="cookieDescription">
        We value your privacy and data security.
        <a href="#">Learn more</a>
      </p>
      <h3>25000</h3>
    </div>

    <div class="cookieCard green">
      <p class="cookieHeading">Notifications.</p>
      <p class="cookieDescription">
        We may send you notifications about updates.
        <a href="#">Read more</a>
      </p>
      <h3>42000</h3>
    </div>

    <div class="cookieCard yellow">
      <p class="cookieHeading">Updates.</p>
      <p class="cookieDescription">
        Keep updated with our latest features.
        <a href="#">Find out more</a>
      </p>
      <h3>7000</h3>
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
    flex-wrap: wrap;
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  }
  
  .cookieCard {
    width: 250px;
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
    margin:10px;
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
    background: linear-gradient(to right, #ec4887, #b754a4);
  }
  
  .red::before {
    background: linear-gradient(to right, #f17ba8, #960779);
  }
  
  .blue {
    background: linear-gradient(to right, #865fc0, #5447b9);
  }
  
  .blue::before {
    background: linear-gradient(to right, #925ee0, #4336ab);
  }
  
  .green {
    background: linear-gradient(to right, #44c4f1, #59a6e4);
  }
  
  .green::before {
    background: linear-gradient(to right, #19a7db, #053f6f);
  }
  
  .yellow {
    background: linear-gradient(to right, #ffb82c, #f57f59);
  }
  
  .yellow::before {
    background: linear-gradient(to right, #ffb82c, #f57f59);
  }
  
  .cookieHeading {
    font-size: 1.5em;
    line-height: 1px !important;
    font-weight: 600;
    z-index: 2;
  }
  
  .cookieDescription {
    font-size: 1em;
    margin-bottom: 0px;
    z-index: 2;
  }
  
  .cookieDescription a {
    color: rgb(241, 241, 241);
  }
</style>
