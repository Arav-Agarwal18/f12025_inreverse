
# F1 2025 Season: The Reverse Championship Analysis

## Project Overview

This project explores an alternative perspective of the Formula 1 2025 season by analyzing race and sprint results in reverse chronological order. Instead of tracking cumulative points from the start of the season, we calculate points cumulatively from the *end* of the season backwards. This novel approach aims to visualize how championship standings would unfold if races were weighted by their proximity to the season finale.

## Data Sources

The analysis uses two primary datasets for the 2025 Formula 1 season:

*   `Formula1_2025Season_RaceResults.csv`: Contains detailed results for all Grand Prix races.
*   `Formula1_2025Season_SprintResults.csv`: Contains detailed results for all Sprint races.

## Data Processing and Analysis

1.  **Data Loading**: Both `RaceResults.csv` and `SprintResults.csv` are loaded into pandas DataFrames.
2.  **Driver Selection**: A subset of prominent drivers ('Lando Norris', 'Max Verstappen', 'Oscar Piastri', 'George Russell') is selected for focused analysis.
3.  **Race Order Assignment**: A unique order is assigned to each track, allowing for sorting and analysis of races in their correct chronological sequence.
4.  **Data Merging**: Race and sprint results are merged, first with the assigned race order, and then concatenated into a single `results` DataFrame.
5.  **Data Cleaning**: 'NC' (Not Classified) and 'DQ' (Disqualified) values in the 'Position' column are replaced with `np.nan`, and the 'Position' column is converted to a numeric type for consistent processing.
6.  **Reverse Sorting**: The combined `results` DataFrame is sorted in reverse chronological order (`Order` descending) and then by 'Position' (ascending) to prepare for backward cumulative point calculation.
7.  **Cumulative Points Calculation**: For each driver, cumulative points (`Points_Cum`) are calculated starting from the last race and moving backwards towards the first race of the season. This is achieved by grouping by 'Driver' and applying a `cumsum` on 'Points' to the `results_reversed` DataFrame.

## Visualization

The project includes a line plot visualizing the reverse cumulative points for the selected drivers across all tracks. Each driver's cumulative score is plotted with a distinct color:

*   Lando Norris: Orange
*   Oscar Piastri: Yellow
*   Max Verstappen: Blue
*   George Russell: Cyan

The plot is titled 'F1 2025 in Reverse' with 'Races' on the x-axis and 'Points' on the y-axis, providing a clear representation of the standings' evolution.

## Key Findings

After processing and visualizing the data in reverse, the analysis reveals the hypothetical championship standings after each race, starting from the season finale. The top 4 drivers are displayed for each race along with their reverse cumulative points.

*   **Max Verstappen** frequently maintains a leading position in the reverse championship, often accumulating points quickly from the latter part of the season.
*   **Lando Norris** and **George Russell** show strong performances in later races, significantly impacting their cumulative points total as the season is unwound.
*   The standings demonstrate how crucial strong finishes in later races would be in a reverse-calculated championship scenario.

## Dependencies

This project requires the following Python libraries:

*   `pandas`
*   `numpy`
*   `matplotlib`

## Usage

To replicate this analysis:

1.  Clone the repository to your local machine or Google Colab environment.
2.  Ensure the `Formula1_2025Season_RaceResults.csv` and `Formula1_2025Season_SprintResults.csv` files are present in the same directory as the notebook, or adjust the file paths accordingly.
3.  Run all cells in the Jupyter/Colab notebook sequentially.
4.  The generated plot will visualize the reverse cumulative points, and the console output will display race results and champion standings after each track.
