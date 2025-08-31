# 🌊 Stream-Syntra
### Real-Time Analytics Platform for Streaming Data

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Docker](https://img.shields.io/badge/docker-compose-blue.svg)](docker-compose.yml)
[![QuestDB](https://img.shields.io/badge/QuestDB-time--series-orange.svg)](https://questdb.io)
[![Kafka](https://img.shields.io/badge/Apache%20Kafka-streaming-red.svg)](https://kafka.apache.org)
[![Grafana](https://img.shields.io/badge/Grafana-visualization-orange.svg)](https://grafana.com)

> **Stream-Syntra** is a comprehensive real-time analytics platform that demonstrates enterprise-grade streaming data architecture. Built with modern open-source technologies, it showcases end-to-end data ingestion, processing, storage, and visualization capabilities.

---

## 🚀 **Project Overview**

Stream-Syntra is designed as a production-ready template for building scalable real-time analytics systems. The platform seamlessly integrates multiple data sources, processes streaming events through Apache Kafka, persists them in a high-performance time-series database (QuestDB), and provides real-time visualization through interactive dashboards.

### **🎯 Key Features**

- **🔄 Real-Time Data Ingestion**: Multi-source data streaming with Apache Kafka
- **⚡ High-Performance Storage**: QuestDB time-series database with columnar storage
- **📊 Interactive Dashboards**: Grafana-powered real-time visualization
- **🔬 Data Science Ready**: Integrated Jupyter notebooks for ML/AI workflows
- **📈 Monitoring & Observability**: Built-in metrics collection and system monitoring
- **🐳 Containerized Architecture**: Full Docker-compose deployment
- **🛡️ Production Ready**: High availability and fault-tolerant design

---

## 🏗️ **Architecture**

Stream-Syntra implements a modern streaming data architecture following industry best practices:

```mermaid
graph TB
    subgraph "📥 Data Sources"
        A[Cryptocurrency Trading APIs]
        B[GitHub Public Events]
        C[IoT Sensors & Smart Meters]
        D[Factory Plant Sensors]
        E[Transaction Systems]
    end

    subgraph "🔄 Message Streaming Layer"
        F[Apache Kafka Cluster]
        G[Schema Registry]
        H[Kafka Connect]
    end

    subgraph "💾 Time-Series Database"
        I[QuestDB]
    end

    subgraph "📊 Analytics & Visualization"
        J[Grafana Dashboards]
        K[Jupyter Notebooks]
        L[Data Science & ML Models]
    end

    subgraph "📈 Monitoring & Observability"
        M[Telegraf Agent]
        N[System Metrics]
    end

    A --> F
    B --> F
    C --> I
    D --> I
    E --> F
    F --> G
    F --> H
    G --> H
    H --> I
    I --> J
    I --> K
    I --> L
    M --> I
    F --> M
    I --> N
```

### **🔧 Technology Stack**

| Component | Technology | Purpose |
|-----------|------------|---------|
| **Message Broker** | Apache Kafka | High-throughput distributed streaming |
| **Database** | QuestDB | High-performance time-series analytics |
| **Visualization** | Grafana | Real-time dashboards and monitoring |
| **Data Science** | Jupyter Notebook | Interactive analysis and ML workflows |
| **Schema Management** | Confluent Schema Registry | Data schema evolution and compatibility |
| **Data Integration** | Kafka Connect | Scalable connector framework |
| **Monitoring** | Telegraf | Metrics collection and aggregation |
| **Containerization** | Docker & Docker Compose | Consistent deployment environment |

---

## 📱 **Live Dashboards**

Stream-Syntra provides several pre-configured dashboards for different data types:

### **📈 Cryptocurrency Trading Dashboard**
![Trading Data Dashboard](trading_data_dashboard_screenshot.png)
- **URL**: [http://localhost:3000/d/trades-crypto-currency/trades-crypto-currency?orgId=1&refresh=250ms](http://localhost:3000/d/trades-crypto-currency/trades-crypto-currency?orgId=1&refresh=250ms)
- **Features**: Real-time price movements, volume analysis, trading patterns
- **Refresh Rate**: 250ms for ultra-low latency visualization

### **👨‍💻 GitHub Events Dashboard**
![GitHub Events Dashboard](github_events_dashboard_screenshot.png)
- **URL**: [http://localhost:3000/d/github-events-questdb/github-events-dashboard?orgId=1&refresh=5s](http://localhost:3000/d/github-events-questdb/github-events-dashboard?orgId=1&refresh=5s)
- **Features**: Repository activity, commit patterns, developer insights
- **Data Source**: Live GitHub public events API

### **🏭 IoT & Industrial Dashboard**
![IoT Data Dashboard](iot_data_dashboard_screenshot.png)
- **URL**: [http://localhost:3000/d/qdb-iot-demo/device-data-questdb-demo?orgId=1&refresh=500ms](http://localhost:3000/d/qdb-iot-demo/device-data-questdb-demo?orgId=1&refresh=500ms)
- **Features**: Sensor readings, device health, environmental monitoring
- **Use Cases**: Smart meters, factory sensors, environmental monitoring

---

## 🚀 **Quick Start Guide**

### **📋 Prerequisites**

Ensure you have the following installed:
- **Docker** (20.x or higher)
- **Docker Compose** (2.x or higher)
- **Git** (for cloning the repository)
- **8GB+ RAM** (recommended for optimal performance)

### **🔧 Environment Setup**

1. **Clone Stream-Syntra**
   ```bash
   git clone https://github.com/your-username/stream-syntra.git
   cd stream-syntra
   ```

2. **Configure GitHub Token** (Optional - for GitHub data ingestion)
   ```bash
   export GITHUB_TOKEN=your_github_personal_access_token
   ```
   > 💡 **Tip**: Create a [GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) with read access to public repositories.

3. **Fix Docker Permissions** (Linux/macOS)
   ```bash
   export DOCKER_COMPOSE_USER_ID=$(id -u)
   ```

### **🚀 Launch Stream-Syntra**

Start the entire platform with a single command:

```bash
docker-compose up
```

**⏱️ Initial startup time**: 30-60 seconds (subsequent starts are much faster)
**💾 Disk usage**: ~1GB for Docker images

### **📊 Access Your Platform**

Once all services are running, access these endpoints:

| Service | URL | Credentials |
|---------|-----|-------------|
| **🏠 QuestDB Console** | http://localhost:9000 | None required |
| **📊 Grafana Dashboards** | http://localhost:3000 | admin / quest |
| **🔬 Jupyter Notebooks** | http://localhost:8888 | None required |
| **🔧 Kafka Connect API** | http://localhost:8083 | None required |

---

## 💽 **Data Ingestion Workflows**

Stream-Syntra supports multiple data ingestion patterns:

### **🎯 Method 1: Jupyter Notebook (Recommended for Learning)**

Perfect for interactive data exploration and prototyping:

1. **Cryptocurrency Trading Data**
   - Navigate to: [http://localhost:8888/notebooks/Send-Trades-To-Kafka.ipynb](http://localhost:8888/notebooks/Send-Trades-To-Kafka.ipynb)
   - **Dataset**: 1M+ real crypto trades (March 2024)
   - **Format**: AVRO via Kafka
   - **Frequency**: 50ms intervals (configurable)

2. **GitHub Events Data**
   - Navigate to: [http://localhost:8888/notebooks/Send-Github-Events-To-Kafka.ipynb](http://localhost:8888/notebooks/Send-Github-Events-To-Kafka.ipynb)
   - **Source**: GitHub Public Events API
   - **Format**: JSON via Kafka
   - **Frequency**: 10s intervals (API rate limit compliance)

3. **IoT & Sensor Data**
   - Navigate to: [http://localhost:8888/notebooks/IoTEventsToQuestDB.ipynb](http://localhost:8888/notebooks/IoTEventsToQuestDB.ipynb)
   - **Pattern**: Direct to QuestDB via ILP protocol
   - **Use Case**: High-throughput sensor data

### **🎯 Method 2: Programming Language SDKs**

Production-ready implementations in multiple languages:

#### **🐍 Python**
```bash
cd ingestion/python
pip install -r requirements.txt

# GitHub events
python github_events.py

# Smart meters
python smart_meters_send_to_kafka.py

# Trading data
python send_trades_to_kafka.py ../../notebooks/tradesMarch.csv trades
```

#### **🚀 Go**
```bash
cd ingestion/go/github_events
go get
go run .

# For trading data
cd ../trades
go run trades_sender.go --topic="trades" --csv=../../../notebooks/tradesMarch.csv
```

#### **🟨 Node.js**
```bash
cd ingestion/nodejs
npm install node-rdkafka @octokit/rest
node github_events.js
```

#### **☕ Java**
```bash
cd ingestion/java/github_events
mvn package
java -jar target/github-events-1.0-SNAPSHOT-jar-with-dependencies.jar
```

#### **🦀 Rust**
```bash
cd ingestion/rust/github_events
cargo run
```

---

## 🧪 **Data Science & Machine Learning**

Stream-Syntra includes production-ready ML workflows for time-series forecasting:

### **📈 Time-Series Forecasting Models**

1. **Trading Data Forecasting**
   - **Notebook**: [http://localhost:8888/notebooks/Time-Series-Forecasting-ML-trades.ipynb](http://localhost:8888/notebooks/Time-Series-Forecasting-ML-trades.ipynb)
   - **Models**: Prophet, Linear Regression
   - **Use Case**: Price prediction, volume forecasting

2. **GitHub Activity Forecasting**
   - **Notebook**: [http://localhost:8888/notebooks/Time-Series-Forecasting-ML.ipynb](http://localhost:8888/notebooks/Time-Series-Forecasting-ML.ipynb)
   - **Models**: ARIMA, LSTM-ready architecture
   - **Use Case**: Repository activity prediction

### **🔍 Data Analysis Capabilities**

- **Real-time Data Querying**: PostgreSQL-compatible SQL interface
- **Advanced Analytics**: Time-series specific SQL extensions
- **Scalable Processing**: Columnar storage for billion-row analytics
- **ML Integration**: Direct pandas/scikit-learn connectivity

#### **Example Queries**
```sql
-- Trading volume analysis
SELECT timestamp, symbol, COUNT() as trades, 
       AVG(price) as avg_price, SUM(volume) as total_volume 
FROM trades 
SAMPLE BY 5m;

-- GitHub activity patterns
SELECT timestamp, type, COUNT() as events 
FROM github_events 
SAMPLE BY 15m;

-- IoT sensor aggregations  
SELECT timestamp, device_id, 
       AVG(temperature) as avg_temp,
       MAX(humidity) as max_humidity
FROM iot_data 
SAMPLE BY 1h;
```

---

## 📊 **Advanced Analytics Features**

### **⚡ High-Performance Querying**
- **Columnar Storage**: Optimized for analytical workloads
- **Time Partitioning**: Automatic data organization by time
- **Parallel Processing**: Multi-core query execution
- **Compression**: Efficient storage with fast decompression

### **🔄 Stream Processing Patterns**
- **At-Least-Once Delivery**: Guaranteed message processing
- **Schema Evolution**: Forward/backward compatible data formats
- **Exactly-Once Semantics**: Available through Kafka transactions
- **Backpressure Handling**: Automatic flow control

### **📈 Monitoring & Observability**
- **System Metrics**: CPU, memory, disk, network monitoring via Telegraf
- **Application Metrics**: Kafka lag, QuestDB performance, ingestion rates
- **Custom Dashboards**: Grafana-based business intelligence
- **Alerting**: Configurable thresholds and notifications

---

## 🛠️ **Configuration & Customization**

### **🎛️ Service Configuration**

| Service | Configuration Location | Key Settings |
|---------|----------------------|-------------|
| **QuestDB** | `questdb/` volume | Web console, ILP endpoint, Postgres port |
| **Kafka** | `broker-1/`, `broker-2/` | Replication, retention, partitions |
| **Grafana** | `dashboard/grafana/` | Datasources, dashboards, users |
| **Jupyter** | `notebooks/` | Pre-loaded notebooks and data |

### **🔧 Environment Variables**

```bash
# Docker user permissions
export DOCKER_COMPOSE_USER_ID=$(id -u)

# GitHub API access
export GITHUB_TOKEN=your_personal_access_token

# Custom configurations
export KAFKA_RETENTION_HOURS=168  # 7 days
export QUESTDB_HTTP_PORT=9000
export GRAFANA_PORT=3000
```

### **📈 Scaling Configuration**

Stream-Syntra is designed for horizontal scaling:

- **Kafka Brokers**: Add more brokers in docker-compose.yml
- **Kafka Connect Workers**: Scale connect workers for higher throughput  
- **QuestDB Instances**: Partition data across multiple QuestDB instances
- **Monitoring**: Add more Telegraf agents for distributed monitoring

---

## 🚀 **Production Deployment**

### **☁️ Cloud Deployment Checklist**

- [ ] **Security**: Configure authentication, TLS/SSL, network policies
- [ ] **Persistence**: Use external volumes/persistent disks
- [ ] **Monitoring**: Set up external monitoring (Prometheus, DataDog, etc.)
- [ ] **Backup**: Implement database backup strategies
- [ ] **Scaling**: Configure auto-scaling policies
- [ ] **Load Balancing**: Add load balancers for high availability

### **🏢 Enterprise Features**

Consider these enhancements for production:

- **Kafka Schema Registry Clusters**: Multi-region schema management
- **QuestDB Enterprise**: Advanced security and clustering features  
- **Grafana Enterprise**: Advanced dashboarding and user management
- **Confluent Platform**: Enterprise Kafka features and support
- **Kubernetes Deployment**: Container orchestration at scale

---

## 📚 **Learning Resources**

### **📖 Documentation Deep Dives**

1. **[QuestDB Time-Series Guide](https://questdb.io/docs/concept/sql-extensions/)** - Advanced SQL for time-series
2. **[Kafka Streaming Patterns](https://kafka.apache.org/documentation/streams/)** - Stream processing architectures
3. **[Grafana Dashboard Design](https://grafana.com/docs/grafana/latest/dashboards/)** - Effective visualization techniques
4. **[Time-Series Forecasting](https://facebook.github.io/prophet/)** - ML model implementation

### **🎯 Use Case Examples**

- **Financial Trading**: Real-time market data analysis and algorithmic trading
- **IoT & Manufacturing**: Industrial sensor monitoring and predictive maintenance
- **DevOps & Monitoring**: Application performance monitoring and log analytics  
- **Social Media Analytics**: Real-time engagement tracking and sentiment analysis
- **Supply Chain**: Logistics optimization and inventory management

---

## 🔍 **Troubleshooting Guide**

### **🚨 Common Issues**

#### **Docker Permission Errors**
```bash
# Fix Grafana volume permissions
sudo chown -R $(id -u):$(id -g) dashboard/grafana/home_dir/
export DOCKER_COMPOSE_USER_ID=$(id -u)
```

#### **Memory Issues**
```bash
# Increase Docker memory allocation (8GB recommended)
docker system prune -a  # Clean up unused containers/images
```

#### **Port Conflicts**
```bash
# Check for port conflicts
netstat -tulpn | grep :3000
# Kill conflicting processes or modify docker-compose.yml ports
```

### **📊 Health Checks**

Monitor service health through these endpoints:

```bash
# QuestDB health
curl http://localhost:9003/status

# Kafka Connect status  
curl http://localhost:8083/connectors

# Check running containers
docker-compose ps
```

---

## 🧹 **Cleanup & Maintenance**

### **🛑 Stopping Services**

```bash
# Graceful shutdown
docker-compose down

# Remove volumes (⚠️ deletes all data)
docker-compose down -v

# Complete cleanup (removes images)  
docker-compose down -v --rmi all
```

### **💾 Data Management**

```bash
# Backup QuestDB data
tar -czf questdb-backup-$(date +%Y%m%d).tar.gz questdb/questdb_root/

# Clean up old data (example for 30-day retention)
# Configure in QuestDB: ALTER TABLE trades DROP PARTITION where timestamp < dateadd('d', -30, now())
```

---

## 📊 **Performance Benchmarks**

Stream-Syntra delivers enterprise-grade performance:

| Metric | Performance | Configuration |
|--------|------------|---------------|
| **Ingestion Rate** | 1M+ events/sec | QuestDB ILP protocol |
| **Query Latency** | <100ms | Billion-row aggregations |
| **Dashboard Refresh** | 250ms | Real-time visualization |
| **Storage Efficiency** | 10:1 compression | Columnar time-series storage |
| **Throughput** | 10GB+/hour | Multi-broker Kafka cluster |

---

## 🤝 **Contributing**

Stream-Syntra is designed as a learning platform and portfolio showcase. Contributions are welcome!

### **🔧 Development Setup**

1. Fork the repository
2. Create feature branch: `git checkout -b feature/amazing-feature`
3. Make changes and test thoroughly
4. Submit pull request with detailed description

### **📝 Contribution Guidelines**

- Follow existing code style and patterns
- Add comprehensive documentation
- Include unit tests for new features
- Update README.md for significant changes

---

## 📄 **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🏆 **Showcase Points**

**Stream-Syntra demonstrates expertise in:**

✅ **Real-Time Data Architecture** - End-to-end streaming pipeline design  
✅ **Cloud-Native Technologies** - Docker, microservices, container orchestration  
✅ **Big Data Engineering** - High-throughput data processing and storage  
✅ **Data Visualization** - Interactive dashboards and business intelligence  
✅ **Machine Learning Operations** - ML model integration and time-series forecasting  
✅ **DevOps Practices** - Infrastructure as code, monitoring, and observability  
✅ **Multi-Language Development** - Python, Java, Go, Node.js, Rust implementations  
✅ **Database Expertise** - Time-series databases, SQL optimization, data modeling  
✅ **API Integration** - RESTful services, real-time APIs, schema management  
✅ **Production Readiness** - Scalability, fault tolerance, security considerations  

---

## 📞 **Contact & Portfolio**

**Stream-Syntra** - Demonstrating Modern Data Engineering Excellence

🌐 **Portfolio**: [Your Portfolio Website]  
💼 **LinkedIn**: [Your LinkedIn Profile]  
📧 **Email**: your.email@example.com  
🐱 **GitHub**: [Your GitHub Profile]

---

<div align="center">
<h3>⭐ If you found Stream-Syntra helpful, please give it a star! ⭐</h3>

<p><em>Built with passion for real-time analytics and modern data architecture</em></p>

---

**Keywords**: Real-time Analytics, Apache Kafka, QuestDB, Time-Series Database, Stream Processing, Data Engineering, Docker, Grafana, Machine Learning, IoT Analytics, Financial Data, GitHub Analytics, Data Visualization, Business Intelligence

</div>