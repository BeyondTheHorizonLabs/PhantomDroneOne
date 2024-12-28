# PhantomDroneOne

PhantomDroneOne is a specialized service-level application for collecting real-time telemetry data from drones. Acting as a companion plugin to **EctoProbe**, it provides live telemetry monitoring and streams data directly to EctoProbe or other centralized log systems for analysis. The application is designed to run directly on drones or field devices such as Raspberry Pi or Orange Pi, enabling robust, real-time environmental monitoring and anomaly detection.

---

## Features

- **Telemetry Monitoring**:
  - Collects live drone telemetry data, including:
    - **GPS coordinates**
    - **Flight data (altitude, speed, direction)**
    - **Sensor readings (temperature, pressure, etc.)**
  - Monitors for:
    - **GPS anomalies and missing data points**
    - **EMF interference**
    - **Signal disruptions causing potential malfunctions**
- **Data Streaming**:
  - Streams data to:
    - **EctoProbe** for visualization and administration.
    - **S3, OpenSearch, or RDBMS systems** for long-term storage.
  - Real-time integration with Prometheus and Loki for telemetry logs.
- **Field Deployment**:
  - Runs directly on drones or on field devices connected to drones.
  - Compatible with Raspberry Pi, Orange Pi, and other embedded systems.
- **Integration with BeyondTheHorizonLabs Ecosystem**:
  - Acts as a plugin for EctoProbe to expand telemetry visualization.
  - Seamlessly integrates with ParaSenseHub for centralized log collection.

---

## Importance

PhantomDroneOne is critical for ensuring safe and accurate drone operations in environments prone to:

- **GPS signal disruptions**:
  - Detects missing or inconsistent GPS data to prevent navigation errors.
- **Environmental anomalies**:
  - Identifies potential hazards, such as high EMF interference zones.
- **Telemetry analysis**:
  - Provides detailed flight data for investigating unusual drone behaviors.

By enabling real-time data collection and anomaly detection, PhantomDroneOne enhances the reliability of drones for applications in exotic physics research, UAP studies, and environmental monitoring.

---

## Prerequisites

- Node.js 18 or later.
- Compatible drone with telemetry sensors.
- Raspberry Pi, Orange Pi, or similar field device (optional for drone-embedded deployments).
- Access to a centralized log collection system (EctoProbe, S3, OpenSearch, etc.).

---

## Installation

1. Clone the PhantomDroneOne repository:

   ```bash
   git clone git@github.com:BeyondTheHorizonLabs/PhantomDroneOne.git
   cd PhantomDroneOne
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Configure the application by editing the `config.json` file:

   ```json
   {
     "logCollection": {
       "type": "opensearch",
       "host": "https://your-opensearch-instance",
       "port": 9200,
       "username": "admin",
       "password": "password"
     },
     "streaming": {
       "enabled": true,
       "ectoProbe": {
         "url": "http://ecto-probe-server:3000",
         "apiKey": "your-api-key"
       }
     },
     "devices": {
       "gps": true,
       "emf": true,
       "telemetry": true
     }
   }
   ```

4. Start the application:

   ```bash
   npm start
   ```

---

## Usage

### Integrating with EctoProbe

1. Ensure PhantomDroneOne is running on the configured drone or field device.
2. Update the EctoProbe configuration to include PhantomDroneOne as a data source:

   ```json
   {
     "phantomDroneOne": {
       "url": "http://drone-device:4000",
       "apiKey": "your-api-key"
     }
   }
   ```

3. Restart EctoProbe to start visualizing real-time drone telemetry data.

### Monitoring Telemetry Logs

- Use OpenSearch Dashboards, Grafana, or Graylog for real-time telemetry log visualization.
- Analyze flight patterns, GPS anomalies, and sensor readings for deeper insights.

---

## Contribution

We welcome contributions! Please see the [CONTRIBUTING.md](CONTRIBUTING.md) file for guidelines.

---

## License

This project is licensed under the [MIT License](LICENSE).
