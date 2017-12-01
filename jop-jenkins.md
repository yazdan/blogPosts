اینم یه تجربه پراکنده دیگه!

خب حدودا سه سال قبل من از جای خالی [continues integration] نوشتم. حالا حدود بعد از سه سال میخوام دوباره به موضوع رجوع کنم و درباره [jenkins] بنویسم

توی این سه سال اتفاقات زیادی افتاده. ما روند build رو با استفاده از [cmake] بهتر کردیم. یادگرفتیم که چی به چیه. حدودا انتهای سال قبل بود که توی شرکت منابع و علم کافی برای پیاده‌سازی روند ci بوجود اومد و ما شروع کردیم به استفاده از [jenkins]. 

نصب و راه‌اندازی [jenkins] به نسبت آسون و راحت بود. کاری که [jenkins] برای ما میکرد این بود که به یه دلیلی(بخونید ماشه) شروع به کامپایل کد میکرد. روند کامپایل هم آسون بود. یعنی اینکه یه سری پروژه معمول رو میشناسه مثل [cmake], [make], [gradle], [maven] داره که کار رو راحت میکنه

ما اول به یه پروژه معمولی که بصورت ساعتی اجرا میشد شروع کردیم فقط نکتش اینه که ما با سخت‌افزارهای مختلف کار میکنیم و این تنها برای یکی از سخت‌افزارهامون کار میکرد. بعدش یه پروژه معمولی دیگه اضافه کردم که با [cppcheck] کار [static analysis] رو روی کدمون بصورت ساعتی انجام میداد. 

در مرحله بعد با استفاده امکانی از [jenkins pipeline] تمامی سخت‌افزارها رو باهم کامپایل کردیم و [cppcheck] هم به عنوان یک مرحله از این خط لوله ما انتخاب شد.

در قدم بعدی هم این ماجرا رو به [git] وصل کردیم و به ازای هر کامیت یا هر درخواست بررسی که روی کدمون انجام میدیم شروع به کامپایل میکنه و ما میدونیم که دیگه تغییرمون چیزی رو خراب نمیکنه.

در قدم‌های بعدی میخوایم تست اتوماتیک و تست روی سخت‌افزار رو هم پیاده کنیم که اون داستان‌های خودش رو داره. ما آهسته و پیوسته حرکت کردیم تا به این نقطه رسیدیم. شاید کند بودیم شاید هم خوب عمل کردیم ولی خوبیش اینه که راه روشنی پیش رو داریم.

فعلا همین!


[continues integration]:https://en.wikipedia.org/wiki/Continuous_integration
[jenkins]:https://en.wikipedia.org/wiki/Jenkins_(software)
[cmake]:https://en.wikipedia.org/wiki/CMake
[make]: https://en.wikipedia.org/wiki/Make_(software)
[gradle]: https://en.wikipedia.org/wiki/Gradle
[maven]:https://en.wikipedia.org/wiki/Apache_Maven
[cppcheck]:https://en.wikipedia.org/wiki/Cppcheck
[static analysis]:https://en.wikipedia.org/wiki/Static_program_analysis
[jenkins pipeline]:https://jenkins.io/doc/book/pipeline/
[git]:https://en.wikipedia.org/wiki/Git
