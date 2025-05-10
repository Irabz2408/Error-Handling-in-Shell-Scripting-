> #  Error-Handling-in-Shell-Scripting

Mini Project - Error Handling in Shell Scripting 
Error handling is a crucial aspect of scripting that involves anticipating and managing errors that may occur during script execution. These errors could arise from various factors such as incorrect user input, unexpected system behavior, or resource unavailability. Proper error handling is essential for improving the reliability, robustness, and usability of shell scripts. 
1. # Implementing Error Handling 
When implementing error handling in shell scripting, it's essential to consider various scenarios and develop strategies to handle them effectively. Here are some key steps to think through ar implement error handling: 
2. # Identify Potential Errors
: Begin by identifying potential sources of errors in your script, such as user input validation, command execution, or file operations. Anticipate scenarios wherE errors may occur and how they could impact script execution. 

3. # Use Conditional Statements
: Utilize conditional statements (if, elif, else) to check for error conditions and respond accordingly. Evaluate the exit status ($?) of commands to determir whether they executed successfully or encountered an error. 
Here is the detailed analysis: 
1. Control Flow Implementation: The task mentioned the utilization of ' if-else' statements and ' for loops' for scripting control flow. However, no code involving these elements has been provided. There is no evidence of script-based iterations or conditional handling to manage multiple scenarios. 
![](./Images/aws%20intsalled.png)


2. Error Handling for S3 Buckets: The instructor emphasized the use of scripts to check for the existence of an S3 bucket before attempting to create it (using 'aws s3api head-bucket'). While the submission shows a command to create an S3 bucket, there is no code provided for error handling if a bucket already exists. 
![](./Images/bucket%20created.png)

3. xit Status Handling (?) * * : Another speci f icrequirementwascheckingandhandlingcommandexecutionstatususing` ?' to provide proper success or error feedback messages. This is entirely absent from the submission. Exit status verification is crucial in error handling and has not been demonstrated. 
![](./Images/file%20seen.png)

4. Execution and Testing: While screenshots are presented showing the installation of AWS CLI and S3 bucket creation, they lack any evidence of error handling logic or script execution. No detailed feedback messages or debugging steps are evident apart from basic CLI usage. 
![](./Images/iam%20user%20.png)



I TOOK A LOT OF TIME AND SERIES OF TEST AND I HAD SOME ERRORS AND SOME COMPLICATIONS ON THE WAY BUT THIS IS WHY WE DO WHAT WE DEVOPS OPERATORS HAVE TO DO 

HERE IS WHERE ARE SOME SNAPSHOT WHERE I RAN SOME COMANNDS LIKEE "CHMOD" AND ADD A SCRIPT AND INSTALLED SOME SOFTWARE E.T.C.



#!/bin/bash

# List of bucket names to create (for loop will go through them)
BUCKET_NAMES=("emma-devops-bucket-1" "emma-devops-bucket-2")
REGION="us-east-1"

# Loop through the list of bucket names
for BUCKET_NAME in "${BUCKET_NAMES[@]}"; do
    echo "Checking if bucket '$BUCKET_NAME' exists..."

    # Check if the bucket already exists
    aws s3api head-bucket --bucket "$BUCKET_NAME" 2>/dev/null

    # Check the exit status of the previous command
    if [ $? -eq 0 ]; then
        echo "❗ Bucket '$BUCKET_NAME' already exists. Skipping creation."
    else
        echo "✅ Bucket '$BUCKET_NAME' does not exist. Creating..."

        # Try to create the bucket
        aws s3api create-bucket --bucket "$BUCKET_NAME" --region "$REGION" \
        --create-bucket-configuration LocationConstraint="$REGION" 2>/dev/null

        # Check if bucket creation was successful
        if [ $? -eq 0 ]; then
            echo "✅ Bucket '$BUCKET_NAME' created successfully."
        else
            echo "❌ Failed to create bucket '$BUCKET_NAME'. Please check permissions or naming."
        fi
    fi

    echo "----------------------------"
done


![](./Images/Screen%20Shot%202025-05-10%20at%203.51.00%20PM.png)


| Requirement                     | Met? | Explanation                                                  |
| ------------------------------- | ---- | ------------------------------------------------------------ |
| ✅ `if-else` control flow        | ✔️   | Used to check if a bucket exists and act accordingly         |
| ✅ `for` loop                    | ✔️   | Iterates over a list of bucket names                         |
| ✅ Error handling (`$?`)         | ✔️   | Checks command success/failure after each AWS CLI call       |
| ✅ `aws s3api head-bucket` usage | ✔️   | Properly used to check if a bucket already exists            |
| ✅ \Execution-ready script        | ✔️   | You can `chmod +x script.sh` and run it directly             |
| ✅ Feedback to user              | ✔️   | Echo statements provide meaningful responses for each action |
