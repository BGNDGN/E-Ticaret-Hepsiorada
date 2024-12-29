<template>
  <div>
    <div id="containeropening">
      <a href="http://192.168.1.67:3000/" class="titleweb">Hepsiorada</a>
  
      <div class="last">
        <input type="text" placeholder="Lütfen bir kategori adı giriniz..." v-model="kategoriAra">
        <button @click="searchCategory">Kategori Ara</button>
      </div>
  
      <nuxt-link to="/sepet"><h3 class="titlecart">Sepetim</h3></nuxt-link>
    </div>
  
    <div v-if="errorMessage" class="error">{{ errorMessage }}</div>
  
    <div class="color">
      <div class="orange"></div>
      <div class="blue"></div>
      <div class="purple"></div>
      <div class="green"></div>
      <div class="black"></div>
    </div>
  
    <div id="containercategories">
      <nuxt-link v-for="kategori in categories" :key="kategori.id" :to="`/categories/${kategori.id}`">
        <p class="categorytext">{{ kategori.title }}</p>
      </nuxt-link>
    </div>
  
    <div class="last2">
      <h3>Çok Satanlar</h3>
    </div>
    <hr>
  
    <div id="maincategories">
      <div id="containerbestsells" v-for="(item, index) in coksatanlar" :key="index">
        <nuxt-link :to="`/categories/${item.title.toLowerCase()}`">
          <img :src="item.img" />
          <p class="baslik">{{ item.ad }}</p>
        </nuxt-link>
      </div>
    </div>
  </div>
  </template>
  
  <script>
  import "/pages/styles/color.css";
  import "/pages/styles/index.css";
  
  export default {
    name: 'IndexPage',
    data() {
      return {
        categories: [
          { id: "bilgisayar", title: "Bilgisayar", name: "bilgisayar" },
          { id: "telefon", title: "Telefonlar", name: "telefon" },
          { id: "giyim", title: "Giyim", name: "giyim" },
          { id: "kisiselbakim", title: "Kişisel Bakım", name: "kisiselbakim" },
          { id: "beyazesya", title: "Beyaz Eşya", name: "beyazesya" },
          { id: "aksesuar", title: "Aksesuar", name: "aksesuar" },
          { id: "sporaletleri", title: "Spor Aletleri", name: "sporaletleri" }
        ],
        coksatanlar: [
          { img: "/categories/bilgisayar/image1.jpg", title: "bilgisayar", ad: "Warp Optima B760" },
          { img: "/categories/telefon/image2.jpg", title: "telefon", ad: "Xiaomi Redmi Note 13 Pro" },
          { img: "/categories/giyim/image3.jpg", title: "giyim", ad: "Bluz Seti" },
          { img: "/categories/kisiselbakim/image4.jpg", title: "kisiselbakim", ad: "Yüz Bakım Seti" },
          { img: "/categories/beyazesya/image5.jpg", title: "beyazesya", ad: "Beyaz Eşya Seti" },
          { img: "/categories/aksesuar/image6.jpg", title: "aksesuar", ad: "Bileklik Aksesuarı" },
          { img: "/categories/sporaletleri/image7.jpg", title: "sporaletleri", ad: "Spor Aleti" }
        ],
        kategoriAra: "",
        errorMessage: "",
      };
    },
    methods: {
      searchCategory() {
        const a = this.kategoriAra.toLowerCase().trim();
        if (!a) {
          this.errorMessage = "Lütfen bir kategori adı giriniz.";
          return;
        }
        const b = this.categories.find((category) => category.name === a);
  
        if (b) {
          this.errorMessage = "";
          this.$router.push(`/categories/${b.id}`);
        } else {
          this.errorMessage = "Girdiğiniz Kategori Adı Yanlış.";
          this.kategoriAra = "";
        }
      }
    }
  };
  </script>  