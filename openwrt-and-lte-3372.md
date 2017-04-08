اینم یه تجربه پراکنده!

توی [پست]  [قبل] من [OpenWrt] رو معرفی کردم. بعدش هم من پول دادم و یدونه از این روترهای به نسبت ارزون خریدم که usb رو پشتیبانی می‌کرد. بعد از یک سال اینترنت خونه به دلایل عملیاتی بایستی قطع میشد و من رفتم یه مودم lte با مدل [Huawei E3372] خریدم. البته این مودم من [sim lock] ایرانسل هست ولی مدلهای بدون [sim lock] هم وجود داره. 

خیلی ساده می‌تونید که این دستگاه رو راه‌اندازی کنید. کافیه که دوتا پکیج اضافه زیر رو نصب کنید

- kmod-usb-net-cdc-ether
- usb-modeswitch

مودم بصورت معمول توی مد [HiLink] هست که یک کارت شبکه رو شبیه سازی میکنه. پس در نهایت شما یه کارت شبکه جدید دارید که بایستی اون رو به عنوان Wan انتخاب کنید. ایراد مد هایلینک این هست که اگه شما valid ip ثابت روی سیم‌کارتتون داشته باشید نمی‌تونید چیزی رو [port forward] کنید.

حالت دیگه ای که مودم کار میکنه بصورت پورت سریال درمیاد که [at command] قبول میکنه. این مد هم البته قابل راه‌اندازی هست که یکم دردسر داره ولی ممکنه. البته این رو من هنوز امتحان نکردم

امیدوارم به دردتون خورده باشه!


همین!

[پست]:http://blog.abyz.ir/1394/08/openwrt-%d8%a7%d9%88%d9%84%db%8c%d9%86-%d8%a8%d8%b1%d8%ae%d9%88%d8%b1%d8%af/
[قبل]:http://blog.abyz.ir/1394/09/openwrt-%d9%88-%da%a9%d8%a7%d8%b1%d9%87%d8%a7%db%8c-%d8%ac%d8%a7%d9%86%d8%a8%db%8c-%d8%a2%d9%86/
[OpenWrt]:https://en.wikipedia.org/wiki/OpenWrt
[Huawei E3372]:http://consumer.huawei.com/en/mobile-broadband/dongles/tech-specs/e3372.htm
[sim lock]:https://en.wikipedia.org/wiki/SIM_lock
[HiLink]:https://wiki.openwrt.org/doc/recipes/3gdongle
[at command]:https://en.wikipedia.org/wiki/Hayes_command_set
[port forward]:https://en.wikipedia.org/wiki/Port_forwarding
