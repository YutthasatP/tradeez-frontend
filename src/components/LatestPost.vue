<template>
  <div class="latest">


    <div class="lastest-card background container">
      <div class="row">
        <div class="col-12 col-md-6 col-lg-4" v-for="alatest in latest" v-bind="alatest.id">
          <div class="card tez-card">
            <img :src="`${alatest.product_img}`" class="card-img-top d-block c-img" alt="">
            <div class="card-body">
              <p class="blockquote-footer mt-1 fs-6 tez-mc"> <text class="tez-mc-author ">{{ alatest.author_name }}</text>
              </p>
              <h5 class="card-title tez-title text-truncate">{{ alatest.product_name }}</h5>
              <p class="card-text">{{ alatest.time }}</p>
              <br v-show="alatest.categories.length === 0" />

              <div class="row">
                <div class="col-auto" v-for="cate in alatest.categories" v-bind="alatest.id">
                  <span class=" card-text text-truncate">• {{ cate }}</span>
                </div>
              </div>
              <br />

              <p class="card-text description" v-show="isReward(alatest)">TEz : {{ alatest.price }} Point</p>
              <p class="card-text description" v-show="!isReward(alatest)">ราคา : {{ alatest.price }} บาท</p>
              <RouterLink :to="`detail/${alatest._id}`">
                <button class="btn btn-primary px-4 py-2 fs-6 tez-btn ">Read More</button>
              </RouterLink>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>
  
<script>
export default {
  name: 'home',
  props: {
    latest: Array
  },
  data() {
    return {
      Blog: []
    }
  }, methods: {
    isReward(post) {
      return post.reward
    }
  }
}

</script>

<style scoped>
.tez-card {
  margin-top: 5%;
  border: none;
}

.text {
  font-family: 'PT Serif';
  font-style: normal;
  font-weight: 700;
  font-size: 42px;
  line-height: 56px;
  color: #272343;
}

.underline {
  text-decoration: underline;
  text-decoration-color: #FB743E;
  text-decoration-thickness: 4px;

}

.background {
  background-color: #F5F5F5;
}

.c-item {
  height: 480px;
}

.c-img {

  height: 292px;
  object-fit: cover;
  display: block;
}

.btn-primary {
  background-color: #FB743E !important;
}

.btn-primary:visited,
.btn-primary:hover,
.btn-primary:active,
.btn-primary::backdrop {
  background-color: #d44911 !important;
}

.tez-title {
  font-family: 'PT Serif';
  font-style: normal;
  font-weight: 700;
  font-size: 28px;
  line-height: 120%;
  color: #272343;
  text-align: left;
}

.tez-title2 {
  font-family: 'PT Serif';
  font-style: normal;
  font-weight: 700;
  font-size: 38px;
  line-height: 120%;
  color: #FB743E;
  text-align: left;
}

.tez-btn {
  border: none;
  width: auto;
  height: auto;
}

.tez-mc {
  font-family: "PT Serif";
  font-style: normal;
  font-weight: 600;
  color: #FB743E;
  text-align: left;

}

.tez-mc-author {
  font-family: "PT Serif";
  font-style: normal;
  font-weight: 100;
  font-size: 15px;
  color: #000000;
  text-align: left;
}

.description {
  font-family: 'Poppins';
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 150%;
  color: #6D7280;
  text-align: left;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>