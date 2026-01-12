# Local Artisans Dataset - Chile

A concise collection of artisan profiles including location, craft type, materials used, and cultural background to support heritage preservation and sustainable development initiatives.

## Overview

This dataset documents traditional artisans across Chile, capturing their craft practices, cultural heritage, and regional distribution. The data serves as a resource for:

- **Heritage Preservation:** Documenting traditional knowledge and cultural practices
- **Sustainable Development:** Supporting artisan livelihoods and fair-trade initiatives
- **Cultural Tourism:** Promoting authentic cultural experiences
- **Research:** Studying traditional craft techniques and indigenous knowledge systems

## Dataset Structure

The dataset is available in two formats:

### 1. CSV Format (`artisans_dataset.csv`)
A tabular format suitable for data analysis, spreadsheets, and database imports.

### 2. JSON Format (`artisans_dataset.json`)
A structured format with JSON Schema validation for programmatic access.

## Fields

Each artisan profile contains the following information:

| Field | Description |
|-------|-------------|
| `artisan_id` | Unique identifier |
| `name` | Full name of the artisan |
| `region` | Administrative region of Chile |
| `city` | City or town location |
| `craft_type` | Type of artisanal craft |
| `materials_used` | Primary materials and resources |
| `cultural_background` | Cultural heritage and traditional knowledge |
| `years_of_experience` | Years practicing the craft |
| `contact_info` | Contact information (anonymized for demonstration) |

## Geographic Coverage

The dataset includes artisans from all major regions of Chile:

- **Northern Chile:** Arica y Parinacota, Tarapacá, Antofagasta, Atacama
- **Central Chile:** Coquimbo, Valparaíso, Metropolitana, O'Higgins, Maule
- **Southern Chile:** Biobío, La Araucanía, Los Ríos, Los Lagos
- **Patagonia:** Aysén, Magallanes

## Craft Types Represented

The dataset includes diverse traditional crafts:

- **Textiles:** Mapuche weaving, Aymara textiles, wool weaving, embroidery
- **Ceramics & Pottery:** Quinchamalí pottery, traditional ceramics
- **Jewelry & Metalwork:** Silverwork, ethnic jewelry, goldsmithing
- **Natural Materials:** Basketry, leatherwork, woodworking
- **Stone Carving:** Combarbalita stone, ornamental carving

## Cultural Heritage

The dataset reflects Chile's rich cultural diversity, including:

- **Indigenous Cultures:** Mapuche, Aymara, Huilliche, Chilota traditions
- **Regional Practices:** Northern desert cultures, central valley traditions, Patagonian adaptations
- **Historical Influences:** Pre-Columbian techniques, colonial-era methods, local innovations

## Usage Examples

### Data Analysis
```python
import pandas as pd

# Load the dataset
df = pd.read_csv('artisans_dataset.csv')

# Analyze craft types by region
craft_distribution = df.groupby(['region', 'craft_type']).size()
print(craft_distribution)
```

### JSON Processing
```javascript
const fs = require('fs');

// Load the JSON dataset
const data = JSON.parse(fs.readFileSync('artisans_dataset.json', 'utf8'));

// Filter artisans by craft type
const weavers = data.artisans.filter(a => a.craft_type.includes('Tejido'));
console.log(weavers);
```

## Documentation

- **[Data Dictionary](data_dictionary.md):** Complete field descriptions and cultural context
- **[JSON Schema](schema.json):** Validation schema for the dataset structure

## Data Quality & Privacy

- All artisan names are representative examples
- Contact information is anonymized for demonstration purposes
- Cultural descriptions are simplified for dataset clarity
- Geographic distribution represents all major Chilean regions

## Applications

This dataset can support:

1. **Cultural Documentation:** Preserving knowledge of traditional crafts
2. **Economic Development:** Connecting artisans with markets and opportunities
3. **Tourism Initiatives:** Promoting cultural tourism and authentic experiences
4. **Educational Programs:** Teaching about Chilean cultural heritage
5. **Policy Development:** Informing cultural preservation policies
6. **Research Projects:** Studying traditional knowledge and craft techniques

## Contributing

This is a demonstration dataset. For real-world applications, consider:

- Obtaining proper consent from artisans
- Ensuring accurate cultural representation
- Protecting sensitive cultural knowledge
- Supporting fair compensation for artisan participation

## License

This dataset is provided for educational and demonstration purposes. When working with real artisan data, ensure compliance with:

- Cultural intellectual property rights
- Indigenous knowledge protocols
- Privacy regulations
- Fair-trade principles

## Contact

For questions or collaboration opportunities regarding this dataset structure, please refer to the repository documentation.

---

*This dataset supports UN Sustainable Development Goals: Goal 8 (Decent Work and Economic Growth), Goal 11 (Sustainable Cities and Communities), and Goal 12 (Responsible Consumption and Production).*
