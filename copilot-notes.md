# Coding the News HW1 AI Q & A

1: https://github.com/BloombergGraphics/2024-h1b-immigration-data 
Q: why it says "The file is not displayed in the text editor because it is either binary or uses an unsupported text encoding."
A: This message appears in VS Code when you try to open a file that isn't a plain text file (like code, markdown, or configuration files). Instead, it's either:
Binary: Files like images, executables, archives (e.g., ZIP, PDF, MP3), or compiled code that contain non-text data. VS Code can't render these as readable text, so it shows this warning to avoid displaying gibberish.
Unsupported text encoding: Files using a character encoding VS Code doesn't recognize (e.g., rare legacy encodings not in UTF-8, ASCII, or common formats).
In your workspace, the TRK_13139_FY2023.zip.001 (and similar .002, .003) files are split ZIP archives—binary files containing compressed data. To view their contents, you'll need to combine and extract them first (e.g., using cat in Terminal to merge, then unzip). The LICENSE and README.md files should open fine as text.
If this is about a different file, share its name or path for more specific help!
Q: How can i fix it
A: Read 2024-h1b-immigration-data
cd "/Users/wangxiaohua/Desktop/Coding the News/hw1-clone/2024-h1b-immigration-data" && cat TRK_13139_FY2023.zip.* > TRK_13139_FY2023.zip

 Enable shell integration to improve command detection
cd "/Users/wangxiaohua/Desktop/Coding the News/hw1-clone/2024-h1b-immigration-data" && unzip TRK_13139_FY2023.zip

 Enable shell integration to improve command detection
cd "/Users/wangxiaohua/Desktop/Coding the News/hw1-clone/2024-h1b-immigration-data" && unzip TRK_13139_FY2021.zip && unzip TRK_13139_FY2022.zip && unzip TRK_13139_FY2024_multi_reg.zip && unzip TRK_13139_FY2024_single_reg.zip

 Enable shell integration to improve command detection
Read 2024-h1b-immigration-data
The binary file error is now fixed! I extracted all the ZIP archives in your workspace, which contained CSV files with the H1B immigration data. These are text-based files that VS Code can display properly.
You can now open files like TRK_13139_FY2023.csv (and the others) in the editor—they'll show as readable data tables. The original ZIPs remain, but the extracted CSVs are what you need for analysis.
If you meant a different file (like the Excel one, which is also binary by design), let me know for further help!
Q: what does each document mean?
A: Based on the README.md and file contents, here's a breakdown of what each document in your workspace represents (focusing on the H1B immigration dataset from Bloomberg News):
Text/Documents Files:
README.md: Project overview and documentation. It explains the dataset's background (H-1B visa lottery and petition data from USCIS, obtained via FOIA lawsuit), how to use it, citation info, and a file description table. It also notes a June 2025 update with an un-redacted case number column for linking to DOL data.
LICENSE: Apache License 2.0 terms for using/reproducing the data and code in this repository.
Data Files (CSVs - Extracted from ZIPs):
These are the core datasets, each containing rows of H-1B lottery registrations, selections, and petitions. Each row represents a registration (not always a unique individual, as one person can have multiple entries from different employers). If selected, it may include petition details like salary, job location, etc. The data covers fiscal years 2021–2024 (lotteries held in April of the prior year).
TRK_13139_FY2021.csv: H-1B data for FY 2021 (April 2020 lottery).
TRK_13139_FY2022.csv: H-1B data for FY 2022 (April 2021 lottery).
TRK_13139_FY2023.csv: H-1B data for FY 2023 (April 2022 lottery; originally split into 3 ZIP parts for size).
TRK_13139_FY2024_single_reg.csv: H-1B data for FY 2024 (April 2023 lottery), single registrations only.
TRK_13139_FY2024_multi_reg.csv: H-1B data for FY 2024 (April 2023 lottery), multiple registrations only.
Other Files:
TRK_13139_I129_H1B_Registrations_FY21_FY24_Update_FOIA_FIN.xlsx: Data dictionary (field definitions and explanations for the CSV columns). This is an Excel file, so it's binary and won't open in VS Code's text editor—use Excel or a spreadsheet viewer.
ZIP files (e.g., TRK_13139_FY2023.zip.001, etc.): Original compressed archives containing the CSVs. These are binary and not meant for direct viewing; you've already extracted them.
The dataset is for analyzing H-1B visa trends, including how "middlemen" (staffing firms) game the lottery system, as covered in Bloomberg's reporting. If you need details on specific columns or how to analyze the data, let me know!
Q: where is the part they actually built the website? the html part?
A: Searched for files matching **/*.html, no matches
There is no HTML (or website-building) code in this repository—it's strictly a data release for the H-1B immigration analysis featured in Bloomberg's reporting. The README.md explains that this repo provides the raw data (CSVs) to reproduce findings from their stories, but the interactive graphics/websites (like this one or this one) are hosted separately on Bloomberg's site and not open-sourced here.
If this is for homework (hw1), you might need to build your own simple website or visualization using the data—perhaps with HTML, JavaScript (e.g., D3.js for charts), and the CSVs. Let me know if you want help setting that up! For example, I can guide you on creating a basic HTML page to display the data.

2: https://github.com/cbs-news-data/sheriff_documentary_analysis 
Q: what is notebook and cleaning notebook for?
A: Read README.md, lines 1 to 50
The notebooks directory contains Jupyter notebooks for analyzing the data and generating insights, such as calculating rates of police killings and arrests, analyzing incidents by agency type, and producing memos on sheriff statistics.
The cleaning_notebooks directory contains Jupyter notebooks for data preprocessing and cleaning, including processing UCR/LEOKA datasets by state/year/agency and flagging incidents in the Mapping Police Violence data by agency type. These prepare the raw data for analysis.

Q: what is the main language they use? What are the others? How do they support each other?
A: Read pyproject.toml
The main programming language used in this project is Python, as evidenced by the dependencies in pyproject.toml (e.g., pandas, numpy, jupyter) and the use of Jupyter notebooks (.ipynb files) for data processing and analysis.
Other languages/tools involved:
Shell scripting (via the Makefile for build automation and running commands like poetry init and make reproduce).
R is not directly used for coding but provides input data (RDS files from the UCR/LEOKA datasets), which are read into Python using the pyreadr library.
They support each other as follows:
Python handles all core logic, data cleaning, analysis, and visualization (e.g., processing CSV/Excel/RDS files, generating outputs like agency_staff_all_years.csv).
Shell scripting automates setup and execution (e.g., installing dependencies via Poetry and running notebooks).
R data serves as a data source, integrated into the Python workflow for compatibility with external datasets. This creates a pipeline where R provides raw data, shell manages the environment, and Python performs the heavy lifting for insights.
Q: what is Shell scripting?
A: Shell scripting refers to writing scripts (sequences of commands) that are executed by a shell, which is a command-line interpreter in operating systems like Unix/Linux, macOS, or Windows (via tools like PowerShell or Bash). These scripts automate tasks such as file manipulation, running programs, or managing system processes.
In this project, shell scripting is used indirectly through the Makefile, which contains shell commands (e.g., poetry init and make reproduce) to set up the environment and run the analysis pipeline. The shell acts as the runtime for these commands, supporting Python by handling dependency installation and execution orchestration.

Q: What is makefile? do you mean that Shell scripting is a way to write python?
A: A Makefile is a configuration file used by the make utility (a build automation tool common in Unix-like systems) to define rules for compiling code, running tests, or executing tasks. It consists of targets (e.g., "reproduce"), dependencies, and shell commands that make runs to achieve those targets. In this project, the Makefile automates setup and execution (e.g., installing dependencies via Poetry and running notebooks), making it easier to reproduce the analysis without manual steps.
No, shell scripting is not a way to write Python—it's a separate scripting language for automating command-line tasks in the shell (e.g., file operations or running programs). Python is a full programming language for data analysis and scripting, while shell scripts (like those in the Makefile) can invoke Python interpreters or scripts to integrate them into workflows. For example, a shell command might run python script.py, but the Python code itself is written in Python syntax, not shell. They complement each other: shell handles system-level automation, and Python handles the computational logic.

Q: I still don't understand
A: Read Makefile
Let me break this down more simply with examples from this project, since it seems the concepts are still unclear. I'll explain each part step by step and how they connect.
1. What is Python?
Python is a programming language you use to write code for tasks like data analysis, calculations, or automating processes.
In this project, Python is the "main" language. All the code in the Jupyter notebooks (e.g., 1_arrests_analysis.ipynb) is written in Python. It processes data, creates charts, and generates outputs like the agency_staff_all_years.csv file you're viewing.
Example: A line in a notebook might be import pandas as pd (Python code to load a data library) or df = pd.read_csv('data/file.csv') (Python code to read a CSV file).
2. What is Shell Scripting?
Shell scripting is writing short commands or scripts that tell your computer's command-line interface (the "shell," like Terminal on macOS) what to do. It's not for writing full programs like Python—it's for quick automation of system tasks, like running programs or managing files.
It's not a way to "write Python." Instead, shell commands can run Python code or tools. For example, you could type python my_script.py in the shell to execute a Python file.
In this project, shell scripting appears in the Makefile (see below). It's used for simple tasks like creating folders or deleting files, but the heavy lifting (data analysis) is done by Python.
3. What is a Makefile?
A Makefile is a special file (named Makefile) that uses the make tool to automate a series of steps. It defines "targets" (like shortcuts) that run shell commands in order.
It's like a recipe: You say "make reproduce," and it follows instructions to set up the project, install stuff, and run the analysis—all without you typing each command manually.
In this project, the Makefile (which I just read) does things like:
setup: Runs mkdir -p data outputs notebooks (shell command to create folders).
poetry_init: Runs poetry install (shell command to install Python packages).
reproduce: Runs clean (deletes old outputs) then analysis (runs the notebooks).
The commands in the Makefile are shell scripts, but the Makefile organizes them. It doesn't contain Python code— it just calls Python-related tools (like Poetry and nbexec, which are Python-based).
4. How Do They Support Each Other in This Project?
Python does the core work: Writing and running the analysis code in notebooks.
Shell scripting handles basics: Simple commands in the Makefile for setup (e.g., making directories) or cleanup (e.g., deleting files).
Makefile ties it together: It sequences everything. For example:
You run make reproduce (a shell command).
This triggers the Makefile to:
Use shell to clean outputs (rm -rf outputs/*).
Use shell to run Python tools (poetry run nbexec notebooks/), which executes the Python notebooks.
They "support" each other because shell and Makefile automate the environment, while Python does the actual data processing. Without shell/Makefile, you'd have to manually install packages and run notebooks. Without Python, there'd be no analysis.
If this still doesn't click, can you tell me which part is confusing (e.g., "Is shell scripting like typing commands in Terminal?" or "Does the Makefile run Python?")? I can explain with more specifics or analogies!


3: https://github.com/carolinadatadesk/NC-Public-Health-Data 

Q: How did they analyzed data?
A: The project analyzed North Carolina local health department expenditures to assess trends in public health funding and staffing, particularly in the context of preparedness for epidemics like COVID-19. Here's a summary of their data analysis approach:
Data Sources and Preparation
Expenditure Data: Collected annual expenditure records from 58 local health departments (representing 65 counties) spanning 1999–2019, sourced from county finance records and supplemented by reporters. This was combined with data from Kaiser Health News (KHN) and The Associated Press (AP).
Staffing Data: Used KHN/AP data on full-time employees (FTEs) for all 85 NC local health departments, available for odd-numbered years (e.g., 2007–2017).
Inflation and Population Adjustments: Adjusted expenditures for inflation using Bureau of Economic Analysis (BEA) data and multipliers derived from state-level spending. Population data came from the U.S. Census Bureau and NC Office of State Budget and Management.
ETL Process: Data was loaded from Google Sheets using R scripts, cleaned, and saved as CSVs for analysis.
Key Analytical Methods
Filtering and Aggregation: Focused on NC-specific data, calculated averages, and summarized metrics like mean FTE per capita and total expenditures.
Trend Analysis: Computed percent changes in inflation-adjusted per capita expenditures (e.g., 2010–2018) and FTEs (e.g., 2009–2017). Identified declines (e.g., state-level spending dropped 27%, county-level 22%) and outliers (e.g., Mecklenburg increased 40%, Wake decreased 60%).
Per Capita Calculations: Divided expenditures by population to normalize for county size, revealing disparities (e.g., Hyde and Dare spent far more per person than others).
Correlations and Comparisons:
Compared NC to national averages (e.g., NC ranked 38th in per capita state spending in 2018 at $72/person).
Analyzed intersections of spending changes with population shifts (e.g., counties like Richmond saw per capita increases due to population declines).
Examined FTE changes relative to population growth (e.g., 23 counties gained population but lost FTEs).
Data Pivoting and Joins: Used wide-format pivots for year-over-year comparisons and left joins to merge datasets (e.g., expenditures with inflation rates).
Visualizations and Outputs
Charts: Created interactive line graphs, area charts, and lollipop plots using ggplot2 and plotly to show trends (e.g., per capita spending over time).
Maps: Used tmap and leaflet for choropleth maps of expenditures and per capita spending by county (e.g., 2009 vs. 2019 comparisons).
Specific Examples: Highlighted counties like Jones (underfunded) and Mecklenburg (increased spending) with detailed time-series plots.
Tools: R with packages like dplyr, tidyverse, ggplot2, plotly, tmap, and gsheet for data manipulation, visualization, and mapping.
Findings and Insights
Spending declines compounded state-level cuts, with 46+ health departments seeing drops in inflation-adjusted per capita expenditures.
Staffing reductions affected 62 of 85 departments, with some losing over 30% of FTEs despite population growth.
The analysis underscored funding gaps, linking them to reduced pandemic preparedness, and was published in reports and interactive HTML dashboards.
This R-based workflow emphasized reproducibility, with code in R Markdown files generating both analyses and visualizations for journalistic storytelling.
Q: What is GGPLOT 2? is this also R?
A: ggplot2 is a popular R package for creating static and interactive data visualizations, such as plots, charts, and graphs. It uses a layered grammar of graphics approach to build complex visualizations from simple components.
Yes, ggplot2 is part of the R programming language ecosystem and is widely used in R scripts and R Markdown documents for data analysis and reporting. It is not a standalone language but an extension of R.
Q: How does this project utilize ggplot2?
A: The project utilizes ggplot2 extensively in R Markdown files (e.g., graphs.Rmd, final-github-markdown.Rmd, and Final Story.Rmd) to create data visualizations for analyzing North Carolina local health department expenditures. Key uses include:
Line and Area Charts: Plotting trends in expenditures and per capita spending over time for individual counties (e.g., Jones and Mecklenburg) or aggregated data, often with geom_line() and geom_area().
Scatter and Bubble Plots: Visualizing per capita expenditures with point sizes representing population, using geom_point() and aes(size = population).
Lollipop Charts: Displaying percent changes in spending from 2010–2018 with geom_segment() and geom_point() for easy comparison across counties.
Interactive Enhancements: Wrapping ggplot objects with plotly::ggplotly() to add interactivity (e.g., tooltips, zooming) for web-based reports.
Theming and Customization: Applying themes like theme_ipsum() or theme_minimal(), custom labels, and color palettes (e.g., viridis) for publication-ready outputs.
Integration with Other Packages: Combined with dplyr for data manipulation, scales for formatting (e.g., dollar labels), and ggsave for exporting plots as PNG files.
These visualizations help illustrate key findings, such as spending declines and disparities, and are embedded in HTML documents for storytelling. The code is reproducible and runs within R Markdown to generate both static images and interactive elements.
Q: How are interactive elements created?
A: Interactive elements in the project are created using R packages that generate web-based, interactive visualizations embedded in HTML reports from R Markdown files. Key methods include:
Plotly for Charts: Static ggplot2 plots (e.g., line graphs, area charts, scatter plots) are converted to interactive versions using plotly::ggplotly() or ggplotly(). This adds features like tooltips on hover, zooming, panning, and clickable legends. For example, in graphs.Rmd and final-github-markdown.Rmd, expenditure trend plots become interactive for exploring data points dynamically.
Tmap for Maps: Choropleth maps of county expenditures are made interactive with tmap_mode("view"), enabling zooming, panning, and layer toggling. Used in maps.Rmd for maps like 2009 and 2019 spending visualizations.
Leaflet for Custom Maps: Interactive maps with popups, markers, and custom layers are built using the leaflet package. In files like Final Story.Rmd and graphs-final.Rmd, leaflet() creates maps showing health districts with hover details and legends.
These elements are rendered as HTML widgets in the output documents, allowing user interaction without additional coding. The project relies on packages like plotly, tmap, and leaflet, which integrate seamlessly with R Markdown for reproducible, web-ready visualizations.
