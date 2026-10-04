AUTO PARTS MANAGER — Standalone App (Firebase)
================================================

YEH APP KAISE USE KAREIN
-------------------------
1. "auto-parts-app.html" file ko seedha kisi bhi mobile/computer ke browser me kholein
   (double-tap karke, ya Chrome me File > Open se).
2. Isko kisi bhi free hosting pe daal sakte ho (Netlify, GitHub Pages, Firebase Hosting)
   taaki ek chhota link ban jaye jo sabko bhej sako — ya seedha file WhatsApp se bhi
   bhej sakte ho, har staff apne phone me file kholke "Add to Home Screen" kar le.
3. Pehli baar kholne par Admin PIN set karna hoga — Settings me jaake Staff add karo.

ZAROORI: FIRESTORE SECURITY RULES SET KARNA
---------------------------------------------
Firebase "test mode" sirf 30 din tak free access deta hai, uske baad data read/write
band ho jayega jab tak rules na badlo. Isliye abhi yeh steps zaroor karo:

1. https://console.firebase.google.com par apna project ("Auto Parts Shop") kholo
2. Build → Firestore Database → upar "Rules" tab par jao
3. Jo bhi likha hai usse hata ke neeche wala paste karo:

   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /{document=**} {
         allow read, write: if true;
       }
     }
   }

4. "Publish" button dabao

NOTE: Yeh rule sabke liye open rakhta hai (kyunki app apna khud ka PIN login use
karta hai, Firebase ka login nahi) — isliye firebaseConfig/link kisi aise insaan ko
mat bhejna jisse aap data access nahi dena chahte. Chhoti dukaan ke internal use
ke liye yeh theek hai.

AGAR AAGE FREE LIMIT KHATAM HO JAYE
-------------------------------------
Firebase ka free (Spark) plan roz ka ek limit deta hai (50,000 reads/writes/din) —
ek chhoti dukaan ke liye yeh kaafi zyada hai, chinta ki baat nahi.

Koi dikkat aaye to wahi screenshot/error message bhej dena, main fix kar dunga.
