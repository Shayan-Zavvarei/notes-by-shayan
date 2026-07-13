## پانداس چیه؟
یک کتابخوانه اوپن  سورس برای پایتون هست برای تحلیل داده ها. برگرفته از عبارت:
panel data
هست.
تقریبا تو همه  پروژه های دیتاساینس توش استفاده میشه. برمنبای numpy هست. 
چرا مهمه؟ 
- اطلاعات و پردازش دیتا روز افزون داره اهمیت پیدا میکنه. 
- از طرف دیگه حجم دیتا خیلی داره زیاد میشه و بنابراین یک ابزار برای استفاده از اون مورد نیاز میشه.
- پانداس بسیار با  سرعت و با انعطاف هست. 
- از اونجایی که کاربرها و توسعه دهنده های اون خیلی زیاد هست همیشه آپدیته.
- برای دیتاهای کوچیک هنوز اکسل بهتره ولی وقتی حجم دیتا زیاد میشه پانداس بهتره. 
## pandas installation
برای نصب پانداس از ابزار پیپ استفاده میکنیم.
```txt
pip install pandas --break-system-packages
```
بعد از نصب برای اینکه ببینیم به درستی نصب شده یا نه باید دستور زیر رو در پایتون و یا ژوپیتر وارد کنیم:
```python
import pandas
```
اگر ارور نداد یعنی به درستی نصب شده. 
میتونیم یک سری اطلاعات بیشتر از پانداس خودمون بگیریم به صورت:
```python
pandas.show_versions()
```
مثلا برای من خروجی زیر رو داد:
```txt
INSTALLED VERSIONS
------------------
commit                : ab90747e3dae0e69b1bdbf083820b8075689b34b
python                : 3.13.11
python-bits           : 64
OS                    : Linux
OS-release            : 6.18.2-arch2-1
Version               : #1 SMP PREEMPT_DYNAMIC Thu, 18 Dec 2025 18:00:18 +0000
machine               : x86_64
processor             : 
byteorder             : little
LC_ALL                : None
LANG                  : en_US.UTF-8
LOCALE                : en_US.UTF-8

pandas                : 3.0.2
numpy                 : 2.4.4
dateutil              : 2.9.0.post0
pip                   : 25.3
Cython                : None
sphinx                : None
IPython               : 9.13.0
adbc-driver-postgresql: None
adbc-driver-sqlite    : None
bs4                   : None
bottleneck            : None
fastparquet           : None
fsspec                : None
html5lib              : None
hypothesis            : None
gcsfs                 : None
jinja2                : None
lxml.etree            : None
matplotlib            : None
numba                 : None
numexpr               : None
odfpy                 : None
openpyxl              : None
psycopg2              : None
pymysql               : None
pyarrow               : None
pyiceberg             : None
pyreadstat            : None
pytest                : None
python-calamine       : None
pytz                  : None
pyxlsb                : None
s3fs                  : None
scipy                 : None
sqlalchemy            : None
tables                : None
tabulate              : None
xarray                : None
xlrd                  : None
xlsxwriter            : None
zstandard             : None
qtpy                  : None
pyqt5                 : None
```
که به ما اطلاعات کلی سیستم و پانداس و کتابخوانه های وابسته رو بهمون نشون میده. 
اگر بخوایم فقط ورژن پانداس رو ببینیم باید به صورت زیر بنویسیم:
```python
pandas.__version__
```
یه کاری که هست اینه که معمولا خود پانداس رو نمینویسیم. میتونیم براش مخفف بنویسیم به صورت زیر:
```python 
import pandas as pd
```

## دیتاست مورد نیاز
توی پوشه آموزش فایل های مختلفی از دیتا ها مثل لیستی از فیلم ها، قیمت بیتکوین و چیزهای دیگه ای وجود داره.

## خواندن اطلاعات فایل csv
```python
import pandas as pd
pd.read_csv('Data/employees.csv')
```
در این صورت فایل دیتا به صورت زیر چاپ خواهد شد:

| First Name | Gender  | Start Date | Salary  | Mgmt     | Team  |              |
| ---------- | ------- | ---------- | ------- | -------- | ----- | ------------ |
| 0          | Douglas | Male       | 8/6/93  | NaN      | True  | Marketing    |
| 1          | Thomas  | Male       | 3/31/96 | 61933.0  | True  | NaN          |
| 2          | Maria   | Female     | NaN     | 130590.0 | False | Finance      |
| 3          | Jerry   | NaN        | 3/4/05  | 138705.0 | True  | Finance      |
| 4          | Larry   | Male       | 1/24/98 | 101004.0 | True  | IT           |
| ...        | ...     | ...        | ...     | ...      | ...   | ...          |
| 996        | Phillip | Male       | 1/31/84 | 42392.0  | False | Finance      |
| 997        | Russell | Male       | 5/20/13 | 96914.0  | False | Product      |
| 998        | Larry   | Male       | 4/20/13 | 60500.0  | False | Business Dev |
| 999        | Albert  | Male       | 5/15/12 | 129949.0 | True  | Sales        |
| 1000       | NaN     | NaN        | NaN     | NaN      | NaN   | NaN          |
نکته ای که هست اینه که برای اینکه خروجی آخرمون رو ببینیم کافیه بنویسیم:
```python 
__
```
برای اینکه ببینیم تایپ خروجی بالا چی هست میتونیم یه کاری کنیم:
```python 
type(_)
```
در این صورت خروجی زیر رو بهمون میده:
```txt
pandas.DataFrame
```
همانطور که میبینیم این یک Data Frame هست. در نتیجه میتونیم خروجی دیتا رو به یک متغیر نسبت بدیم
```python
df = pd.read_csv('Data/employees.csv')
```
با اجرا کردن این کد دیگه چیزی نمایش داده نمیشه بلکه دیتا فریممون به df  نسبت داده میشه. 
میتونیم سر تیترهای این دیتا فریم رو به صورت زیر ببینیم:
```python
df.head()
```
که خروجیش به صورت زیر نمایش داده میشه:
