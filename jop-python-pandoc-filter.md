اینم یه تجربه پراکنده دیگه!

همنطور که اخیرا [زیاد]  [نوشتم] فرمت مورد علاقه تولید مستندات من [markdown] شده و برای تبدیل کردنش به یه متن تر و تمیز pdf از [pandoc] به همراه [xepersian] استفاده می‌کنم. حالا این وسط من یه مشکلی داشتم و اونم این بود که متون انگلیسی توی فارسی به درستی به فرمت [xepersian] تبدیل نمی‌شدند و هی مجبور بودم بصورت دستی متن [latex] بدست آمده رو ویرایش کنم. به همین خاطر علاقه مند شدم که ببینم چطور می‌شه این مشکل رو توی [pandoc] حل کرد. راه حل از این قراره که شما بایستی یه فیلتر برای [pandoc] تعریف کنی و اون [pandoc] filter اون کاری که ما دوست داریم رو برای ما انجام میده!

## فیلترهای [pandoc]

زبان برنامه نویسی که [pandoc] با اون توسعه یافته [haskell] هست که خب به نظر من زبان عجیب غریبی هست. شما می‌تونید با استفاده از این زبان فیلترها رو توسعه بدید. کل ماجرای فیلترها هم از این قراره که ابتدا [pandoc] متن ورودی رو میخونه و به ساختار سلسله مراتبی داخلی خودش تبدیل می‌کنه. حالا این ساختار رو بصورت اصلی (که فقط در زبان [haskell] در دسترسه) یا بصورت json در اختیار فیلتر شما قرار می‌ده و فیلتر شما بر اساس فرمت نهایی، نوع المنت و متا دیتاهای مربوط به اون المنت تصمیم می‌گیره که چه کاری انجام بده. تقریبا هیچ مستندات درست حسابی من پیدا نکردم که همه چیز رو توضیح داده باشه، اما سعی کردم به کمک آزمایش و خطا و همچنین دیدن فیلترهای مشابهی که برای کارهای مختلف توسعه پیدا کرده بود گلیم خودم رو از آب بیرون بکشم.

همچنین میشه این فیلترها رو به زبانی غیر از [haskell] توسعه داد. این زبان‌های پایتون، جاوا اسکریپت(در محیط nodejs)، پرل و php هست. من به علت آشنایی بیشترم با پایتون از اون استفاده کردم

## نحوه توسعه

کل روند از این قراره که شما فایل پایتون رو بصورت یک فیلتر با دسترسی اجرایی در اختیار [pandoc] قرار میدید و اون تابع main رو صدا میزنه. پس از اون اطلاعات از stdin به برنامه داده شده و خروجی‌ها از stdout گرفته می‌شه. خود توسعه دهنده [pandoc] هم پکیجی به نام [pandocfilters] توسعه داده که با استفاده از [pip] یا ابزارهای مشابه قابل نصب و استفاده است.

تنها کاری که باید انجام بشه اینه که تابعی نوشته بشه و به عنوان آرگومان به تابع ‍‍`toJSONFilter` پاس داده بشه. این تابع بایستی چهارتا ورودی داشته باشه که به ترتیبت ‍‍`def behead(key, value, format, meta):` هستن و نوع، مقدار، فرمت خروجی و متادیتاهاست. همین من با استفاده از همین‌‌ها فیلترم رو توسعه دادم و گذاشتم روی [گیت‌هاب] که اگه دیگران هم خواستن ازش استفاده کنن.

همین!
پ.ن.: برای مطالعه بیشتر به [اینجا] مراجعه کنید.

[pandoc]: http://pandoc.org/
[markdown]: http://daringfireball.net/projects/markdown/
[xepersian]:http://parsilatex.com/site/
[latex]:https://en.wikipedia.org/wiki/LaTeX
[haskell]:https://en.wikipedia.org/wiki/Haskell_(programming_language)
[pandocfilters]:https://github.com/jgm/pandocfilters
[pip]:https://en.wikipedia.org/wiki/Pip_(package_manager)
[گیت‌هاب]:https://github.com/yazdan/pandoc-xepersian
[اینجا]:http://pandoc.org/scripting.html
[زیاد]: http://blog.abyz.ir/1394/03/markdown-my-doc-generation-format/
[نوشتم]:http://blog.abyz.ir/1393/10/markdown-latex-html/
