
# Aim: COVID-19 Dataset Analysis using Python

# Introduction:

COVID-19 dataset analysis helps in understanding the spread and impact of the pandemic across different countries.

Using Python, we can clean, process, and visualize this data to extract meaningful insights.


## 1. Data Cleaning

  Remove Unnecessary Columns - data = data.drop(['SNo','Last Update'], axis=1)

  Check Data Information - data.info()

## 2. Data Type Conversion


  data['ObservationDate'] = data['ObservationDate'].astype('datetime64[ns]')
   
  data['Confirmed'] = data['Confirmed'].astype('int64')
   
  data['Deaths'] = data['Deaths'].astype('int64')
   
  data['Recovered'] = data['Recovered'].astype('int64')

## 3. Active Cases Calculation

  data['Active'] = data['Confirmed'] - data['Recovered'] - data['Deaths']

  Active = Confirmed − Recovered − Deaths

## 4. Data Exploration

  View Specific Rows - data.iloc[50:100]

  Find Latest Date - data['ObservationDate'].max()

  Filter Latest Data - latest_data = data[data['ObservationDate'] == data['ObservationDate'].max()]


## 5. Country-wise Analysis

  Count Countries - latest_data['Country/Region'].value_counts() , latest_data['Country/Region'].nunique()

  Group Data by Country - countries = latest_data.groupby("Country/Region")[["Confirmed","Deaths","Recovered","Active"]].sum(), countries = countries.reset_index()

  Example: Specific Countries -
    countries[countries['Country/Region'] == "US"]

  countries[countries['Country/Region'] == "India"]

## 6. Data Visualization

   World Map (Choropleth)

  import plotly.express as px

  world_map = px.choropleth(
      countries,
      locations="Country/Region",
      locationmode="country names",
      color="Confirmed",
      color_continuous_scale="reds",
      range_color=[0, 1000000]
  )

  world_map


   Visualizes global distribution of confirmed cases.


##  Top 20 Countries Analysis

  top = latest_data.groupby("Country/Region")[["Confirmed", "Recovered"]].sum().reset_index()
  top = top.sort_values(['Confirmed'], ascending=False)

  top_20 = top.head(20)

#  Applications

* Pandemic tracking
* Healthcare analysis
* Government decision-making
* Data visualization dashboards
* Predictive modeling

# Conclusion

COVID-19 data analysis helps in understanding the global health situation.

Using Python, we can:

* Process large datasets
* Extract meaningful insights
* Visualize data effectively

This experiment demonstrates real-world data analysis and visualization techniques.
