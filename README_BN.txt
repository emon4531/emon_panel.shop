EMON RESELLER PANEL — LIVE ADMIN SETUP (বাংলা)

এই প্যাকেজে আছে:
- index.html: কাস্টমার ওয়েবসাইট; অনলাইন Supabase ডেটাবেস থেকে প্রোডাক্ট/দাম পড়বে।
- admin.html: Supabase Auth লগইন; দাম/নাম/মেয়াদ পরিবর্তন, নতুন প্রোডাক্ট, delete, backup import/export।
- config.js: Supabase Project URL, anon/publishable key, Admin email বসানোর জায়গা।
- supabase_setup.sql: টেবিল, RLS নীতি, এবং বর্তমান 66টি প্রোডাক্টের প্রাথমিক ডেটা।

গুরুত্বপূর্ণ: ZIP আপলোড করলেই একা কাজ করবে না। একবার Supabase সেটআপ করতে হবে।

ধাপ ১ — Supabase project তৈরি করুন।
ধাপ ২ — Authentication > Users থেকে আপনার নিজের ইমেইল দিয়ে একটি user তৈরি করুন; email confirmed করে দিন। এই user-টাই একমাত্র Admin হবে। Password হিসেবে শক্তিশালী পাসওয়ার্ড ব্যবহার করুন; আগের emon00100 পাসওয়ার্ডটি দুর্বল, তাই বদলানো ভালো। Username emon420 থাকবে; login screen-এ ওই username এবং Supabase user-এর password ব্যবহার করবেন।
ধাপ ৩ — ওই user-এর ইমেইল কপি করুন। supabase_setup.sql খুলে admin@example.com দু জায়গায় সেই ইমেইল দিয়ে replace করুন। তারপর Supabase > SQL Editor-এ পুরো SQL paste করে Run দিন।
ধাপ ৪ — Supabase Project Settings > API (বা Connect) থেকে Project URL এবং anon/public/publishable key কপি করুন। SERVICE_ROLE/secret key কখনো ব্যবহার করবেন না।
ধাপ ৫ — config.js-এ YOUR_SUPABASE_PROJECT_URL, YOUR_SUPABASE_ANON_OR_PUBLISHABLE_KEY, YOUR_ADMIN_EMAIL_USED_IN_SUPABASE_AUTH—এই placeholders বদলান।
ধাপ ৬ — GitHub repo root-এ index.html, admin.html, config.js তিনটি ফাইল upload/replace করুন। SQL file repo-তে আপলোড করার দরকার নেই।
ধাপ ৭ — https://emon4531.github.io/emon-reseller-panel/admin.html খুলুন; username emon420 এবং Supabase Auth-এ সেট করা password দিয়ে login করুন।

এরপর Admin-এ Save করলে ডেটাবেসে সেভ হবে এবং ওয়েবসাইটে ঢোকা সব দর্শক একই নতুন দাম দেখবে (পেজ refresh/নতুন করে ঢোকার পর)।

SECURITY: anon key frontend-এ প্রকাশ করা স্বাভাবিক; service_role key কখনো প্রকাশ করবেন না। SQL policy শুধু config.js-এ নির্দিষ্ট করা Admin email-কে update করতে দেয়। Admin user-এর password কাউকে দেবেন না।
