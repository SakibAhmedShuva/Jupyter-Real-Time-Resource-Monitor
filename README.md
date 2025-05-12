# Jupyter Real-Time Resource Monitor 📊💻⏱️

A Jupyter Notebook utility created by [SakibAhmedShuva](https://github.com/SakibAhmedShuva) to help in managing and monitoring system resources directly within your Jupyter environment. This tool provides both a live, plotting-based real-time resource monitor and a static HTML snapshot of your system's current state.

![image](https://github.com/user-attachments/assets/94aec003-5741-4492-a26b-146a42ee9001)



![image](https://github.com/user-attachments/assets/546278c1-0149-440c-8f84-6d4a2dcb0fd5)


## 🌟 Features

This notebook (`utils.ipynb` or your chosen name) contains two main cells:

1.  **Live Resource Plotter:**
    *   Continuously monitors and plots CPU usage (%), RAM usage (%), and (if available) NVIDIA GPU statistics in real-time.
    *   For GPUs, it plots Load (%), Temperature (°C), and Memory Utilization (%).
    *   Uses `matplotlib` for dynamic plotting within the Jupyter output cell.
    *   Configurable update interval and history length for plots.
    *   Automatically detects available NVIDIA GPUs and creates dedicated subplots.
    *   Handles dynamic changes in GPU availability (e.g., if `GPUtil` starts working or a GPU appears/disappears mid-monitoring).

2.  **Static Resource Snapshot:**
    *   Generates a detailed HTML report of the current system resources.
    *   Includes:
        *   System Information (OS, Kernel, Boot Time)
        *   CPU Usage (Physical/Total Cores, Total & Per-CPU Usage)
        *   Memory Usage (RAM & Swap - Total, Used, Free, Percentage)
        *   NVIDIA GPU Usage (ID, Name, Load, Memory, Temperature) - if available
        *   Disk Usage (Mount Point, Device, File System, Total, Used, Free, Percentage) for relevant partitions.
    *   Option for continuous monitoring with updates or a single snapshot.
    *   Human-readable byte formatting (KB, MB, GB).

## 🎯 Motivation

This utility was developed to provide a convenient way for developers and data scientists to monitor system resource consumption directly within their Jupyter Notebooks. This is especially useful when running resource-intensive tasks, training machine learning models, or debugging performance issues, allowing for real-time insight without switching contexts.

## ⚙️ Prerequisites

*   Python 3.x
*   Jupyter Notebook or JupyterLab
*   The following Python libraries (the first cell in the notebook attempts to install them):
    *   `psutil`
    *   `matplotlib`
    *   `numpy`
    *   `GPUtil` (for NVIDIA GPU monitoring)
*   For NVIDIA GPU monitoring:
    *   An NVIDIA GPU
    *   NVIDIA drivers installed
    *   `nvidia-smi` command-line utility accessible

## 🚀 How to Use

1.  **Clone or Download:**
    Get the `utils.ipynb` (or your chosen filename) file into your working environment.
    ```bash
    # If you make this a git repository:
    git clone https://github.com/SakibAhmedShuva/Jupyter-Real-Time-Resource-Monitor.git
    cd Jupyter-Real-Time-Resource-Monitor
    ```

2.  **Open in Jupyter:**
    Launch Jupyter Notebook or JupyterLab and open the `.ipynb` file.

3.  **Install Dependencies (First Cell):**
    The first code cell in the notebook contains:
    ```python
    !pip install gputil psutil matplotlib numpy
    ```
    Run this cell to ensure all necessary libraries are installed.

4.  **Run the Desired Utility:**

    *   **Live Resource Plotter (Second Cell):**
        *   This cell initializes and runs a live plot of system resources.
        *   You can configure `UPDATE_INTERVAL_SECONDS`, `HISTORY_LENGTH`, and `CHECK_GPU` at the top of this cell's code.
        *   To stop the live monitoring, click the "Interrupt Kernel" button (the square icon) in the Jupyter toolbar.

    *   **Static Resource Snapshot (Third Cell):**
        *   This cell generates an HTML snapshot of the current system resources.
        *   You can configure `CONTINUOUS_MONITORING`, `UPDATE_INTERVAL_SECONDS` (if continuous), and `CHECK_GPU` at the top of this cell's code.
        *   If `CONTINUOUS_MONITORING` is `True`, it will refresh the snapshot at the specified interval. Stop it using the "Interrupt Kernel" button.

## 🔧 Configuration

Key configuration options are available at the top of each utility's code cell:

**For Live Plotter:**
*   `UPDATE_INTERVAL_SECONDS`: How often to update the plots (e.g., `2.0`).
*   `HISTORY_LENGTH`: Number of data points to keep for plotting (e.g., `60`).
*   `CHECK_GPU`: `True` to enable GPU monitoring, `False` to disable.

**For Static Snapshot:**
*   `CONTINUOUS_MONITORING`: `True` for periodic updates, `False` for a single snapshot.
*   `UPDATE_INTERVAL_SECONDS`: Update frequency if `CONTINUOUS_MONITORING` is `True` (e.g., `5`).
*   `CHECK_GPU`: `True` to include GPU information, `False` to exclude.

## ⚠️ Known Issues & Limitations

*   **GPU Monitoring:** Currently only supports NVIDIA GPUs via `GPUtil` and `nvidia-smi`.
*   **Plotting Overhead:** Very frequent updates in the live plotter (small `UPDATE_INTERVAL_SECONDS`) can themselves consume some CPU resources.
*   **Disk Information:** The disk usage utility prioritizes common mount points (`/`, home, current working directory). It might not display all mounted partitions by default to avoid clutter, but this can be adjusted in the `get_disk_info` function.
*   **Dynamic Plot Resizing:** If the number of detected GPUs changes while the live plotter is running, the plot figure will be re-initialized. This can cause a brief flicker.

## 💡 Future Enhancements (Ideas)

*   Support for AMD GPUs.
*   Network I/O monitoring and plotting.
*   Option to log resource usage to a file.
*   More sophisticated disk filtering options.
*   Packaging as a pip-installable library or Jupyter extension.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/SakibAhmedShuva/Jupyter-Real-Time-Resource-Monitor/issues) (if you create a repo) or contact Sakib.

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

## 👤 Author

*   **Sakib Ahmed Shuva** - [GitHub Profile](https://github.com/SakibAhmedShuva)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
