<template>
  <div class="container">
    <div class="itemLeft">
      <img class="mountain" src="../assets/mountain.jpeg" alt="" />
      <h1>Unrecognized genius</h1>
      <p>
        Rising star Alexandra's new work causes a lot of controversy in creative
        circles. According to the artist, the picture illustrates a state of
        horror. <span>16h ago</span>
      </p>
      <div class="author">
        <img class="profile" src="../assets/profile.png" alt="" />
        <b>Wade Warren <br /><span>Newsman</span></b>
      </div>
      <hr />
      <h1>Photography</h1>
      <p>
        An exhibition of photographers from all over the world took place in
        Berlin. Over 100 photographers present their work to the world. The
        exhibition aroused great interest among the public.<span>16h ago</span>
      </p>
    </div>
    <div class="itemMiddle">
      <img src="../assets/architecture.jpg" alt="" />
      <h1>Museum of Modern Art completed in London</h1>
      <p>
        On March 10, 2022, the Museum of Modern Art opened in London. More than
        53,000 people have already booked tickets to the new museum. The
        permanent exhibition includes over ,000 works many of which were donated
        by the English collector Robert Fox. The opening of the square building
        has been postponed several times since the beginning of 2020. Those who
        have already visited the museum are really lucky.
        <span>5h ago</span>
      </p>
    </div>
    <div class="itemRight">
      <div class="orangeDiv">
        <p>NUMBER OF THE DAY</p>
        <h1>$80, 000</h1>
        <p>
          was earned at a charity auction on Paris. The money raised goes to
          children's hospitals.
        </p>
      </div>
      <hr />
      <img src="../assets/chairs.jpg" alt="" />
      <h1>Installation per million</h1>
      <p>
        During the first two days of the exhibition, Pierre was visited by more
        than 30,000 people. The artist did not expect that his installation
        would arouse such interest. In two days, he managed to break the record
        for the number of visitors to the exhibition among all artists of our
        time. <span>10h ago</span>
      </p>
    </div>
  </div>
</template>
<script>
export default {
  name: 'ContentList',
};
</script>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
hr {
  display: block;
  height: 1px;
  border: 0;
  border-top: 1px solid #000000;
  margin: 1em 0;
  padding: 0;
}
.dark hr {
  border-top: 1px solid #ffffff;
}
span {
  color: #c47b6f;
}
.itemLeft {
  flex: 1;
  margin: 1rem;
  display: inline-block;
  max-width: 22.5%;
  min-width: 12rem;
}
.itemMiddle {
  flex: 1;
  margin: 1rem;
  display: inline-block;
  max-width: 50%;
  min-width: 22rem;
}
.itemRight {
  flex: 1;
  margin: 1rem;
  display: inline-block;
  max-width: 22.5%;
  min-width: 12rem;
}

.mountain {
  max-width: 100%;
}
.profile {
  width: 3rem;
  height: auto;
  margin-right: 10px;
}

.author {
  display: flex;
  align-items: center;
  flex: 1;
  padding: 1rem 1rem 1rem 0;
}
.orangeDiv {
  background-color: #af695c;
  padding: 1rem;
  color: white;
}
@media (max-width: 768px) {
  .itemLeft {
    max-width: 90%;
    margin-top: 3rem;
    width: 100%;
  }
  .itemRight {
    max-width: 90%;
    margin-top: 3rem;
    width: 100%;
  }
  .itemMiddle {
    max-width: 90%;
    min-width: 15rem;
    margin-top: 3rem;
    width: 100%;
  }
}
</style>
