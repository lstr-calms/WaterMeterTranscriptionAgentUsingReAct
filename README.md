# Water Meter Transcription Agent Using ReAct
This project contains a simple Python class "SimpleWaterMeterAgent" that acts as a basic agent using the ReAct pattern to extract water meter readings from natrual language text and convert them into a structured JSON format.

# How it Works
The 'SimpleWaterMeterAgent' class has a 'transcribe' method that takes a string as input, which represents the natural language text containing water meter readings. It performs the following steps:

Step 1: Thought --> Identifies the need to find the unit names and their corresponding readings in the input text.

Step 2: Action --> Uses a regular expression pattern (regex) to extract potential unit names (alphanumeric) and their

corresponding readings (numbers) from the text. The pattern looks for phrases such as "Unit X reads Y or X is Y".

Step 3: Observation --> Reports the number of potential readings found and displays the extracted matches.

Step 4: Thought --> Determines the next step is to convert the extracted data into JSON format and handle any duplicate unit names (case sensitive).

Step 5: Action --> Formats the extracted unit and reading pairs into a list of dictionaries. It uses a 'set' to keep track of unit names already added to the result, ensuring that only the first occurence of a unit is included in the final JSON output.

Step 6: Observation --> Reports the numbber of unique JSON entries created.

Step 7: Final Answer --> Dumps the list of dictionaries into a formatted JSON string and prints it.


#Using the Agent
Simple run the Python script and the code will prompt the user to enter a water meter reading.
```
Sample Input:
"Unit 19A reads 30 cubid meters, 19B is 5 cubic meters, 19C reads 8 cubic meter, 19B reads 5 cubic meters"
```
```
Output:
Enter the water meter readings: Unit 19A reads 30 cubid meters, 19B is 5 cubic meters, 19C reads 8 cubic meter, 19B reads 5 cubic meters
Water Meter Agent Starting...
Input: Unit 19A reads 30 cubid meters, 19B is 5 cubic meters, 19C reads 8 cubic meter, 19B reads 5 cubic meters

Thought: I need to find unit names and their readings in this text.
Action: Extract units and numbers using regex pattern.
Observation: Found 4 readings: [('19A', '30'), ('19B', '5'), ('19C', '8'), ('19B', '5')]
Thought: Now I need to convert these to JSON format and handle duplicates.
Action: Format as JSON array and ignore duplicates.
Observation: Created 3 unique JSON entries.
Final Answer:
[
  {
    "unit": "19A",
    "reading": 30
  },
  {
    "unit": "19B",
    "reading": 5
  },
  {
    "unit": "19C",
    "reading": 8
  }
]
```
