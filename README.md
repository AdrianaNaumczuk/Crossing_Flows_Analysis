# Crossing_Flows_Analysis

## Description
This project involves calculating and visualizing Time-Dependent Delayed Speed Correlation (TDSC) between pairs of agents using a dataset of pedestrian trajectories. The dataset includes positional coordinates of agents, which are used to compute velocities and TDSC values. The calculation functions are defined in the TDSC.py file, while the PLOTS.py file handles the generation and saving of visual plots.

## Purpose
The main objective of this study is to explore how delays in one agent's velocity relate to another agent's velocity over time. By analyzing visual representations of these correlations, the project aims to provide insights into how agents' movements are interrelated, which can be valuable for understanding complex behaviors in scenarios such as pedestrian dynamics, vehicle traffic, and multi-agent systems.

## Features

### Calculation Functions (TDSC.py):

#### Velocity Calculation:
calculate_velocity(data, agent_num): Computes the velocity of an agent based on its position data over time, converting position changes into speed.

#### Delayed Velocity Analysis:
calculate_velocity_with_tau(data, agent_num, tau): Computes the velocity of an agent and then adjusts it by a specified time delay (tau).

#### Delta Speed Calculation:
delta_sij(data, agent_i, agent_j, tau): Measures the absolute difference in velocities between two agents, considering a time delay.

### TDSC Computation:
calculate_tdsc(data, agent_i, agent_j, tau, delta_t=1 / 120, omega=80): Computes the Time-Dependent Delayed Speed Correlation (TDSC) between two agents. This method aggregates the differences in velocities over a range of time delays to capture the dynamic relationship between agents.

### Plotting Functions (PLOTS.py):

#### Data Reading:
read_data(file_path): Reads TDSC results from a CSV file into a pandas DataFrame.

#### Plot Generation:
plot_data(df_plot, my_file, my_agent_i, my_agent_j, output_path): Generates and saves a heatmap plot of the TDSC values with time delay (tau) on the y-axis and time on the x-axis. Includes visual annotations to highlight key aspects.

## How It Works

### 1. Compute Velocities and TDSC:

#### Data Preparation: Start with positional coordinates of agents from the dataset.
#### Velocity Calculation: Use the calculate_velocity function to compute velocities from the positional data.
#### Delayed Velocity Calculation: Apply time delays to the velocities using the calculate_velocity_with_tau function.
#### Delta Speed and TDSC: Compute delta speeds and TDSC values using the delta_sij and calculate_tdsc functions.

### 2. Generate Plots:

#### Data Reading: Load the computed TDSC values from CSV files using the read_data function.
#### Plotting: Create heatmap plots with time delay and time on the axes using the plot_data function. The plots visualize TDSC values and highlight the best tau values.

## Usage

### Calculating TDSC
#### Prepare Your Data:
Ensure you have CSV files with positional coordinates for each agent.
#### Run TDSC Calculations:
Utilize the functions from TDSC.py to:
- Compute velocities from positional data.
- Calculate TDSC values for different pairs of agents and time delays.
Save the computed TDSC results to CSV files.

### Visualizing Results
#### Prepare Your Data for Plotting:
Ensure that the TDSC results are saved in CSV files with the appropriate format.
#### Generate Plots:
Run the main() function from PLOTS.py to read the TDSC data and generate visual plots.

Example of PLOTS.py usage:

    import pandas as pd
    from TDSC import calculate_tdsc
    from PLOTS import read_data, plot_data

    def main():
        # Parameters
        my_file = 'CF102'
        my_agent_i = 1
        my_agent_j = 4
    
        # Define file paths
        input_path = f'{my_file}_{my_agent_i}_{my_agent_j}.csv'
        output_path = f'{my_file}_{my_agent_i}_{my_agent_j}.png'
    
        # Read data and generate plot
        print('Reading data from:', input_path)
        df_plot = read_data(input_path)

    print('Generating plot and saving to:', output_path)
    plot_data(df_plot, my_file, my_agent_i, my_agent_j, output_path)

    if __name__ == "__main__":
        main()

## Summary
This project provides a structured approach for analyzing and visualizing Time-Dependent Delayed Speed Correlation (TDSC). The TDSC.py file contains functions for calculating velocities and TDSC values from positional data, while the PLOTS.py file generates visual plots of the results. Together, these components facilitate a comprehensive analysis of dynamic interactions between agents.

