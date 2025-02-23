# Logging System with ELK Stack

### Prerequisites

- Docker and Docker Compose installed on your system
- Git for cloning the repository

### Installation

1. Clone the repository:
```bash
git clone git@github.com:fauzank8s/logging-system-elk.git
```

2. Navigate to the project directory and start the containers:
```bash
cd logging-system-elk
docker compose up -d
```

3. Copy the CA certificate from the Elasticsearch container:
```bash
docker cp logging-system-elk-es01-1:/usr/share/elasticsearch/config/certs/ca/ca.crt /tmp/.
```

4. Verify Elasticsearch is running:
```bash
curl --cacert /tmp/ca.crt -u elastic:changeme https://localhost:9200
```

## 🔧 Configuration

### Kibana Setup

1. Access Kibana web interface:
   - URL: http://localhost:5601
   - Default credentials:
     - Username: elastic
     - Password: changeme

2. Create index patterns:
   - Navigate to Stack Management → Index Patterns → Create index pattern
   - Create the following patterns:
     - `logs-*` for application logs
     - `metrics-*` for system metrics
