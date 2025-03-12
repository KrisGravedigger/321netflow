# 321netflow
Binance NetFlow Monitor
A capital flow monitoring tool (NetFlow) for cryptocurrencies on Binance exchange. This tool allows tracking and visualization of capital flows, which can be an indicator of future price movements.
Features

Automatic data collection from Binance API
NetFlow calculation (difference between capital inflow and outflow)
Data visualization with charts
Alert system for significant changes (above 10%)
Regular data updates (every 30 minutes by default)
Multi-threaded processing for efficient data collection
Selective analysis of significant trading pairs based on volume

Screenshots
Show Image
Requirements

Python 3.8 or newer
Internet connection
Required Python libraries:

pandas
numpy
matplotlib
requests
schedule
python-dateutil



Installation

Clone the repository:
Copygit clone https://github.com/yourusername/binance-netflow-monitor.git

Navigate to the project directory:
Copycd binance-netflow-monitor

Install required libraries:
Copypip install pandas matplotlib numpy requests schedule python-dateutil


Usage
Data Collector
Run the data collector to start gathering and analyzing NetFlow data:
Copypython binance_netflow_collector.py
The collector will:

Detect all trading pairs containing the target cryptocurrency
Identify the most important pairs based on trading volume
Download historical data and calculate NetFlow
Save data to a CSV file
Regularly update data based on the configured frequency
Automatically detect and fill gaps in data if the program was offline

Visualizer
To view the data on a chart without waiting for an alert:
Copypython binance_netflow_visualizer.py
Options:

--days DAYS - number of days to display (default: 30)
--data-file FILE - custom path to CSV file
--alert-mode - run in alert mode (displays only the last week)

Configuration
The most important parameters can be changed in the netflow_config.json file:
ParameterDescriptionDefault Valuetarget_coinSymbol of the monitored cryptocurrency"BTC"intervalTime interval for data (1m, 5m, 15m, 30m, 1h, 4h, 1d)"1h"update_frequencyHow often to update data (15m, 30m, 1h, 4h)"30m"max_history_daysHow many days of history to download14alert_thresholdPercentage threshold for alerts10.0enable_alertsEnable/disable alerts (true/false)truemax_threadsMaximum number of threads for parallel processing10
How It Works

The tool identifies all trading pairs on Binance that include the target cryptocurrency
It analyzes historical trading data for these pairs
For each period, it calculates:

Inflow: Amount of cryptocurrency entering the exchange
Outflow: Amount of cryptocurrency leaving the exchange
NetFlow: The difference between inflow and outflow


The data is saved to a CSV file for historical analysis
The visualizer generates charts showing the trends in NetFlow
When a significant change is detected, an alert is triggered

Understanding the Chart
The chart displays:

Top panel: NetFlow values (blue line) and moving average (purple dashed line)

Green areas indicate positive NetFlow (capital inflow)
Red areas indicate negative NetFlow (capital outflow)


Bottom panel: Trading volume

Green bars: Inflow
Red bars: Outflow



Troubleshooting

Collector logs are saved in the netflow_collector.log file
Visualizer logs are saved in the netflow_visualizer.log file
If the system is working correctly, it should automatically handle:

Gaps in data
API errors
Connection problems



Future Enhancements

 Add more alert notification channels (email, Telegram)
 Implement correlation analysis with price
 Create a web interface for data viewing
 Add support for multiple cryptocurrencies simultaneously
 Implement machine learning for predictive analysis

License
MIT
Acknowledgments

Binance for providing the API
The open-source community for the libraries used in this project
