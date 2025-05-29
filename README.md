## InsightMe: A Data-Analytics System to Deeply Understand Yourself\!

*Main interface of the InsightMe application (Tkinter GUI)*
![image](https://github.com/user-attachments/assets/acd810be-2b3e-4ee2-bd23-07a063a529e7)
![image](https://github.com/user-attachments/assets/5044d453-95d8-4ac5-972f-70e309657df2)
![image](https://github.com/user-attachments/assets/baae932a-6709-4df2-8ded-e002b71c8a2d)
![image](https://github.com/user-attachments/assets/94cc2cdd-3ac3-44b4-8a25-c616b42d18d3)
![image](https://github.com/user-attachments/assets/edda9b21-fb3e-49a9-8106-fef31b6b1b06)
![image](https://github.com/user-attachments/assets/fe2146f1-4664-43e2-a265-d6fb60ded773)
![image](https://github.com/user-attachments/assets/4a79a4e2-bd73-48a0-b3ca-a9a70cbf25f1)
![image](https://github.com/user-attachments/assets/345a0c7f-98b9-44e5-b175-8c023c888fe5)
![image](https://github.com/user-attachments/assets/4ec0187b-91c2-42bf-97ba-52037645dc2e)
![image](https://github.com/user-attachments/assets/a83764d4-0854-4a77-a00e-fd7ac6802385)
![image](https://github.com/user-attachments/assets/8b574897-7453-4c75-b07b-80ed1b320667)
![image](https://github.com/user-attachments/assets/ab8a3595-f80c-433b-aeb0-729fb4863a24)
![image](https://github.com/user-attachments/assets/ee35e6cd-806e-49f1-a6c1-4524fccdb778)
![image](https://github.com/user-attachments/assets/6c0f89d7-1760-46dc-9807-07dd0c369782)

-----

## 🌟 Project Introduction

**InsightMe** is a powerful Python application designed to help users explore and gain a deeper understanding of themselves through a comprehensive personal self-assessment system. The application goes beyond simple response collection, offering in-depth data analysis and visualizations to provide personalized development insights.

This project aims to be more than just an assessment tool; it strives to be a personal development platform, providing users with a detailed "portrait" of their psychological, behavioral, and cognitive aspects.

-----

## ✨ Key Features and Enhancements

The project has undergone significant development and has been upgraded with numerous impactful features and improvements:

### 1\. Architectural Improvements

  * **Modular Design:** Clear separation of concerns with dedicated modules and classes (UI, Core Logic, Data, Visualization, Reporting).
  * **Configuration Management (Planned):** A centralized configuration system for easy customization of application aspects.
  * **Session Management (Planned):** Track user assessment history and work sessions.
  * **Professional Error Handling:** Robust exception handling mechanisms implemented throughout the application.

### 2\. New Features

  * **Multiple UI Modes:**
      * **GUI (Tkinter):** An intuitive and user-friendly graphical user interface (default mode).
      * **Console:** A command-line interface for users who prefer minimalism or work in non-GUI environments.
      * **Web (Planned with Streamlit/Flask):** Support for an interactive web interface, easily accessible remotely.
  * **Advanced Analytics (Planned Expansion):**
      * Competency gap analysis.
      * Development priority suggestions.
      * Learning style analysis.
      * Career alignment assessment.
  * **Data Management:**
      * **Automatic Backups (Planned):** Automatically back up data before new changes or saves.
      * **Data Validation (Planned):** Ensure the integrity of input and output data.
      * **Data Export Capabilities:** Stores responses in JSON format (current), and is expandable to CSV.
  * **Enhanced Reporting:**
      * **Comprehensive HTML Reports:** Combines analytical text with visual charts.
      * **Diverse Visualization Types:**
          * **Radar Chart:** Illustrates a personal competency/values map.
          * **Bar Chart:** Compares scores across different aspects, highlighting strengths/weaknesses.
          * **Pie Chart:** Shows proportions of core values or motivation trends.
          * *(Planned) Heatmap:* Analyzes correlations between factors.
      * **Session Tracking (Planned):** Ability to review history and compare results across assessments.

### 3\. User Experience (UX) Improvements

  * **Professional Command Line Interface (CLI - Planned):** Argument parsing with help an (e.g., using `argparse`).
  * **Progress Indicators:** Clear feedback to the user during processing (e.g., "Saving...", "Generating report...").
  * **Post-Assessment Options:** A menu or action buttons after completing an assessment (view results, retake, exit).
  * **Auto-Open Reports:** Automatically opens the generated HTML report in the default web browser.
  * **UI Theme Support (Planned):** Allows users to customize the application's appearance.

### 4\. Technical Enhancements

  * **Logging System (Planned):** Comprehensive logging of application activities with configurable levels.
  * **Backup Manager (Planned):** Automatic data backup mechanism.
  * **Validator (Planned):** Ensures data integrity.
  * **Type Hints:** Full type annotation throughout the codebase for improved code quality and development support.
  * **Documentation:** Detailed docstrings and comments within the source code.

-----

## 🛠️ Technologies Used

  * **Programming Language:** Python 3.x
  * **Core Libraries:**
      * **Tkinter:** For the Graphical User Interface (GUI).
      * **JSON:** For data storage (user responses, questions).
      * **OS, Datetime:** Standard Python libraries for file/directory operations and time management.
  * **Data Analysis & Visualization:**
      * **NumPy:** For numerical operations, especially with Matplotlib.
      * **Matplotlib:** For generating static charts (Radar, Bar, Pie) embedded in reports and the Tkinter UI.
      * *(Planned/Optional) Pandas:* For more complex data manipulation if needed.
      * *(Planned/Optional) Plotly, Seaborn:* For alternative or more interactive visualizations, especially for a web UI.
  * **Image Handling:**
      * **Pillow (PIL Fork):** For loading and displaying images (like charts) within the Tkinter UI.
  * **Web Interaction (for opening reports):**
      * **Webbrowser:** Standard Python library to open HTML reports in the default browser.
  * **Development Environment:**
      * Visual Studio Code (or any preferred Python IDE).
      * Git for version control.

-----

## ⚙️ How It Works

The application consists of the following main components:

1.  **User Interface (`ui/tkinter_app.py`):**

      * Presents an introduction and prompts the user for their ID.
      * Sequentially displays assessment questions fetched from `assets/questions.json`.
      * Collects user responses via various Tkinter widgets (Radiobuttons for Likert scales and multiple-choice, Entry/Text widgets for open-ended questions).
      * Provides navigation (Next, Previous, Finish).
      * Displays an analysis results window with visualizations and textual summaries.

2.  **Question Management (`core/question_generator.py`):**

      * Loads a predefined set of (approximately 50) self-assessment questions from a JSON file (`assets/questions.json`).
      * Each question is structured with an ID, category, text, type (Likert, multiple-choice, yes/no, open-ended), and scoring information.

3.  **Data Storage (`core/data_storage.py`):**

      * Saves the user's ID and their responses to a timestamped JSON file in the `data/` directory. This allows for tracking and potential future re-analysis.

4.  **Analysis Engine (`core/analyzer.py`):**

      * Receives the user's responses and the question data (including scoring info).
      * Calculates scores for various predefined dimensions (e.g., "Linguistic Intelligence," "Intrinsic Motivation," "Integrity") based on the scoring logic defined in `questions.json`.
      * Identifies top strengths and areas for improvement.
      * Analyzes proportions for categorical questions (e.g., core values choices, motivation types).

5.  **Visualization (`visualization/plotter.py`):**

      * Takes the analyzed scores and generates various charts using Matplotlib:
          * **Radar Chart:** To visualize the user's profile across multiple key dimensions.
          * **Bar Chart:** To compare scores or highlight strengths/weaknesses.
          * **Pie Chart:** To show the distribution of preferences (e.g., core values, motivation types).
      * Saves these charts as PNG image files in the `output_charts_tkinter_enhanced/` directory.

6.  **Report Generation (`reporting/report_generator.py`):**

      * Combines the textual analysis summaries and the paths to the generated chart images.
      * Creates a comprehensive HTML report.
      * Uses relative paths for images to ensure the report is portable as long as the `output_reports...` and `output_charts...` directories maintain their relative structure.
      * Saves the HTML report in the `output_reports_tkinter_enhanced/` directory.

7.  **Main Application Flow (`main.py`):**

      * Initializes all core components.
      * Starts the Tkinter UI.
      * Orchestrates the process: user input -\> assessment -\> data saving -\> analysis -\> visualization -\> report display/saving.

-----

## 🚀 Getting Started & Usage

### Prerequisites

  * Python 3.7+
  * The following Python packages (can be installed via pip):
    ```bash
    pip install Pillow matplotlib numpy
    ```

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-repository-link-here.git
    cd InsightMe # Or your project's root directory name
    ```
2.  **Ensure `assets/questions.json` is present:**
      * This file is crucial and contains all the assessment questions. You need to create this file and populate it with your \~50 questions formatted in JSON, including `id`, `category`, `text`, `type`, and `scoring_info` for each.
3.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    (Currently, only `Pillow`, `matplotlib`, and `numpy` are strict dependencies for the Tkinter version. Add others to `requirements.txt` as you implement web UI or advanced features.)

### Running the Application

The primary way to run the application is using the Tkinter GUI:

```bash
python main.py
```

This will launch the graphical user interface.

*(Planned) Future Command Line Options:*

```bash
# Console mode
python main.py --mode console

# Web mode (e.g., Streamlit)
python main.py --mode web

# Run in debug mode (for more verbose logging)
python main.py --debug

# Use a custom configuration file
python main.py --config my_custom_config.json
```

### How to Use

1.  **Launch the application:** Run `python main.py`.

2.  **Enter User ID:** Provide a name or unique identifier.

3.  **Answer Questions:** Progress through the assessment, selecting your responses for each question.

4.  **Finish Assessment:** Once all questions are answered, click "Hoàn thành ✔" (Finish).

5.  **View Results:**
    A new window will appear with tabs for:

      * **Tổng Quan (Overview):** Displays a radar chart of your key dimensions and a summary of strengths and weaknesses.
      * **Điểm Số Chi Tiết (Detailed Scores):** Shows numerical scores for all analyzed dimensions.
      * **Phản Hồi Mở (Open-ended Responses):** Lists your answers to open-ended questions.

    You can save a detailed **HTML report** by clicking the "Lưu Báo Cáo HTML" button. The report will be saved in the `output_reports_tkinter_enhanced` directory and an option to open it in your browser will be provided.

-----

## 📁 Project Structure

```
InsightMe/
├── main.py                   # Main application entry point
├── core/
│   ├── __init__.py
│   ├── question_generator.py # Generates/loads questions
│   ├── data_storage.py       # Handles data saving and loading
│   └── analyzer.py           # Performs data analysis
├── ui/
│   ├── __init__.py
│   └── tkinter_app.py        # Tkinter GUI implementation
│   # └── console_ui.py       # (Planned/Existing) Console UI
│   # └── web_app.py          # (Planned) Web UI (Streamlit/Flask)
├── visualization/
│   ├── __init__.py
│   └── plotter.py            # Creates charts (Matplotlib)
├── reporting/
│   ├── __init__.py
│   └── report_generator.py   # Generates HTML reports
├── assets/
│   └── questions.json        # << CRITICAL: Contains all assessment questions
├── data/                     # Stores user response JSON files
├── output_charts_tkinter_enhanced/ # Stores generated chart images for Tkinter
├── output_reports_tkinter_enhanced/ # Stores generated HTML reports for Tkinter
├── utils/                    # (Planned) Utility modules
│   # ├── logger.py
│   # ├── validator.py
│   # └── backup_manager.py
├── tests/                    # (Recommended) Unit tests
├── requirements.txt          # Python package dependencies
└── README.md                 # This file
```

-----

## 💡 Potential Future Enhancements

  * Implement the planned **Web UI** (Streamlit prioritized for data apps).
  * Integrate **Pandas** for more sophisticated data analysis.
  * Add **advanced analytics** modules (competency gap, career alignment, etc.).
  * Implement **user accounts and session management** to track progress over time.
  * Develop a **configuration system** (`config_manager.py`).
  * Integrate a robust **logging system** (`logger.py`).
  * Add **data validation** (`validator.py`) and **automatic backups** (`backup_manager.py`).
  * Support for **multiple languages**.
  * Export results to **PDF** in addition to HTML.
  * Develop a **plugin architecture** for extensibility.

-----

## 🤝 Contributing

Contributions are welcome\! If you'd like to contribute, please fork the repository and submit a pull request. For major changes, please open an issue first to discuss what you would like to change.

-----

## 🧑‍💻 Author

**Tran The Hao**
University of Transport Ho Chi Minh City (UTH)

-----

## 📜 License

This project is licensed under the MIT License. See the `LICENSE` file for details.

Copyright (c) 2025 Trần Thế Hảo
