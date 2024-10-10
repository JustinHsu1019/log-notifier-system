# Log Notifier System

## Overview
The **Log Notifier System** is a tool designed to automate the return of logs from programs running on virtual servers to a local repository. It also provides features for process completion notifications and file transfer functionalities via LINE.

## Features
- **Automated Setup**: The `setup.py` script automatically configures your environment, setting up necessary keys and tokens (e.g., LINE Messaging API).
- **Process Completion Notification**: Monitors a process by PID and sends a LINE message upon completion, detailing the total execution time.
- **File Transmission**: Allows you to send files or folders from the server to your LINE account or upload them to a cloud storage service and share a download link.

## Project Structure

```
log-notifier-system/
├── config/
│   └── config.yaml         # Configuration file for LINE tokens, server settings, etc.
├── logs/                   # Directory for storing logs
├── src/                    
│   ├── __init__.py         # Initializes the src package
│   ├── monitor.py          # Script for process monitoring and notifications
│   ├── file_sender.py      # Script for sending files or folders via LINE or cloud
│   └── utils.py            # Helper functions for file compression, time calculations
├── .env.example            # Example file for environment variables setup
├── setup.py                # Script to configure environment and setup secrets
├── README.md               # Project documentation
└── requirements.txt        # Python dependencies
```

## Getting Started

### Prerequisites
- **Python 3.x**
- **LINE Messaging API credentials**
- A virtual server (e.g., AWS, Google Cloud, etc.)

### Installation

1. **Clone the repository**:
    ```bash
    git clone https://github.com/JustinHsu1019/log-notifier-system.git
    cd log-notifier-system
    ```

2. **Install dependencies**:
    Make sure to install all required Python packages using the following command:
    ```bash
    pip install -r requirements.txt
    ```

3. **Configure environment variables**:
    - Copy the `.env.example` file to `.env`:
      ```bash
      cp .env.example .env
      ```
    - Fill in your `LINE_ACCESS_TOKEN` and other necessary values in `.env`.

4. **Run the setup script**:
    The `setup.py` script will handle initial configuration.
    ```bash
    python setup.py
    ```

### Usage

#### Process Completion Notification

1. **Monitor a process**:
   Start monitoring a process using its PID. Once the process finishes, you'll receive a LINE notification with the total execution time.
    ```bash
    python src/monitor.py --pid <process_id>
    ```

2. **View logs**:
   If the monitored process produces logs, they will be stored in the `logs/` directory for future reference.

#### File Transmission

1. **Send a file or folder**:
    Use the `file_sender.py` script to send a specific file or all files in a folder to your LINE account. The script will compress files if necessary or upload them to cloud storage if they exceed the size limit for LINE.
    ```bash
    python src/file_sender.py --path <file_or_folder_path>
    ```

2. **Receive download links**:
    For larger files that cannot be sent directly via LINE, a cloud storage link will be shared with you.

## Configuration

### config.yaml
The `config/config.yaml` file stores all critical configurations like:
- **LINE tokens**
- **Server settings**

You can modify this file to match your environment. 

### Environment Variables
- **LINE_ACCESS_TOKEN**: The access token for the LINE Messaging API.
- **SECRET_KEY**: Any other secret keys needed for authentication or services.

## Contributing
We welcome contributions! If you have suggestions or find bugs, please open an issue or submit a pull request.

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.
