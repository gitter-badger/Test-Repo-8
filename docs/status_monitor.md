# Status Monitor

Status.py monitors the linuxcnc.status attributes and emits GObject signals on a value change. Python scripts can connect a callback to these signals to get status updates without having to periodically poll the status channel themselves. This is referred to as event-driven programming, and reduces the load on the status channel while making it simpler for python scripts to get status updates from linuxcnc.


!!! note
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.


## Syntax

status.on_value_changed(_**attribute**_, _**callback**_)

Where _**attribute**_ is any [linuxcnc.stat](http://linuxcnc.org/docs/devel/html/config/python-interface.html#_linuxcnc_stat_attributes) attribute and _**callback**_ is the method to be called when the value of that attribute changes.

## Examples

Here is a basic example that prints the tool number when the _linuxcnc.stat.tool_in_spindle_ attribute changes.

    :::python
    #!/usr/bin/env python

    import status.Status

    self.status = Status

    # Connect "update_tool" callback to "tool_in_spindle" changed signal
    self.status.on_value_changed('tool_in_spindle', self.update_tool)

    self.update_tool(widget, tool_num):
        print tool_num
