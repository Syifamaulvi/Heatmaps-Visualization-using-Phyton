# Heatmaps Visualization

## What is Heatmaps?
A heatmap is a two-dimensional visualization of data that uses color to represent numerical values. This can be either different intensities of the same hue, or different colors from a palette. Heatmap represents data values through colors, each cell in a table or matrix is shaded according to its value. Higher or more significant values are usually displayed in darker/stronger colors, while lower or missing values are shown in lighter colors.

Heatmapswereimportedintocartographyfromdatavisualization techniques, similar  to other maptypesalreadywellestablishedincartography, suchasdiagrams, charts, dots or choropleths.  Heat maps are not necessarily connected strictly to geography. They aresed in medicine, chemistry, biology and ecology, the social sciences for non spatial data, and eye-tracker analysis.

<img width="712" height="356" alt="image" src="https://github.com/user-attachments/assets/e5170d9c-15ab-4d61-878b-65846e2e5782" />

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

<img width="623" height="527" alt="image" src="https://github.com/user-attachments/assets/9ed430c6-90cf-49ff-bf8e-17e270844471" />

Detect gaps or empty slots for potential rescheduling.
