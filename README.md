# PostgreSQL

1️⃣ PostgreSQL কী?
PostgreSQL একটি শক্তিশালী, ওপেন সোর্স রিলেশনাল ডাটাবেজ ম্যানেজমেন্ট সিস্টেম (RDBMS), যেটি SQL (Structured Query Language) এবং আরও অনেক আধুনিক ডেটা ফিচার সাপোর্ট করে। এটি ACID কমপ্লায়েন্ট এবং বড় আকারের অ্যাপ্লিকেশনের জন্য উপযুক্ত।

🔍 উদাহরণ:

CREATE DATABASE myapp;
PostgreSQL ব্যবহার করে আপনি ডেটা সংরক্ষণ, অনুসন্ধান, আপডেট এবং বিশ্লেষণ করতে পারেন। এটি JSON, ARRAY, এবং CUSTOM TYPES-এর মতো অ্যাডভান্স ফিচারও সাপোর্ট করে।

2️⃣ PostgreSQL-এ একটি ডেটাবেজ স্কিমার উদ্দেশ্য কী?
একটি স্কিমা হল ডেটাবেজের ভিতরের একটি যুক্তিসংগত কাঠামো যেখানে টেবিল, ভিউ, ফাংশন ইত্যাদি সংগঠিত করা যায় । এটি ডেটা আলাদা ও সুরক্ষিত রাখতে সাহায্য করে এবং একই ডাটাবেজে বিভিন্ন ইউজারের জন্য আলাদা কাঠামো তৈরি করতে দেয়।

🔍 উদাহরণ:

CREATE SCHEMA wildlife;
এরপর টেবিল তৈরি:

CREATE TABLE wildlife.rangers (
  ranger_id SERIAL PRIMARY KEY,
  name VARCHAR(100)
);
এভাবে একাধিক স্কিমা ব্যবহার করে একই ডাটাবেজে আলাদা মডিউল বা ডিপার্টমেন্টের ডেটা আলাদা রাখা যায় ।

3️⃣ Primary Key এবং Foreign Key-এর ব্যাখ্যা দিন।
Primary Key: একটি টেবিলের এমন একটি কলাম যা ইউনিক এবং নাল নয়। এটি প্রতিটি রেকর্ডকে আলাদাভাবে সনাক্ত করে।

🔍 উদাহরণ:

CREATE TABLE species (
  species_id SERIAL PRIMARY KEY,
  common_name VARCHAR(100)
);
Foreign Key: অন্য একটি টেবিলের Primary Key-কে রেফারেন্স করে এবং সম্পর্ক তৈরি করে।

🔍 উদাহরণ:


CREATE TABLE sightings (
  sighting_id SERIAL PRIMARY KEY,
  species_id INT REFERENCES species(species_id)
);
এই সম্পর্ক নিশ্চিত করে যে এমন কোনো species_id ইনসার্ট করা যায় না যা species টেবিলে নেই।

4️⃣ VARCHAR এবং CHAR ডেটা টাইপের মধ্যে পার্থক্য কী?
CHAR(n): নির্দিষ্ট দৈর্ঘ্যের ফিক্সড-লেংথ স্ট্রিং। যদি ডেটা ছোট হয়, তাহলে এটি অটোমেটিকালি বাকি অংশ ফাঁকা (padding) দিয়ে পূরণ করে।

VARCHAR(n): ভ্যারিয়েবল লেংথের স্ট্রিং যেখানে যতটুকু ইনপুট দেওয়া হয়, ততটুকু জায়গা ব্যবহার হয়।

🔍 তুলনা:

name CHAR(10);   -- 'Bob      ' → 10 characters
name VARCHAR(10);-- 'Bob'       → 3 characters
VARCHAR মেমোরি-সাশ্রয়ী এবং বেশি ব্যবহারযোগ্য।

5️⃣ SELECT স্টেটমেন্টে WHERE ক্লজের কাজ কী?
WHERE ক্লজ ব্যবহার করে নির্দিষ্ট শর্ত অনুযায়ী রেকর্ডগুলো ফিল্টার করা যায়।

🔍 উদাহরণ:


SELECT * FROM species
WHERE conservation_status = 'Endangered';
এই কোয়েরি শুধু সেই species গুলো দেখাবে যেগুলোর স্ট্যাটাস "Endangered"।

WHERE ক্লজ ছাড়া সব রেকর্ড ফেরত আসে — তাই এটি বিশ্লেষণ ও রিপোর্ট তৈরিতে অত্যন্ত গুরুত্বপূর্ণ।
