# Log Archiver Tool

## Overview
The Log Archiver Tool is a simple CLI utility that compresses log files into a `.tar.gz` archive and stores them in a specified directory. This helps in cleaning up old logs while preserving them in a compressed format for future reference.

## Features
- Accepts the log directory as an argument
- Compresses log files into a `.tar.gz` format
- Stores the compressed logs in a specified archive directory
- Logs the date and time of the archive operation

## Prerequisites
- Python 3.x installed

## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/ArjaySabalboro/log-archiver.git
   cd log-archiver
   ```
2. Make the script executable:
   ```bash
   chmod +x log_archiver.py
   ```

## Usage
Run the script using the command line:
```bash
./log_archiver.py /path/to/log_directory --archive-dir /path/to/archive_directory --log-file /path/to/log_file.log
```

### Arguments:
- `log_directory` (required): Path to the directory containing logs to archive.
- `--archive-dir` (optional): Directory to store archived logs (default: `archives`).
- `--log-file` (optional): Path to the log file for tracking archive operations (default: `archiver.log`).

### Example Usage:
```bash
./log_archiver.py /var/logs --archive-dir /backup/logs --log-file /var/logs/archiver.log
```

## Error Handling
- If the specified log directory does not exist, the script will return an error.
- If the provided log file path is a directory instead of a file, the script will notify the user.

## License
This project is licensed under the MIT License.

## Contributing
Feel free to submit issues or pull requests to improve the tool.

