---
tags:
  - "#python"
  - "#software-development"
  - "#developer-tools"
  - "#browser-history"
  - "#open-source"

  - "#google-maps"
  - "#obsidian"
  - "#markdown-conversion"
---
# Google Maps Timeline to Obsidian Converter
This Python script, timelineToObsidian.py, is designed to convert your Google Location History data into Markdown files suitable for use in Obsidian or other note-taking applications.
It creates separate Markdown files for each day's location history, providing a structured and readable format. Here's how to use and understand the script:

## Prerequisites
Before you begin, ensure you have the following:
- Google Location History data in JSON format - This can be retrieved from Google Takeout.
- Python 3 installed on your computer.

## Setup
- Clone or download this repository to your computer.
- Create an input folder named "input".
- Copy your "Semantic Location History" folder from your Google Takeout to the "input" folder.

```
- Google Timeline to Obsidian
  - input
    - Semantic Location History
```

- Configure your output preferences in the config.json file. You can choose to include or exclude various details from the generated Markdown files. Refer to the configuration section below for more details.

## Configuration
In the config.json file, you can customize the script's behavior by adjusting the following settings.

### Activity Segments
`output_activity_segments`: Set to true to include activity segments in the output Markdown files. An Activity Segment when you move from one location to another.
- `output_activity_activityType`: Set to true to include activity types in the activity segment section. This may be walking, driving, getting a bus or train etc.
- `output_activity_formatted_duration`: Set to true to include the formatted duration in the activity segment section. This is the duration of the travel. It includes `output_activity_start_time_24_hour` and `output_activity_end_time_24_hour`.
- `output_activity_start_time_24_hour`: Set to true to include the 24-hour start time in the activity segment section.
- `output_activity_start_iframe`: Set to true to include an iframe with the starting location map in the activity segment section.
- `output_activity_end_time_24_hour`: Set to true to include the 24-hour end time in the activity segment section.
- `output_activity_end_iframe`: Set to true to include an iframe with the ending location map in the activity segment section.

### Place Visits
`output_place_visits`: Set to true to include place visits in the output Markdown files. A Place Visit is when you stop at a location.
- `output_place_location`: Set to true to include the location name in the place visit section. The location name is a friendly name. This usually uses something like a business name or known location name or the road name etc.
- `output_place_formatted_duration`: Set to true to include the formatted duration in the place visit section. This is the duration of the stop. It includes `output_place_start_time_24_hour` and `output_place_end_time_24_hour`.
- `output_place_iframe`: Set to true to include an iframe with the location map in the place visit section.
- `output_place_start_time_24_hour`: Set to true to include the 24-hour start time in the place visit section.
- `output_place_end_time_24_hour`: Set to true to include the 24-hour end time in the place visit section.
- `output_place_address`: Set to true to include the address in the place visit section.
- `output_place_semanticType`: Set to true to include the semantic type in the place visit section. This could be something like `TYPE_HOME` or `TYPE_WORK`.
- `output_place_place_id`: Set to true to include the place ID in the place visit section. This is a unique location identifier used by Google... I think...

### Output Folder Structure
`output_folder_structure`: Define the structure of the output folders for the Markdown files. You can customize the output folder hierarchy using the following settings:
- `output_folder`: The root folder where output files will be stored. The dafault is `./output`
- `main_folder_name`: The name of the main folder. The default is `Location History`.
- `year_format`: A Python strftime format string for the year folder (e.g., "%Y" for the year in four digits).
- `month_format`: A Python strftime format string for the month folder (e.g., "%m-%B" for the month in numeric and full name format).
- `day_format`: A Python strftime format string for the day folder (e.g., "%Y-%m-%d-%A" for the date in year-month-day-day_of_week format).

### General config option
`input_folder`: Specify the path to the folder containing your "Semantic Location History" folder. The default is `./input`
`iframe_base_url`: The base URL for generating iframes for location maps. You can use this to customize the map provider and styling. You may also be able to use the variables `loc_lat` and `loc_long` with another map provider.

### Frontmatter for Obsidian
`output_frontmatter_toggle`: If set to true, adds the below frontmatter to the markdown files
- `title`: A Python strftime format string for the day folder (e.g., "%Y-%m-%d-%A" for the date in year-month-day-day_of_week format).
- `tags`: A comma seperated list of tags (e.g. "LocationHistory,GoogleTakeout").

## Running the Script
After configuring the config.json file, run the script using the following command:

`python timelineToObsidian.py`
Be patient. This took a minute or two on my computer when processing ~10 years of data.
The script will process your Google Location History data, generate Markdown files, and store them in the specified output folders according to the configured folder structure.

## Output
The script will create a structured set of Markdown files, organized by year, month, and day, based on your location history data. Each Markdown file contains information about your daily activities and place visits, as per your configuration.

### File Organization
The generated Markdown files will be organized in a folder structure based on the date and the configuration settings defined in `output_folder_structure`. This allows you to easily navigate and find location history for specific dates.

### Cleaning Invalid Characters
The script also includes a function called clean_filename to remove characters not allowed in Windows filenames. This ensures that generated filenames are valid and do not contain any problematic characters.

### Markdown Content
Here's a breakdown of the content in the generated Markdown files:

#### Activity Segments
If you've enabled output_activity_segments, the Markdown files will include sections for each activity segment. Each section contains:
- Activity type (if output_activity_activityType is enabled).
- Formatted duration (if output_activity_formatted_duration is enabled).
- 24-hour start time (if output_activity_start_time_24_hour is enabled).
- 24-hour end time (if output_activity_end_time_24_hour is enabled).
- Iframes with starting and ending location maps (if output_activity_start_iframe and output_activity_end_iframe are enabled).

#### Place Visits
If you've enabled output_place_visits, the Markdown files will include sections for each place visit. Each section contains:
- Location name (if output_place_location is enabled).
- Formatted duration (if output_place_formatted_duration is enabled).
- Iframe with the location map (if output_place_iframe is enabled).
- 24-hour start time (if output_place_start_time_24_hour is enabled).
- 24-hour end time (if output_place_end_time_24_hour is enabled).
- Address (if output_place_address is enabled).
- Semantic type (if output_place_semanticType is enabled).
- Place ID (if output_place_place_id is enabled).

## Notes
- Make sure to back up your original Google Location History data before running the script to avoid data loss.
- This script provides a starting point for converting Google Location History data into Markdown files. You can further customize it to suit your specific needs or integrate it into your note-taking workflow.
- Please note that the script processes data based on your configuration settings. Ensure that you have configured the script to include the information you need in your Markdown files.

## Contributing
Contributions are welcome! If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.

Author Staples1010
