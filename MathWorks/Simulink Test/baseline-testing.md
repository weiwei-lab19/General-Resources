# Baseline Testing 

This guide shows how to use Simulink® Test™ to create and run a baseline test to test for regression after you make changes to a model.

Link for the full guide can be found [here](https://www.mathworks.com/help/sltest/ug/regression-test-workflow.html)

Model under test: `sldemo_absbrake.slx`\
This model can be found by running the following in the command window:
```matlab
openExample('simulinktest/BaselineTestExample')
```
This model simulates the behavior of a wheel with an anti-lock braking system (ABS) and logs the signals in the MATLAB workspace. 

## Author a Baseline Test Case
1) Set Up your Test File\
    Create a new test file
    ```matlab
    testFile = sltest.testmanager.TestFile('baselineTestFile');
    ```
    If the test file doesn't exist, this will by default, create a new test suite and test case named `New Test Suite 1` and `New Test Case 1`. \
    Rename the test case to `baselineTestCase`
    ```matlab
    testCase = testFile.getAllTestSuites.getTestCases;
    testCase.Name = 'baselineTestCase';
    ```

2) Configure the Test Case\
    Set up the model and simulation settings:
    ```matlab
    % Set the model to test, this is where you define the Simulink model being tested. Here it is 'sldemo_absbrake.slx'
    testCase.setProperty('Model', 'sldemo_absbrake');
    % Enable 'Recover coverage for system under test'
    cov_settings = getCoverageSettings(testFile);
    cov_settings.RecordCoverage = true;
    ```

3) Capture and Validate Baseline Data
    ```matlab
    % This simulates the model and captures signals that are selected for signal logging, and saves the logged signals in a .mat file named 'absbrake_baselinedata'
    baseline = captureBaselineCriteria(testCase, 'absbrake_baselinedata', false);
    ```
    Run the test case
    ```matlab
    resultSet = run(testCase)
    ```
    ```
    resultSet = 

        ResultSet with properties:

                        Outcome: Passed
                    NumPassed: 1
                    NumFailed: 0
                    NumDisabled: 0
                NumIncomplete: 0
                    NumTotal: 1
            NumTestCaseResults: 1
            NumTestSuiteResults: 0
            NumTestFileResults: 0
                    StartTime: 27-Dec-2025 14:49:50
                    StopTime: 27-Dec-2025 14:49:58
                    Duration: 8.331 sec
                    Description: []
                        Name: 'Results: 2025-Dec-27 19:49:48'
                CoverageResults: [1×1 cvdata]
                    UserData: []
    ```
4) Generate a baseline test report\
    The following will generate a test report in HTML inside 'baselineReport.zip'
    ```matlab
    sltest.testmanager.report(resultSet,'baselineReport.zip',...
    'IncludeTestResults',0,'IncludeComparisonSignalPlots',true,...
    'IncludeSimulationSignalPlots',true,'NumPlotRowsPerPage',3);
    ```
    This report will include plots showing signals that were logged. For this case, the baseline signals and the simulated output signals should be the same since there were no difference between the captured baseline model and the simulated test.\
    Save test file 
    ```matlab
    saveToFile(testFile);
    ```

## Compare Simulation to Baseline Data