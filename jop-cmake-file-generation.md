اینم یه تجربه پراکنده دیگه!

با توجه به شلوغی‌های روز افزون زندگی، دارم سعی میکنم که به حد یک نوشته در ماه برسم.  [قبلا] در [مورد]  [cmake]  [نوشتم] و حالا خواستم یه مورد دیگه که شاید به درد کسی بخوره رو بنویسم.

ما توی کارهایی که انجام می‌دیم سعی کردیم که ویژگی‌های مختلف نرم‌افزارمون قابل فعال و غیر فعالسازی باشه. هر مشتری هم نیازهای خاص خودش رو داره و یه زیرمجموعه از ویژگی‌ها رو تحویل میگیره. کاری که انجام داده بودیم استفاده از پیش‌پردازندهها برای این کار بود. بدین شکل که هر ویژگی یه پیش پردازنده مخصوص خودش داشت که فعال یا غیر فعال میشد. 

این روند فعال و غیر فعال سازی همیشه با مشکلات جدی همراه بود بدین صورت که همکارها به علت زیاد بودن و متغیر بودن ویژگی‌ها برای مشتری‌ها بایستی این فایل رو زیاد تغییر میدادن و این تغییرات زیاد باعث می‌شد که خطای انسانی داشته باشن و یه چیزایی یادشون بره و یا اضافه کامپایل کنند و به مشتری بدن

کاری که ما کردیم این بود که این هدر خاص که همه این تعاریف توش بود رو بجای دستی ساختن به کمک [cmake] ساختیم به این شکل که

1.  یه متغیر از نوع cached تعریف کردیم که بشه به عنوان پارامتر زمان کامپایل اضافه بشه
2. بر اساس اون متغیر برای هریک از ویژگی‌ها یک مقدار فعال و غیر فعال تخصیص دادیم
3. از اون متغیرها استفاده کردیم و فایل اصلی رو ساختیم

نمونه این کار به این شکل هست که توی [CMakeLists.txt] یه چنین چیزی نوشتیم


	PROJECT(abyz-cmake-test)

	CMAKE_MINIMUM_REQUIRED(VERSION 3.0)
	
	SET(customer "a" CACHE STRING "This is customer name")

	IF(custome STREQUAL "a")
		SET(F1 "TRUE")
		SET(F2 "TRUE")
		SET(F3 "FALSE")
	ENDIF(custome STREQUAL "a")

	IF(custome STREQUAL "b")
		SET(F1 "TRUE")
		SET(F2 "FALSE")
		SET(F3 "TRUE")
	ENDIF(custome STREQUAL "b")

	CONFIGURE_FILE("${CMAKE_SOURCE_DIR}/module.h.in" "${CMAKE_SOURCE_DIR}/module.h")


	INCLUDE_DIRECTORIES("${CMAKE_SOURCE_DIR}/inc")

	SET(appLib_src
	    src/utility.c
	  )
	ADD_LIBRARY(applibstatic
	    STATIC
	    ${appLib_src}
	  )
	ADD_EXECUTABLE(abyz-cmake-test
	    src/main.cpp
	  )
	TARGET_LINK_LIBRARIES(abyz-cmake-test
	    applibstatic
	  )
	ADD_EXECUTABLE(unittester
	    tst/main.c
	  )

	TARGET_LINK_LIBRARIES(unittester
	    applibstatic
	  )

توی فایل `module.h.in` هم یه چنین چیزی هست

	#ifndef MODULE_H_
	#define MODULE_H_

	#define F1	${F1}
	#define F2	${F2}
	#define F3	${F3}

	#endif /* MODULE_H_ */

و به این شکل این فایل بصورت اتوماتیک ساخته میشه و قابل استفاده است

برای اجرا کردن هم میشه با این دوتا دستور برای مشتری‌های مختلف کامپایل کرد

	$ mkdir build_a
	$ cd build_a
	$ cmake -G "Unix Makefiles" -Dcustomer:STRING=a ../
	$ make
	$ cd ..
	$ mkdir build_b
	$ cd build_b
	$ cmake -G "Unix Makefiles" -Dcustomer:STRING=b ../
	$ make
همین!

[cmake]: http://cmake.org
[make]: https://en.wikipedia.org/wiki/Make_(software)
[static]:https://en.wikipedia.org/wiki/Static_library
[dynamic]:https://en.wikipedia.org/wiki/Dynamic_linker
[CMakeLists.txt]:https://en.wikipedia.org/wiki/CMake

[قبلا]:http://blog.abyz.ir/1394/04/jop-cmake-introduction/
[مورد]:http://blog.abyz.ir/1395/07/jop-cmake-project-structure/
[نوشتم]:http://blog.abyz.ir/1395/12/لذت-برنامه-نویسی-معرفی-ninja-سیستم-build-سریع/
