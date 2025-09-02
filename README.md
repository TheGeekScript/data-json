# Country State City Dataset

A comprehensive JSON dataset containing hierarchical geographic data for countries, states/provinces, cities, and country phone codes. This dataset is designed for developers, researchers, and applications requiring structured location data with telecommunications information.

![GitHub license](https://img.shields.io/github/license/TheGeekScript/data-json)
![Dataset Size](https://img.shields.io/badge/dataset-JSON-blue)
![Last Updated](https://img.shields.io/badge/updated-2025-green)
![Visitor Count](https://komarev.com/ghpvc/?username=TheGeekScript&repo=data-json)

## 📊 Dataset Overview

This repository provides a structured JSON dataset that includes:

- **Countries**: Complete list with ISO country codes
- **States/Provinces**: Administrative divisions within each country  
- **Cities**: Major cities within each state/province
- **Phone Country Codes**: International dialing codes for each country

### Key Features

- ✅ **Hierarchical Structure**: Country → State → City organization
- ✅ **ISO Standards**: Uses official country and state codes
- ✅ **Phone Codes**: International dialing prefixes included
- ✅ **Clean Format**: Well-structured JSON for easy parsing
- ✅ **Regular Updates**: Maintained with current geographic data
- ✅ **Open Source**: Free to use and contribute

## 📁 Dataset Structure

```json
[
  {
    "country": "United States",
    "countryCode": "US",
    "phoneCode": "+1",
    "states": [
      {
        "state": "California",
        "stateCode": "CA",
        "cities": [
          "Los Angeles",
          "San Francisco",
          "San Diego"
        ]
      }
    ]
  }
]
```

## 🚀 Usage Examples

### JavaScript/Node.js
```javascript
// Load the dataset
const locationData = require('./countries-states-cities.json');

// Find all states in a country
const usStates = locationData
  .find(country => country.countryCode === 'US')
  .states;

// Get phone code for a country
const phoneCode = locationData
  .find(country => country.country === 'India')
  .phoneCode;
```

### Python
```python
import json

# Load the dataset
with open('countries-states-cities.json', 'r') as f:
    location_data = json.load(f)

# Find cities in a specific state
def get_cities(country_name, state_name):
    for country in location_data:
        if country['country'] == country_name:
            for state in country['states']:
                if state['state'] == state_name:
                    return state['cities']
    return []

cities = get_cities('India', 'Maharashtra')
```

### PHP
```php
// Load the dataset
$locationData = json_decode(file_get_contents('countries-states-cities.json'), true);

// Search for country by phone code
function findCountryByPhoneCode($phoneCode, $data) {
    foreach ($data as $country) {
        if ($country['phoneCode'] === $phoneCode) {
            return $country;
        }
    }
    return null;
}
```

## 📈 Use Cases

- **Web Applications**: Location dropdowns and forms
- **Mobile Apps**: Address input and validation  
- **APIs**: Geographic data services
- **Analytics**: Location-based data analysis
- **E-commerce**: Shipping and billing addresses
- **Telecommunications**: Phone number validation
- **Research**: Geographic and demographic studies

## 🛠️ Data Sources & Methodology

The dataset is compiled from multiple authoritative sources:

- **ISO 3166**: Country and subdivision codes
- **ITU-T E.164**: International telephone numbering
- **OpenStreetMap**: Geographic boundary data
- **Government Sources**: Official administrative divisions
- **UN Statistics**: Standardized country information

### Data Quality
- Regular validation against official sources
- Automated consistency checks
- Community-driven corrections and updates
- UTF-8 encoding for international characters

## 📥 Installation & Setup

### Direct Download
```bash
# Clone the repository
git clone https://github.com/TheGeekScript/data-json.git

# Or download specific file
wget https://github.com/TheGeekScript/data-json/blob/main/countries.json
wget https://github.com/TheGeekScript/data-json/blob/main/country-codes.json
wget https://github.com/TheGeekScript/data-json/blob/main/countries_states_cities.json
```

### Package Managers
```bash
# NPM (if published)
npm install data-json

# Bower
bower install data-json
```

### CDN Usage
```html

<!-- Direct link to raw file countries data -->
<script src="https://cdn.jsdelivr.net/gh/TheGeekScript/data-json@main/countries.json"></script>

<!-- Direct link to raw file country codes data -->
<script src="https://cdn.jsdelivr.net/gh/TheGeekScript/data-json@main/country-codes.json"></script>

<!-- Direct link to raw file country state city data -->
<script src="https://cdn.jsdelivr.net/gh/TheGeekScript/data-json@main/countries_states_cities.json"></script>
```

## 🤝 Contributing

We welcome contributions to improve and expand this dataset!

### How to Contribute
1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/add-new-country`)
3. **Add/Update** data following the existing structure
4. **Validate** JSON format and schema compliance
5. **Commit** changes with clear messages
6. **Push** to your branch and create a **Pull Request**

### Contribution Guidelines
- Follow the existing JSON structure
- Verify data accuracy with official sources
- Include source citations for new data
- Test JSON validity before submitting
- Update documentation if needed

### Reporting Issues
Found incorrect data or missing information? Please [open an issue](../../issues) with:
- Specific location details
- Current vs. expected values
- Reliable source references

## 📋 Data Schema

```json
{
  "type": "array",
  "items": {
    "type": "object",
    "properties": {
      "country": {"type": "string"},
      "countryCode": {"type": "string", "pattern": "^[A-Z]{2}$"},
      "phoneCode": {"type": "string", "pattern": "^\\+[0-9]+$"},
      "states": {
        "type": "array",
        "items": {
          "type": "object",
          "properties": {
            "state": {"type": "string"},
            "stateCode": {"type": "string"},
            "cities": {
              "type": "array",
              "items": {"type": "string"}
            }
          }
        }
      }
    }
  }
}
```

## 📊 Statistics

- **Countries**: XXX total countries covered
- **States/Provinces**: X,XXX administrative divisions
- **Cities**: XX,XXX cities included  
- **Last Updated**: Month Year
- **File Size**: XXX KB (uncompressed)

## 🔄 Changelog

### Version 2.1.0 (2025-09-03)
- Added missing cities for Eastern European countries
- Updated phone codes for recent changes
- Fixed encoding issues for special characters
- Improved JSON structure validation

### Version 2.0.0 (2025-08-01)
- Major restructure with phone codes integration
- Added state/province codes where available
- Enhanced data validation pipeline
- Breaking changes in JSON schema

[See full changelog](CHANGELOG.md)

## 📄 License

This dataset is released under the **MIT License**. You are free to use, modify, and distribute this data in both personal and commercial projects.

```
MIT License - see LICENSE file for details
```

### Attribution
While not required, attribution is appreciated:
```
Data from Country State City Dataset (https://github.com/TheGeekScript/data-json)
```

## 🌐 API Integration

### REST API Example
If you're hosting this as an API:

```bash
# Get all countries
GET /api/countries

# Get states by country
GET /api/countries/US/states

# Get cities by state  
GET /api/countries/US/states/CA/cities

# Search by phone code
GET /api/phone-code/+1
```

## 🙏 Acknowledgments

- **Contributors**: All community members who helped improve this dataset
- **Data Sources**: Government agencies and international organizations
- **Tools**: Various validation and processing tools used
- **Inspiration**: Similar open-source geographic datasets

## 📞 Support & Contact

- **Issues**: [GitHub Issues](../../issues)
- **Discussions**: [GitHub Discussions](../../discussions) 
- **Email**: thegeekscript@aol.com
- **Documentation**: [Wiki Pages](../../wiki)

---

⭐ **If this dataset helped your project, please give it a star!** ⭐

**Keywords**: country data, state data, city data, phone codes, geographic dataset, JSON, location data, international dialing codes, administrative divisions
