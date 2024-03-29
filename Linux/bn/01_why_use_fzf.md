# Why Use FZF(The Ultimate Command Line Tool For Fuzzy Finder)

---

ফাজি ফাইন্ডারের টিউটরিয়ালে আপনাকে স্বাগতম। এখানে আমরা শেখাবো কিভাবে আপনি ফাজি ফাইন্ডার ব্যবহার করবেন? কেন ব্যবহার করবেন? আপনি ফাইল ম্যনাজার ছাড়াই একজন দক্ষ প্রোগ্রামারের মতো কিভাবে ফাইল খুঁজে বের করবেন? কমান্ড হিস্টোরি কিভাবে খুঁজে পাবেন? এসএসএইচ এর হোস্টনেম খুঁজে পাওয়া, প্রসেস কিল করা, ইনস্ট্যান্ট ফাইল প্রিভিইউ এবং তার সাথে সিনট্যাক্স হাইলাইট করা সব কিছু পাবেন ফাজি ফাইন্ডারে। এই ফাজি ফাইন্ডার আপনাকে কাজে দিতে পারে বিভিন্ন যায়গায়। চলুন তাহলে কথা না বাড়িয়ে কাজ শুরু করা যাক।

ফাইল খুঁজে বের করাঃ
আপনারা যারা ইউনিক্স বেসড ওপারেটিং সিস্টেম(লিনাক্স/ম্যাক) ব্যবহার করেন তারা জানেন ইউনিক্স সিস্টেমে ফিল্টার বলতে একটা টপিক আছে। ফিল্টার বা পাইপলাইন ব্যবহার করে একই সাথে অনেকগুলো প্রোগ্রাম ব্যবহার করা যায়। যেমনঃ প্রোগ্রাম ১ | প্রোগ্রাম ২ | প্রোগ্রাম ৩, এখানে, প্রোগ্রাম ১ রান করার পরে যে আউটপুট পাওয়া যাবে, তা প্রোগ্রাম ২ তে ইনপুট হিসেবে যাবে আবার একই ভাবে, প্রোগ্রাম ২ থেকে যা আউটপুট পাওয়া যাবে তা কিনা প্রোগ্রাম ৩ এ ইনপুট হিসেবে যাবে। এইভাবে ৩ টা প্রোগ্রাম একই সাথে কাজ করবে। ফাইনালি আমরা আমাদের আউটপুট পাবো। চলুন একটা ভালো উদাহরণ দেয়া যাকঃ

```bash
yes | head -10 | awk '{ print NR, NR%2==0?"even":"odd"}'
```

এখানে প্রতিটা প্রোগ্রাম ফিল্টারের মতো কাজ করেছে। একইভাবে FZF হলো ইউনিক্সের আরও একটি ফিল্টার। এটা stdin থেকে লাইন পড়ে, একটা ইন্টারেক্টিভ ফাইন্ডার ডাইলগ ওপেন করে, আর সিলেক্টেড আইটেমগুলোকে stdout এ প্রিন্ট করে ফেলে। এই প্রোগ্রামের সাথে GNU এর Find প্রোগ্রামের মিল থাকলেও এটাতে যে ইন্টারেক্টিভ ফাইন্ডার আছে যা লেখার সাথে সাথে ফিল্টার করা শুরু করে, কিন্তু Find প্রোগ্রামে তা নেই। এই কারণে FZF অনন্য।

fzf দিয়ে কমান্ড লাইনে ফাইল এবং সে কোথায় আছে, তার পাথ খুঁজে বের করা হয়। যেহেতু এতে ইন্টারেক্টিভ ফাইন্ডার আছে, তাই কয়েক সেকেন্ডের মাঝেই যে ফাইল খুজতেছি সেটা খুঁজে পাওয়া যায়।

fzf ফাজি ম্যাচ করে ফাইল খোজার সময়, মানে হলো আপনি কয়েকটা ক্যারেক্টার লিখতে লিখতেই হয়তো ফাইল পেয়ে যাবেন। এইটা হলো ফাজি ম্যাচিং আবার এইটা এক্স্যাক্ট ম্যাচিংও করে থাকে। যদি আপনি fzf ব্যবহার করে এক্স্যাক্ট ম্যাচ খুঁজে পেতে চান, তাহলে, আপনি সিঙ্গেল কোটেশন ব্যবহার করে নাম দিতে পারেন, তাহলে এক্স্যাক্ট ম্যাচ খুঁজবে কিংবা আপনি চাইলে, `fzf --exact ` দিয়ে রান করেতে পারেন, তাহলেও এক্স্যাক্ট ম্যাচ খুঁজে দিবে।

FZF ফাজি ফাইন্ডার হলেও কিন্তু ইনি রেগুলার এক্সপ্রেশন কিংবা গ্লোব সাপোর্ট করেন না, সুতরাং, আপনি যদি `*.sh` প্যাটার্ন দিয়ে খোজার চেষ্টা করেন তাহলে হয়ত এইটা কাজই করবে না। আমাদের টার্গেট প্রোডাক্টিভিটি এবং কাজের স্পিড, আপাতত কঠিন কঠিন রেগুলার এক্সপ্রেশন নিয়ে ভাবার সময় নেই। এত ঝামেলার থেকে শুধু যা খুজতেছেন তার কয়েকটি ওয়ার্ড লিখতে পারলেই পাওয়া যাবে সেটা কোথায় আছে। এর পরেও না হলে, `^` দিয়ে কোনো শব্দের নাম শুরু করতে পারেন আর শেষ করবেন `$` দিয়ে। `!` দিয়ে আপনি ম্যাচিংটা ডিলেট করতে ব্যবহার করতে পারেন।

আপনি যে ফাইল খুঁজে পেয়েছেন, সেইটা কমান্ড লাইনে প্রিন্ট করে সব সময় লাভ হবে না। হয়ত, আমার দরকার ফাইলটিকে `vim` দিয়ে ওপেন করা অথবা আমি চাই, সেইটাকে পাইপ দিয়ে অন্য কোনো প্রোগ্রামে ইনপুট দিতে। যেইভাবে করতে পারি, তাহলোঃ

```bash
# open file in vim
vim -o `fzf`
```

```bash
# print info for each selected file
fzf | xargs ls -l
```

ফাজি কমপ্লিট bash এবং zsh এর জন্যঃ
যদি ফাজি ফাইন্ডারকে টার্মিনাল থেকে রান করাতে চাই, তাহলে আমরা সাধারণত `fzf` কমান্ড দিয়েই রান করাতে পারি। কিন্তু আমি চাই, `**` দিয়ে `TAB` বাটন প্রেস করলেই ফাজি ফাইন্ডার চালু হবে। এইভাবে ব্যবহার করলে মনে হবে, ন্যাটিভ টার্মিনাল ব্যবহার করতেছি, ফাজি ফাইন্ডার মাঝে থেকে এসে চালু হয়ে কাজ করে দিয়ে যাচ্ছে বোঝারই উপায় থাকবে না।

```COMMAND [DIRECTORY/][FUZZY_PATTERN]**<TAB>```

ডিরেক্টরি চেঞ্জ করার সময়েও চাইলে এই ফাজি ফাইন্ডারকে ব্যবহার করা যেতে পারে।
কমান্ড হিস্টোরি দেখার সময়েও একইভাবে ফাজি ফাইন্ডার ব্যবহার করা যেতে পারে।
ssh ** দিয়ে চাইলে লাস্ট ব্যবহারকৃত আইপি এড্রেস থেকে হোস্টানেমগুলো দিয়ে দিতে পারে যেগুলো আপনি `~/.ssh/config` এর মধ্যে রেখে দিয়েছেন।

কোন একটা প্রসেসকে যদি কোনো টাইপের সিগনাল পাঠানোর দরকার হয়, তাহলে সেই প্রসেস এর PID জানা দরকার। PID ছাড়া কোনো process এর কাছে কোন সিগনাল পাঠানো কঠিন হতে পারে। সাধারণত, `pgrep <process_name>` ব্যবহার করা হয়, pid খুঁজে পাওয়ার জন্য। `fzf` এইখানেও ব্যবহার করা যেতে পারে, যেমনঃ `kill` লিখে ট্যাব প্রেস করে যদি আমরা লিস্ট করি কতগুলো প্রসেস আছে, তাহলে সেটা কিনা `fzf` দিয়ে দেখাবে, যেটা কিনা অনেকাংশে `Activity Monitor` এর মতো কাজ করবে।

চাইলে ফাইল খোজার পাশাপাশি ফাইলের মধ্যে যা আছে, তার একটা প্রিভিও ও দেখা সম্ভব। সাধারণত এইটা বন্ধ করা থাকে, তবে আপনি চাইলে এইটাকে চালু রাখতে পারেন এবং ফাইল প্রিভিও দেখার জন্য `bat` টুল ব্যবহার করতে পারেন। এই টুল ব্যবহার করলে ফাইল প্রিভিউ এর পাশাপাশি কালার আউটপুট এবং সিনট্যাক্স হাইলাইট দেখাবে।

