---
title: "Exploratory data analysis in Python: Missed hospital appointments"
#excerpt: "Health care systems are both expensive to run and valuable for patients. So why do so many patients miss their medical appointments? In this exploratory analysis I sought some preliminary insights."
layout: post

---
Health care systems are both expensive to run and extremely valuable for patients. So why do so many patients miss their medical appointments? 

I tried to gain some preliminary insights into factors associated with no-shows using a dataset of 110k hospital appointments in Brazil. It collects information about both appointments and patient characteristics in 14 variables.

![alt]({{ site.url }}{{ site.baseurl }}/assets/project_assets/noshow-hospital-appointments-screenshot.png)
<!-- break -->

### Project purpose
The purpose of the project, which is a part of the [Data Analyst](https://github.com/PierreHentges/DAND) course I did, was to learn about the data analysis process of questioning, wrangling, exploring, analyzing, and communicating data. It only aimed for preliminary observations as it did not involve statistical analysis or model building.

This was the first longer data analysis project I did using the Python libraries pandas, and matplotlib and seaborn for visualisation. It was carried out in a Juypter notebook [ available here]({{ site.url }}{{ site.baseurl }}/assets/project_assets/noshow-hospital-appointments.html).

## Data wrangling
I obtained the data set [from Kaggle](https://www.kaggle.com/joniarroba/noshowappointments) as a csv file that I read into a pandas dataframe.

It encompasses 14 variables, and a small amount of data cleaning was necessary. I converted some dates and booleans to the appropriate format, corrected some typos in variable names, and dropped one record with a negative patient age.


## Exploratory Data Analysis (EDA)
### Approach
My analysis approach had 3 stages focussing either on the patient, on the organisation of appointments, or on the hospital where the appointment took place. 

As the data set contains information on the patients' health and socio-economic characteristics, I tried to identify if these were associated with missed appointments to find out if there was a typical profile of patients who miss their appointment. 

I also tried to identify associations between no-shows and factors of how medical appointments are organised - these are of course interesting if we want to reduce the proportion of missed appointments, since organisational aspects can in principle be changed more easily than patient characteristics.

Finally, I wanted to check if any associations I had identified held up when the data were disaggregated according to the hospital where it took place. 

In the exploratory data analysis, I sought these trends and associations mainly through the means of visualisation, tabulation and correlation of variables.

### Waiting for an appointment
Overall, 20.2% of the appointments in the data set are missed. I then looked at how appointments are organised.

Both the date when the appointment was scheduled, and the date for which it was set are available, enabling calculation of how long patients need to wait for their appointment. 

I divided appointments into 5 categories according to how long the patient needed to wait, and calculated the proportion of missed appointments in each category.

![image-right]({{ site.url }}{{ site.baseurl }}/assets/project_assets/dand-noshows_vs_waittime.png){: .align-center}

It turns out that missed appointments are particularly low for same-day appointments at 4.64%, compared to the overall percentage of no-shows of 20.2%.  The percentage of no-shows then rises as the wait time increases.

How does wait time impact the volume of missed appointments?
 
<figure style="width: 921px">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/project_assets/dand-noshows_impact_wait.png" alt="">
  <figcaption>Categories of wait-time: same day, 1-2 days, 3-7 days, 8-21days, 22-180 days.</figcaption>
  </figure> 

The majority of all no-shows occur after a wait time longer than a week - while these wait times only make up roughly one-third of the total of appointments.

#### Do reminders work?

The data set records whether or not an SMS reminder was sent to the patient. Is this linked to the proportion of no-shows?

![image-right]({{ site.url }}{{ site.baseurl }}/assets/project_assets/dand-noshows_vs_sms.png){: .align-center}

Counterintuitively, more appointments are missed in the category of appointments where an SMS reminder was sent out (27.6%) than those without (16.7%). 

How can we make sense of this? Could it be linked to wait time?

![image-right]({{ site.url }}{{ site.baseurl }}/assets/project_assets/dand-noshows_sms_disaggregated.png){: .align-center}

It turns out that no reminders are sent out for same-day appointments, nor for 1-2 day wait times. 

Since no-shows are much lower for these appointments, their amalgamation with longer-wait appointments where no-SMS is sent out reduces the percentage of no-shows when no reminder is sent.

However, in those categories of appointments where they are sent, SMS reminders are associated with significantly lower no-show rates. 

This effect is stronger the longer patients wait for their appointment.

### Patient characteristics
The data set also records a number of patient characteristics. To look for associations, I categorised all appointments according to whether the patient had a particular characteristic, and visualised the proportion of no-shows.

![image-right]({{ site.url }}{{ site.baseurl }}/assets/project_assets/dand-noshows_vs_characteristics.png){: .align-center}
The proportion of missed appointments is somewhat lower for patients with a disability, with diabetes and with hypertension.

The proportion of missed appointments is somewhat higher for patients in the welfare program *Bolsa Família* ("scholarship").

Another variable is patient age. Is it associated with no-show rates?
![image-right]({{ site.url }}{{ site.baseurl }}/assets/project_assets/dand-noshows_vs_age.png){: .align-center}

The lowest proportion of missed appointments is seen in appointments with the very young, and the old ; the highest proportion of missed appointments is seen with teenagers and patients in their early 20s. There's a steady decline of the proportion of no-shows in appointments with patient age from mid-20s to mid-60s.

How does this affect the volume of missed appointments?

<figure style="width: 921px">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/project_assets/dand-noshows_impact_age.png" alt="">
  <figcaption>Age categories : infant (0-2 years), child (3-10 years), adolescent(11-17), young adult(18-24), adult(25-44), middle age(45-64), old age(65-115)</figcaption>
  </figure> 
Although no-shows are disproportionately higher for appointments with children, adolescents, young adults, the impact on the volume of missed appointments is relatively modest, because the bulk of hospital appointments are with patients in the older age categories.

### Trends disaggregated by hospital
Finally I wanted to check if the associations observed held up if data were divided according to hospital.

More specifically I asked, do hospitals with more frequent SMS reminders have lower no-show rates? Do hospitals with older patients have lower no-show rates?

<figure style="width: 891px">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/project_assets/dand-noshows_corr_sms.png" alt="">
  </figure> 

There is an inverse correlation between the proportion of SMS reminders sent for wait periods over 7 days (and over 21 days) and no-show rates. This means that hospitals with a high no-show rate tend to have a lower proportion of SMS reminders. 

<figure style="width: 891px">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/project_assets/dand-noshows_corr_age.png" alt="">
  </figure> 

There is a moderate (r=-0.32) inverse correlation between the proportion of appointments with older patients and no-show rates. This means that hospitals with a higher proportion of older patients tend to have a lower no-show rate.

Conversely there is a moderate (r=0.32) correlation between the proportion of appointments with younger patients (infants are excluded from this group) and no-show rates. This means that hospitals with a higher proportion of younger patients tend to have a higher no-show rate.

In conclusion, variations between hospitals in no-show rates correlate with factors found to be associated with no-shows earlier. No-shows tend to be lower in hospitals that have a higher proportion of SMS reminders, of older patients, and of same-day appointments. No-shows tend to be higher in hospitals that have a higher proportion of younger patients and welfare recipients.
 

#### links & files:
* [local link]({{ site.url }}{{ site.baseurl }}/assets/project_assets/noshow-hospital-appointments.html): Jupyter notebook
* [noshowappointments-kagglev2-may-2016.csv](https://www.kaggle.com/joniarroba/noshowappointments): original dataset on Kaggle

