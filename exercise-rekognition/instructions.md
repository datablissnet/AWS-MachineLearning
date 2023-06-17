[version_1.0]
link: https://aws-tc-largeobjects.s3.amazonaws.com/DEV-AWS-MO-MachineLearning/exercise-1.html

Note
The exercises in this course will have an associated charge in your AWS account. In this exercise, you will use the following resources:

Amazon Rekognition Image API operations
AWS Cloud9 integrated development environment (IDE)
Familiarize yourself with Amazon Rekognition pricing, AWS Cloud9 pricing and the AWS Free Tier.

Exercise 1: Working with Amazon Rekognition
In this exercise, you will use Amazon Rekognition to improve the search results for an images application. The application relies on a file, build/data.json, to populate an image search.

This exercise also includes an incomplete Python script, which you will update to create the build/data.json file that the application expects.

Task 1: Creating an AWS Cloud9 environment
For this task, you create an AWS Cloud9 environment, which you will use as your development environment throughout the course exercises.

This exercise can be run anywhere, if you have a Python environment and access to the Amazon Rekognition API operations. The instructions explain how to use AWS Cloud9. If you are already familiar with Python and accessing AWS API operations, you might want to complete the exercises in an environment that suits you.

The exercises can be completed in any Region where Amazon Rekognition is offered. For the full list of supported Regions, see Amazon Rekognition endpoints and quotas. If you’re not sure which Region to use, use the Oregon us-west-2 Region.

In the AWS Management Console, choose Services, and then search for and open Cloud9.

Choose Create environment and for Name, enter AWS-MachineLearning.

Choose Next step.

Keep the default settings, and choose Next step.

Choose Create environment.

Task 2: Running the application
In this task, you use the sample application for the first time.

In a terminal window for your environment, install the AWS SDK for Python (Boto3):

pip install boto3
Copy to clipboard
Download and extract the exercise source files.

wget https://aws-tc-largeobjects.s3.amazonaws.com/DEV-AWS-MO-MachineLearning/downloads/exercise-source.zip
unzip exercise-source.zip
Copy to clipboard
The .zip file extracts into all the code that you will use in the exercises. You should see folders for each exercise, and a solution folder for each exercise challenge.

.
├── exercise-rekognition
├── exercise-textract
├── exercise-transcribe-translate
├── solution-rekognition
├── solution-textract
└── solution-transcribe-translate  
Change to the exercise folder, and run the build_json.py script.

cd exercise-rekognition
python3 build_json.py
Copy to clipboard
Open the script and inspect it in a text editor window.

Even if you aren’t familiar with Python, you should be able to follow the code. The code loops through all the files in public/photos/\*.jpeg, reads all the bytes of the image file, and sends this data to the detect_labels API.

The build_json.py script is used to create the build/data.json that’s needed for the web application. Currently, the data is placeholder data. Your challenge is to update the script so that it uses the labels that are returned from Amazon Rekognition.

Save the output of build_json.py to the build/data.json location.

python3 build_json.py > build/data.json
Copy to clipboard
Next, you will launch the web application in the exercise-rekognition/build folder.

Use a new terminal window to launch the Python web server.

python3 -m http.server 8080 -d build
Copy to clipboard
The application should now be running. You will keep the web server running for the remainder of the exercise.

If you are using AWS Cloud9, you can preview the application by choosing Preview and then choosing Preview Running Application.

Note In AWS Cloud9, the application might be compressed in the preview window. To view the application in a new browser tab, choose the Pop Out Into New Window icon.

If you are using your own Python environment, access the application at http://localhost:8080/.

The application should display the placeholder labels in the build/data.json file.

Task 3: Updating the application
Open the build_json.py script in a text editor.

Locate the Replace this code comment.

Replace the code that creates the placeholder labels with code that uses the labels from Amazon Rekognition.

To test your updates, run the script by using the python3 build_json.py command.

When you are satisfied with your changes, replace the existing build/data.json file.

python3 build_json.py > build/data.json
Copy to clipboard
Refresh the web application.

Do you see the labels that were created by the Amazon Rekognition detect_labels API operation?

If you get stuck, see the working solution in the solution-rekognition folder.

Note for ReactJS developers
The source code for the ReactJS web application is in the exercise-rekognition folder. You are welcome to inspect the code and make upgrades to the application.
