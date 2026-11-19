# 📦 SupplyChainAI Agent (v1)
### Commercial-Grade Supply Chain Management & Predictive Analytics Platform

[![Java 19](https://img.shields.io/badge/Java-19%2B-orange.svg?style=flat-square&logo=openjdk)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.2.5-brightgreen.svg?style=flat-square&logo=springboot)](https://spring.io/projects/spring-boot)
[![Thymeleaf](https://img.shields.io/badge/Thymeleaf-3.1-005F0E.svg?style=flat-square&logo=thymeleaf)](https://www.thymeleaf.org/)
[![H2 Database](https://img.shields.io/badge/Database-H2_Embedded-blue.svg?style=flat-square)](https://www.h2database.com/)
[![Chart.js](https://img.shields.io/badge/Chart.js-4.4-FF6384.svg?style=flat-square&logo=chartdotjs)](https://www.chartjs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

> **SupplyChainAI Agent v1** is a full-featured SaaS application built with **Spring Boot 3.2.5**, **Thymeleaf**, and **Spring Security**. It delivers modern glassmorphism dashboards, interactive Chart.js visualizations, AI-driven demand and revenue forecasting, one-click PDF/Excel export generation, and complete CSV ingestion pipelines.

*Looking for the v2 distributed microservices architecture? Check out [SupplyChainAI-Agent-2](https://github.com/KarthikK04042006/SupplyChainAI-Agent-2).*

---

## ✨ Key Features & Capabilities

| Module | Features & Capabilities |
| :--- | :--- |
| 🛡️ **Authentication & Security** | Form-based login, self-registration, "Remember Me", session management, and server-side RBAC (`ROLE_ADMIN` vs `ROLE_USER`). |
| 📊 **Executive Dashboard** | 4 primary KPI cards (Total Orders, Revenue, Net Profit, Average Order Value), interactive Sales Trends, Regional Doughnut distribution, and Category Performance charts. |
| 📁 **CSV Ingestion Pipeline** | Drag-and-drop CSV upload with real-time progress indicators, column schema validation, and upload history tracking (compatible with global Superstore datasets). |
| 🧠 **Predictive AI Engine** | Demand trend predictions, revenue estimations, stockout risk gauges, confidence scoring, and automated reorder recommendations. |
| 📑 **Report Generation Center** | Production-ready one-click export to **PDF** (via iText 7), **Excel spreadsheets** (via Apache POI), and direct browser print stylesheets. |
| 🌓 **Glassmorphism UI & Dark Mode** | Built with CSS custom properties supporting instant dark mode toggling, accent color customization, and responsive mobile-first navigation. |
| ⚙️ **Admin Control Panel** | User management console (enable/disable, delete), database inspection via embedded H2 web console, and high-level system telemetry. |

---

## 🏛️ Application Architecture

```
  ┌─────────────────────────────────────────────────────────────┐
  │                 Client Browser / Desktop UI                 │
  │      (Thymeleaf Templates + Glassmorphism CSS + Chart.js)   │
  └──────────────────────────────┬──────────────────────────────┘
                                 │ HTTP / Form Actions / CSRF
  ┌──────────────────────────────▼──────────────────────────────┐
  │                   Spring Boot 3.2.5 Monolith                │
  │                                                             │
  │   [Security Layer]                                          │
  │   ├── BCrypt Password Encoder                               │
  │   └── Role-Based Access Filter (/admin/** vs /user/**)      │
  │                                                             │
  │   [Controller & Service Layer]                              │
  │   ├── Dashboard & Analytics Service                         │
  │   ├── Predictive AI Analytics Engine                        │
  │   ├── CSV Data Stream Parser & Validator                    │
  │   └── Document Exporters (iText PDF + Apache POI Excel)     │
  │                                                             │
  │   [Persistence Layer]                                       │
  │   └── Spring Data JPA + Hibernate ORM                       │
  └──────────────────────────────┬──────────────────────────────┘
                                 │ JDBC
  ┌──────────────────────────────▼──────────────────────────────┐
  │              H2 Embedded File Database                      │
  │            (jdbc:h2:file:./data/supplychain)                │
  └─────────────────────────────────────────────────────────────┘
```

---

## 🚀 Quickstart & Setup

### Prerequisites
* **Java 19** (or OpenJDK 19+)
* **Maven 3.8+**

### Build and Run

```bash
# Clone the repository
git clone https://github.com/KarthikK04042006/SupplyChainAI-Agent-1.git
cd SupplyChainAI-Agent-1/supply-chain-app

# Package and run
mvn clean package -DskipTests
java -jar target/supply-chain-ai-agent-1.0.0.jar
```

The application will start on **`http://localhost:8099`**.

### Default Demo Credentials

| Role | Username | Password | Access Scope |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin` | `admin123` | Full access (Dashboard, Analytics, Reports, Uploads, Admin Panel, H2 Console) |
| **User** | `demo` | `demo123` | Standard access (Dashboard, Analytics, Reports, Uploads) |

---

## 🗄️ Database & CSV Ingestion Schema

The app utilizes an embedded file-backed **H2 Database** (`./data/supplychain`).

### H2 Web Console
* **URL**: [http://localhost:8099/h2-console](http://localhost:8099/h2-console) *(requires Admin login)*
* **JDBC URL**: `jdbc:h2:file:./data/supplychain`
* **Username**: `sa` | **Password**: *(leave blank)*

### Supported CSV Format
Upload standard retail/supply chain CSV files containing the following headers:
```csv
Order ID, Order Date, Ship Date, Ship Mode, Customer ID, Customer Name,
Segment, Country, City, State, Region, Category, Sub-Category,
Product Name, Sales, Quantity, Discount, Profit, Shipping Cost, Order Priority
```

---

## 🛠️ Technology Stack

* **Framework**: Spring Boot 3.2.5
* **Security**: Spring Security 6 with BCrypt & CSRF protection
* **View Layer**: Thymeleaf 3 with Spring Security Dialect
* **Database**: H2 Database Engine (embedded file mode)
* **Document Exporting**: iText 7.2.5 (PDF), Apache POI 5.2.5 (Excel)
* **CSV Processing**: OpenCSV 5.9
* **Styling & Charts**: Bootstrap 5.3, Chart.js 4, FontAwesome 6, Inter Font

---

## 📄 License
This project is licensed under the [MIT License](LICENSE).
