<template>
    <div class="about">
      <header class="header">
        <h1>เกี่ยวกับเรา</h1>
        <nav>
          <ul>
            <li><a href="/home">หน้าหลัก</a></li>
            <li><a href="/about">เกี่ยวกับเรา</a></li>
            <li><a href="/contact">ติดต่อเรา</a></li>
          </ul>
        </nav>
      </header>
  
      <section class="about-us">
        <h2>เราเป็นใคร?</h2>
        <p>เราเป็นบริษัทที่มุ่งมั่นในการให้บริการที่ดีที่สุดแก่ลูกค้า ก่อตั้งขึ้นในปี 2024 ด้วยวิสัยทัศน์ที่ต้องการสร้างสรรค์สิ่งใหม่ๆ และการบริการที่ประทับใจ.</p>
      </section>
  
      <section class="our-mission">
        <h2>ภารกิจของเรา</h2>
        <p>ภารกิจของเราคือการพัฒนาผลิตภัณฑ์และบริการที่ช่วยให้ลูกค้าของเราประสบความสำเร็จและมีความสุขในชีวิตประจำวัน.</p>
      </section>
  
      <section class="our-team">
        <h2>ทีมงานของเรา</h2>
        <div class="team-member" v-for="(member, index) in team" :key="index">
          <h3>{{ member.name }}</h3>
          <p>{{ member.role }}</p>
          <p>{{ member.bio }}</p>
        </div>
      </section>
  
      <footer>
        <p>&copy; 2024 เว็บไซต์ของเรา. สงวนลิขสิทธิ์.</p>
      </footer>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        team: [
          {
            name: "สมชาย ศรีสวัสดิ์",
            role: "ประธานเจ้าหน้าที่บริหาร",
            bio: "สมชายมีประสบการณ์มากกว่า 20 ปีในอุตสาหกรรมและเป็นผู้นำที่มีวิสัยทัศน์.",
          },
          {
            name: "สมหญิง ใจดี",
            role: "ประธานเจ้าหน้าที่ฝ่ายการตลาด",
            bio: "สมหญิงนำทัพด้านการตลาดด้วยกลยุทธ์ที่สร้างสรรค์และนวัตกรรม.",
          },
          {
            name: "สมปอง รักเรียน",
            role: "หัวหน้าฝ่ายเทคโนโลยี",
            bio: "สมปองเป็นผู้เชี่ยวชาญด้านเทคโนโลยีที่ทำงานเพื่อนำผลิตภัณฑ์ที่ดีที่สุดมาให้ลูกค้า.",
          },
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  .about {
    font-family: 'Arial', sans-serif;
    color: #333;
    text-align: center;
    margin: 0;
    padding: 0;
  }
  
  .header {
    background-color: #4CAF50;
    color: white;
    padding: 20px 0;
  }
  
  .header nav ul {
    list-style-type: none;
    padding: 0;
  }
  
  .header nav ul li {
    display: inline;
    margin: 0 15px;
  }
  
  .header nav ul li a {
    color: white;
    text-decoration: none;
    font-weight: bold;
  }
  
  .about-us, .our-mission, .our-team {
    margin: 40px 0;
    padding: 0 20px;
  }
  
  h2 {
    font-size: 2em;
    margin-bottom: 20px;
  }
  
  p {
    font-size: 1.2em;
    margin-bottom: 20px;
  }
  
  .team-member {
    margin: 20px 0;
    text-align: left;
  }
  
  footer {
    background-color: #333;
    color: white;
    padding: 10px 0;
    margin-top: 30px;
  }
  </style>
  