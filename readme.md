# 👨🏻‍🏫 Long Sorn (ลองสอน)

> **Super AI Innovation**
>**Team Members:**
- "**Kiadtisak Preechanon** -  "         
- "**Kittiphat Noikate**    - ??? "
- "**Suphawadi Poolpuang**  - ??? "
- "**Saranwich Pochai**     - ??? "
- "**Krittikorn Sangthong** - ??? "

---

```
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
📝 Long-Sorn project:
│
├── 📁.github/
│   └── 📁workflows/
│       ├── frontend_deploy.yml                 // CI/CD: Deploy Frontend ไปยัง Vercel 
│       ├── backend_ci.yml                      // CI: รันเทสสำหรับ Backend ทุก service 
│       └── backend_deploy.yml                  // CD: Deploy Backend ไปยัง OCI VM 
│
├── 📁backend/                                  // โฟลเดอร์หลักสำหรับ Server-side ทั้งหมด 
│   │
│   ├── 📁services/                             // ที่เก็บโค้ดของแต่ละ Microservice 
│   │   │
│   │   ├── 📁api_server/                       // Main API (FastAPI) - [ดูแลโดย: API & DB Dev] 
│   │   │   ├── 📁app/                          // Source code หลัก 
│   │   │   │   ├── 📁routers/                  // แยกไฟล์ตามกลุ่มของ API เช่น users.py, videos.py 
│   │   │   │   ├── 📁core/                     //  จัดการ Config และการตั้งค่าต่างๆ
│   │   │   │   └── main.py                     //  จุดเริ่มต้นของแอป FastAPI 
│   │   │   ├── 📁tests/                        //  ที่เก็บเทสสำหรับ API service นี้ 
│   │   │   ├── Dockerfile                      //  ไฟล์สำหรับสร้าง Container 
│   │   │   └── requirements.txt                //  รายการ Library ของ Python 
│   │   │
│   │   ├── 📁video_worker/                     // Service ประมวลผลวิดีโอ - [ดูแลโดย: AI Dev] 
│   │   │   ├── 📁app/
│   │   │   │   ├── processor.py                //  Logic หลักในการใช้ FFmpeg 
│   │   │   │   └── main.py                     //  จุดเริ่มต้นในการดึงงานจาก Queue 
│   │   │   ├── Dockerfile 
│   │   │   └── requirements.txt 
│   │   │
│   │   └── 📁ai_orchestrator/                  // Service จัดการ AI - [ดูแลโดย: AI Dev] 
│   │       ├── 📁app/
│   │       │   ├── 📁services/                 //  Logic การเรียก AI ภายนอก (Google STT, Gemini) 
│   │       │   ├── nlp_custom.py               //  Logic NLP เฉพาะของโปรเจกต์ 
│   │       │   └── main.py                     //  จุดเริ่มต้นของ AI service 
│   │       ├── Dockerfile 
│   │       └── requirements.txt 
│   │
│   └── 📁shared/                               // โค้ด Python ที่ใช้ร่วมกันใน Backend 
│       ├── 📁db/                               //  จัดการการเชื่อมต่อ Database 
│       ├── 📁models/                           //  Pydantic Models สำหรับกำหนดโครงสร้างข้อมูลที่รับ-ส่ง 
│       └── 📁core/                             //  Config หลัก เช่น การโหลด .env 
│
├── 📁database/                                 // จัดการ Schema และ Migration ของฐานข้อมูล 
│   └── 📁migrations/                           //  เก็บไฟล์ Migration script (เช่น Alembic) 
│
├── 📁docs/                                     // เอกสารทั้งหมดของโปรเจกต์ 
│   ├── architecture.png                        //  แผนภาพสถาปัตยกรรม 
│   └── api_endpoints.md                        //  คำอธิบาย API endpoint 
│
├── 📁frontend/                                 // โฟลเดอร์หลักสำหรับ Next.js 
│   ├── 📁public/                               //  เก็บไฟล์ static เช่น รูปภาพ, font 
│   ├── 📁src/                                  //  Source code หลักของ Frontend 
│   │   ├── 📁app/                              //  (App Router) 
│   │   ├── 📁components/                       //  React Components ที่ใช้ซ้ำ 
│   │   │   ├── 📁ui/                           //  _// Dumb Components (Button, Input) - [ดูแลโดย: UX/UI Dev]_
│   │   │   └── 📁features/                     //  _// Smart Components (ProfileForm) - [ดูแลโดย: Prog Dev]_
│   │   ├── 📁hooks/                            //  Custom React hooks 
│   │   └── 📁lib/                              //  ฟังก์ชันช่วยเหลือ, API clients 
│   │
│   ├── 📁__tests__/                            //  ที่เก็บเทสของฝั่ง Frontend 
│   ├── next.config.mjs                         //  _// แก้ไขจาก .js เพื่อรองรับ ES Module ในเวอร์ชันใหม่_
│   ├── package.json                            //  Dependencies และ script ของโปรเจกต์ 
│   ├── tailwind.config.ts                      //  _// ใช้ .ts เพื่อให้ type-safe ยิ่งขึ้น_
│   └── tsconfig.json                           //  _// ไฟล์ตั้งค่า TypeScript_
│
├── .gitignore                                  //  ไฟล์และโฟลเดอร์ที่ Git จะไม่ติดตาม 
├── docker-compose.yml                          //  ใช้สำหรับรัน Backend ทั้งหมดในเครื่อง local ด้วยคำสั่งเดียว 
└── README.md                                   //  ภาพรวมและข้อมูลโปรเจกต์ 
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────