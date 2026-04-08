git restore — সবচেয়ে নিরাপদ ও সাধারণ কাজের জন্য
এটা শুধু ফাইলের পরিবর্তন undo করে।
Commit হয়নি এমন কাজ নষ্ট করার জন্য ব্যবহার করো।
সাধারণ কমান্ড:
git restore filename.txt → working directory থেকে পরিবর্তন মুছে আগের অবস্থায় ফিরিয়ে দেয়।
git restore --staged filename.txt → staged (add করা) ফাইল unstaged করে (কিন্তু পরিবর্তন থেকে যায়)।
git restore . → সব ফাইল restore করে।
কখন ব্যবহার করবে?
তুমি কিছু কোড লিখেছো, কিন্তু ভালো লাগছে না, আবার আগের অবস্থায় ফিরে যেতে চাও — তাহলে restore।
