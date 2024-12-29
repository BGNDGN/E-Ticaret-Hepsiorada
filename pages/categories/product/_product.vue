<template>
    <div>
  
      <div id="titlecontainer">
        <a href="http://192.168.1.67:3000/" class="titlewebid">Hepsiorada</a>
        <h1>{{ product.title }}</h1>
        <nuxt-link to="/sepet" class="sepetButton"><h3>Sepetim</h3></nuxt-link>
      </div>
  
      <div class="color">
        <div class="orange"></div>
        <div class="blue"></div>
        <div class="purple"></div>
        <div class="green"></div>
        <div class="black"></div>
      </div>
      
  
      <div id="product">
        <div>
          <img class="image" :src="product.img" alt="Ürün Resmi">
        </div>
  
        <ul>
          <li v-for="(specName, index) in specNames" :key="index">
            {{ specName }}: {{ product.ozellik[index] }}
          </li>
          <hr>
          <div>
            <p>Fiyat: {{ product.price }} TL</p>
          </div>
  
          <div class="addToCart">
            <button @click="addToCart" class="cart">Ürünü Sepete Ekle</button>
          </div>
        </ul>
  
      </div>
  
    </div>
  </template>
  
  <script>
  import "@/pages/styles/color.css";
  import "@/pages/styles/product.css";
  export default {
    async asyncData({params}) {
      try {
      const idid = params.id.trim();
      const productid = params.product.trim();
  
      if (!idid) {
        console.log("idid parametresi eksik.");
      }
  
      if (!productid) {
        console.log("productid parametresi eksik.");
      }
  
        const kategoriozellikleri = {
          bilgisayar:["İşlemci", "Ekran Kartı", "RAM Kapasitesi", "Depolama", "Garanti Süresi"],
          telefon:["Model", "Renk", "Garanti Süresi"],
          giyim: ["Tür", "Kumaş", "Beden", "Renk"],
          kisiselbakim: ["Tür", "İçeriği"],
          beyazesya: ["Tür", "Set İçeriği", "Garanti Süresi", "Renk"],
          aksesuar: ["Tür", "İçerik", "Renk"],
          sporaletleri:["Tür", "İçerik", "Garanti Süresi", "Renk"], 
        }
  
        const productDetails = {
          bilgisayar:   [{ title: "Warp Optima B760", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Intel Core i5 12400F", "RTX 4060", "16 GB", "512GB SSD", "2 Yıl"]},
                         { title: "Casper Excalibur", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Intel Core i7 12700", "RTX 4080", "32 GB", "1TB SSD", "3 Yıl"]},
                         { title: "Dragos DRx5245", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Ryzen 5 5600", "RTX 4060", "15 GB", "1TB SSD", "3 Yıl"]},
                         { title: "Güneysu Teknoloji", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Ryzen 5 7500F ", "RTX 4060TI", "16 GB", "1TB SSD", "3 Yıl"]},
                         { title: "Turbox DRX6875", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Ryzen 5 5600", "RTX3050", "32 GB", "1TB SSD", "3 Yıl"]},
                         { title: "Warp Optima", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Intel Core i5 11400F", "RTX 3050", "16 GB", "512GB SSD", "3 Yıl"]},
                         { title: "Warp Optima", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Intel Core i7 11400F ", "RTX 4060", "32 GB", "1TB SSD", "3 Yıl"]}],
  
          telefon:      [{ title: "Evkur", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Trident A60 6/128GB Akıllı Telefon", "Açık Mavi", "2 Yıl"]},
                         { title: "Hepsiorada", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Xiaomi Redmi Note 13 Pro 4G 256GB 8GB Ram", "Siyah", "2 Yıl"]},
                         { title: "Samsung", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Samsung Galaxy S24 Ultra 256 GB", "Toz Pembe", "2 Yıl"]},
                         { title: "Gizerler", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Samsung Galaxy A25 SM-A256ELBDTUR 6 GB/128 GB Telefon", "Buz Kırağı", "2 Yıl"] },
                         { title: "Vatan Bilgisayar", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["iPhone 15 Pro 128 Gb Akıllı Telefon", "Natural Titanium", "2 Yıl"]},
                         { title: "Casper", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Casper VIA X40 Telefon", "Siyah", "2 Yıl"]},
                         { title: "AppleStore", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Apple iPhone XS 64GB", "Gümüş", "2 Yıl"]}],
  
          giyim:        [{ title: "S", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["hırka", "İpek", "L", "Mavi"]},
                         { title: "S", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Palto", "İpek", "XL", "Gri"]},
                         { title: "S", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Bluz Seti: x4 Bluz", "Pamuk", "L", "Beyaz-Kahverengi-Açık Kahverengi-Yeşil-Beyaz"]},
                         { title: "S", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Elbise", "İpek", "L", "Yosun Yeşili"]},
                         { title: "S", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Uzun Hırka", "Pamuk", "XL", "Koyu Yeşil"]},
                         { title: "S", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Kadın Ceket", "İpek", "L", "Kahverengi"]},
                         { title: "S", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Kadın Ceket", "İpek", "XL", "Gri"]}],     
                         
          kisiselbakim: [{ title: "Yüz Bakım", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Yüz Bakım", "Krem"]},
                         { title: "Yüz Bakım", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Yüz Bakım", "Losyon"]},
                         { title: "Tarak", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Saç Bakım", "Tarak"]},
                         { title: "Yüz Bakım Seti", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Yüz Bakım Paketi", "x2 Yüz Kremi, x2 Yüz Losyonu"]},
                         { title: "Yüz Bakım", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Yüz Bakım", "Yüz Temizleme Pamuğu"]},
                         { title: "Ağız Bakım", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Ağız Bakım", "Diş Fırçası Seti"]},
                         { title: "Yüz Bakım Seti", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Yüz Bakım", "x2 Yüz Bakım Serumu, x2 Yüz Bakım Kremi"]}],
  
          beyazesya:    [{ title: "Bosch", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Beyaz Eşya Seti", "Buzdolabı: Bosch KGP76AIC0N 526 Lt No-Frost Buzdolabı, Fırın: Bosch HBJ558YH0T Gri Ankastre Fırın, Çamaşır Makinesi: Bosch WAL24PH0TR 1200 Devir 10 kg Çamaşır Makinesi , Aspiratör: Bosch DHI625H Ankastre Sürgülü Aspiratör, Bulaşık Makinesi: Bosch SMS44DI00T 4 Programlı Bulaşık Makinesi", "2 Yıl", "Gri"]},
                         { title: "Bosch", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Beyaz Eşya Seti", "Buzdolabı: Bosch KDN86AWF1N 641 Lt Çift Kapılı No-Frost Buzdolabı , Fırın: Bosch HBF514BS1T 66L Ankastre Fırın Paslanmaz Çelik , Çamaşır Makinesi: Bosch WGA252Z0TR 1200 Devir 10 kg Çamaşır Makinesi , Aspiratör: Bosch DFT63CA51T 60 cm Inox Sürgülü Aspiratör, Bulaşık Makinesi: Bosch SMS4IKI51T 5 Programlı D Sınıfı Bulaşık Makinesi", "2 Yıl", "Gri"]},
                         { title: "Beko",  img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Beyaz Eşya Seti", "Buzdolabı: Beko 966375 Ieg E Enerji Sınıfı 375 lt No Frost Buzdolabı, Fırın: Beko Bfe 400 B A Enerji Sınıfı 66 lt Ocaklı Fırın , Çamaşır Makinesi: Beko Cmx 10120 10 kg A Enerji Sınıfı 1200 Devir Beyaz Çamaşır Makinesi, Aspiratör: Beko P 38 Beyaz Tek Motor Sürgülü Aspiratör , Bulaşık Makinesi: Beko Bm 6047 I 6 Program Bulaşık Makinesi", "2 Yıl", "Gri"]},
                         { title: "Beko", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Beyaz Eşya Seti", "Buzdolabı: Beko 970406 MB E Enerji Sınıfı 406 L No Frost Buzdolabı, Fırın: Beko Bfm 430 D Beyond Serisi Ankastre , Çamaşır Makinesi: Beko cm 11140 11 kg 1400 Devir A Sınıfı Enerjili Çamaşır Makinası , Bulaşık Makinesi: Beko Bm 5045 5 Programlı 14 Kişilik Bulaşık Makinesi ", "2 Yıl", "Beyaz"]},
                         { title: "Beko", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Beyaz Eşya Seti", "Buzdolabı: Beko 176478 Eı No Frost Gardırop Tipi Buzdolabı InoxBeko 970357 MB E Enerji Sınıfı 357 Litre No Frost Buzdolabı , Fırın: Beko Bfe 400 Eb Ocaklı Fırın , Çamaşır Makinesi: Beko Cmx 10120 10 kg A Enerji Sınıfı 1200 Devir Çamaşır Makinesi: Beko Cmxd 9100 A Enerji Sınıfı 9kg 1000 Devir Çamaşır Makinası, Aspiratör: Beko P 40 S Siyah Cam Dekorlu Aspıratör, Bulaşık Makinesi: Beko Bm 4044 I 4 Programlı E enerji Sınıfı Inox Bulaşık Makinesi", "2 Yıl", "Gri"]},
                         { title: "Beko", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Beyaz Eşya Seti", "Buzdolabı: Beko 684580 MB Kombi No Frost Buzdolabı , Fırın: Beko Bfm 310 B 72LT Beyaz Ankastre Fırın , Çamaşır Makinesi: , Aspiratör: Beko P 38 Tı Inox Ankastre Sürgülü Aspiratör , Bulaşık Makinesi: Beko Bm 4144 D Enerji Sınıfı 4 Programlı Bulaşık Makinesi", "2 Yıl", "Gri"]},
                         { title: "Bosch", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Beyaz Eşya Seti", "Buzdolabı: Bosch KDN86AWF1N 641 Lt Çift Kapılı No-Frost Buzdolabı , Fırın: Bosch HBF514BS1T 66L Ankastre Fırın Paslanmaz Çelik , Çamaşır Makinesi: Bosch WGA252Z0TR 1200 Devir 10 kg Çamaşır Makinesi , Aspiratör: Bosch DFT63CA51T 60 cm Inox Sürgülü Aspiratör, Bulaşık Makinesi: Bosch SMS4IKI51T 5 Programlı D Sınıfı Bulaşık Makinesi", "2 Yıl", "Gri"]}],
  
          aksesuar:     [{ title: "OneDekor.com", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Salon Aksesuarı", "3 Parça Salon Aksesuar Takımı Model B", "Açık Sarı"]},
                         { title: "Casadebella", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Dekoratif Aksesuar", "7 Parça Tepsili Dekoratif Aksesuar Seti", "Mor"]},
                         { title: "Aysira Shop", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["SAÇ AKSESUARI", "Kadın Taç", "Açık", "Beyaz"]},
                         { title: "Türkay Aksesuar ", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Toka", "Mavi Boncuklu Taraklı Ikili Gelin Saç Tokası", "Mavi"]},
                         { title: "Eminönü Boncuk", img: `/categories/${idid}/image${productid}.jpg`, price: 1200, ozellik: ["Aksesuar Kancaları", "Anahtarlık ve Aksesuar Kancaları ", "Sarı"]},
                         { title: "handeliaksesuar.com", img: `/categories/${idid}/image${productid}.jpg`,price: 1200, ozellik: ["Bileklik Aksesuarı", "Altın Kelepçe", "Belirtilmemiş"]},
                         { title: "Sima Eşarp", img: `/categories/${idid}/image${productid}.jpg`,price: 1200, ozellik: ["Kadın Taç", "ZÜMRÜT Taşlı Aksesuar", "Zümrüt Yeşili"]}],
  
          sporaletleri: [{ title: "PASİFİK", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Spor Aleti", "Koşu Bandı", "3 Yıl", "Gri"]},
                         { title: "PASİFİK", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Tenis Seti", "Tenis Raketi, Tenis Topu, Bluetooth Kulaklık, x2 Tenis Topu x1 Futbol Topu", "6 Ay", "Sarı"]},
                         { title: "Aydın Sport", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Spor Aleti", "x1 Crossfit", "1 Ay", "Kırmızı"]},
                         { title: "Kochler Total Crunch", img: `/categories/${idid}/image${productid }.jpg`,  price: 1200, ozellik: ["Spor Aleti", "x1 Tüm Vücut Fitness Aleti – Kondisyon Aleti – Mekik Aleti, x2 Tenis Topu x1 Futbol Topu", "1 Ay", "Turuncu"]},
                         { title: "PASİFİK", img: `/categories/${idid}/image${productid }.jpg`, price: 1200, ozellik: ["Spor Aleti", "ÇOK FONKSİYONLU SPOR ALETİ", "3 Ay", "Siyah"]},
                         { title: "Aydın Sport",img: `/categories/${idid}/image${productid }.jpg`,price: 1200, ozellik: ["Spor Aleti", "25 Kg Halter Ve Dambıl Seti Ağırlık Fitness Seti", "6 Ay", "Siyah"],},
                         { title: "Wtfit",img: `/categories/${idid}/image${productid }.jpg`,price: 1200, ozellik: ["Spor Aleti", "Alt Sırt Spor Fitness Ekipmanı ", "6 Ay", "Bordo"]}],               
        };
  
        const categoryProduct = productDetails[idid];
        const product = categoryProduct[productid - 1];
        const specNames = kategoriozellikleri[idid];
  
        return {
          product,
          specNames,
          idid, 
          productid
        };
        
        } catch (error) {
          console.log("Bir hata oluştu",error);
        }
    },
  
    methods: {
      addToCart() {
        let cart = JSON.parse(localStorage.getItem("cart")) || [];
        cart.push(this.product);
        localStorage.setItem("cart", JSON.stringify(cart));
        console.log("Ürün Eklendi!", (this.product))
        alert("Ürün Sepetinize Eklendi!")
      },
    },
  }
  </script>