# Assignment-staynest-azure-data-factory-week_05
Azure Data Factory StayNest assignment — building a data movement pipeline using Linked Service, datasets, Copy Data, Get Metadata, and an optional metadata-driven ForEach pipeline to move raw CSV files into the Bronze layer.

# 🏨 StayNest — Azure Data Factory Assignment

An end-to-end **Azure Data Factory (ADF) data orchestration assignment** based on the StayNest hotel booking platform.

The project demonstrates how Azure Data Factory can be used to ingest raw CSV files from Azure Data Lake Storage and move them into a Bronze layer using a **metadata-driven pipeline**.

---

## 📌 Project Overview

StayNest receives multiple CSV files containing hotel booking-related data.

The objective of this assignment is to build an automated data pipeline that:

1. Connects Azure Data Factory with Azure Storage.
2. Reads files from the **Raw** layer.
3. Dynamically identifies files available in the Raw folder.
4. Uses a **ForEach** activity to process each file.
5. Copies each file into the **Bronze** layer.
6. Preserves the original filename.
7. Uses GitHub for version control of the ADF project.

---

## 🏗️ Architecture

```text
                Azure Data Factory
                       │
                       │
                Linked Service
                       │
                       ▼
              Azure Data Lake Storage
                       │
                       ▼
                  RAW LAYER
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
     hotels.csv   customers.csv  bookings.csv
          │            │            │
          └────────────┼────────────┘
                       │
                       ▼
                 Get Metadata
                       │
                       ▼
                    ForEach
                       │
                 @item().name
                       │
                       ▼
                  Copy Data
                       │
                       ▼
                 BRONZE LAYER
                       │
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
     hotels.csv   customers.csv  bookings.csv
