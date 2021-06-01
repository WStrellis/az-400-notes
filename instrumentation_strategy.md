# Logging

Apps running on Windows runtime can write logs either to the filesystem of their container or to Blob Storage. Apps running in Linux containers can only write logs to the docker filesystem.

When file system logging is enabled it will only save logs for 12h to prevent negative impacts on app performance.