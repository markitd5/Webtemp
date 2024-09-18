<template>
    <div class="contact">
      <header class="header">
        <h1>ติดต่อเรา</h1>
        <nav>
          <ul>
            <li><a href="/home">หน้าหลัก</a></li>
            <li><a href="/about">เกี่ยวกับเรา</a></li>
            <li><a href="/contact">ติดต่อเรา</a></li>
          </ul>
        </nav>
      </header>
  
      <section class="contact-form">
        <h2>ส่งข้อความถึงเรา</h2>
        <form @submit.prevent="submitForm">
          <div class="form-group">
            <label for="name">ชื่อของคุณ:</label>
            <input type="text" id="name" v-model="name" required />
          </div>
          <div class="form-group">
            <label for="email">อีเมล:</label>
            <input type="email" id="email" v-model="email" required />
          </div>
          <div class="form-group">
            <label for="message">ข้อความ:</label>
            <textarea id="message" v-model="message" required></textarea>
          </div>
          <button type="submit">ส่งข้อความ</button>
        </form>
      </section>
  
      <section class="contact-info">
        <h3>ข้อมูลการติดต่อ</h3>
        <p><strong>ที่อยู่:</strong> 123 ถนนสายหลัก, กรุงเทพมหานคร, ประเทศไทย</p>
        <p><strong>โทร:</strong> 02-123-4567</p>
        <p><strong>อีเมล:</strong> contact@ourwebsite.com</p>
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
        name: '',
        email: '',
        message: '',
      };
    },
    methods: {
      submitForm() {
        if (this.name && this.email && this.message) {
          alert(`ขอบคุณ ${this.name} ที่ส่งข้อความถึงเรา!`);
          // คุณสามารถเพิ่มโค้ดสำหรับการส่งข้อมูลไปยังเซิร์ฟเวอร์ได้ที่นี่
          this.name = '';
          this.email = '';
          this.message = '';
        } else {
          alert('กรุณากรอกข้อมูลให้ครบถ้วน');
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .contact {
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
  
  .contact-form {
    margin: 40px 0;
  }
  
  .contact-form h2 {
    font-size: 2em;
    margin-bottom: 20px;
  }
  
  .form-group {
    margin-bottom: 15px;
    text-align: left;
  }
  
  .form-group label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }
  
  .form-group input, .form-group textarea {
    width: 100%;
    padding: 10px;
    margin: 5px 0 15px 0;
    display: inline-block;
    border: 1px solid #ccc;
    box-sizing: border-box;
  }
  
  button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #007BFF;
    color: white;
    border: none;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  .contact-info {
    margin-top: 40px;
    text-align: left;
    padding: 20px;
  }
  
  footer {
    background-color: #333;
    color: white;
    padding: 10px 0;
    margin-top: 30px;
  }
  </style>
  