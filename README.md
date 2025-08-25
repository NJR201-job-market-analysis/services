# 服務 (Services)

本目錄包含「就業市場分析平台」所有後端服務的設定與部署文件。

## 專案用途

此專案旨在建立一個功能強大的就業市場資料分析平台。所有服務都被容器化，並設計為在 **Docker Swarm** 環境中進行部署與管理，以實現高可用性與擴展性。

## 架構特色

-   **分散式爬蟲**: 平台的資料收集核心是一個分散式爬蟲系統。`producer` 服務負責產生爬取任務，而多個 `worker` 服務可以同時消費這些任務，從而實現高效、可擴展的網頁資料抓取。
-   **Docker Swarm 叢集**: 所有的服務都透過 Docker Compose 文件進行定義，這些文件同樣適用於 Docker Swarm 的部署。這使得服務的管理、擴展和負載平衡變得簡單而高效。

## 檔案說明

以下是本地區中主要設定檔案的用途簡介：

-   **`compose.api.yml`**: 定義核心 API 服務。
-   **`compose.producer.yml`**: 定義分散式爬蟲的**任務生產者**服務。
-   **`compose.worker.yml`**: 定義分散式爬蟲的**任務消費者**服務，可水平擴展。
-   **`compose.mysql.yml`**: 定義 MySQL 資料庫服務。
-   **`compose.rabbitmq.yml`**: 定義 RabbitMQ 訊息佇列服務，用於爬蟲任務的派發。
-   **`compose.airflow.yml`**: 定義 Apache Airflow 工作流程排程服務。
-   **`compose.airflow.gce.yml`**: Airflow 在 Google Cloud Engine (GCE) 環境的特定設定。
-   **`portainer.yml`**: 定義 Portainer 服務，一個 Docker 圖形化管理介面，支援 Swarm 模式。
-   **`Pipfile`**: 定義 Python 專案的相依套件。
-   **`.gitignore`**: Git 版本控制的忽略清單。

## 部署教學

關於詳細的環境設定與部署教學 (包含 Docker Swarm 的設定)，請參考 `../docs/environment-and-deployment.md` 文件。