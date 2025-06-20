# Simple logger by Syhmac

## About
A simple logging library for Python. It's designed to be easy to use and class based.

## Installation
Put the `simple_logger` directory in your project or merge it with your project.

## Features
- Easy to use
- Class based
- Supports multiple log levels (DEBUG, INFO, WARNING, ERROR, CRITICAL)
- Automatic file saving
- Automatic timestamps
- Flexible
- Supports docstring

## Usage
### Initialization
Code below shows an example initialization with the DEBUG level logging. Argument names are optional.
`LOG` is a basic class for the logger, and it will handle all the work. Logger will automatically createe the specified directory if it's not found.
Remember to add `/` at the end of the path.
```python
import simple_logger

log = simple_logger.LOG(level = 0, filename = "latest.log", filepath = "logs/")
```

### Changing log lever mid execution
You can change the log level at any time by using `set_level` method. For example:
```python
import simple_logger

log = simple_logger.LOG(level = 0, filename = "latest.log", filepath = "logs/")

log.set_level(1)
```
Code above will change the log level to INFO. You can use any of the following levels:
- 0 - DEBUG
- 1 - INFO
- 2 - WARNING
- 3 - ERROR
- 4 - CRITICAL

Any value above 4 will be defaulted to 0.

### Logging messages
You can log messages using the following methods:
```python
import simple_logger

log = simple_logger.LOG(level = 0, filename = "latest.log", filepath = "logs/")

log.debug("This is a debug message")
log.info("This is an info message")
log.warn("This is a warning message")
log.error("This is an error message")
log.critical("This is a critical message")
```

### Saving logs
Logger will always save the logs to the file specified during initialization, but there is additional method that allows 
you to save the copy to a different log - presumably with a unique name so it won't get overwritten.

To do that use the `save` method:

```python
import simple_logger

log = simple_logger.LOG(level = 0, filename = "latest.log", filepath = "logs/")

log.debug("This is a debug message")

log.save("final.log") # use "time" as an argument to save with the current timestamp
```
Code above will result in 2 files being saved: `latest.log` and `final.log`.
'latest.log' is meant to be overwritten. When using `save` method you should generate a filename that will be unique.
You can also use `"time"` as the argument, which will save the log with the current timestamp as the filename.