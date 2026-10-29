# Daily Python Practice with ChatGPT, Claude & Meta AI (WhatsApp) 29th October 2026
<b>Challenge: Flood-risk station analysis 🌧️</b></br>
Imagine you're analysing rainfall and river levels across six monitoring stations.</br>
```Python
stations = {
    "Kolkata": {
        "rainfall": [280, 320, 300],
        "river_level": [4.2, 4.8, 4.5]
    },
    "Delhi": {
        "rainfall": [90, 120, 100],
        "river_level": [2.1, 2.4, 2.2]
    },
    "Mumbai": {
        "rainfall": [250, 290, 270],
        "river_level": [3.8, 4.1, 4.0]
    },
    "Chennai": {
        "rainfall": [180, 210, 195],
        "river_level": [3.0, 3.2, 3.1]
    },
    "Guwahati": {
        "rainfall": [380, 420, 400],
        "river_level": [5.1, 5.8, 5.5]
    },
    "Patna": {
        "rainfall": [220, 240, 230],
        "river_level": [4.0, 4.3, 4.2]
    }
}
```
<b>Your mission</b>
<ul>
  <li><b>Calculate averages</b> Calculate each station's average rainfall and average river level.</li>
  <li>
    <b>A station is <code>"High Risk"</code> when both conditions are true:</b>
    <li>Average rainfall ≥ 250</li>
    <li>Average river level ≥ 4.0</li>
    <li>Otherwise <code>"Normal Risk"</code></li>
  </li>
  <li><b></b></li>
</ul>

# Solution (Script)
```Python
stations = {
    "Kolkata": {
        "rainfall": [280, 320, 350],
        "water_level": [7.2, 8.1, 8.5],
        "elevation": 6
    },
    "Delhi": {
        "rainfall": [70, 110, 90],
        "water_level": [2.1, 2.5, 2.3],
        "elevation": 215
    },
    "Mumbai": {
        "rainfall": [250, 290, 310],
        "water_level": [5.8, 6.4, 7.0],
        "elevation": 14
    },
    "Chennai": {
        "rainfall": [180, 220, 200],
        "water_level": [4.0, 4.5, 4.2],
        "elevation": 7
    },
    "Guwahati": {
        "rainfall": [380, 420, 400],
        "water_level": [8.8, 9.2, 9.0],
        "elevation": 55
    },
    "Patna": {
        "rainfall": [210, 240, 230],
        "water_level": [5.0, 5.5, 5.2],
        "elevation": 53
    }
}
def myfunction(stations):
    report = {}
    statistics = {}
    count_high_risk_rainfall = 0
    total_high_risk_rainfall = 0
    highest_average = None
    highest_average_station = None
    count_risk_water_level = 0
    total_risk_water_level = 0
    count_low_risk = 0
    for station, data in stations.items():
        average_rainfall    = sum(data["rainfall"]) / len(data["rainfall"])
        average_water_level = sum(data["water_level"]) / len(data["water_level"])
        if average_rainfall >= 250 and average_water_level >= 4.0:
            status = "High Risk"
            count_high_risk_rainfall += 1
            total_high_risk_rainfall += average_rainfall
            if highest_average is None or average_water_level > highest_average:
                highest_average = average_water_level
                highest_average_station = station
        elif average_rainfall >= 200 and average_water_level >= 5:
            status = "Risk"
            count_risk_water_level += 1
            total_risk_water_level += average_water_level
        else:
            status = "Low Risk"
            count_low_risk += 1
        report[station] = {"Average Rainfall":average_rainfall,
                           "Average Water Level":average_water_level,
                           "Status":status}
    overall_rainfall_average_among_high = total_high_risk_rainfall / count_high_risk_rainfall if count_high_risk_rainfall > 0 else 0
    overall_water_level_average_among_moderate = total_risk_water_level / count_risk_water_level if count_risk_water_level > 0 else 0
    statistics = {"Number of High risk stations":count_high_risk_rainfall,
                  "Average rainfall among the High Risk stations only":overall_rainfall_average_among_high,
                  "Average water level among the moderate risk stations only":overall_water_level_average_among_moderate,
                  "Station with highest average rainfall across all station":highest_average_station,
                  "Station with highest average rainfall across all station's value":highest_average,
                  "Number of Low risk stations":count_low_risk}
    return report,statistics
print(myfunction(stations))
```

# Solution (Output)
```
PS C:\Users\hp\Downloads\sql_practice(0)> & C:\Users\hp\AppData\Local\Programs\Python\Python313\python.exe "c:/Users/hp/Downloads/sql_practice(0)/test2.py"
({'Kolkata': {'Average Rainfall': 316.6666666666667, 'Average Water Level': 7.933333333333334, 'Status': 'High Risk'}, 'Delhi': {'Average Rainfall': 90.0, 'Average Water Level': 2.3000000000000003, 'Status': 'Low Risk'}, 'Mumbai': {'Average Rainfall': 283.3333333333333, 'Average Water Level': 6.3999999999999995, 'Status': 'High Risk'}, 'Chennai': {'Average Rainfall': 200.0, 'Average Water Level': 4.233333333333333, 'Status': 'Low Risk'}, 'Guwahati': {'Average Rainfall': 400.0, 'Average Water Level': 9.0, 'Status': 'High Risk'}, 'Patna': {'Average Rainfall': 226.66666666666666, 'Average Water Level': 5.233333333333333, 'Status': 'Risk'}}, {'Number of High risk stations': 3, 'Average rainfall among the High Risk stations only': 333.3333333333333, 'Average water level among the moderate risk stations only': 5.233333333333333, 'Station with highest average rainfall across all station': 'Guwahati', "Station with highest average rainfall across all station's value": 9.0, 'Number of Low risk stations': 2})
PS C:\Users\hp\Downloads\sql_practice(0)> 
```
