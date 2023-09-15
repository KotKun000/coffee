<template>
  <div class="container">
    <div v-for="(shop, index) in coffeeShops" :key="index" class="shop-card">
      <img :src="shop.image" alt="ร้านกาแฟ">
      <h2>{{ shop.name }}</h2>
      <p>{{ shop.details }}</p>
      <button @click="openModal(index)">จองโต๊ะ</button>
    </div>
    
  </div>
  <div class="container2">
    <div v-if="selectedShop !== null" class="modal">
      <div class="modal-content">
        <h3>{{ coffeeShops[selectedShop].name }}</h3>
        <label for="name">ชื่อ:</label>
        <input type="text" id="name" v-model="reservation.name">
        <label for="phone">เบอร์โทร:</label>
        <input type="text" id="phone" v-model="reservation.phone">
        <label for="datetime">วันที่ เวลา:</label>
        <input type="datetime-local" id="datetime" v-model="reservation.datetime">
        <label for="tableCount">จำนวนโต๊ะ:</label>
        <input type="number" id="tableCount" v-model="reservation.tableCount">
        <button @click="bookTable">จอง</button>
        <button @click="closeModal">ปิด</button>
      </div>
    </div>
    <div v-if="selectedShop !== null" class="reservation-details">
      <h2>รายละเอียดการจอง</h2>
      <p><strong>ชื่อ:</strong> {{ reservation.name }}</p>
      <p><strong>เบอร์โทร:</strong> {{ reservation.phone }}</p>
      <p><strong>วันที่ เวลา:</strong> {{ reservation.datetime }}</p>
      <p><strong>จำนวนโต๊ะ:</strong> {{ reservation.tableCount }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      coffeeShops: [
        {
          name: "ร้าน A",
          details: "ร้านกาแฟที่มีบรรยากาศเงียบสงบ",
          image: "https://upload.wikimedia.org/wikipedia/commons/thumb/e/e4/Latte_and_dark_coffee.jpg/800px-Latte_and_dark_coffee.jpg"
        },
        {
          name: "ร้าน B",
          details: "ร้านกาแฟสไตล์บราวน์",
          image: "https://neurosciencenews.com/files/2023/06/coffee-brain-caffeine-neuroscincces.jpg"
        },
        {
          name: "ร้าน C",
          details: "ร้านกาแฟที่เน้นเมล็ดกาแฟคุณภาพ",
          image: "https://uwm.edu/letters-science/wp-content/uploads/sites/255/2016/11/coffee-cup.jpg"
        },
        {
          name: "ร้าน D",
          details: "ร้านกาแฟในสไตล์สมุนไพร",
          image: "https://www.tastingtable.com/img/gallery/coffee-brands-ranked-from-worst-to-best/intro-1645231221.jpg"
        },
      ],
      selectedShop: null,
      reservation: {
        name: "",
        phone: "",
        datetime: "",
        tableCount: 0,
      },
      
    };
  },
  methods: {
    openModal(index) {
      this.selectedShop = index;
    },
    closeModal() {
      this.selectedShop = null;
    },
    bookTable() {
      console.log("จองโต๊ะสำเร็จ");
      this.closeModal();
      
    },
  },
};
</script>

<style scoped>


.shop-card {
  background: linear-gradient(135deg, #dab57e, #8b7261);
  margin: 10px;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  text-align: center;
  
  
}

.shop-card img {
  width: 70%;
  height: 10vw;
  object-fit: cover;
  border-radius: 10px;
  
}

.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 999;
}

.modal-content {
  background-color: rgba(0, 0, 0, 0.514);
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(240, 14, 14, 0.918);
  display: grid;
  grid-template-columns: repeat( 1fr);
}

.reservation-details {
  background-color: #d84e4e;
  margin: 10px;
  padding: 20px;
  border: 1px solid #f5f5f5;
  border-radius: 5px;
  text-align: center;
}

.container{
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  column-gap: 20px;
  row-gap: 20px;
  margin-top: 50x;
  object-fit: cover;
  
}
.container2{
  max-width: auto;
}
button{
  background: linear-gradient(135deg, #71b7e6, #9b59b6);
}

</style>
