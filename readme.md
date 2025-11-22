<h1>Retail Sales Analysis – Data Engineering Case Study</h1>

<p>
  This project focuses on building an end-to-end retail data analytics pipeline using
  <strong>AWS</strong>, <strong>Snowflake</strong>, and <strong>dbt Cloud</strong>, following the
  Medallion Architecture (Bronze → Silver → Gold). The dataset contains over a million
  anonymized retail order records, enabling detailed analysis of pricing trends, customer
  behavior, campaign effectiveness, and product return patterns.
</p>

<h2>📌 Project Overview</h2>

<p>The objectives of this case study include:</p>

<ul>
  <li>Designing a Snowflake-based data pipeline</li>
  <li>Implementing Medallion Architecture</li>
  <li>Building dimensional models and fact tables</li>
  <li>Preparing the data for dashboards, ML, and analytics</li>
</ul>

<p>
  Exploratory analysis identifies trends, anomalies, and patterns in customer orders,
  engagement, and campaign performance.
</p>

<h2>📊 Data Modeling (Star Schema)</h2>

<p>The data model uses a <strong>Star Schema</strong> optimized for analytical workloads.</p>

<h3>Core Tables</h3>

<ul>
  <li><strong>Fact Table:</strong> <code>FACT_SALES</code></li>
  <li><strong>Dimensions:</strong>
    <ul>
      <li><code>DIM_CUSTOMER</code></li>
      <li><code>DIM_SUPPLIER</code></li>
      <li><code>DIM_PART</code></li>
      <li><code>DIM_DATE</code></li>
      <li><code>DIM_NATION</code></li>
      <li><code>DIM_REGION</code></li>
    </ul>
  </li>
</ul>

<h3>Why Star Schema?</h3>

<ul>
  <li>Fast analytical query performance</li>
  <li>Flexible slicing/dicing across dimensions</li>
  <li>Separation of facts and descriptive attributes</li>
  <li>Snowflake-optimized columnar storage</li>
</ul>

<h3>FACT_SALES Includes</h3>

<ul>
  <li>Customer_SK, Part_SK, Supplier_SK, Nation_SK, Region_SK</li>
  <li>Order_Date_Key, Ship_Date_Key, Receipt_Date_Key</li>
  <li>Quantity, Extended Price, Discount, Tax</li>
</ul>

<h3>Dimension Attributes</h3>

<ul>
  <li>Customer demographics</li>
  <li>Supplier details</li>
  <li>Product details: brand, type, size, price</li>
  <li>Date attributes: Year, Month, Day, Quarter, Week</li>
  <li>Nation and Region metadata</li>
</ul>

<p>This schema supports downstream Silver & Gold modeling in Snowflake + dbt.</p>

<h2>🥉 Bronze Layer (Raw Layer)</h2>

<p>The <strong>Bronze Layer</strong> is the raw, unprocessed landing zone.</p>

<h3>Key Characteristics</h3>

<ul>
  <li>Stores raw files exactly as ingested</li>
  <li>No transformations or cleansing applied</li>
  <li>Loaded via <strong>Snowpipe</strong> from AWS S3</li>
  <li>Source of truth for auditing and reprocessing</li>
</ul>

<h3>Responsibilities of Bronze Layer</h3>

<ul>
  <li>Ingest files (CSV, Parquet, JSON) into Snowflake</li>
  <li>Use <code>STAGE</code> and <code>FILE FORMAT</code> configurations</li>
  <li>Automate ingestion using <strong>Snowpipe</strong></li>
  <li>Capture ingestion errors via Snowflake COPY validation</li>
</ul>

<h3>Typical Raw Tables</h3>

<ul>
  <li><code>RAW_CUSTOMER</code></li>
  <li><code>RAW_SUPPLIER</code></li>
  <li><code>RAW_PART</code></li>
  <li><code>RAW_NATION</code></li>
  <li><code>RAW_REGION</code></li>
  <li><code>RAW_LINEITEM</code></li>
  <li><code>RAW_ORDER</code></li>
</ul>

<p>
  These tables will be cleaned, standardized, and processed further in the Silver layer.
</p>
