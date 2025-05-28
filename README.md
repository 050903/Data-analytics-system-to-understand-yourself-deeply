# Data-analytics-system-to-understand-yourself-deeply
## DEMO
![image](https://github.com/user-attachments/assets/8f736753-443f-4a77-8d0e-14179d65d5c7)
![image](https://github.com/user-attachments/assets/b81a03a7-eb66-4395-83bd-3b41d366b492)
![image](https://github.com/user-attachments/assets/7ddd02b6-b1b6-4741-b27c-31e157d4319a)
![image](https://github.com/user-attachments/assets/0cfd09f8-4bf2-4e44-af69-2caa0b9fbf48)

# 🎯 Personal Insight & Development Tool 🧠✨

A comprehensive Python application designed for personal self-assessment, analysis, and visualization of psychological, behavioral, and cognitive traits. This tool guides users through a structured questionnaire, processes their responses, and generates insightful reports including data visualizations to foster self-awareness and personal growth.

The application's user interface and question content are primarily in Vietnamese.

## 🌟 Core Features

*   **Structured Questionnaire:** 📝 A curated set of 50 questions spanning five key personal dimensions:
    *   **Core Values (Giá trị cốt lõi):** Understanding fundamental beliefs and principles.
    *   **Multiple Intelligences (Trí thông minh đa dạng):** Identifying dominant types of intelligence based on Howard Gardner's theory (adapted).
    *   **Learning Motivation (Động lực học tập):** Assessing drivers and motivations behind learning.
    *   **Personal Goals (Mục tiêu cá nhân):** Evaluating clarity and focus on personal objectives.
    *   **Self-Awareness (Tự nhận thức):** Gauging the level of understanding of one's own emotions, strengths, and weaknesses.
*   **Interactive GUI:** 💻 A user-friendly graphical interface built with Tkinter for a smooth assessment experience.
*   **Timed Responses:** ⏱️ Each question has a configurable time limit (default: 15 seconds) to encourage intuitive answers.
*   **Likert Scale Input:** Users respond on a 1-5 scale (Strongly Disagree to Strongly Agree).
*   **Data Persistence:**
    *   💾 **SQLite Database:** Assessment results (responses, analysis) are stored locally in a `personal_assessment.db` file for historical tracking.
    *   📄 **JSON & CSV Export:** Individual assessment data and raw responses can be saved in JSON and CSV formats.
*   **In-depth Analysis:** 🔍
    *   **Descriptive Statistics:** Calculates mean, median, standard deviation, min, and max scores for each assessment category.
    *   **Strengths & Weaknesses Identification:** Highlights areas of high and low scores based on percentile ranking of category averages.
    *   **K-Means Clustering (Simplified):** Applies K-Means clustering on response values to identify patterns (e.g., groups of low, medium, high responses). *Note: This is a simplified application for pattern discovery.*
*   **Rich Data Visualization (using Plotly):** 📊
    *   **Radar Chart:** Provides a holistic view of an individual's profile across the five main dimensions.
    *   **Bar Chart:** Compares average scores across different assessment categories, color-coded for quick interpretation.
    *   **Pie Chart:** Illustrates the proportion of identified strengths, weaknesses, and neutral areas.
*   **Report Generation:** 🗂️ Automatically saves generated charts as PNG files and data files (JSON, CSV) into a structured `reports/` directory.
*   **Historical Review:** Allows users to view a list of past assessments stored in the database.

## 🛠️ Technologies, Algorithms & Tools

### 1. Programming Language
    *   **Python 3.x:** The core language used for development.

### 2. Core Libraries & Frameworks
    *   **Tkinter:** (Python's standard GUI toolkit) Used for building the graphical user interface, providing an interactive experience for the assessment.
    *   **Pandas:** Employed for data manipulation, especially for creating DataFrames to facilitate CSV export and potentially more complex data analysis in future extensions.
    *   **NumPy:** Utilized for numerical operations, particularly for statistical calculations (mean, median, std deviation, percentiles) and array manipulations required by Scikit-learn.
    *   **Plotly:** A powerful interactive graphing library used to generate dynamic and visually appealing charts (Radar, Bar, Pie). These charts can be viewed in a web browser or saved as static images.
    *   **Scikit-learn:**
        *   `StandardScaler`: Used for feature scaling (standardizing response values) before applying K-Means clustering. This ensures that all responses contribute equally to the distance calculations.
        *   `KMeans`: The K-Means clustering algorithm is applied to the (scaled) response values to group them into a predefined number of clusters (dynamically adjusted, max 3). This helps in identifying general patterns or tendencies in the user's responses (e.g., predominantly high, medium, or low scores).
    *   **SQLite3:** (Python's built-in module) Used for creating and managing a local SQLite database to store assessment history, allowing users to track their progress over time.
    *   **JSON & CSV Modules:** (Python's built-in modules) Used for serializing assessment data into JSON format and for writing raw responses into CSV files, enabling data portability and external analysis.

### 3. Key Algorithms & Techniques
    *   **Descriptive Statistics:** Standard statistical measures (mean, median, standard deviation, min, max) are calculated for scores within each assessment category. This provides a quantitative summary of the user's responses.
    *   **Percentile-based Strength/Weakness Identification:** Strengths are identified as categories where the average score is above the 75th percentile of all category averages. Weaknesses are categories with average scores below the 25th percentile. This is a relative measure within the user's own assessment.
    *   **K-Means Clustering:**
        *   **Purpose:** To uncover underlying patterns in the overall response set by grouping similar response values.
        *   **Process:**
            1.  Response values are collected.
            2.  Data is scaled using `StandardScaler` to have zero mean and unit variance.
            3.  `KMeans` algorithm partitions the scaled responses into 'k' clusters (dynamically set, typically 2 or 3 based on data variance).
            4.  The cluster centers and labels are used to infer general response tendencies.
    *   **Timed Event Handling (Tkinter `after`):** Tkinter's `after` method is used to implement the per-question timer, automatically advancing or defaulting the answer if the time limit is reached. Careful management of these timed events (canceling previous ones) is crucial for stability.
    *   **Threading:** The analysis and report generation process is offloaded to a separate thread (`threading` module) after the assessment is complete. This prevents the GUI from freezing during potentially time-consuming calculations and file I/O operations, improving user experience.

### 4. Development & Debugging Tools
    *   **Visual Studio Code (VS Code):** (Assumed IDE) With Python extension and `debugpy` for debugging.
    *   **Git & GitHub:** (Assumed for version control and collaboration, if applicable).

## ⚙️ How It Works

1.  **Initialization:**
    *   The `PersonalAssessmentSystem` class initializes the question set and the SQLite database.
    *   The `AssessmentGUI` class sets up the main Tkinter window and styles.

2.  **Welcome Screen:**
    *   The user is greeted and prompted to enter their name.

3.  **Assessment Process:**
    *   Upon starting, the GUI iteratively displays each of the 50 questions.
    *   For each question:
        *   The question text and its category are shown.
        *   A progress bar indicates overall completion.
        *   A countdown timer (e.g., 15 seconds) starts.
        *   The user selects a response from 1 (Strongly Disagree) to 5 (Strongly Agree) using radio buttons or corresponding number keys.
        *   If the timer expires before a selection, a neutral response (3) is automatically recorded.
        *   The selected response and question ID are stored.

4.  **Data Analysis (Post-Assessment):**
    *   Once all questions are answered, the collected responses are passed to the `PersonalAssessmentSystem`.
    *   **Category Scoring:** Average, median, standard deviation, min, and max scores are computed for each of the five main categories.
    *   **Strength/Weakness Analysis:** Categories are flagged as strengths or weaknesses based on percentile comparisons of their average scores.
    *   **Clustering:** K-Means clustering is performed on the raw response values to identify general response patterns.

5.  **Report Generation & Visualization:**
    *   The analysis results are used to generate:
        *   A Radar Chart (Plotly) showing the overall profile.
        *   A Bar Chart (Plotly) comparing category averages.
        *   A Pie Chart (Plotly) showing the distribution of strengths/weaknesses.
    *   These charts are saved as PNG images.
    *   The full assessment data (user info, responses, analysis) is saved as a JSON file.
    *   Raw responses are saved as a CSV file.
    *   All results are also committed to the SQLite database.

6.  **Results Display:**
    *   The GUI displays the analysis results in a tabbed interface:
        *   **Overview Tab:** Shows identified strengths, weaknesses, and general statistics.
        *   **Details Tab:** Presents a table with detailed scores for each category.
        *   **Charts Tab:** Provides buttons to view the generated Plotly charts (which open in a browser or Plotly's default viewer).
        *   **Export Tab:** Lists the paths to the saved report files (PNGs, JSON, CSV) and offers options to export to a custom directory or view assessment history.

7.  **Historical Data:**
    *   Users can access a "View History" feature to see a list of their past assessments retrieved from the SQLite database.

## 🚀 Installation & Setup

1.  **Prerequisites:**
    *   Python 3.7 or higher.
    *   `pip` (Python package installer).

2.  **Clone the Repository (or download the script):**
    ```bash
    # If it's a Git repository
    git clone <repository_url>
    cd <repository_directory>
    ```
    If you only have the script, save it as `personal_assessment_tool.py` (or your preferred name).

3.  **Create a Virtual Environment (Recommended):**
    ```bash
    python -m venv venv
    # On Windows
    .\venv\Scripts\activate
    # On macOS/Linux
    source venv/bin/activate
    ```

4.  **Install Required Libraries:**
    ```bash
    pip install pandas numpy matplotlib seaborn plotly scikit-learn kaleido
    ```
    *   `kaleido` is required by Plotly to save charts as static images (e.g., PNG).
    *   `matplotlib` and `seaborn` are included for completeness, though Plotly is the primary charting tool in the GUI version.

5.  **Font for Vietnamese Characters:**
    *   Ensure you have a font that supports Vietnamese characters installed on your system (e.g., Arial, DejaVu Sans, Tahoma). The script attempts to use 'DejaVu Sans' or 'Arial Unicode MS' for Matplotlib (if used), and Plotly generally handles Unicode well but relies on system fonts.

## ▶️ Usage Instructions

1.  **Run the Application:**
    Navigate to the project directory in your terminal (ensure your virtual environment is activated) and run:
    ```bash
    python personal_assessment_tool.py
    ```
    (Replace `personal_assessment_tool.py` with the actual name of your Python file.)

2.  **Welcome Screen:**
    *   The application will launch, displaying a welcome screen.
    *   Enter your name in the provided field.
    *   Click the "BẮT ĐẦU ĐÁNH GIÁ" (Start Assessment) button or press Enter.

3.  **Answering Questions:**
    *   Questions will be displayed one by one.
    *   Read each question and select your level of agreement on the 1-5 scale using the buttons or by pressing the corresponding number key (1-5).
    *   A timer will count down for each question. If you don't answer within the time limit, a neutral response (3) will be recorded.
    *   A progress bar at the top shows your overall progress.

4.  **Viewing Results:**
    *   After completing all questions, the system will analyze your responses. This may take a few moments.
    *   A multi-tabbed interface will appear:
        *   **Tổng quan (Overview):** Summary of strengths, weaknesses, and overall statistics.
        *   **Chi tiết (Details):** A table with detailed scores for each assessment category.
        *   **Biểu đồ (Charts):** Buttons to display the Radar, Bar, and Pie charts. Clicking these will typically open the interactive charts in your default web browser.
        *   **Xuất báo cáo (Export Report):**
            *   Lists the paths to the automatically saved report files (PNG images, JSON data, CSV responses) in the `reports/` sub-directory.
            *   Allows you to "Mở" (Open) these files.
            *   Option to "Xuất vào thư mục khác" (Export to another directory).
            *   Option to "Xem lịch sử đánh giá" (View assessment history) from the database.

5.  **Restart or Exit:**
    *   Click "ĐÁNH GIÁ LẠI" (Re-assess) to take the assessment again.
    *   Close the window to exit the application.

## 📁 Output Files Structure

Upon completion of an assessment, the following files are typically generated:

*   `personal_assessment.db`: SQLite database file in the root project directory, storing all assessment histories.
*   `reports/`: A sub-directory created in the root project directory.
    *   `radar_<UserName>_<Timestamp>.png`
    *   `bar_<UserName>_<Timestamp>.png`
    *   `pie_<UserName>_<Timestamp>.png`
    *   `data_<UserName>_<Timestamp>.json` (Contains user info, responses, and full analysis results)
    *   `responses_<UserName>_<Timestamp>.csv` (Contains raw question IDs, categories, questions, and responses)

*(<UserName> will be a sanitized version of the input name, and <Timestamp> will be in YYYYMMDD_HHMMSS format.)*

## 🧑‍💻 Author

*   **Tran The Hao**
*   University of Transport Ho Chi Minh City (UTH)

## 📜 License

### MIT License

### Copyright (c) 2025 Trần Thế Hảo

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights  
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell  
copies of the Software, and to permit persons to whom the Software is  
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all  
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR  
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,  
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE  
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER  
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,  
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE  
SOFTWARE.
