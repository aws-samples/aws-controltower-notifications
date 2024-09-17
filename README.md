# Control Tower Notification Center

## Overview

This CloudFormation template sets up a comprehensive notification system for AWS Control Tower environments. It's designed to help administrative users easily configure and manage alerts for important Control Tower events, enhancing security awareness and operational oversight.

**Important:** This template MUST be deployed in the Control Tower management account.

## Features

This solution provides alerts for the following events:

1. Control Tower Updates
2. Account Creation
3. Organizational Unit (OU) Creation and Deletion
4. Account Suspension
5. Root User Login

## Parameters

The template accepts the following parameters:

- **NotificationEmail**: A comma-separated list of email addresses to receive notifications.
- **SubscribeToCTAlerts**: Choose to subscribe to Control Tower update alerts (Yes/No).
- **SubscribeToAccountCreation**: Choose to subscribe to account creation alerts (Yes/No).
- **SubscribeToOUAlerts**: Choose to subscribe to OU creation/deletion alerts (Yes/No).
- **SubscribeToAccountSuspension**: Choose to subscribe to account suspension alerts (Yes/No).
- **SubscribeToRootLoginAlerts**: Choose to subscribe to management account root user login alerts (Yes/No).

## Alert Details

1. **Control Tower Updates**
   - Monitors the AWS Control Tower RSS feed for new updates.
   - Sends notifications when new updates are published within the last 24 hours.

2. **Account Creation Alerts**
   - Triggers when a new account is created in Control Tower.
   - Provides details such as the account name and ID.

3. **OU Alerts**
   - Notifies when an Organizational Unit is created or deleted.
   - Includes information like OU name, ID, and ARN.

4. **Account Suspension Alerts**
   - Sends an alert when an AWS account is suspended.
   - Includes the suspended account ID.

5. **Root Login Alerts**
   - Triggers when there's a root user login to the management account.
   - Provides the account ID and timestamp of the login event.

## How It Works

The solution uses a combination of AWS services:

- Amazon SNS topics for each alert type
- Lambda functions to process events and send notifications
- EventBridge rules to capture specific AWS events
- Custom resources to handle email subscriptions

## Deployment

To deploy this solution:

1. Upload the CloudFormation template to your AWS account.
2. Provide the required parameters, especially the notification email(s).
3. Review and create the stack.
4. Confirm the subscription emails sent by SNS to start receiving notifications.

## Note

This solution is designed for use within a Control Tower environment and requires appropriate permissions to create and manage the specified AWS resources.