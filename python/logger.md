```python
import logging

logging.basicConfig(format='%(asctime)s - %(message)s', datefmt='%d-%b-%y %H:%M:%S', level='DEBUG')

logger = logging.getLogger('example_logger')
```
Levels:  
CRITICAL 50  
ERROR 40  
WARNING 30  
INFO 20  
DEBUG 10  
NOTSET 0  
  
Loggers, handlers, filters, and formatters.
- Loggers expose the interface that application code directly uses.
- Handlers send the log records (created by loggers) to the appropriate destination.
- Filters provide a finer grained facility for determining which log records to output.
- Formatters specify the layout of log records in the final output.  

By using logging.error() or error() (imported from logging) or logging.getLogger().error() you are using root logger.  

The most widely used methods on logger objects fall into two categories: configuration and message sending.  

You can create logger, register handlers, register separate filters for logger, handlers, specify from what severity level to log, register your own levels.  
___
getLogger() returns a reference to a logger instance with the specified name if it is provided, or root if not. The names are period-separated hierarchical structures. Multiple calls to getLogger() with the same name will return a reference to the same logger object. Loggers that are further down in the hierarchical list are children of loggers higher up in the list. For example, given a logger with a name of foo, loggers with names of foo.bar, foo.bar.baz, and foo.bam are all descendants of foo.  

Loggers have a concept of effective level. If a level is not explicitly set on a logger, the level of its parent is used instead as its effective level. If the parent has no explicit level set, its parent is examined, and so on - all ancestors are searched until an explicitly set level is found. The root logger always has an explicit level set (WARNING by default). When deciding whether to process an event, the effective level of the logger is used to determine whether the event is passed to the logger’s handlers.

Child loggers propagate messages up to the handlers associated with their ancestor loggers. Because of this, it is unnecessary to define and configure handlers for all the loggers an application uses. It is sufficient to configure handlers for a top-level logger and create child loggers as needed. (You can, however, turn off propagation by setting the propagate attribute of a logger to False.)