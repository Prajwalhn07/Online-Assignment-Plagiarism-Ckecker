# Online-Assignment-Plagiarism-Ckecker

This project is a Python-based plagiarism checker designed to detect similarities in variable assignments between two given code snippets. The checker scans both pieces of code to extract variable assignments, compares them, and reports whether there are any common assignments. It uses regular expressions to match simple assignment patterns (variable = value) and detects potential plagiarism when similar assignments are found in both code snippets.

###Features

- Regular Expression Matching: It uses regular expressions to extract variable assignments from the code snippets.
- Plagiarism Detection: Compares the assignments in two pieces of code to detect any similarities or plagiarized content.
- Set Operations: Uses set intersections to identify common assignments between the two code snippets.

### Prerequisites

- Python Version: Python 3.8+
  Why: Python 3.8 and above have better support for type hinting, more efficient syntax, and newer features like f-strings.
- You can install it from Python's official site
- Ensure you have the latest minor version (like 3.9 or 3.10).

 ### Installation

1. **Clone the repository:
  - git clone https://github.com/your-username/plagiarism-checker.git
   cd plagiarism-checker
2. **Install dependencies (if any are required):
   - pip install -r requirements.txt
3. **Run the script:
   - python plagiarism_checker.py

### Usage

 - You can call the check_plagiarism function with two Python code snippets as string inputs.
 - It will return whether plagiarism is detected or not, and if detected, it will also show the common assignments.

### Example usage
 
- code_snippet1 = """ x = 5
y = x + 2
z = x * y
"""
- code_snippet2 = """
a = 5
b = a + 2
c = a * b
"""
result = check_plagiarism(code_snippet1, code_snippet2)
print(result)

### Expected Output

- Plagiarism detected. Common assignments: {'x = 5', 'y = x + 2', 'z = x * y'}

### Functions

- find_assignments(code):
   - This function extracts variable assignments from a given piece of code using a regular expression.
   - Input: A string containing Python code.
   - Output: A set of assignments (strings) found in the code.
- check_plagiarism(code1, code2):
   - This function checks if two code snippets contain any common assignments, indicating potential plagiarism.
   - Input: Two strings, code1 and code2, containing Python code.
   - Output: A string indicating whether plagiarism is detected and, if so, the common assignments.
 
 ### Example

  code_snippet1 = """ x = 5
  y = x + 2
  z = x * y
  """
  code_snippet2 = """ a = 5
  b = a + 2
  c = a * b
  """
  result = check_plagiarism(code_snippet1, code_snippet2)
  print(result)

 ### The output will be

   Plagiarism detected. Common assignments: {'x = 5', 'y = x + 2', 'z = x * y'}

 ### Improvements/Extensions 

   - Enhanced Assignment Matching: The current implementation uses simple regular expressions for assignment matching. To handle more complex assignments (such        as assignments with functions, lists, or dictionaries), you could enhance the regular expression pattern.
   - Line Number Tracking: Add the functionality to track the line numbers of assignments in the code, which can be useful for teachers or code reviewers.
   - Variable Renaming Detection: Detect plagiarism even if the variables are renamed (e.g., x changed to a, y to b).
   - Percentage Similarity: Provide a percentage of similarity based on the number of common assignments compared to the total number of assignments.
   - Functionality for Multiple Code Snippets: Extend the checker to handle multiple code snippets at once, especially useful in large assignments.

 ### Contributions

    - Fork the repository and create a new branch.
    - Implement your changes and ensure the code runs correctly.
    - Submit a pull request with a clear description of your changes.
