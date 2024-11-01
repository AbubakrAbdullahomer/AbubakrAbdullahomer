- 👋 Hi, I’m @AbubakrAbdullahomer
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
- 
import pandas as pd

# تحميل البيانات
data = pd.read_csv("epa-sea-level.csv")

# عرض أول بضع صفوف من البيانات
print(data.head())
import pandas as pd
import matplotlib.pyplot as plt
from scipy.stats import linregress

# الخطوة 1: تحميل البيانات
data = pd.read_csv("epa-sea-level.csv")

# الخطوة 2: إنشاء الرسم البياني النقاطي
plt.scatter(data['Year'], data['CSIRO Adjusted Sea Level'], label="Original Data", color='blue')

# الخطوة 3: خط الانحدار الأول باستخدام جميع البيانات
slope, intercept, _, _, _ = linregress(data['Year'], data['CSIRO Adjusted Sea Level'])
years_extended = pd.Series(range(1880, 2051))
sea_levels_predicted = intercept + slope * years_extended
plt.plot(years_extended, sea_levels_predicted, 'r', label="Fit Line (1880-2050)", color='red')

# الخطوة 4: خط الانحدار الثاني باستخدام بيانات من عام 2000
data_recent = data[data['Year'] >= 2000]
slope_recent, intercept_recent, _, _, _ = linregress(data_recent['Year'], data_recent['CSIRO Adjusted Sea Level'])
sea_levels_recent_predicted = intercept_recent + slope_recent * years_extended
plt.plot(years_extended, sea_levels_recent_predicted, 'green', label="Fit Line (2000-2050)")

# الخطوة 5: إعدادات الرسم البياني
plt.xlabel("Year")
plt.ylabel("Sea Level (inches)")
plt.title("Rise in Sea Level")
plt.legend()

# حفظ الصورة
plt.savefig("sea_level_plot.png")

# عرض الرسم البياني
plt.show()

<!---
AbubakrAbdullahomer/AbubakrAbdullahomer is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
