اینم یه تجربه پراکنده دیگه!

اول از همه بگم که این پست ۱۰۰ امین پست وبلاگ من هست که در نزدیک به سه سال منتشر شده! اولایی که تصیمم به نوشتن گرفتم فکر نمی‌کردم اینقدر بتونم دوام بیارم که ۱۰۰ تا پست بنویسم اما به نظر میرسه نوشتم! پس خوشحالم!

بریم سراغ پست ایندفعه. خب موضوعی که برای من همیشه مطرح بوده و باز هم مطرح هست اینه که شما چطور می‌تونید در زمان اجرا در زبان C یک کتابخانه‌ای که قبلا حتی از وجودش خبر نداشتید رو اجرا کنید. یه چیزی تو مایه‌های اینکه چطور می‌تونید یه پلاگین داشته باشید که بصورت پویا اجرا بشه. در زبان‌های سطح بالاتر این کار با آسونی بیشتری انجام میشه و حتی زبان برای شما امکاناتی رو فراهم کرده که به راحتی این کار رو می‌تونید انجام بدید. اما در C این عملیات خیلی سطح پایین بوده و بوسیله یه سری توابع خاص انجام میشه. لازم به ذکر میدونم که بگم که این کدها همشون توی محیط لینوکس و بهتره بگم مبتنی بر استاندارد [POSIX] قابل استناد هستن و در ویندوز احتمالا روند متفاوت خواهد بود.

شما با دوتا مساله روبرو هستید. 
- اول اینکه یه فایل رو باز کنید و با اون به عنوان فایل اجرایی برخورد کنید! یعنی بصورت دقیقتر بگم که با محتوای اون کد به شکل [Code Segment] برخورد کنید.
- دوم اینکه بتونید حالا که فایل رو باز کردید بتونید توابع درون اون فایل رو به صورتی تشخیص بدید و صدا بزنید!

برای این کار کتابخانه استاندارد C توابعی را در فایل هدر [dlfcn.h] قرار داده است. روند کار نیز بدین صورت است که ابتدا فایل کتابخانه را باز کرده و سپس با اسم تابع فایل را جستجو کرده و اشاره‌گری به آدرس آن تابع باز می‌گرداند. از این پس با استفاده از این اشاره گر به تابع می‌توان آنرا اجرا نمود. کد نمونه این عملیات نیز به شکل زیر است. 

	#include <stdio.h>
	#include <stdlib.h>
	#include <dlfcn.h>

	int
	main(int argc, char **argv)
	{
	    void *handle;
	    double (*cosine)(double);
	    char *error;

	   handle = dlopen("libm.so", RTLD_LAZY);
	    if (!handle) {
		fprintf(stderr, "%s\n", dlerror());
		exit(EXIT_FAILURE);
	    }

	   dlerror();    /* Clear any existing error */

	   /* Writing: cosine = (double (*)(double)) dlsym(handle, "cos");
	       would seem more natural, but the C99 standard leaves
	       casting from "void *" to a function pointer undefined.
	       The assignment used below is the POSIX.1-2003 (Technical
	       Corrigendum 1) workaround; see the Rationale for the
	       POSIX specification of dlsym(). */

	   *(void **) (&cosine) = dlsym(handle, "cos");

	   if ((error = dlerror()) != NULL)  {
		fprintf(stderr, "%s\n", error);
		exit(EXIT_FAILURE);
	    }

	   printf("%f\n", (*cosine)(2.0));
	    dlclose(handle);
	    exit(EXIT_SUCCESS);
	}

همین!

برای [مطالعه]ی [بیشتر]

[POSIX]:https://en.wikipedia.org/wiki/POSIX
[Code Segment]:http://en.wikipedia.org/wiki/Code_segment
[dlfcn.h]:http://linux.die.net/include/dlfcn.h
[مطالعه]:http://tldp.org/HOWTO/Program-Library-HOWTO/dl-libraries.html
[بیشتر]:http://linux.die.net/man/3/dlopen
