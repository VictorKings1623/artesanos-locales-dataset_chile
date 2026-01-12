# Usage Examples - Local Artisans Dataset

This document provides practical examples of how to use the Chilean Local Artisans Dataset for various purposes.

## Loading the Dataset

### Python (Pandas)

```python
import pandas as pd

# Load CSV dataset
artisans_df = pd.read_csv('artisans_dataset.csv')

# Display basic information
print(artisans_df.info())
print(artisans_df.head())
```

### Python (JSON)

```python
import json

# Load JSON dataset
with open('artisans_dataset.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

artisans = data['artisans']
print(f"Total artisans: {len(artisans)}")
```

### JavaScript/Node.js

```javascript
const fs = require('fs');

// Load JSON dataset
const data = JSON.parse(fs.readFileSync('artisans_dataset.json', 'utf8'));
const artisans = data.artisans;

console.log(`Total artisans: ${artisans.length}`);
```

### R

```r
# Load CSV dataset
artisans <- read.csv('artisans_dataset.csv', encoding = 'UTF-8')

# Display structure
str(artisans)
head(artisans)
```

## Data Analysis Examples

### 1. Regional Distribution Analysis

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('artisans_dataset.csv')

# Count artisans by region
region_counts = df['region'].value_counts()
print(region_counts)

# Visualize
region_counts.plot(kind='barh', figsize=(10, 8))
plt.title('Artisans Distribution by Region')
plt.xlabel('Number of Artisans')
plt.tight_layout()
plt.savefig('regional_distribution.png')
```

### 2. Craft Types Analysis

```python
import pandas as pd

df = pd.read_csv('artisans_dataset.csv')

# Count by craft type
craft_counts = df['craft_type'].value_counts()
print("Craft Types Distribution:")
print(craft_counts)

# Analyze materials used
print("\nMaterials Analysis:")
for craft in df['craft_type'].unique():
    materials = df[df['craft_type'] == craft]['materials_used'].values[0]
    print(f"{craft}: {materials}")
```

### 3. Experience Level Analysis

```python
import pandas as pd
import numpy as np

df = pd.read_csv('artisans_dataset.csv')

# Experience statistics
print("Experience Statistics:")
print(f"Average years: {df['years_of_experience'].mean():.1f}")
print(f"Median years: {df['years_of_experience'].median():.1f}")
print(f"Min years: {df['years_of_experience'].min()}")
print(f"Max years: {df['years_of_experience'].max()}")

# Group by experience level
df['experience_level'] = pd.cut(df['years_of_experience'], 
                                bins=[0, 15, 25, 50],
                                labels=['Early Career', 'Experienced', 'Master'])
print("\nExperience Level Distribution:")
print(df['experience_level'].value_counts())
```

### 4. Cultural Heritage Mapping

```python
import pandas as pd

df = pd.read_csv('artisans_dataset.csv')

# Extract indigenous culture references
def extract_culture(background):
    cultures = []
    if 'mapuche' in background.lower():
        cultures.append('Mapuche')
    if 'aymara' in background.lower():
        cultures.append('Aymara')
    if 'chilota' in background.lower():
        cultures.append('Chilota')
    return ', '.join(cultures) if cultures else 'Regional'

df['indigenous_culture'] = df['cultural_background'].apply(extract_culture)

print("Cultural Heritage Distribution:")
print(df['indigenous_culture'].value_counts())
```

## Filtering and Searching

### Find Artisans by Region

```python
import pandas as pd

df = pd.read_csv('artisans_dataset.csv')

# Find all artisans in a specific region
region = "Región de La Araucanía"
artisans_in_region = df[df['region'] == region]

print(f"Artisans in {region}:")
for _, artisan in artisans_in_region.iterrows():
    print(f"- {artisan['name']}: {artisan['craft_type']}")
```

### Find Artisans by Craft Type

```python
import json

with open('artisans_dataset.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# Filter by craft type
craft = "Tejido"
weavers = [a for a in data['artisans'] if craft in a['craft_type']]

print(f"Artisans specializing in weaving ({len(weavers)}):")
for artisan in weavers:
    print(f"- {artisan['name']} ({artisan['city']}): {artisan['materials_used']}")
```

### Find Artisans by Material

```python
import pandas as pd

df = pd.read_csv('artisans_dataset.csv')

# Find artisans working with specific material
material = "lana"
artisans_with_material = df[df['materials_used'].str.contains(material, case=False, na=False)]

print(f"Artisans working with {material}:")
for _, artisan in artisans_with_material.iterrows():
    print(f"- {artisan['name']}: {artisan['craft_type']}")
```

## Data Validation

### Validate JSON Schema

```python
import json
import jsonschema
from jsonschema import validate

# Load schema and data
with open('schema.json', 'r') as f:
    schema = json.load(f)

with open('artisans_dataset.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# Validate
try:
    validate(instance=data, schema=schema)
    print("Dataset is valid according to schema!")
except jsonschema.exceptions.ValidationError as e:
    print(f"Validation error: {e.message}")
```

## Export and Conversion

### Convert CSV to JSON

```python
import pandas as pd
import json

# Read CSV
df = pd.read_csv('artisans_dataset.csv')

# Convert to JSON structure
artisans_list = df.to_dict('records')
output = {'artisans': artisans_list}

# Save to JSON
with open('artisans_export.json', 'w', encoding='utf-8') as f:
    json.dump(output, f, ensure_ascii=False, indent=2)

print("Converted CSV to JSON successfully!")
```

### Convert JSON to CSV

```python
import json
import pandas as pd

# Read JSON
with open('artisans_dataset.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# Convert to DataFrame and save
df = pd.DataFrame(data['artisans'])
df.to_csv('artisans_export.csv', index=False, encoding='utf-8')

print("Converted JSON to CSV successfully!")
```

## Visualization Examples

### Create a Geographic Distribution Map

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('artisans_dataset.csv')

# Create summary by region
region_summary = df.groupby('region').agg({
    'artisan_id': 'count',
    'craft_type': lambda x: ', '.join(x.unique())
}).rename(columns={'artisan_id': 'count', 'craft_type': 'crafts'})

print(region_summary)
```

### Experience vs Craft Type

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('artisans_dataset.csv')

# Box plot of experience by craft type
plt.figure(figsize=(12, 6))
df_plot = df.sort_values('years_of_experience')
sns.boxplot(data=df, x='craft_type', y='years_of_experience')
plt.xticks(rotation=45, ha='right')
plt.title('Experience Distribution by Craft Type')
plt.tight_layout()
plt.savefig('experience_by_craft.png')
```

## Integration Examples

### Create a Simple Web API

```python
from flask import Flask, jsonify
import pandas as pd

app = Flask(__name__)
df = pd.read_csv('artisans_dataset.csv')

@app.route('/api/artisans', methods=['GET'])
def get_all_artisans():
    return jsonify(df.to_dict('records'))

@app.route('/api/artisans/<int:artisan_id>', methods=['GET'])
def get_artisan(artisan_id):
    artisan = df[df['artisan_id'] == artisan_id]
    if artisan.empty:
        return jsonify({'error': 'Artisan not found'}), 404
    return jsonify(artisan.to_dict('records')[0])

@app.route('/api/regions', methods=['GET'])
def get_regions():
    regions = df['region'].unique().tolist()
    return jsonify({'regions': regions})

if __name__ == '__main__':
    app.run(debug=True)
```

### Database Import (SQLite)

```python
import pandas as pd
import sqlite3

# Load dataset
df = pd.read_csv('artisans_dataset.csv')

# Create database and import
conn = sqlite3.connect('artisans.db')
df.to_sql('artisans', conn, if_exists='replace', index=False)

# Query example
query = "SELECT name, craft_type, region FROM artisans WHERE years_of_experience > 25"
result = pd.read_sql_query(query, conn)
print(result)

conn.close()
```

## Statistical Analysis

### Correlation Analysis

```python
import pandas as pd
from scipy.stats import chi2_contingency

df = pd.read_csv('artisans_dataset.csv')

# Analyze relationship between region and craft type
contingency_table = pd.crosstab(df['region'], df['craft_type'])
chi2, p_value, dof, expected = chi2_contingency(contingency_table)

print(f"Chi-square statistic: {chi2}")
print(f"P-value: {p_value}")
print("\nContingency Table:")
print(contingency_table)
```

## Reporting

### Generate Summary Report

```python
import pandas as pd
from datetime import datetime

df = pd.read_csv('artisans_dataset.csv')

# Generate report
report = f"""
Chilean Local Artisans Dataset - Summary Report
Generated: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}

{'='*60}
DATASET OVERVIEW
{'='*60}
Total Artisans: {len(df)}
Regions Covered: {df['region'].nunique()}
Craft Types: {df['craft_type'].nunique()}

{'='*60}
EXPERIENCE STATISTICS
{'='*60}
Average Experience: {df['years_of_experience'].mean():.1f} years
Minimum Experience: {df['years_of_experience'].min()} years
Maximum Experience: {df['years_of_experience'].max()} years

{'='*60}
TOP 5 REGIONS
{'='*60}
{df['region'].value_counts().head().to_string()}

{'='*60}
CRAFT TYPES DISTRIBUTION
{'='*60}
{df['craft_type'].value_counts().to_string()}
"""

print(report)

# Save report
with open('dataset_summary_report.txt', 'w', encoding='utf-8') as f:
    f.write(report)
```

## Notes

- All examples use UTF-8 encoding to properly handle Spanish characters
- Replace file paths as needed based on your directory structure
- Install required packages: `pandas`, `matplotlib`, `seaborn`, `jsonschema`, `scipy`, `flask`
- For production use, implement proper error handling and validation
