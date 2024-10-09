# pyswimplot

`pyswimplot` is a Python library and CLI tool for creating swimmer plots, commonly used in survival analysis. The tool visualizes patient treatment timelines, survival durations, responses to treatment, and statuses (alive, dead, or under therapy). It supports customizable plots with several options for representing patient data, treatment types, and survival outcomes.

## Features

- Visualizes survival duration for each patient.
- Displays treatments and responses, including chemotherapy, immunotherapy, surgery, or diagnosis without treatment.
- Highlights patients currently under therapy.
- Adds patient IDs, survival status, and survival time labels.
- Supports generating plots in PDF format.

## Installation

To use this tool, clone the repository and install the necessary dependencies using `pip`:

```bash
git clone https://github.com/yourusername/pyswimplot.git
cd pyswimplot
pip install -r requirements.txt
```

## Usage
You can use pyswimplot either as a command-line tool or in a Python script.

## CLI Usage
```bash
Copy code
python swimmer_plot.py -input_csv <INPUT_CSV> -output_file <OUTPUT_FILE> [OPTIONS]
```
### Required Arguments
-input_csv <INPUT_CSV>: The path to the input CSV file containing patient data.
-output_file <OUTPUT_FILE>: The path where the generated swimmer plot (in PDF format) will be saved.

### Optional Arguments
-input_delimiter <INPUT_DELIMITER>: Delimiter used in the CSV file (default: ,).
-survival_column <SURVIVAL_COLUMN>: Column containing patient survival time (default: disease_free_time).
-treatment_id <TREATMENT_ID>: Identifier for the treatment type.
-treatment_column <TREATMENT_COLUMN>: Column indicating the treatment type per patient.
-response_column <RESPONSE_COLUMN>: Column specifying the treatment response (default: empty).
-status_column <STATUS_COLUMN>: Column indicating patient survival status (default: status).
-patient_id_column <PATIENT_ID_COLUMN>: Column with the unique patient identifier (default: patient_id).
-max_days <MAX_DAYS>: Maximum number of days to display on the plot (default: 1825 days or 5 years).
-survival_right_labels_column <SURVIVAL_RIGHT_LABELS_COLUMN>: Column for labels on the right, showing survival times greater than max_days.
-on_therapy_column <ON_THERAPY_COLUMN>: Column to mark patients still receiving therapy.
-plot_patient_id: If set, patient IDs will be displayed on the plot.
-plot_title <PLOT_TITLE>: Title of the plot (default: "Swimmer plot").
--verbose <VERBOSE>: Set verbosity level for logging (default: 2).
--show: If set, the plot will be displayed after creation.
## Example Command
``` bash
python swimmer_plot.py -input_csv data.csv -output_file swimmer_plot.pdf \
    -survival_column "SurvivalDays" -treatment_id "Treatment1" \
    -treatment_column "Treatment" -response_column "Response" \
    -status_column "Status" -patient_id_column "PatientID" \
    -max_days 1000 --show
```
This example reads patient data from data.csv and generates a swimmer plot, displaying patients' survival days, treatments, responses, and statuses. The plot will be saved as swimmer_plot.pdf, and it will also be shown on screen.
