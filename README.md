
```markdown
# Hadoop Ecosystem Setup with Docker

This project sets up a complete Hadoop ecosystem using Docker. It includes Hadoop, Spark, and other related components.

## Prerequisites

Before starting, ensure you have the following installed on your machine:

### Docker

Docker is essential for containerizing and running our Hadoop ecosystem.

- **Download Docker**: [Docker Download](https://www.docker.com/get-started)

### Java 8

Hadoop requires Java 8 to run. Ensure Java 8 is installed on your machine.

- **For macOS**: [Java 8 for macOS](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)
- **For Windows**: [Java 8 for Windows](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)

## Docker Setup

### Launch Docker

After installing Docker, launch it and ensure it is running. Assign enough memory to Docker to handle the Hadoop ecosystem:

- Go to Docker Desktop > Preferences > Resources
- Increase the memory allocation (at least 4GB)

### Create Hadoop Directories

On your local machine, create the necessary directories for Hadoop. The paths differ based on your operating system.

#### For macOS/Linux:

Open your terminal and run:

```bash
sudo mkdir -p /usr/local/hadoop/etc/hadoop
```

#### For Windows:

Open Command Prompt as Administrator and run:

```bash
mkdir C:\hadoop\etc\hadoop
```

## Setting Up Environment Variables

### For macOS/Linux:

Open your terminal and navigate to your Java installation directory:

```bash
cd /Library/Java/JavaVirtualMachines/jdk1.8.0_231.jdk/Contents/Home
```

Get the path by running:

```bash
pwd
```

Use this path to set the `JAVA_HOME` in your environment variables. Edit your `.zprofile` or `.bash_profile` (depending on the shell you use):

```bash
nano ~/.zprofile
```

Add the following lines (replace the path with the one you copied):

```bash
export JAVA_HOME="/Library/Java/JavaVirtualMachines/jdk1.8.0_231.jdk/Contents/Home"
export HADOOP_HOME="/usr/local/hadoop"
export HADOOP_CONF_DIR="/usr/local/hadoop/etc/hadoop"
```

Save the file and source it:

```bash
source ~/.zprofile
```

### For Windows:

Open Command Prompt as Administrator and navigate to your Java installation directory:

```bash
cd C:\Program Files\Java\jdk1.8.0_231
```

Get the path by running:

```bash
cd
```

Set the environment variables:

```cmd
setx JAVA_HOME "C:\Program Files\Java\jdk1.8.0_231"
setx HADOOP_HOME "C:\hadoop"
setx HADOOP_CONF_DIR "C:\hadoop\etc\hadoop"
```

## Cloning the Repository

Clone the repository to your local machine:

```bash
git clone https://github.com/your-username/hadoop-ecosystem-setup.git
cd hadoop-ecosystem-setup/hadoop_docker
```

## Project Structure

Your project structure should look like this:

```
hadoop-ecosystem-setup
├── hadoop_docker
│   ├── docker-compose.yml
│   └── hadoop-hive.env
└── README.md
```

## Environment Variables File

The `hadoop-hive.env` file in the `hadoop_docker` directory should look like this:

### For macOS/Linux:

```env
HADOOP_HOME=/usr/local/hadoop
HADOOP_CONF_DIR=/usr/local/hadoop/etc/hadoop
JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_231.jdk/Contents/Home  # Adjust this path based on your Java installation
```

### For Windows:

```env
HADOOP_HOME=C:\hadoop
HADOOP_CONF_DIR=C:\hadoop\etc\hadoop
JAVA_HOME=C:\Program Files\Java\jdk1.8.0_231  # Adjust this path based on your Java installation
```

Make sure these paths are correctly set according to your machine setup.

## Running the Hadoop Ecosystem

Navigate to the `hadoop_docker` directory and start the services using Docker Compose:

```bash
docker-compose up -d
```

## Accessing the Services

- **NameNode UI**: http://localhost:50070
- **DataNode UI**: http://localhost:50075
- **Spark Master UI**: http://localhost:8080
- **Spark Worker UI**: http://localhost:8081

## Stopping the Services

To stop the services, run:

```bash
docker-compose down
```

## Troubleshooting

If you encounter any issues with ports or services, ensure that:

- The ports are not being used by other services on your machine.
- Docker has enough allocated memory and CPU resources.

For any issues related to Docker, refer to the [Docker Documentation](https://docs.docker.com/get-started/).

## Additional Notes

This setup includes the following components:
- Hadoop NameNode
- Hadoop DataNode
- Spark Master
- Spark Worker

You can extend this setup to include more components like Hive, HBase, Kafka, etc., by modifying the `docker-compose.yml` file and adding the necessary configurations.