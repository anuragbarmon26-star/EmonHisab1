# EMON হিসাব

একটি সম্পূর্ণ অফলাইন Android দৈনন্দিন হিসাব (আয়-ব্যয়) অ্যাপ।

## ফিচার সমূহ
- আয় ও খরচ যোগ করা
- আজকের মোট আয়, আজকের মোট খরচ, বর্তমান ব্যালেন্স
- মাসিক হিসাব (মাস অনুযায়ী আয়/খরচ ব্রাউজ করা)
- খরচ/আয়ের ক্যাটাগরি নির্বাচন
- প্রতিটি হিসাবে তারিখ ও সময়
- হিসাব Edit ও Delete করার সুবিধা
- সহজ বাংলা UI (বাংলা সংখ্যা ও মাসের নাম সহ)
- সম্পূর্ণ অফলাইন — সব ডাটা ফোনের লোকাল ডাটাবেজে (Room/SQLite) সংরক্ষিত হয়, ইন্টারনেট প্রয়োজন নেই

## প্রযুক্তি
- Kotlin
- Jetpack Compose (Material 3)
- Room Database (লোকাল স্টোরেজ)

## যেভাবে বিল্ড করবেন (APK তৈরি করবেন)

1. [Android Studio](https://developer.android.com/studio) ইনস্টল করুন (সর্বশেষ ভার্সন)।
2. এই `EmonHisab` ফোল্ডারটি Android Studio দিয়ে **Open** করুন (`File > Open`)।
3. প্রথমবার Gradle sync হতে কিছুটা সময় লাগবে (ইন্টারনেট প্রয়োজন শুধু এই ধাপে, নির্ভরতা ডাউনলোডের জন্য)।
4. উপরে ডিভাইস/এমুলেটর নির্বাচন করে ▶ (Run) বাটনে চাপুন — সরাসরি ফোনে/এমুলেটরে চলবে।
5. ইনস্টলযোগ্য APK পেতে: `Build > Build Bundle(s) / APK(s) > Build APK(s)` — তৈরি হওয়া APK পাবেন
   `app/build/outputs/apk/debug/app-debug.apk` এই পাথে। এটি যেকোনো Android ফোনে (Android 7.0+) ইনস্টল করা যাবে।

## প্রোজেক্ট স্ট্রাকচার
```
app/src/main/java/com/emon/hisab/
├── MainActivity.kt          # অ্যাপের প্রবেশদ্বার ও নেভিগেশন
├── data/
│   ├── Transaction.kt        # ডাটা মডেল ও ক্যাটাগরি তালিকা
│   ├── TransactionDao.kt     # ডাটাবেজ কোয়েরি
│   └── AppDatabase.kt        # Room ডাটাবেজ সেটআপ
└── ui/
    ├── HisabViewModel.kt     # বিজনেস লজিক
    ├── HomeScreen.kt         # হোম স্ক্রিন (আজকের হিসাব)
    ├── MonthlyScreen.kt      # মাসিক হিসাব স্ক্রিন
    ├── AddEditSheet.kt       # আয়/খরচ যোগ ও এডিট ফর্ম
    └── Formatting.kt         # বাংলা সংখ্যা/তারিখ ফরম্যাটিং
```

## ইচ্ছেমতো পরিবর্তন
- ক্যাটাগরি তালিকা পরিবর্তন করতে `data/Transaction.kt` ফাইলের `Categories` অবজেক্ট এডিট করুন।
- রঙ পরিবর্তন করতে `ui/HomeScreen.kt` ও `ui/MonthlyScreen.kt`-এ Color কোডগুলো এডিট করুন।
- অ্যাপ আইকন যোগ করতে Android Studio-এর `Image Asset Studio` ব্যবহার করুন
  (`res` ফোল্ডারে right-click > New > Image Asset)।
