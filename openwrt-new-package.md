اینم یه تجربه پراکنده!

توی [پست]  [قبل] من [OpenWrt] رو [معرفی] کردم. بعد از یه مدت متوجه شدم که یه پروژه جدید به نام [LEDE] ایجاد شده که انگار همونه و الان حدود ۲ سال هست که [OpenWrt] زیاد بروزرسانی نمی‌شه. حالا با توجه به علاقه‌ام به کارهای نزدیک سخت‌افزار و مسائل مرتبط به [cross compile] سعی کردم که کل [OpenWrt] رو کامپایل کنم و سعی کنم یه پکیج جدید بهش اضافه کنم.

البته پکیجی که من دنبالش بودم [tun2socks] بود که پکیجش بصورت غیر رسمی وجود داشت. کاری که من کردم این بود که آدرس‌ها رو عوض کردم و یادگرفتم که چطور میتونم اون رو برای روترم کامپایل کنم. نتیجه کار من رو میتونید توی [گیت‌هاب من] پیدا کنید

روند کار به ترتیب اینجوریه که:

1. اول سورس کد رو با گیت از گیت‌هاب میگیرید
2. دوم با توجه به راهنمای آنلاین تمام پکیج‌ها رو دانلود میکنید
3. پکیج رو اضافه می‌کنید
3. با استفاده از `make menuconfig` نوع معماری سیستم و نوع دستگاه و پکیج‌ها رو انتخاب می‌کنید
4. و از ابتدا کامپایلر و کل لینوکس و پکیج رو کامپایل میکنید

پینشهاد میکنم که برای شروع اینها بخونید:

- شروع به کار برای [کامپایل LEDE]
- نمونه از [یک پکیج]



امیدوارم به دردتون خورده باشه!


همین!

[پست]:http://blog.abyz.ir/1394/08/openwrt-%d8%a7%d9%88%d9%84%db%8c%d9%86-%d8%a8%d8%b1%d8%ae%d9%88%d8%b1%d8%af/
[قبل]:http://blog.abyz.ir/1394/09/openwrt-%d9%88-%da%a9%d8%a7%d8%b1%d9%87%d8%a7%db%8c-%d8%ac%d8%a7%d9%86%d8%a8%db%8c-%d8%a2%d9%86/
[معرفی]:http://blog.abyz.ir/1396/01/openwrt-%d9%88-%d9%85%d9%88%d8%af%d9%85-lte/
[گیت‌هاب من]:https://github.com/yazdan/tun2socks-Openwrt
[کامپایل LEDE]:https://lede-project.org/docs/guide-developer/quickstart-build-images
[یک پکیج]:https://github.com/mwarning/lede-examples

[LEDE]:https://lede-project.org/
[OpenWrt]:https://en.wikipedia.org/wiki/OpenWrt
[cross compile]:https://en.wikipedia.org/wiki/Cross_compiler
[tun2socks]:https://github.com/ambrop72/badvpn/wiki/Tun2socks
