# Heatmaps Visualization

## What is Heatmaps?
A heatmap is a two-dimensional visualization of data that uses color to represent numerical values. This can be either different intensities of the same hue, or different colors from a palette. Heatmap represents data values through colors, each cell in a table or matrix is shaded according to its value. Higher or more significant values are usually displayed in darker/stronger colors, while lower or missing values are shown in lighter colors.

Heatmapswereimportedintocartographyfromdatavisualization techniques, similar  to other maptypesalreadywellestablishedincartography, suchasdiagrams, charts, dots or choropleths.  Heat maps are not necessarily connected strictly to geography. They aresed in medicine, chemistry, biology and ecology, the social sciences for non spatial data, and eye-tracker analysis.

<img width="712" height="356" alt="image" src="https://github.com/user-attachments/assets/e5170d9c-15ab-4d61-878b-65846e2e5782" />

https://www.mdpi.com/2220-9964/10/8/562 

### Heatmaps are widely used for:
1. Detecting patterns in datasets (clustering, distribution, frequency).
2. Comparing categories across two dimensions (e.g., time vs. location).
3. Identifying anomalies or missing values.
4. Supporting decision-making through quick, intuitive visualization.

## Implementing Heatmaps in Python
In Python, heatmaps can be created using Seaborn or Matplotlib.
In the provided example, the dataset represents Posyandu (community health service) schedules across several days (columns) and facilities (rows).
Purpose of using a heatmap in this case is to:
1. Check schedule availability: whether a Posyandu has activities on a certain day.
2. Highlight distribution: colors indicate filled cells (scheduled activities) versus empty ones (no activity).
3. Support planning:
  Identify which Posyandu has the most scheduled events.
  See which days are busier.
  Detect gaps or empty slots for potential rescheduling.

<img width="623" height="527" alt="image" src="https://github.com/user-attachments/assets/9ed430c6-90cf-49ff-bf8e-17e270844471" />

The heatmap reveals uneven distribution of posyandu visits, with some facilities (e.g., F32, F63) overscheduled while others (e.g., F37, F43) are often left empty. Day 1 is the busiest, whereas Days 3 and 5 are lighter, leading to workload imbalance and unequal community services. To improve, schedules should be more evenly distributed across days and facilities, supported by regular monitoring through heatmap analysis to ensure balanced planning and optimal service quality.

## Code

### Install Package
pip install pandas matplotlib seaborn
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

### Data input
data = {
    "1": ["J3, J49", "J45", "J58", "J57, J43, J60", "J34, J52", "", "J44", "", "J11", "J10, J67", "J41, J36, J7", "J65, J62", "J13, J51"],
    "2": ["J19, J37", "J6, J48", "J20", "J35", "J34", "", "J17", "", "", "", "J12", "J24", "J56"],
    "3": ["J42, J53", "", "J27, J50", "J8, J33", "J38", "J23, J46", "", "", "", "J22", "", "", ""],
    "4": ["J5", "J68", "", "J21, J4", "", "J25, J59", "", "J18", "J16, J39", "J31, J40", "J47, J14", "", "J30"],
    "5": ["J1", "", "", "J2", "", "", "", "", "", "", "J61", "", ""]
}

index = ["F10", "F2", "F3", "F32", "F34", "F37", "F4", "F43", "F50", "F60", "F63", "F70", "F8"]

### Mengubah data menjadi DataFrame
df = pd.DataFrame(data, index=index)

### Fungsi untuk menghitung jumlah kunjungan per hari untuk setiap Puskesmas
def count_visits(entry):
    if pd.isna(entry) or entry == "":
        return 0
    else:
        # Hitung jumlah kunjungan dengan menghitung jumlah koma + 1
        return len(entry.split(", "))

### Terapkan fungsi ke seluruh DataFrame
visit_counts = df.applymap(count_visits)

### Menggunakan seaborn untuk membuat heatmap
plt.figure(figsize=(10, 8))
sns.heatmap(visit_counts, annot=True, fmt="d", cmap="viridis_r", cbar=True, linewidths=.5, linecolor='black')
plt.title("Jumlah Posyandu yang Dikunjungi")
plt.xlabel("Hari")
plt.ylabel("Puskesmas")
plt.show()


### Input Data from File
# Membaca data dari file Excel
df = pd.read_excel('Penjadwalan.xlsx', index_col='Puskesmas')

# Konversi data ke integer
df = df.astype(int)



