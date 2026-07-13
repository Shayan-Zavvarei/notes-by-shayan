- Based on the Samuel, 1959, Machine Learning algorithm enable the computers to **learn** from data, and even **improve**  themselves, without being explicitly **programmed**. 
  
- Tom Mitchell, 1977: A computer program is said to learn from experience E with respect to some task T and some performance measure P, if its performance on T, as measured by P, improves with experience E. 
---
Two approach can be use two solve a problem in programming.
 
- Traditional way: 
 
- Machine Learning :
---
We  can use ML where:
1. Finding the rule of the problem is difficult 
2. No other method can solve the problem
3. High oscillating problem 
4. Situations with a Large amount of data
---
### Variations of ML 
1. **Supervised Learning**: Data has it's own solution of label or target.
2. **Unsupervised**: Data don't have any label. We can compress data or some variations on the dimensions of the data, Clustering... . 
   To say it n the simple way, you don't Know what you want.
3. **Reinforcement Learning**: Machine Learns based on the choose and result of the agent.
---
### Systems of ML
1. Instance-Based: Model compares each data point with other data points to find a model.
2. Model-Based: Model of Machine use a basic and fundamental model(e.g. a physics model) to find the rule of learning.  
---
### Challenges of  ML
1. Lack of data 
2. Non-representative Data: your data doesn't represent the model
3. Low quality Data(Noisiness)
4. Featureless Data
5. Over-fitting: TOO complex model for data
6. Under-fitting: TOO simple model for the data
---
### Validation and Test of the data 
#### Hyperparameters configuration
We need to separate the data into 3 part;
1. Train: Input data for training 
2. Validation: input data for prediction of output result.
3. Test: This part wont go to the data. so after the training we show it to the model and find an output result to ignore bias.
---
### Regression 
Since a major category  of machine learning is supervised learning with a known target we can categorized it into
1. **Regression**: for Continuous variables.
2. **Classification**: for discrete variables.
--- 

#### Steps of ML
1. DATA: 
   I. Data gathering
   II. Data analysis --> Pandas 
   III. Data cleaning 
   IV. make ready for using data in tho model
2. Model:
---
### Data for Machine Learning
1. Data gathering:  
2. Data Analysis: Visualization and finding some parameters
3. Make data ready for ML algorithm:
- Data cleaning
- text data 
- scaling the data: like normalizing the data 
---
### Resources for Data 
- kaggle.com
- openml.org
- paperswithcode.com
- amazon aws dataset 
- tensorflow.org 
---
### Step by Step on data of California home market
```python
# Import libraries
import numpy as np
import pandas as pd

# Read the csv file using pandas 
pd.read_csv("directory of the csv data")
# You can put this data that pandas has been read into a vairiable df(data frame)
df = pd.read_csv("/home/directories/...")
```
You can see the information of the data using `.info()`:
```python
df.info()
```
After that you can even call the row or column of the data by using `df.<nameofthetitle>`
```python
df.ocean_proximity.value_counts()
# This will show the number of values of title ocear_proximity
```

You can even describe some information of the data set using `.describe`in pandas
```python
df.describe()
```
This will show you some statistical properties of your data set for example meadian, max, min, ... .

---
### Visualization
Visualizing the data can be helpful to understand the problem and finding the solution. 
Most famous library for visualizing the data is `matplotlib` with multiple modules and properties. for example for the dataset df above we can use `.hist` to plot a histogram of the df:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt 

df = pd.read_csv("directory of the dataset")

# Plotting the histogram of your data frame
df.hist(bins=40, figsize=(11,7))  
```

### Dividing data into train and test set
#### Test set
We can(should) divide data to test set to see the result of the model in our data with out model see the complete data. we should do it **randomly**.
```python
random_indices = np.random.permutation(len(df))
# This will give us data randomly in our data set
test_set_size = int(len(df)*0.2) 
test_random_indices = random_indices[:test_set_size]
# SO the train set will become:
train_random_indices = random_indices[test_set_size:]
# These are just indix, we need data itself
df.iloc[train_random_indices]
# OR
df.iloc[test_random_indices]
```
Let's write a function for above, a ready to use one:
```python
def shuffle_and_split_df(df, test_ratio):
	random_indices = np.random.permutation(len(df))
	test_set_size = int(len(df)*test_ration) 
	test_random_indices = random_indices[:test_set_size]
	train_random_indices = random_indices[test_set_size:]
	return df.iloc[train_random_indices], df.iloc[test_random_indices]
```
for finding a constant and static result we can set a constant random seed of save split data.
```python
def shuffel_and_split_df(df, test_ration):
# We set a constant seed to get static result
	np.random.seed(40)
	test_set_size = int(len(df)*test_ration) 
	test_random_indices = random_indices[:test_set_size]
	train_random_indices = random_indices[test_set_size:]
	return df.iloc[train_random_indices], df.iloc[test_random_indices]

```
But we want to split completely test and train data set. if we change the data set, sometimes train data move to test data. What should we do to solve this problem?

We can use **zlib library and module crc32**.
In this case we can track the data blocks by giving id(Hash) to data. here we want to give a hash(identifier) to each line so we can track each line by their id.
```python
from zlib import crc32
# crc32 turn every thing to 32 bites 
def is_identifier_in_test_set(identifier, test_ration):
	return crc32(np.int64(identifier)) < test_ration*2**32
```
now we can split data to test and train dataset even for updating data:
```python
def split_train_test_with_identifier_hash(df, test_ratio, identifier_column):
	identifiers = df[identifer_column]
	in_test_set = identifier.apply(lamba id_: is_identifier_in_test_set(id_, test_ration))
	return df.loc[in_test_set], df.loc[in_test_set]
```
for train dataset we can simply use **not** in above function:
```python
def split_train_test_with_identifier_hash(df, test_ratio, identifier_column):
	identifiers = df[identifer_column]
	in_test_set = identifier.apply(lamba id_: is_identifier_in_test_set(id_, test_ration))
	return df.loc[~in_test_set], df.loc[in_test_set]
```
خب حالا بحث اینه که ما اینجا ستون آیدنتیفایر نداریم. میتونیم براش یه ستون درست کنیم که اون ستون آیدنتیفایر ها رو نشون بده بهم. برای مثال میتونیم:
```python
df.reset_index()
```
این میاد اندیس ها رو هم به دیتا فریممون اضافه میکنه. برای مثال با استفاده از این ایندکس گذاری بالا میتونیم اسپلیت کردن دیتای تست و ترین رو به صورت پایین بنویسیم:

```python
split_train_test_with_identifier_hash(df.reset._index(), 0.2, "index")
```
حالا یه مشکلی که استفاده از اندیس سطرها به عنوان آیدنتیفایر داره اینه که در صورتی کار میکنه که همیشه دیتای جدید رو به انتهای دیتای قبلی اضافه کنیم و در غیر این صورت همه چیز به هم میریزه و جای اندیس ها عوض میشه. باید چیکار کنیم؟ کار منطقی اینه که خودمون با استفاده از یه ترکیبی از خصوصیات دیتامون که برای هر سطر از دیتا اختصاصی هست یه آیدنتیافیر درست کنیم. برای مثال توی دیتای خونه ها میتونیم از ترکیب طول و عرض جغرافیایی استفاده کنیم چرا که طول و عرض تغییر نمیکنن و برای هر سطر دیتا منحصر به فرد هست. برای مثال:
```python
df_with_identifier = df
df_with_identifier["identifier"] = df["longitude"]*1000 + df["latitude"]
```
اینجوری عملا یه ستون آیدنتیفایر اختصاصی خودمون رو درست میکنیم. حالا بر اساس این آیدنتیفایر جدید میتونیم ترین و تست دیتا رو اسپلیت کنیم.
```python
train_set, test_set = split_train_test_with_identifier_hash(df_with_identifier, 0.2, "identifier")
```
حالا دیگه با آپدیت کردن  دیتا فریم و تغییر دیتا فریم به مشکلات ذکر شده  نمیخوریم و همیشه با هش درست شده میتونیم بدون مشکل دیتا فریممون رو به تست و ترین  اسپلیت کنیم.  
آیا این همه کاره؟ آسون ترین کاره؟ نه. یه کتاب خونه خیلی مهم توی ماشین لرنینگ هست به اسم sikit-learn یا sklearn که خودش در یه ماژول این اسپلیت کردن رو داره که میتونیم به صورت ساده ازش استفاده کنیم به صورت:
```python
from sklearn.model_selection import train_test_split(df, test_size = 0.2 , random_state = 40)
```
که رندوم استیت عملا همون سید نامبر هست. 
### Stratified Sampling
نکته ای که برای پروسه ای که نوشتیم وجود داره اینه که بالاخره توی هر کدوم از این ها برای دیتاست های بزرگ کار کنیم این کارایی که کردیم خوبه اما اگر دیتاستمون خیلی بزرگ نبود باید چیکار کنیم؟ به خصوص اگر دیتا ستمون نسبت به فیچر ها کم باشه چی؟ این موقع پدیده sampling bias که توی آمار هست به وجود میاد.
#### Sampling bias
فرض کنیم تو یه شرکت میخوایم با هزار نفر از مشتری ها میخوایم تماس بگیریم. نمیایم این هزار نفر رو کاملا رندوم انتخاب کنیم. ممکنه مثلا ۵۲ درصد از مشتری ها خانوم باشه وو ۴۸ درصد خانوم. در این صورت ۵۲۰ نفر باید خانوم باشه و ۴۸۰ نفر آقا باشن. اگر اینکارو نکنیم و رندوم انتخاب کنیم سمپلینگ بایاس به وجود میاد. 
بنابر این راهکار اینه که نسبت درصد یه اتریبیوت توی دیتای train با درصد اون اتریبیون توی دیتای تست هم یکی باشه.
این کاری هست که ما بهش میگیم stratified sampling یا نمونه برداری طبقه بندی شده که توش کاملا رندوم سمپلینگ نمیکنیم و دسته بندی ها رو هم توی سمپلینگ در نظر میگیریم. فرض کنید یه فیچر توی دیتامون خیلی اهمیت داره و باید بر اساس اون استرتیفاید سمپلینگ انجام بدیم. 
توی دیتاستی که داریم مثلا median_income  میتونه برامون مهم باشه که یه فیچر پیوسته هم هست.
اگه داده اون فیچر ما پیوسته باشه میتونیم بین بندی کنیم (همون کاری که تو کیهان شناسی من انجام میدم).

میشه خیلی ساده از سایکیت لرن استفاده کرد ولی با پانداس هم میشه:
```python
pd.cut(df["median_income"], bins = [0.0,1.5,3.0,4.5,6.0, np,inf],
labels = [1,2,3,4,5])
```
اینجوری خروجی توی هر بین یه لیبل هم میگیره. عملا ما اینجوری میتونیم سمپلینگ دیتا رو وزندار(weighted) کنیم.  
### Stratified Sampling implementation
برای اینکار میتونیم از سایکیت لرن اضافه کنیم. 
```python
from sklearn.model_selection import StratifiedShuffleSplit
sss = StratifiedShuffleSplit(n_split = 10, test_size = 0.2, random_state = 40)
stratified_split = []
for train_im test_i in sss.split(df, df["median_income_categories"]):
	stratified_train_set_n = df.iloc[train_i]
	stratified_test_set_n = df.iloc[test_i]
	stratified_split.append([stratified_train_set_n, stratified_test_set_n])
```
این چی بر میگردونه؟ یه اسپلیتر برمیگردونه که متد اسپلیت داره و متد اسپلیت به ما اندیس میده. بعد  از اون باید بیایم این کتگوری هایی که درست کردیم رو حذف کنیم چون دیگه نیاز نداریم و فقط برای سمپلینگ استفاده شده. یه راهی که داریم استفاده از drop هست:
```python
str_train_set = str_train_set.drop("median_income_categories", axis = 1)
str_test_set = str_test_set.drop("median_income_categories", axis = 1)
```
### Visualization
حالا که داده رو بهتر شناختیم حالا میخوایم یکم دقیق تر داده رو بررسی کنیم و مصور سازی بهتری کنیم تا مشخص تر ببینیم چی تو داده ما هست.
اولا که میتونیم با توجه به وجود دیتای طول و عرض جغرافیایی بیایم اینها رو با یه اسکتر پلات رسم کنیم. یکی از راه هاش استفاده از seaborn هست.
```python
train = str_train_set
sns.scatterplot(data = train, x="longitude" , y = "latitude")

```
کاری که میتونیم انجام بدیم اینه که نوع پلات کردن رو یکم تنظیم کنیم. مثلا میتونیم توی پلات کردن رنگ رو مربوط بدیم به پاپیولیشن و جمعیت. چیکار کنیم؟‌
```python
train = str_train_set
ax = sns.scatterplot(data = train, x="longitude" , y = "latitude", size = "population", alpha = 0.2, hue="median_house_value")
sns.move_legend = (ax, "upper left", bbox_to_anchor = (1,1))
#نکته اینکه چون این اطلاعات تو تصویر بود و تصویر رو ناخوانا میکرد ما با استفاده از ابزار موولجند سیبورن اونو گذاشتیم کنار تصویر که هم تصویر خوانا باشه هم لجندش.
```
!!!!یه آموزش از سیبورن اضافه بشه اینجا به طور خلاصه
### Correlation
ممکنه پارامتر ها با هم ارتباط داشته باشن بنابراین ممکنه که نیاز باشه کورولیشن رو بین پارامتر ها حساب کنیم. در واقع کورولیشن نحوه ارتباط بین دوتا متغیر رو بهمون بده. که به صورت:
$$
\rho_{X,Y} = \mathrm{corr}(X,Y)
= \frac{\mathrm{cov}(X,Y)}{\sigma_X \sigma_Y}
= \frac{\mathbb{E}\!\left[(X-\mu_X)(Y-\mu_Y)\right]}{\sigma_X \sigma_Y},
\qquad \text{if } \sigma_X \sigma_Y > 0 .
$$

![[Pasted image 20260426114904.png]]
نکته ای که هست اینه که کورولیشن یک رابطه خطی رو به ما نشون میده و نوع استقلال بین پارامتر ها رو به طور دقیق به ما نمیده. توی پانداس باید چیکار کنیم؟
```python
train.corr()
```
که این دستور میاد کورولیشن بین همه پارامتتر ها رو جدا جدا بهمون میده. درواقع به شکل یک شبه  ماتریس بهمون میده این کورولیشن ها رو. 
چجوری باید کورولیشن رو تفسیر کنیم؟ چیزی که تو آمار خطرناک هست اینه که تفسیر مستقیم داشته باشیم بابت کازالیتی برای مثال تفسیر کنیم اگر دوتا پارامتر کورولیشن زیاد هست بگیم یکی باعث ایجاد اون یکی هست. این نوع تفسیر اشتباه هست و نمیشه اینجوری استنتاج علی انجام بدیم. 
ارتباطات علت و معلولی کار بسیار سخت تری هست.  
چجوری کورولیشن ها رو رسم کنیم؟
```python
sns.scatterplot(data = train, x="median_income", y="median_house_value" , alpha = 0.2)

```
برای  خط های افقی بالای نمودار که ممکنه به دست بیاد در کل نمودار مثلا ممکنه علتش این باشه که اومدن قیمت ها رو رند کردن و نوشتن و باعث این خطوط شده.
![[Pasted image 20260426115843.png]]
کاری که میتونیم بکنیم اینه که این خطوط رو حذف کنیم چون بایاس به وجود میاره توی پیشبینی مدل

### Attribute Combination
گاهی فیچرهامون مثلا تعداد کلی اتاق ها و تعداد کلی خانوار ها رو داریم ولی این شاید مناسب نباشه و مناسب ترش این باشه که بیایم تعداد اتاق ها رو برای هر خونه با توجه به تعداد خانوارها  به دست بیاریم.
```python
train["rooms_per_house"] = train["total_rooms"] / train["total_households"]
train["bedrooms_ratio"] = train["total_bedrooms"]/ train["total_rooms"]
train["peaple_per_house"] = train["population"] / train["households"]
```
حالا که دیتا رو به طور کلی بررسی کردیم حالا میتونیم بریم سراغ آماده سازی دیتامون برای وارد کردنش به مدل.
### Deleting Missing values 
#### prepare data
چند مرحله داره که قدم به قدم باید بریم جلو و از امکانات تنسور فلو استفاده میکنیم.
قدم اول بیایم یک سری از ستون هایی که لازم نداریم رو حذف کنیم. مثلا:
```python
train_features = train.drop("median_house_value", axis =1 )
train_target = train["median_house_value"]
```
تا الان ورودی مدل و چیزی که باید خروجی بده رو جدا کردیم. 
حالا باید یکم دیتا رو تمیز کنیم:
#### Data cleaning 
چیزی که منظور هست اینه که ببینیم کجا میسینگ ولیو داریم. یعنی جاهایی که NA یا NAN داریم و جاهایی رو که خالی هستن مشخص کنیم. 
```python
train_features.info()
```
با توجه به خروجی این باید مثلا  اون ستون  هایی که مقادیر ما رو نداره  حذف کنیم. ممکنه این خوب نباشه لزوما چون منجر به از دست رفتن اطلاعات یک فیچری که میخوایم بشه. میشه یک درصدی رو حذف کرد مثلا ۵ درصد. ولی خب برای دقیق شدن میشه سطرهای خالی رو فقط حذف کرد. 
کار دیگه ای که میشه اینه که اونجاهایی که مقدار نیست رو خودمون بیایم مقدار بذاریم. مثلا بیایم میانگین رو بذاریم. 
بیایم اول اونایی که توی سطر ها مقدار خالی هست رو حذف کنیم.

```python
#remove rooms with NA values with dropna
train_feature.dropna(subset=["total_bedrooms"]).info()
```
حالا بیایم جای مسیسنگ ولیو ها یه مقدار منطقی بذاریم. مثلا بیایم مدین اون ستون رو بذاریم.
```python
total_bedrooms_median = train_features["total_bedrooms"].median()
# train_features_with_imputed_na_value
train_features_with_imputed_na_value = total_features["total_bedrooms"].fillna(total_bedrooms_median)
```
یه امکانی از سایکیت لرن که کار ما رو راجت تر میکنه امکان imputer هست. 
#### sklearn impute: sklearn.impute.Simpleimputer
تمرین
```python
from sklearn.impute import SimpleImputer
simple_imputer = SimpleImputer(strategy = "median")
```
نکته: اگه ابزار پی پراسس استفاده میکنیم بهتره اول یه آبجکت درست کنیم به اسم اون ابزار و بعد دیتاها رو بریزیم تو اون. مثل مثال بالا. جالا میخوایم همینکارو روی دیتای ترین فیچر ها انجام بدیم. 
```python
train_features_numeric = train_features_dtype(include = [np.number])
#با اینکار بالا فقط دیتاهای عددی رو نگه میداریم چون مدل فقط دیتا میبینه.
simple_imputer.fit(train_features_numeric)
# میاد نتایج رو فیت میکنه رو این آبجکتی که درست کردیم برای ابزارمون
simple_imputer.transform(train_features_numeric)
pd.DataFrame(simple_imputer.transform(train_features_numeric), columns=train_features_numeric.columns,
index = train_features_numeric.index)
```

### Other methods of Impute
میشه به جای صرفا سیمپل از روش های دیگه ای هم توی متد ایمپیوت استفاده کرد مثلا میشه از خود مدل استفاده کرد برای پر کردن و یا مدل مشخص مثلا knn. مدل های مختلفی هست که تو داکیومنتیشن ها موجوده.

### Sklearn architucure
یکی از ویژگی های خوب سایکیت لرن طراحی خیلی خوبش هست. یکی از این ویژگی ها:
#### Consistency
  یک اینترفیس ساده و شبیه به هم استفاده میکنن. مثلا:
  - estimator:
هر چیزی که بتونه بر اساس آبجکت یه پارامتر رو تخمین بزنه یه استیمیتور هست.
هر کدوم از این استیمیتور ها یه متد ‍`fit‍` دارند.
- transformer:
بعضی از این استیمتورها میتونه ترنسفورمر باشن یعنی یه دیتا رو بگیره وتخمین بزنه و بعد از اون تخمین استفاده کنه برای استفاده دوباره از دیتا. به نوعی دیتا رو ترنسفورم میکنه و بهم یه دیتاست جدید میده بهمون.
- Predictor:
مدل هایی که داریم مثل knn یه متد فیت دارن یعنی مدل رو روی دیتا فیت میکنن و بعد پارامتر رو پیشبینی میکنن.
#### Inspection
تمامی ویژگی هایی که توی سایکیت لرن استفاده میکنیم یه سری هایپرپارامتر دارن که میتونیم اونا رو به طور دقیق تنظیم کنیم. 

سوالی که ما رو به مبحث بعدی میبره اینه که با داده های کتگوریکال که عدد نیستن توی ماشین لرنینگ باید چیکار  کنیم؟ چون ماشین صرفا عدد میفهمه.

### Ordinal Encoder
همونطور که گفته شد مدل ها صرفا عدد رو میفهمن. باید یک سری دیتاها که عدد ندارد و کتگوریکال هستن رو به نحوی تبدیل به عدد کنیم.
برگردیم به دیتامون:
```python
# categorical features
train_features[["ocean_proximity"]]
```
که خروجی به صورت رشته هستند. حالا بیایم یه اسم جدید بهشون بدیم. کار زیر رو معمولا انجام میدیم که توی دیتا مشخص کنیم با چی طرف هستیم و عدد ها و رشته ها رو به نوعی از هم جدا کنیم چون که قراره کارهای مختلفی روشون انجام بشه. پس حالا یه دیتافریم کتگوریکال داریم.
```python
train_features_categorical = train_features[["ocean_proximity"]]
```
حالا میتونیم برای هر کدوم از این مقادیر یه عدد بذاریم. مثلا اگه جزیره بود بذاریم صفر و برای بقیه هم همینطور. عملا داریم به هر ویژگی رشته ای یه عدد ایندکسی مشخص کنیم. این متد برای وقتی که ۵ تا کتگوری داریم ساده هست ولی اگه ۵۰ تا باشه چی؟ از امکانات سایکیت لرن استفاده میکنیم. یکی از ابزارها:
```python
from sklearn.preprocessing import OrdinalEncoder
oe = OrdinalEncoder()
ocean_proximity_index = oe.fit_transform(train_features_categorical)
oe.categories_
```
یه مشکلی که هست اینه اگر بین کتگوری ها ترتیبی وجود داشته باشه مشابه به بد، خوب، عالی مدل میتونه خوب بیاد اینا رو تبدیل به عدد کنه.
ولی وقتی مثل بالا این ترتیب ملموس نباشه باید کار دیگه ای کرد:
```python
from sklearn.preprocessing import OneHotEncoder
ohe = OneHotEncoder()
ocean_proximity_ohe = ohe.fit_transform(train_features_categorical)
```

حالا بیایم این دیتای جدید رو به دیتافریممون اضافه کنیم:
```python 
train_features_categorical_ohe = pd.DataFrame(ocean_proximity_ohe.toarray(),columns = ohe.get_features_names_out())
```
نکته اینکه در بحث فیت ترنسفورم همیشه روی داده ترین اعمالش میکنیم یعنی روی ترین فیت میکنیم و بعد روی داده تست ترنسفورم میکنیم. علتش هم اینه که میخوایم داده تست کاملا برای مدلمون ناشناخته باشه. 
### MinMax Scalar 
