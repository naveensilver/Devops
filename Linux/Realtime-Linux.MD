# Real-Time Linux Commands for DevOps Engineers

**Author: Naveen Thurkapally**

## 1. System Monitoring and Performance

### `top`

- **Use Case:** Monitor real-time system performance, CPU usage, memory usage, and running processes.
- **Command:** `top`
- **Example:** 
  ```sh
  top
  ```
  This command displays the top processes consuming the most resources.

### `htop`

- **Use Case:** Enhanced version of `top` with a more user-friendly interface and additional features.
- **Command:** `htop`
- **Example:** 
  ```sh
  htop
  ```
  This command allows you to navigate through processes and kill them directly from the interface.

### `vmstat`

- **Use Case:** Report virtual memory statistics.
- **Command:** `vmstat 2`
- **Example:** 
  ```sh
  vmstat 2
  ```
  This command displays system performance every 2 seconds.

### `iostat`

- **Use Case:** Report CPU and I/O statistics.
- **Command:** `iostat -x 2`
- **Example:** 
  ```sh
  iostat -x 2
  ```
