# data-science-project

This is my first repository on GitHub about pursuing my career in Data Science

## Code for the Project from Datacamp titled:<br>DR. SEMMELWEIS AND THE DISCOVERY OF HANDWASHING

I personally practice doing data science projects in Datacamp and this is my first project in that platform.
For that reason, I write the codes that I 

### Task 1

```
import pandas as pd

yearly = pd.read_csv("datasets/yearly_deaths_by_clinic.csv")

print(yearly)`
```
### Task 2

```
yearly["proportion_deaths"] = (yearly["deaths"]/yearly["births"])

yearly1 = yearly[yearly["clinic"] == "clinic 1"]
yearly2 = yearly[yearly["clinic"] == "clinic 2"]

print(yearly1)
```

### Task 3

```
%matplotlib inline
df2 = yearly2[['year', 'proportion_deaths']]
ax = df1.plot(x="year", y="proportion_deaths", label="Clinic1")
df2.plot(x="year", y="proportion_deaths", label="Clinic2", ax=ax)
ax.set_ylabel("Proportion deaths")
```

### Task 4

```
monthly = pd.read_csv("datasets/monthly_deaths.csv", parse_dates=["date"])
monthly.head()

monthly["proportion_deaths"] = (monthly["deaths"] / monthly["births"])

print(monthly.head())
```

### Task 5

```
ax = monthly.plot(x="date", y="proportion_deaths")
ax.set_xlabel("Date")
ax.set_ylabel("Proportion deaths")
ax
```

### Task 6

```
import pandas as pd
handwashing_start = pd.to_datetime('1847-06-01')

before_washing = monthly[monthly["date"] < handwashing_start]
after_washing = monthly[monthly["date"] >= handwashing_start] 

ax = before_washing.plot(x="date", y="proportion_deaths", label="death proportion before washing")
after_washing.plot(x="date", y="proportion_deaths", label="death proportion after washing", ax=ax)
ax.set_ylabel("Proportion deaths")
```

### Task 7

```
before_proportion = before_washing["proportion_deaths"]
after_proportion = after_washing["proportion_deaths"]
mean_diff = after_proportion.mean() - before_proportion.mean()
mean_diff
```

### Task 8

```
boot_mean_diff = []
for i in range(3000):
    boot_before = before_proportion.sample(frac=1, replace=True)
    boot_after = after_proportion.sample(frac=1, replace=True)
    boot_mean_diff.append(boot_after.mean() - boot_before.mean())

# Calculating a 95% confidence interval from boot_mean_diff 
confidence_interval = pd.Series(boot_mean_diff).quantile([0.025, 0.975])
confidence_interval
```

### Task 9

```
doctors_should_wash_their_hands = True
```


