# 📘 TailwindCSS Comprehensive Summary & Examples

สรุปคุณสมบัติ (Utilities) ของ TailwindCSS ที่ใช้บ่อย พร้อมตัวอย่างการใช้งานจริงแบบละเอียด เพื่อช่วยให้การพัฒนา Web Application รวดเร็วและสวยงามยิ่งขึ้น

---

## 1. Layout (การจัดวางโครงสร้าง)
จัดการโครงสร้างพื้นฐานของ Element และลำดับการแสดงผล

- **Container**: `container` ช่วยจัดกึ่งกลางและกำหนดความกว้างสูงสุดตาม Breakpoints (นิยมใช้คู่กับ `mx-auto`)
- **Display**: 
  - `block`, `inline-block`, `flex`, `grid`, `hidden` (เท่ากับ `display: none`)
- **Position**:
  - `relative`: เป็นฐานให้ลูกที่ใช้ `absolute`
  - `absolute`: วางซ้อนทับ (มักใช้คู่กับ `top-0`, `left-0`, `z-10`)
  - `fixed`: ตรึงไว้กับหน้าจอ (เช่น Navbar)
  - `sticky`: ตรึงไว้เมื่อเลื่อนมาถึง (เช่น Table Header)
- **Z-Index**: `z-0`, `z-10` ... `z-50` (ควบคุมลำดับการซ้อนทับ)

> **💡 ตัวอย่าง: Overlay Card**
> ```html
> <div class="relative w-64 h-40 bg-gray-200 rounded-lg overflow-hidden">
>   <img src="image.jpg" class="w-full h-full object-cover">
>   <div class="absolute inset-0 bg-black bg-opacity-40 flex items-center justify-center">
>     <span class="text-white font-bold">Featured Project</span>
>   </div>
> </div>
> ```

---

## 2. Flexbox & Grid (ระบบการจัดเลย์เอาท์)
หัวใจสำคัญของการทำ Modern Layout

### Flexbox
- `flex`: เริ่มต้นใช้ Flexbox
- `flex-col` / `flex-row`: แนวตั้งหรือแนวนอน
- `justify-between`: เว้นระยะห่างระหว่างไอเทมให้เต็มพื้นที่
- `items-center`: จัดกึ่งกลางแนวตั้ง (Cross Axis)

> **💡 ตัวอย่าง: Navigation Bar**
> ```html
> <nav class="flex justify-between items-center p-4 bg-white shadow">
>   <div class="font-bold text-xl">Logo</div>
>   <ul class="flex space-x-6">
>     <li class="hover:text-blue-500 cursor-pointer">Home</li>
>     <li class="hover:text-blue-500 cursor-pointer">About</li>
>     <li class="hover:text-blue-500 cursor-pointer">Contact</li>
>   </ul>
> </nav>
> ```

### Grid
- `grid-cols-{n}`: กำหนดจำนวนคอลัมน์
- `gap-{n}`: ระยะห่างระหว่างช่อง

> **💡 ตัวอย่าง: Photo Gallery (Responsive Grid)**
> ```html
> <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
>   <div class="bg-blue-100 p-10 text-center">Item 1</div>
>   <div class="bg-blue-100 p-10 text-center">Item 2</div>
>   <div class="bg-blue-100 p-10 text-center">Item 3</div>
>   <div class="bg-blue-100 p-10 text-center">Item 4</div>
> </div>
> ```

---

## 3. Spacing & Sizing (ระยะห่างและขนาด)
Tailwind ใช้ระบบหน่วย 1 หน่วย = 0.25rem (4px)

- **Padding (ภายใน)**: `p-4` (16px รอบด้าน), `px-2` (ซ้าย-ขวา), `py-8` (บน-ล่าง)
- **Margin (ภายนอก)**: `m-4`, `mt-2` (บน), `-mt-4` (Negative margin ก็ทำได้)
- **Width/Height**:
  - `w-full`: กว้าง 100%
  - `w-screen`: กว้างเต็มหน้าจอ Browser
  - `h-64`: สูง 16rem (256px)
  - `max-w-md`: จำกัดความกว้างสูงสุด (นิยมใช้กับ Card หรือ Form)

---

## 4. Typography (การจัดการตัวอักษร)
- **Size**: `text-xs`, `text-base` (ปกติ), `text-2xl`, `text-5xl`
- **Weight**: `font-light`, `font-medium`, `font-bold`, `font-black`
- **Colors**: `text-slate-700`, `text-indigo-600`
- **Leading & Tracking**:
  - `leading-tight`: ระยะห่างระหว่างบรรทัดน้อย
  - `tracking-widest`: ระยะห่างระหว่างตัวอักษรมาก

---

## 5. Effects & Interactivity (เอฟเฟกต์และการตอบสนอง)
- **Rounded**: `rounded-md` (มุมโค้งเล็กน้อย), `rounded-full` (วงกลม/วงรี)
- **Shadow**: `shadow-sm`, `shadow-lg` (เงาลึก), `shadow-inner` (เงาด้านใน)
- **States (สำคัญมาก)**:
  - `hover:`: เมื่อเมาส์ชี้
  - `focus:`: เมื่อคลิกเลือก (เช่น Input)
  - `active:`: เมื่อกำลังกดปุ่ม
  - `group-hover:`: สั่งให้ลูกเปลี่ยนสีเมื่อ Hover ที่ตัวแม่

> **💡 ตัวอย่าง: Interactive Button**
> ```html
> <button class="bg-blue-600 text-white px-6 py-2 rounded-lg 
>                hover:bg-blue-700 active:scale-95 transition-all 
>                focus:ring-4 focus:ring-blue-300 outline-none">
>   Click Me
> </button>
> ```

---

## 6. Responsive Design (Mobile-First)
Tailwind บังคับใช้หลักการ **Mobile-First** (เขียนโค้ดสำหรับมือถือก่อน แล้วค่อยขยาย)

- `sm:` (640px)
- `md:` (768px)
- `lg:` (1024px)
- `xl:` (1280px)

> **💡 ตัวอย่าง: Responsive Text**
> ```html
> <h1 class="text-xl md:text-3xl lg:text-5xl font-bold">
>   Hello Responsive World!
> </h1>
> ```

---

## 7. Customization (tailwind.config.js)
เราสามารถกำหนดสี หรือระยะห่างส่วนตัวได้ที่ไฟล์ Config

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        'brand-primary': '#1da1f2', // สร้างชื่อสีใหม่
      },
      spacing: {
        '128': '32rem', // เพิ่มขนาดความกว้างใหม่
      }
    }
  }
}
```
*การใช้: `bg-brand-primary` หรือ `w-128`*

---

## 8. Common Components (ตัวอย่างคอมโพเนนต์ที่ใช้บ่อย)

### Modern Profile Card
```html
<div class="max-w-sm mx-auto bg-white rounded-xl shadow-md overflow-hidden md:max-w-2xl">
  <div class="md:flex">
    <div class="md:shrink-0">
      <img class="h-48 w-full object-cover md:h-full md:w-48" src="profile.jpg" alt="Profile">
    </div>
    <div class="p-8">
      <div class="uppercase tracking-wide text-sm text-indigo-500 font-semibold">User Profile</div>
      <a href="#" class="block mt-1 text-lg leading-tight font-medium text-black hover:underline">Jane Doe</a>
      <p class="mt-2 text-slate-500">Software Engineer specialized in TailwindCSS and React development.</p>
    </div>
  </div>
</div>
```

---
*จัดทำขึ้นเพื่อเป็นสรุปประกอบการเรียนรู้ TailwindCSS เบื้องต้น*
