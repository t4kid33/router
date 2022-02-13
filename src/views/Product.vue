<template>
  <div
    class="bg-image d-flex justify-content-center align-items-center"
    style="background-color: rgb(4, 40, 75)"
  >
    <v-container>
      <center><h1 style="color: white">Product</h1></center>
      <v-container class="d-flex flex-wrap">
        <v-card
          class="mx-auto mb-5"
          max-width="400"
          v-for="(i, index) in productlist"
          :key="index"
        >
          <v-img class="text-black align-end" height="350px" :src="i.imageurl">
            <v-card-title>{{ i.name }}</v-card-title>
          </v-img>

          <v-card-subtitle class="pb-0">{{ i.rightText }}</v-card-subtitle>

          <v-card-text class="text--primary">
            <div style="font-size: large">{{ i.leftText }}</div>
          </v-card-text>

          <v-card-actions>
            <v-btn color="info" text :to="'/detail/' + i.rightText"
              >detail</v-btn
            >
            <v-btn color="orange" @click="selected(i)"> Add </v-btn>
          </v-card-actions>
        </v-card>
      </v-container>

      <table class="table table-striped table-hover"></table>
      <v-container
        ><h4 class="text-danger fs-1">Total {{ total() }} Baht</h4></v-container
      >
      <v-container grid-list-xs class="white">
        <router-view :key="$route.path"></router-view>
      </v-container>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      productlist: [
        {
          name: "iPhone 7",
          imageurl:
            "https://res.cloudinary.com/cenergy-innovation-limited-head-office/image/fetch/c_scale,q_70,f_auto,h_740/https://d1dtruvuor2iuy.cloudfront.net/media/catalog/product/P/W/PWB000226688.jpg",
          rightText:
            "iPhone 7 มาพร้อมกล้องความละเอียด 12MP, วิดีโอระดับ 4K, ระบบป้องกันภาพสั่นไหวแบบออปติคอล, จอภาพ Retina HD ขอบเขตสีกว้าง ขนาด 4.7 นิ้ว และ 3D Touch, ชิพ A10 Fusion เพื่อประสิทธิภาพการทำงานสูง, ระยะเวลาการใช้งานแบตเตอรี่ที่ยอดเยี่ยม, ความสามารถในการทนน้ำและฝุ่น รวมถึง iOS 12 ซึ่งเป็นระบบปฏิบัติการบนมือถือที่ล้ำสมัยที่สุด ที่มาพร้อมเครื่องมือใหม่ๆ อันทรงพลังที่จะทำให้ iPhone ของคุณเป็นส่วนตัวยิ่งกว่าครั้งไหนๆ",
          leftText: "Price : 6,504",
          active: false,
          price: 199,
        },

        {
          name: "iPhone 8",
          imageurl:
            "https://res.cloudinary.com/cenergy-innovation-limited-head-office/image/fetch/c_scale,q_70,f_auto,h_740/https://d1dtruvuor2iuy.cloudfront.net/media/catalog/product/P/W/PWB000235477.jpg",
          rightText:
            "iPhone 8 มาพร้อมดีไซน์แบบกระจกทั้งหมดและขอบอะลูมิเนียมเกรดเดียวกับที่ใช้ในอุตสาหกรรมอวกาศ, การชาร์จแบบไร้สาย, ความสามารถในการทนน้ำและฝุ่น, จอภาพ Retina HD ขนาด 4.7 นิ้ว พร้อมการแสดงผลแบบ True Tone, กล้องความละเอียด 12MP พร้อมโปรเซสเซอร์รับสัญญาณภาพสุดล้ำ, ขับเคลื่อนโดยชิพ A11 Bionic รวมถึงรองรับประสบการณ์ความจริงเสริมในเกมและแอพต่างๆ และมีระบบปฏิบัติการบนมือถือที่ล้ำสมัยที่สุดอย่าง iOS 12 ซึ่งมาพร้อมเครื่องมือใหม่ๆ อันทรงพลังที่จะทำให้ iPhone ของคุณเป็นส่วนตัวยิ่งกว่าครั้งไหนๆ",
          leftText: "Price : 15,900",
          active: false,
          price: 15900,
        },

        {
          name: "iPhone X",
          imageurl:
            "https://res.cloudinary.com/cenergy-innovation-limited-head-office/image/fetch/c_scale,q_70,f_auto,h_740/https://d1dtruvuor2iuy.cloudfront.net/media/catalog/product/i/p/iphonex-silver-34br-34fl-2up-us-en-screen.jpg",
          rightText:
            "iPhone X โดดเด่นด้วยจอภาพ Super Retina ขนาด 5.8 นิ้ว พร้อม HDR และการแสดงผลแบบ True Tone1, ดีไซน์แบบหน้าจอทั้งหมดและขอบสแตนเลสสตีลเกรดเดียวกับที่ใช้ทำเครื่องมือศัลยกรรม, การชาร์จแบบไร้สาย2, ความสามารถในการทนน้ำและฝุ่น3, กล้องคู่ความละเอียด 12MP พร้อมระบบป้องกันภาพสั่นไหวคู่แบบออปติคอล, กล้อง TrueDepth พร้อมโหมดภาพถ่ายบุคคลและคุณสมบัติ การจัดแสงภาพถ่ายบุคคล, การปลดล็อค iPhone X อย่างปลอดภัยด้วยความสามารถในการรู้จำใบหน้าอันล้ำสมัยเพียงแค่เหลือบมอง, ชิพ A11 Bionic อันทรงพลังที่จะพาคุณไปสัมผัสกับประสบการณ์จากเทคโนโลยีความจริงเสริมบน iPhone X ไม่ว่าจะเล่นเกมหรือใช้แอพ รวมถึง iOS 12 ซึ่งเป็นระบบปฏิบัติการบนมือถือที่ล้ำสมัยที่สุด ที่มาพร้อมเครื่องมือใหม่ๆ อันทรงพลังที่จะทำให้ iPhone ของคุณเป็นส่วนตัวยิ่งกว่าครั้งไหนๆ",
          leftText: "Price : 13,994",
          active: false,
          price: 13994,
        },

        {
          name: "iPhone XR",
          imageurl:
            "https://res.cloudinary.com/cenergy-innovation-limited-head-office/image/fetch/c_scale,q_70,f_auto,h_740/https://d1dtruvuor2iuy.cloudfront.net/media/catalog/product/p/w/pwb000244777_x1_5_.jpg",
          rightText:
            "iphone XR มาพร้อมจอภาพ Liquid Retina ซึ่งเป็น LCD ที่ล้ำสมัยที่สุดในอุตสาหกรรม ทั้งยังมี FaceID",
          leftText: "Price : 25,900",
          active: false,
          price: 25900,
        },
        {
          name: "iPhone XS",
          imageurl:
            "https://res.cloudinary.com/cenergy-innovation-limited-head-office/image/fetch/c_scale,q_70,f_auto,h_740/https://d1dtruvuor2iuy.cloudfront.net/media/catalog/product/p/w/pwb000244795_4_.jpg",
          rightText:
            "	หน้าจอแสดงผลกว้าง 5.8 นิ้ว แบบ OLED Multi-Touch (Super Retina HD Display) Capacitive Touchscreen 16.7 ล้านสี ความละเอียด 2436 x 1125 พิกเซล (458 ppi)",
          leftText: "Price : 16,994",
          active: false,
          price: 16994,
        },
        {
          name: "iPhone 11",
          imageurl:
            "https://res.cloudinary.com/cenergy-innovation-limited-head-office/image/fetch/c_scale,q_70,f_auto,h_740/https://d1dtruvuor2iuy.cloudfront.net/media/catalog/product/0/0/000252914_1.jpg",
          rightText:
            "ระบบกล้องคู่แบบใหม่หมดที่มาพร้อมกล้องอัลตร้าไวด์ โหมดกลางคืน และวิดีโอที่มีคุณภาพเหนือชั้น รวมถึงความสามารถในการทนน้ำและฝุ่นทั้งยังมีแบตเตอรี่ที่ใช้งานได้ตลอดวัน ทั้งหมดนี้ใน 6 สีสันสุดโดดเด่น นี่แหละ iPhone ที่เก่งยกกำลัง 11 ถ่ายวิดีโอระดับ 4K, ภาพถ่ายบุคคลที่สวยงามและทิวทัศน์สุดอลังการด้วยระบบกล้องคู่แบบใหม่หมด แล้วเก็บภาพในสภาวะแสงน้อยที่ดีที่สุดด้วยโหมดกลางคืน พร้อมเต็มอิ่มกับสีสันที่สมจริงในรูปภาพ วิดีโอและเกมบนจอภาพ Liquid Retina ขนาด 6.1 นิ้ว และยังมีชิพ A13 Bionic ที่ให้คุณได้สัมผัสกับประสิทธิภาพในแบบที่ไม่เคยมีมาก่อน ทั้งการเล่นเกม เทคโนโลยีความจริงเสริม (AR) และการถ่ายภาพ ทั้งยังทำอะไรๆ ได้มากขึ้นแต่ชาร์จน้อยลงด้วยแบตเตอรี่ที่ใช้งานได้ตลอดวัน และอุ่นใจยิ่งขึ้นด้วยความสามารถในการทนน้ำได้ถึงระดับสูงสุดไม่เกิน 2 เมตร ภายในระยะเวลา 30 นาที",
          leftText: "Price : 19,500",
          active: false,
          price: 19500,
        },
        {
          name: "iPhone 12",
          imageurl:
            "https://res.cloudinary.com/cenergy-innovation-limited-head-office/image/fetch/c_scale,q_70,f_auto,h_740/https://d1dtruvuor2iuy.cloudfront.net/media/catalog/product/i/p/iphone_12_purple_pure_back_iphone_12_purple_pure_front_2-up_print__usen_3.jpg",
          rightText:
            "iPhone 12 มาพร้อม 5G ที่ให้คุณดาวน์โหลดภาพยนตร์ได้ทุกที่ทุกเวลา รวมทั้งสตรีมวิดีโอคุณภาพสูง,1 จอภาพ Super Retina XDR ขนาด 6.1 นิ้วที่สดใสสวยงาม,2 Ceramic Shield ที่ทนต่อการตกกระแทกได้ดีขึ้น 4 เท่า,3 การถ่ายภาพในสภาวะแสงน้อยที่สวยงามน่าทึ่งด้วยโหมดกลางคืนบนกล้องทุกตัว, การบันทึก ตัดต่อ และเล่นวิดีโอระดับภาพยนตร์ ในแบบ Dolby Vision, ชิป A14 Bionic อันทรงพลัง และอุปกรณ์เสริม MagSafe ใหม่เพื่อการยึดติดที่ง่ายดายและ การชาร์จแบบไร้สายที่เร็วขึ้น4 พร้อมเริ่มความสนุกได้เลย",
          leftText: "Price : 25,590",
          active: false,
          price: 25590,
        },
        {
          name: "iPhone 13",
          imageurl:
            "https://res.cloudinary.com/cenergy-innovation-limited-head-office/image/fetch/c_scale,q_70,f_auto,h_740/https://d1dtruvuor2iuy.cloudfront.net/media/catalog/product/0/0/000270700_mllm3tha.jpg",
          rightText:
            "iPhone 13 Pro Max การอัปเกรดระบบกล้องระดับโปรครั้งใหญ่ที่สุดเท่าที่เคยมีมา จอภาพ Super Retina XDR พร้อม ProMotion จึงทั้งเร็วขึ้นและรู้สึกได้ถึงการตอบสนองที่ฉับไวยิ่งขึ้น พร้อมชิป A15 Bionic ที่เร็วสุดขั้ว 5G ที่เร็วสุดแรง1 แถมยังมีดีไซน์ที่ทนทาน และแบตเตอรี่ที่ใช้งานได้ดีที่สุดเท่าที่เคยมีมาใน iPhone อีกด้วย2",
          leftText: "Price : 62,900",
          active: false,
          price: 62900,
        },
      ],
    };
  },
  methods: {
    selected: function (i) {
      i.active = !i.active;
    },
    total: function () {
      var sum = 0;
      this.productlist.forEach(function (i) {
        if (i.active) {
          sum += i.price;
        }
      });
      return sum;
    },
  },
};
</script>

<style>
h2 {
  color: white;
}
</style>
