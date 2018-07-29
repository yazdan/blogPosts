اینم یه تجربه پراکنده دیگه!

مدتی هست که دوست دارم بنویسم و نمیرسم. حالا بعد از مدتها اشتیاق به نوشتن اونقدر زیاد هست که دارم مینویسم.

هدف از این پست معرفی روندها ذخیره سازی دیتا توی کد هست. بارها میشه که ما دوست داریم یه اطلاعاتی رو ذخیره کنیم و اون رو بعدا بازیابی کنیم. وقتی سطح پایین با این اطلاعات برخورد میشه معمولا مساله عجیبی هستند و بایستی به روش مناسب اونها رو پیاده سازی کرد تا ویژگی‌های زیر رو داشته باشه.

1. سایز دیتا و فایل متغیر باشه و بشه اون رو اضافه کرد
2. فیلدهای دیتا قابل اضافه و کم کردن باشه
3. حجم کد لازم برای این کار کم باشه که بشه روی دستگاه‌های سطح پایین مختلف ازش استفاده کرد.

# راه حل‌ها

چیزهایی که من با توجه به جستجوهام پیدا کردن اینها هستن:

1. پیاده‌سازی از اول: یعنی وابسته به نیازمون یه ساختار قابل افزایش خوب پیاده‌سازی کنیم
2. استفاده از فرمت‌های متنی: فرمت‌های متنی که معمولا میشه استفاده کرد [ini], [xml], [cvs], [json], [yaml] هست. ایراد اینها اینه که چون متن هستن حجم زیادی میگیرن و عملا به صرفه نیستن. معمولا میزان پردازش لازم برای parse اونها هم کم نیست.
3. استفاده از تکنولوژی های [serialization] مثل [protocol buffer], [thrift] هست که با استفاده از اونها میتونید یه دیتا رو توصیف کنید و همون دیتا رو بصورت آرایه ذخیره کنید. اونها معمولا از [schema evolution] یعنی تغییر ساختار دیتا هم پشتیبانی می‌کنن.
4. استفاده از دیتابیس های سبک مانند [sqlite]
5. استفاده از کتابخانه‌های ذخیره سازی [nosql] مثل [unqlite] یا [level db] یا [berkeley db] که هر کدومشون به ما امکان ذخیره سازی دیتای با فرمت نامشخص رو میدن.

# انتخاب من

من در پروژه‌هام از یه ساختار با سایز مشخص، [ini] ، [sqlite] و [unqlite] استفاده کردم. الان ترجیحم استفاده از با این اولویت هست:

1. اول [sqlite] چون خیلی امکانانت سطح بالایی میده
2. استفاده از [unqlite] و یا [ini]. البته با [ini] ما به مشکلات زیادی خوردیم اما [unqlite] رو هم اونقدر توی فیلد تست نکردم
3. تهش پیاده کردن ساختار با سایز مشخص هست که کلی دردسر داره

همین

[ini]:https://en.wikipedia.org/wiki/INI_file
[xml]:https://en.wikipedia.org/wiki/XML
[cvs]:https://en.wikipedia.org/wiki/Comma-separated_values`
[json]:https://en.wikipedia.org/wiki/JSON
[yaml]:https://en.wikipedia.org/wiki/YAML
[serialization]:https://en.wikipedia.org/wiki/Serialization
[protocol buffer]:https://en.wikipedia.org/wiki/Protocol_Buffers
[thrift]:https://en.wikipedia.org/wiki/Apache_Thrift
[schema evolution]:https://en.wikipedia.org/wiki/Schema_evolution
[sqlite]:https://en.wikipedia.org/wiki/SQLite
[nosql]:https://en.wikipedia.org/wiki/NoSQL
[unqlite]:https://unqlite.org/
[level db]:http://leveldb.org/
[berkeley db]:https://en.wikipedia.org/wiki/Berkeley_DB
