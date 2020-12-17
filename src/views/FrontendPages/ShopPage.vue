<template>
  <b-container fluid>
    <!-- <b-row class="row"> -->
    <Slick id="shop-slider" class="slider m-0 p-0">
      <div class="shop">
        <div
          class="shop-title"
          data-animation-in="fadeInUp"
          data-delay-in="0.2"
        >
          <span>Shop</span>
        </div>
        <!-- <div
          class="d-flex align-items-center"
          data-animation-in="fadeInUp"
          data-delay-in="1"
        >
          <span class="badge badge-secondary p-2">
            age +
          </span>
          <span class="ml-3">
            season
          </span>
        </div>
        <p data-animation-in="fadeInUp" data-delay-in="1.2">
          text
        </p> -->
        <b-row class="shop-page_row">
          <b-col sm="12" class="overflow-hidden">
            <div
              class="iq-main-header d-flex align-items-center justify-content-between"
            >
              <h4
                class="main-title"
                v-b-tooltip.hover
                title="View All"
                data-animation-in="fadeInUp"
                data-delay-in="0.4"
              >
                <router-link :to="{ path: '#' }" class="text-white"
                  >Suggested For You</router-link
                >
              </h4>
              <div class="d-flex slick-aerrow-block">
                <button
                  class="slick-prev slick-arrow"
                  aria-label="Previous"
                  type="button"
                  style="display: block"
                  @click="prev()"
                ></button>
                <button
                  class="slick-next slick-arrow"
                  aria-label="Next"
                  type="button"
                  style="display: block"
                  @click="next()"
                ></button>
              </div>
            </div>
            <div class="suggestede-contens">
              <div
                class="list-inline favorites-slider row p-0 mb-0"
                data-animation-in="fadeInUp"
                data-delay-in="0.7"
              >
                <li
                  class="slide-item"
                  v-for="(item, index) in suggestionData"
                  :key="index"
                >
                  <router-link :to="{ path: item.path }">
                    <div class="block-images position-relative">
                      <div class="img-box">
                        <!-- {{ item.images[0] }} -->
                        <img
                          :src="getImage(item.images[0])"
                          class="img-fluid"
                          alt=""
                        />
                        <!-- <img src="@/assets/images/shop/Bruce/1.png" class="img-fluid" alt=""> -->
                      </div>
                      <div class="block-description">
                        <h6>{{ item.title }}</h6>
                        <div class="movie-time d-flex align-items-center my-2">
                          <div class="badge badge-secondary p-1 mr-2">
                            {{ item.age }}
                          </div>
                          <span class="text-white">{{ item.time }}</span>
                        </div>
                        <div class="hover-buttons">
                          <span class="btn btn-hover"
                            ><i class="fa fa-play mr-1" aria-hidden="true"></i>
                            Buy now</span
                          >
                        </div>
                      </div>
                      <!-- <div class="block-social-info">
                            <ul class="list-inline p-0 m-0 music-play-lists">
                                <li><span><i class="ri-volume-mute-fill"></i></span></li>
                                <li><span><i class="ri-heart-fill"></i></span></li>
                                <li><span><i class="ri-add-line"></i></span></li>
                            </ul>
                          </div> -->
                    </div>
                  </router-link>
                </li>
              </div>
              <!-- </Slick> -->
            </div>
          </b-col>
        </b-row>
      </div>
    </Slick>
    <!-- <div class="shop">
      <div class="shop-title">
        <span>Shop</span>
      </div>

    </div> -->
    <!-- </b-row> -->
  </b-container>
</template>

<script>
// import Vue from 'vue'

export default {
  name: 'Shop',
  data() {
    return {
      // Products: [
      //   {
      //     name: 'B.R.U.C.E. Saves Christmas',
      //     path: '/games/Bruce-Saves-Christmas',
      //     price: '£19.99',
      //     images: [
      //       '@/assets/images/shop/1.png',
      //       '@/assets/images/shop/2.png',
      //       '@/assets/images/shop/3.png',
      //       '@/assets/images/shop/4.png',
      //       '@/assets/images/shop/5.png',
      //       '@/assets/images/shop/6.png',
      //       '@/assets/images/shop/7.png',
      //       '@/assets/images/shop/8.png',
      //       '@/assets/images/shop/9.png',
      //       '@/assets/images/shop/10.png',
      //     ],
      //   },
      // ],
      suggestionData: [
        {
          title: 'B.R.U.C.E. Saves Christmas',
          age: '',
          path: '/game/Bruce-Saves-Christmas',
          time: '£19.99',
          images: [
            'bruce/1.png',
            'bruce/2.png',
            'bruce/3.png',
            'bruce/4.png',
            'bruce/5.png',
            'bruce/6.png',
            'bruce/7.png',
            'bruce/8.png',
            'bruce/9.png',
            'bruce/10.png',
          ],
        },
        {
          title: 'Sector X - The B.R.U.C.E. Project: Part 1',
          age: '',
          path: '#',
          time: '£15.00',
          images: ['bruce-project-part-1/1.png'],
        },
        {
          title: 'Sector X - The B.R.U.C.E. Project: Part 2',
          age: '',
          path: '#',
          time: '£15.00',
          images: ['bruce-project-part-2/1.png'],
        },
        // {
        //   title: 'Sector X - The B.R.U.C.E. Project: Part 2',
        //   age: '',
        //   time: '£15.00',
        //   images: ['bruce-project-part-1/1.png']
        // }
        // { image: require('@/assets/images/frontend/suggested/01.jpg'), title: 'The Last Breath', age: '5+', time: '2h 30m' },
        // { image: require('@/assets/images/frontend/suggested/02.jpg'), title: 'Last Night', age: '22+', time: '2h 30m' },
        // { image: require('@/assets/images/frontend/suggested/03.jpg'), title: '1980', age: '25+', time: '2h 30m' },
        // { image: require('@/assets/images/frontend/suggested/03.jpg'), title: '1980', age: '25+', time: '2h 30m' },
        // { image: require('@/assets/images/frontend/suggested/03.jpg'), title: '1980', age: '25+', time: '2h 30m' }
      ],
      suggestionSliderOption: {
        dots: false,
        arrows: false,
        infinite: true,
        speed: 300,
        autoplay: false,
        slidesToShow: 4,
        slidesToScroll: 1,
        responsive: [
          {
            breakpoint: 1200,
            settings: {
              slidesToShow: 3,
              slidesToScroll: 1,
              infinite: true,
              dots: true,
            },
          },
          {
            breakpoint: 768,
            settings: {
              slidesToShow: 2,
              slidesToScroll: 1,
            },
          },
          {
            breakpoint: 480,
            settings: {
              slidesToShow: 1,
              slidesToScroll: 1,
            },
          },
        ],
      },
    };
  },
  methods: {
    getImage(path) {
      return require(`@/assets/images/shop/${path}`);
    },
  },
};
</script>

<style lang="scss" scoped>
.shop {
  // border: 1px solid red;
  margin-top: 80px;
  // min-height: calc(100vh - 550px);

  .shop-title {
    text-align: center;
    margin: 0 auto;
    font-size: 34px;
    font-weight: bold;
  }
  .shop-page_row {
    // margin-top: 50px;
    padding: 120px 0 100px 0;
    // border: 1px solid red;
  }
}
</style>
