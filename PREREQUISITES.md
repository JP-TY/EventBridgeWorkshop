# 📋 Prerequisites: The Reactive Web Workshop

Welcome to the Reactive Web Workshop! To ensure you can jump right into building our event-driven system on the day of the workshop, please complete the following setup steps beforehand. 

If you run into any issues, don't worry—our volunteers will be available at the start of the event to help you troubleshoot.

---

## 1. AWS Account Requirements

You will need an active Amazon Web Services (AWS) account to participate. 

* **Create an Account:** If you don't have one, you can sign up for the [AWS Free Tier](https://aws.amazon.com/free/). 
* **Permissions:** Ensure the IAM User or Role you are using has the necessary permissions to create and manage the following services:
    * Amazon EventBridge
    * AWS Lambda
    * Amazon SNS (Simple Notification Service)
    * Amazon CloudWatch
* **Billing:** We will be keeping everything within the Free Tier, and the final step of the workshop is dedicated to deleting all resources so your bill remains at $0.

## 2. Local Environment Setup

While a lot of the workshop can be done in the AWS Management Console, having your local environment ready is highly recommended for writing and testing your JSON configurations.

* **Code Editor:** Install a modern code editor. We recommend [Cursor](https://cursor.sh/) or [Visual Studio Code](https://code.visualstudio.com/).
* **AWS CLI (Optional but Recommended):** * Install the [AWS Command Line Interface](https://aws.amazon.com/cli/).
    * Once installed, open your terminal and run `aws configure` to link it to your account using your Access Key ID and Secret Access Key.

## 3. Recommended Knowledge

This workshop is designed to be beginner-friendly, but having a basic grasp of the following will make your experience much smoother:
* **JSON (JavaScript Object Notation):** We will be using JSON heavily to define our events and routing rules. Understanding basic JSON structure (keys, values, arrays, and objects) is highly beneficial.
* **AWS Console Navigation:** Familiarity with logging into the AWS Management Console and using the top search bar to find services.

---

## ✅ Pre-Workshop Checklist

Before joining the session, make sure you can check off all these boxes:

- [ ] I have an active AWS account.
- [ ] I can successfully log into the AWS Management Console.
- [ ] I have a code editor installed on my machine.
- [ ] I have reviewed the [JSON Snippets Library](JSONSNIPPETS.md) to familiarize myself with the code we will be using.

We can't wait to see you there and start building!
