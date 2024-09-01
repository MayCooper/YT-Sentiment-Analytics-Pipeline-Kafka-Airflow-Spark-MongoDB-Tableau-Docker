# YouTube Sentiment Analytics Pipeline: Using Kafka, Airflow, Spark, MongoDB, Tableau, Docker

A comprehensive pipeline for performing sentiment analysis on YouTube comments using Python, Kafka, Airflow, Spark, and MongoDB. The project includes data processing and visualization with Tableau, with core components containerized in Docker for seamless deployment.

### Overview
The **YouTube Sentiment Analytics Pipeline** is an end-to-end data processing pipeline designed to extract, process, analyze, and visualize sentiment data from YouTube comments. This project aims to provide actionable insights into the sentiment expressed by viewers on YouTube, enabling content creators, marketers, and researchers to understand audience reactions in a scalable and automated manner.

### Objectives
The primary objectives of this project are:
- **Automated Data Ingestion**: Seamlessly fetch and ingest comments from specified YouTube videos in near real-time using the YouTube Data API.
- **Scalable Data Processing**: Handle large volumes of comment data through distributed processing, ensuring the pipeline can scale as data volumes grow.
- **Sentiment Analysis**: Apply natural language processing techniques to assess the sentiment of each comment, categorizing them as positive, negative, or neutral.
- **Data Storage and Accessibility**: Store the processed comments and sentiment scores in a NoSQL database (MongoDB) for easy querying and further analysis.
- **Visualization**: Provide an intuitive and insightful visualization of sentiment trends over time and across different videos using Tableau, enabling stakeholders to make data-driven decisions.
- **Modular and Extensible Architecture**: Design the pipeline with modularity in mind, allowing for easy integration of additional features or adaptation to new data sources.

### Pipeline Components
The pipeline is composed of several integrated components, each responsible for a specific part of the process:

1. **YouTube Data API**  
   This API is used to fetch comments from YouTube videos. The pipeline can be configured to target specific videos or channels, allowing for tailored sentiment analysis.

   ![image](https://github.com/user-attachments/assets/5c2aa9b8-089b-4fe9-b944-237a010b8cd4)
   ![image](https://github.com/user-attachments/assets/0957926f-d53c-4f47-a8dc-e41aca423d69)

2. **Apache Kafka**  
   Kafka serves as the backbone of the data streaming process, enabling real-time ingestion and transmission of comments to the processing component. It ensures that the data flows smoothly through the pipeline and can handle large-scale data ingestion without bottlenecks.

   ![image](https://github.com/user-attachments/assets/3012b8de-9e5c-48b3-bd7a-79f0cb5ec76a)

3. **Apache Airflow**  
   Airflow orchestrates the entire workflow, managing task dependencies, scheduling, and monitoring the execution of each stage in the pipeline. It provides a clear and user-friendly interface to manage and monitor the pipeline's operations.

   ![image](https://github.com/user-attachments/assets/f599d395-80e1-4893-84ac-42b0ba22b20f)
   ![image](https://github.com/user-attachments/assets/3baa6d12-40ac-429a-9ec9-32727e534d51)

4. **Apache Spark**  
   Spark is employed for distributed data processing, enabling the pipeline to handle large datasets efficiently. Spark processes the comments in parallel, performing necessary transformations and sentiment analysis at scale.

5. **Sentiment Analysis with Python**  
   Leveraging Python's powerful natural language processing libraries, the pipeline performs sentiment analysis on the fetched comments. Each comment is analyzed and categorized based on its sentiment, providing a quantitative measure of audience reactions.

   ![image](https://github.com/user-attachments/assets/8aa4267f-7064-486a-b5ac-69d06ddcd5af)
   ![image](https://github.com/user-attachments/assets/b444b5b3-3a44-442d-af48-30a79947bd29)

6. **MongoDB**  
   As a NoSQL database, MongoDB is used to store the processed comments and their associated sentiment scores. It offers flexibility in handling unstructured data and provides efficient querying capabilities for subsequent analysis.

   ![image](https://github.com/user-attachments/assets/05e27863-fa7b-4fee-b037-42beb9dd1493)
   ![image](https://github.com/user-attachments/assets/c913933b-6f39-417f-871e-ebf58f745f5c)

7. **Docker Setup**  
   Docker is used to containerize the core components of the pipeline, ensuring that the environment is consistent across different deployments and making it easier to manage dependencies. The following steps outline how to set up Docker for this project:

   ![image](https://github.com/user-attachments/assets/5b38d86a-67c0-4d21-a317-3d4fa158c80f)

   1. **Docker Compose Configuration**  
      The `docker-compose.yml` file is provided in the repository to define and configure the services required by the pipeline, including Kafka, Zookeeper, Spark, and MongoDB.

   2. **Build and Start Containers**  
      - Navigate to the root directory of the project where the `docker-compose.yml` file is located.
      - Run the following command to build and start the containers:
        ```bash
        docker-compose up -d
        ```
      - This command will pull the necessary Docker images and start the services in detached mode.

      ![image](https://github.com/user-attachments/assets/20e7e466-8f5a-4892-95e9-c39aedf3bf28)

   3. **Verify Running Containers**  
      - To verify that all services are running correctly, use the following command:
        ```bash
        docker ps
        ```
      - This will display a list of running containers, and you should see entries for Kafka, Zookeeper, Spark, MongoDB, and any other services defined in your `docker-compose.yml` file.

      ![image](https://github.com/user-attachments/assets/ea164721-647f-4788-a102-552bc213b30a)

   4. **Accessing Services**  
      - Once the containers are running, you can access the services through their respective ports as defined in the `docker-compose.yml` file. For example:
        - Kafka: `localhost:9092`
        - MongoDB: `localhost:27017`
        - Spark: `localhost:8080`
      - These services can be accessed from your local machine or from other containers in the Docker network.

      ![image](https://github.com/user-attachments/assets/0020a1ae-e9ac-42ca-9e27-d3809ddabee1)

   5. **Shutting Down Containers**  
      - To stop the running containers, use the following command:
        ```bash
        docker-compose down
        ```
      - This command will stop and remove the containers, but the data volumes will be preserved.

   6. **Persistent Data Storage**  
      - The `docker-compose.yml` file is configured to mount data volumes for MongoDB and other services to ensure that data is persisted between container restarts. This is important for retaining the processed comments and sentiment analysis results in MongoDB.

   By containerizing the pipeline's components, Docker ensures that the environment remains consistent across different development and production environments. This simplifies deployment and makes it easier to manage dependencies and configurations.

8. **Tableau**  
   Tableau is used to visualize the results of the sentiment analysis. By connecting Tableau to MongoDB, users can create dashboards and reports that illustrate sentiment trends across videos, time periods, or other dimensions of interest.

![image](https://github.com/user-attachments/assets/478b0ddf-14bd-4da4-ad38-6317abf6483b)
![image](https://github.com/user-attachments/assets/835727a8-a896-42da-a87b-d2e8b44517ce)
![image](https://github.com/user-attachments/assets/25419716-8e07-4323-9b1e-e6ae1a04274d)


### Benefits and Use Cases
The YouTube Sentiment Analytics Pipeline offers several benefits:
- **Real-Time Insights**: By processing and analyzing comments in near real-time, stakeholders can quickly respond to emerging trends or audience feedback.
- **Scalability**: The use of distributed processing and scalable components like Kafka and Spark ensures that the pipeline can handle increasing data volumes without performance degradation.
- **Actionable Data**: The sentiment analysis provides actionable insights that can inform content strategy, marketing campaigns, and audience engagement efforts.
- **Customizable and Extensible**: The pipeline's modular design allows for easy customization and the integration of additional features, such as advanced sentiment analysis models, additional data sources, or alternative storage solutions.

### Future Enhancements
Future enhancements to this project could include:
- **Advanced Sentiment Analysis**: Implementing more sophisticated sentiment analysis techniques, such as deep learning models, to improve accuracy.
- **Additional Data Sources**: Integrating other social media platforms or data sources to provide a more comprehensive view of audience sentiment across multiple channels.
- **Enhanced Visualizations**: Expanding the Tableau dashboards to include more complex visualizations, such as sentiment over time, comparisons between videos, or demographic-based sentiment analysis.
- **Automated Reporting**: Adding automated reporting features to generate and distribute sentiment analysis reports to stakeholders on a regular basis.

### Conclusion
The YouTube Sentiment Analytics Pipeline is a powerful tool for extracting, processing, and analyzing sentiment data from YouTube comments. By leveraging a robust tech stack and following best practices in data engineering, this project demonstrates an efficient, scalable, and insightful approach to understanding audience sentiment. Whether you're a content creator looking to gauge audience reactions or a marketer interested in the impact of campaigns, this pipeline provides the insights needed to make data-driven decisions.
