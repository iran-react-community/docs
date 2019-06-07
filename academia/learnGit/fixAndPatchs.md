

<h2 dir="rtl">اشتباهات و راه حل آنها در گیت</h2>
<div dir="rtl">

<p>
گیت سخته، اشتباه کردن توش آسون...اینکه چجوری راه حل مشکلی رو پیدا کنیم با توجه به
 حجم داکیومنت این برنامه، و طرح اون بر اساسی که حداقل باید نام دستور مورد نیازمون رو بدونیم تا بتونیم مطلبش رو پیدا کنیم، با اینکه مسائل و موارد استفادش بیشتر به صورت عملی هست، کمی تئوریکی تر به داکیومنت پرداخته، که البته چیز بدی هم نیست برای کسی که از یاد گرفتن لذت میبره عمیقا یادگرفتن خیلی میتونه لذت بخش باشه.
</p><p>
اما توی این مطلب قرار نیست از چیزای لذت بخش حرف بزنیم، اصل مطلب اینجاست که گاهی توی کار با گیت به مشکلاتی بر می خوریم. رویکرد ما برای نجاد یک مخزن داده، که فقط حتی یک نفر غیر از خودمون همزنمان به کار با اون مشغول هست در صورت بروز مشکل میتونه بسیار حیاتی باشه، مهارت با تجربه به دست میاد و تجربه توی مسائل فنی هزینه هنگفتی می تونه داشته باشه، البته منظورم از **هزینه** اون لغت تخصصی علوم کامپیوتر هست. زمان بزرگترین سرمایه ماست، اینکه چقدر به سرعت شروع به جست و جو برای یافتن راهکار حل مشکلمون میکنیم، و اینکه چقدر زمان صرف پیدا کردن نقشه فرار از این حالت میشه میتونه توی ریپوزیتوری هایی بامشارکت کنندگان بیشتر به میزان بسیاری مهم باشه.
</p>


<h3 dir="rtl">ماشین زمان گیت</h3>


در مواقعی که مطلبی را به اشتباه حذف، یا از مرجی اشتباه همه چیز به هم ریخته است میتوانید از 
 
<code class="language-git">git reflog </code> استفاده کنید، ریفاکتور به شما نمایی از تمام برنجها نشان میدهد که هر یک شامل یک آدرس به این صوزت می

 باشند:

<pre dir=ltr>b29db5d HEAD@{83}: rebase: checkout master
5f92901 HEAD@{84}: checkout: moving from master to dev
b29db5d HEAD@{85}: pull: Fast-forward
5f92901 HEAD@{86}: merge dev: Fast-forward
4d14cc1 HEAD@{87}: checkout: moving from dev to master
5f92901 HEAD@{88}: commit: Dictation of newly added howto writh rtl updated</pre>


کافیست ایندکس کامیتی که مشکلات را به وجود آورده پیدا کنید و دستور زیر را اجرا نمایید تا ماشین زمان گیت شما را به آن کامیت بازگرداند.


<pre dir=ltr>git reset HEAD@{index}</pre>


<h3 dir="rtl">بدنه پیام کامیت قبلی را اشتباه نوشته ام</h3></div>

<pre dir=ltr>git commit --amend</pre>


<h3 dir=rtl>:warning: Warning </h3>

<b dir=rtl>
> -  هرگز از دستورات حاوی آمِند و ریست بر روی ریپوزیتوری های مشترک استفاده نکنید
> 
> -  تنها در صورت مطالعه دقیق و اطمینان باید از چنین دستورات بازگشتی استفاده شود


<h3 dir="rtl">نیاز به تغییر نام یا جابجایی فایل دارم
<div dir="ltr">

    git-mv(1) Manual Page
    NAME
    git-mv - Move or rename a file, a directory, or a symlink
    
    SYNOPSIS
    git mv <options>… <args>…
    DESCRIPTION
    Move or rename a file, directory or symlink.
    
    git mv [-v] [-f] [-n] [-k] <source> <destination>
    git mv [-v] [-f] [-n] [-k] <source> ... <destination directory>
    In the first form, it renames <source>, which must exist and be either a file, symlink or directory, to <destination>. In the second form, the last argument has to be an existing directory; the given sources will be moved into this directory.
    
    The index is updated after successful completion, but the change must still be committed.
    
    OPTIONS
    -f
    --force
    Force renaming or moving of a file even if the target exists
    
    -k
    Skip move or rename actions which would lead to an error condition. An error happens when a source is neither existing nor controlled by Git, or when it would overwrite an existing file unless -f is given.
    
    -n
    --dry-run
    Do nothing; only show what would happen
    
    -v
    --verbose
    Report the names of files as they are moved.
