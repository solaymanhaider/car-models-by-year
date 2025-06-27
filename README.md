# 🚗 Car Models by Year

A structured JSON file containing car brands, their models, and the years those models were available.

## 📂 File

- [`cars.json`](cars.json)  
  Contains a JSON array of car brands, with each brand having:
  - `name`: Brand name (e.g. `"BUICK"`)
  - `slug`: URL-friendly name (e.g. `"buick"`)
  - `years`: Array of model years and available models

---

## ✅ Use Cases

- Automotive apps or APIs
- Vehicle dropdown filters
- Historical model availability
- Car search or comparison tools
- ML and data analysis projects

---

## 💡 Example Usage

### 🔷 React (JavaScript)

```jsx
import { useEffect, useState } from 'react';

function CarModels() {
  const [carData, setCarData] = useState([]);

  useEffect(() => {
    fetch('/cars.json')
      .then(res => res.json())
      .then(data => setCarData(data));
  }, []);

  return (
    <div>
      <h1>Buick Models (1991)</h1>
      <ul>
        {carData
          .find(brand => brand.slug === 'buick')
          ?.years.find(y => y.year === 1991)
          ?.models.map(model => (
            <li key={model}>{model}</li>
          ))}
      </ul>
    </div>
  );
}

export default CarModels;
