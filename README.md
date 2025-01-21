# log_archiver_tool
// Log Archiver Tool

!/usr/bin/env python3

import os
import tarfile
import argparse
from datetime import datetime

// Function to compress logs
def compress_logs(log_dir, archive_dir, log_file):
    try:
        // Create archive directory if it doesn't exist
        os.makedirs(archive_dir, exist_ok=True)

        // Generate the archive filename with timestamp
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        archive_name = f"logs_{timestamp}.tar.gz"
        archive_path = os.path.join(archive_dir, archive_name)

        // Compress logs into tar.gz
        with tarfile.open(archive_path, "w:gz") as tar:
            tar.add(log_dir, arcname=os.path.basename(log_dir))

        // Log the archiving activity
        with open(log_file, "a") as log:
            log.write(f"[{datetime.now()}] Archived logs to {archive_path}\n")

        print(f"Logs successfully archived to {archive_path}")
    except Exception as e:
        print(f"Error: {e}")

// Main function to parse arguments and invoke compression
def main():
    parser = argparse.ArgumentParser(description="Log Archiver Tool")
    parser.add_argument("log_directory", help="Path to the directory containing logs to archive")
    parser.add_argument("--archive-dir", default="archives", help="Directory to store archived lo>
    parser.add_argument("--log-file", default="archiver.log", help="Path to the log file (default>
    
    args = parser.parse_args()
       log_dir = args.log_directory
    archive_dir = args.archive_dir
    log_file = args.log_file

    if not os.path.exists(log_dir):
        print(f"Error: The specified log directory '{log_dir}' does not exist.")
        return

    compress_logs(log_dir, archive_dir, log_file)

if __name__ == "__main__":
    main()


// https://roadmap.sh/projects/log-archive-tool

