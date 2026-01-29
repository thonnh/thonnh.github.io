---
layout: default
title: Home
---

<div class="profile-img" style="background-image: url('IMG.png');"></div>

.profile-img {
  /* 1. กำหนดขนาดกรอบวงกลม */
  width: 200px;  /* ปรับขนาดตามต้องการ */
  height: 200px;
  border-radius: 50%;
  /* จัดให้อยู่กึ่งกลางหน้าเว็บ (ถ้าจำเป็น) */
  margin: 0 auto;

  /* 2. ตั้งค่ารูปพื้นหลัง */
  background-position: center 25%; /* เลื่อนตำแหน่งโฟกัส (แกน X กึ่งกลาง, แกน Y ต่ำลงมา 25%) */
  background-repeat: no-repeat;

  /* --- พระเอกตัวจริงอยู่ตรงนี้ --- */
  /* ถ้าใส่ 100% คือพอดีกรอบ (เหมือน cover) */
  /* ถ้าอยากซูม ให้ใส่ค่ามากกว่า 100% ยิ่งเยอะยิ่งซูม */
  background-size: 160%;  /* <--- ลองปรับเลขนี้ดูครับ เช่น 150%, 180%, 200% */
}

# Thonn Homsnit

### About Me
Hi, I'm Thonn. I am a researcher interested in **Physics-Informed Neural Networks (PINNs)** and computational mechanics. Currently working on Euler-Bernoulli beam problems.

