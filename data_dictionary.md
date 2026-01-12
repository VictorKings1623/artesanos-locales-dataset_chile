# Data Dictionary - Local Artisans Dataset (Chile)

## Overview
This document describes the structure and meaning of each field in the artisans dataset.

## Field Descriptions

### artisan_id
- **Type:** Integer
- **Description:** Unique identifier for each artisan in the dataset
- **Example:** 1, 2, 3

### name
- **Type:** String
- **Description:** Full name of the artisan
- **Example:** "María González"

### region
- **Type:** String
- **Description:** Administrative region of Chile where the artisan is based
- **Valid Values:** Any of the 16 regions of Chile
- **Example:** "Región Metropolitana", "Región de Los Lagos"

### city
- **Type:** String
- **Description:** City or town where the artisan operates
- **Example:** "Santiago", "Puerto Montt"

### craft_type
- **Type:** String
- **Description:** Primary type of craft or artisanal work
- **Examples:** 
  - Cerámica (Ceramics)
  - Tejido en lana (Wool weaving)
  - Orfebrería (Goldsmithing)
  - Cestería (Basketry)
  - Textiles mapuche (Mapuche textiles)
  - Tallado en piedra (Stone carving)

### materials_used
- **Type:** String (comma or hyphen separated)
- **Description:** Primary materials and resources used in the artisan's craft
- **Example:** "Arcilla greda roja", "Lana de oveja chilota - tintes naturales"

### cultural_background
- **Type:** String
- **Description:** Cultural heritage, traditions, and knowledge systems that inform the artisan's practice
- **Example:** "Tradición familiar mapuche - técnicas ancestrales de alfarería"
- **Notes:** This field captures:
  - Indigenous heritage (Mapuche, Aymara, etc.)
  - Family traditions
  - Regional cultural practices
  - Historical influences

### years_of_experience
- **Type:** Integer
- **Description:** Number of years the artisan has been practicing their craft
- **Example:** 25, 18, 30

### contact_info
- **Type:** String
- **Description:** Contact information for the artisan (email format)
- **Example:** "maria.gonzalez@example.cl"
- **Privacy Note:** Contact information in this dataset is anonymized for demonstration purposes

## Cultural Context

### Indigenous Cultures Referenced
- **Mapuche:** The largest indigenous group in Chile, primarily in southern regions
- **Aymara:** Indigenous people from the Altiplano region in northern Chile
- **Chilota:** Cultural identity from Chiloé Island with unique traditions
- **Huilliche:** Mapuche subgroup from southern Chile

### Traditional Craft Types
- **Cerámica Quinchamalí:** Black pottery from the Quinchamalí area using traditional techniques
- **Tejidos Mapuche:** Traditional Mapuche textiles with symbolic patterns
- **Tejidos Aymaras:** Andean textiles with geometric designs
- **Cestería:** Traditional basketry using native plant fibers

## Usage Guidelines

### Heritage Preservation
This dataset supports:
- Documentation of traditional knowledge
- Recognition of indigenous and local craft traditions
- Preservation of cultural techniques and practices

### Sustainable Development
This dataset facilitates:
- Connection between artisans and fair-trade markets
- Promotion of sustainable livelihood opportunities
- Economic empowerment of traditional craftspeople
- Support for cultural tourism initiatives

## Data Quality Notes
- All artisan names are representative examples
- Contact information is anonymized
- Cultural descriptions are simplified for dataset purposes
- Geographic distribution covers all major regions of Chile
