# Explore Azure Databricks

This lab guides you through exploring Azure Databricks, provisioning a workspace, creating a cluster, and analyzing data using both SQL and PySpark.

## Lab Title
**Explore Azure Databricks**

Azure Databricks is a Microsoft Azure-based version of the popular open-source Databricks platform. This lab introduces key concepts and capabilities of Azure Databricks.

**Estimated Time**: 20 minutes

---

## Prerequisites
- An active Azure subscription with administrative access.

---

## Provision an Azure Databricks Workspace

> 💡 *Tip: If you already have an Azure Databricks workspace, skip this step.*

1. Sign into the Azure portal: [https://portal.azure.com](https://portal.azure.com)
2. Create a new Azure Databricks resource with the following settings:
   - **Subscription**: Your Azure subscription
   - **Resource group**: `msl-xxxxxxx`
   - **Workspace name**: `databricks-xxxxxxx`
   - **Region**: Any available region
   - **Pricing tier**: Premium or Trial
   - **Managed Resource Group**: `databricks-xxxxxxx-managed`
3. Select **Review + create** and wait for the deployment to complete.
4. Go to the resource and **Launch Workspace**.

---

## Create a Cluster

1. In the Databricks workspace, click **+ New** > **Cluster**.
2. Use the following settings:
   - **Cluster name**: Your Name's Cluster
   - **Policy**: Unrestricted
   - **Cluster mode**: Single Node
   - **Access mode**: Single user
   - **Databricks Runtime Version**: 13.3 LTS or later
   - **Use Photon Acceleration**: Enabled
   - **Node type**: `Standard_D4ds_v5`
   - **Terminate after inactivity**: 20 minutes
3. Wait for the cluster to be provisioned.

---

## Use Spark to Analyze Data

1. Download `products.csv` from:
   [Download Link](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-databricks/main/data/products.csv)
2. In Databricks sidebar, go to **+ New** > **Add or upload data**.
3. Upload the `products.csv` file and create a table:
   - **Catalog**: `hive_metastore`
   - **Schema**: `default`
   - **Table Name**: `products`
4. Open **Catalog Explorer**, select the `products` table and click **Create > Notebook**.

### Run SQL to View Data

In the notebook:
```sql
%sql
SELECT * FROM `hive_metastore`.`default`.`products`;
Create a Visualization

    Click + Visualization above the result table.

    Set the following:

        Type: Bar

        X Column: Category

        Y Column: ProductID with Count aggregation

    Save the visualization.
