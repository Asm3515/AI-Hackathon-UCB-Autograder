# AI-Hackathon-UCB-Autograder|

##Git Link - https://github.com/Asm3515/AI-Hackathon-UCB-Autograder/


# Code Grader System Architecture

This project implements a code grading system that utilizes advanced machine learning models and optimizations to provide efficient and accurate grading. The system is designed to run on Intel Development Cloud with Intel Extension for PyTorch (IPEX) optimizations. The following architecture diagram outlines the major components and their interactions.

## Architecture Diagram


+----------------------------+   +---------------------------+   +----------------------------+
|                            |   |                           |   |                            |
|    Code Submission         |   |   Questionnaire           |   |   Grading Server           |
|    Interface               |   |   Interface               |   |                            |
|                            |   |                           |   |                            |
+-------------+--------------+   +-------------+-------------+   +-------------+--------------+
              |                              |                               |
              |                              |                               |
              v                              v                               |
+-------------+--------------+   +-------------+-------------+               |
|                            |   |                           |               |
|    Code Content            |   |   Questionnaire Content   |               |
|                            |   |                           |               |
+-------------+--------------+   +-------------+-------------+               |
              |                              |                               |
              v                              v                               |
+-------------+--------------+   +-------------+-------------+               |
|                            |   |                           |               |
| Summarization using        |   | Summarization using       |               |
| Tiny T5 Model              |   | Tiny T5 Model             |               |
|                            |   |                           |               |
+-------------+--------------+   +-------------+-------------+               |
              |                              |                               |
              |                              |                               |
              v                              v                               |
+-------------+--------------+   +-------------+-------------+               |
|                            |   |                           |               |
| Code Summary               |   | Questionnaire Summary     |               |
|                            |   |                           |               |
+-------------+--------------+   +-------------+-------------+               |
              \                              /                                |
               \                            /                                 |
                \                          /                                  |
                 \                        /                                   |
                  \                      /                                    |
                   \                    /                                     |
                    v                  v                                      |
+-------------------+------------------+                                      |
|                                      |                                      |
| Check Code Against Summarized Points |                                      |
|                                      |                                      |
+-------------------+------------------+                                      |
                    |                                                         |
                    v                                                         |
+-------------------+------------------+                                      |
|                                      |                                      |
| Test Results                         |                                      |
|                                      |                                      |
+-------------------+------------------+                                      |
                    |                                                         |
                    v                                                         |
+-------------------+------------------+                                      |
|                                      |                                      |
| Generate Feedback and Score          |                                      |
| using PHI 3 Model                    |                                      |
|                                      |                                      |
+-------------------+------------------+                                      |
                    |                                                         |
                    v                                                         |
+-------------------+------------------+                                      |
|                                      |                                      |
| Feedback and Score                   |                                      |
|                                      |                                      |
+-------------------+------------------+                                      |
                    |                                                         |
                    v                                                         |
+-------------------+------------------+                                      |
|                                      |                                      |
| Display Feedback and Score to User   |                                      |
|                                      |                                      |
+-------------------+------------------+                                      |



## Explanation

1. **Code Submission Interface**: 
   - Students submit their code through a web interface.
   - The interface captures the code content.

2. **Questionnaire Interface**:
   - Students or instructors provide a questionnaire describing the expected functionality of the code.
   - The interface captures the questionnaire content.

3. **Summarization using Tiny T5 Model**:
   - The code content and questionnaire content are passed to the Tiny T5 model to generate summaries.
   - This step helps to condense the content to key points for easier analysis.

4. **Check Code Against Summarized Points**:
   - The summarized points from the code and questionnaire are used to generate test cases.
   - The student's code is then executed against these test cases to verify its correctness.

5. **Generate Feedback and Score using PHI 3 Model**:
   - Based on the test results and the summarized points, the PHI 3 model generates human-like feedback.
   - The model also assigns a score to the submission.

6. **Display Feedback and Score to User**:
   - The feedback and score are displayed back to the user through the interface.

## Steps to Implement

1. **Setup Environment**:
   - Configure Intel Development Cloud and install necessary libraries such as `transformers`, `pytest`, and `intel_extension_for_pytorch`.

2. **Summarization Module**:
   - Implement the summarization function using Tiny T5 and optimize it with IPEX.

3. **Test Case Generation and Execution**:
   - Write functions to generate test cases from the summary and execute the code against these cases.

4. **Feedback and Scoring Module**:
   - Implement the feedback generation and scoring using the PHI 3 model, also optimized with IPEX.

5. **Integration**:
   - Integrate all the components into a cohesive system that handles the flow from code submission to feedback display.

6. **Web Interface**:
   - Develop a web interface for students to submit their code and view feedback and scores.

By following this architecture, you can create a scalable and efficient code grading system optimized for Intel's hardware using the specified models and tools.


