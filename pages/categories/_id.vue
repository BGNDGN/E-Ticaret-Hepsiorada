<template>
    <div id="main">
      <div id="titlecontainer">
        <div>
            <a href="http://192.168.1.67:3000/" class="titlewebid">Hepsiorada</a>
        </div>

        <nuxt-link to="/sepet"><h3 class="titlecart">Sepetim</h3></nuxt-link>
    </div> 

        <div class="color">
          <div class="orange"></div>
          <div class="blue"></div>
          <div class="purple"></div>
          <div class="green"></div>
          <div class="black"></div>
        </div>

        <div id="ürünler">
          <div v-for="(item,index) in images" :key="index" class="ürün">
              <img :src="item.src" alt="Ürün">
              <p>{{ item.description }}</p>
              <nuxt-link :to="`/categories/${abc}/product/${index + 1}`"><button>Ürünü İncele</button></nuxt-link>
          </div>
        </div>  
    </div>  
</template>

<script>
import "@/pages/styles/color.css";
import "@/pages/styles/id.css";
export default {
    async asyncData({ params }) {
        try {
            const abc = params.id;
            const abc2 = abc.toUpperCase()

            const categoryDescriptions = {
                bilgisayar:["Warp Optima B760", "Casper Excalibur", "Dragos DRx5245", "Güneysu Teknoloji", "Turbox DRX6875", "Warp Optima", "Warp Optima"],
                telefon:["Trident A60 6/128GB Akıllı Telefon", "Xiaomi Redmi Note 13 Pro 4G 256GB 8GB Ram", "Samsung Galaxy S24 Ultra 256 GB", "Samsung Galaxy A25 SM-A256ELBDTUR 6 GB/128 GB Telefon", "iPhone 15 Pro 128 Gb Akıllı Telefon", "Casper VIA X40 Telefon", "Apple iPhone XS 64GB"],
                giyim:["Hırka", "Palto", "Bluz Seti", "Elbise", "Uzun Hırka", "Kadın Ceket", "Kadın Ceket"],
                kisiselbakim:["Yüz Bakım", "Yüz Bakım", "Saç Bakım", "Yüz Bakım", "Yüz Bakım", "Ağız Bakım", "Yüz Bakım"],
                beyazesya:["Beyaz Eşya Seti", "Beyaz Eşya Seti", "Beyaz Eşya Seti", "Çamaşır Makinesi", "Beyaz Eşya Seti", "Beyaz Eşya Seti", "Beyaz Eşya Seti"],
                aksesuar:["Salon Aksesuarı", "Dekoratif Aksesuar", "Saç Aksesuarı", "Toka", "Aksesuar Kancaları", "Bileklik Aksesuarı", "Kadın Taç"],
                sporaletleri:["Koşu Bandı", "Tenis Seti", "Crossfit", "Tüm Vücut Fitness Aleti", "Çok Fonksiyonlu Spor Aleti", "Halter Ve Dambıl Seti", "Alt Sırt Spor Fitness Seti"],

            };

            const images = Array.from({ length:7 }, ( _,i ) => ({src: `/categories/${ abc }/image${ i + 1 }.jpg`,
                                                                description: categoryDescriptions[abc]?.[i]}));

            return {
                abc,
                abc2,
                images,
            };

        } catch (error) {
            error({ statusCode: 404, message: 'Veriler alınamadı' });
        }
    }
}
</script>
