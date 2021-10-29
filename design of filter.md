# design of filter

## Slave Type
1. buffer in Ax, available time one cycle -- execellent 
2. buffer in Ax, available time N cycles  -- Normal
3. no buffer in Ax, available time N cycles -- Bad
### Since cpu core is always connected to caches, we use the execellent slave type

