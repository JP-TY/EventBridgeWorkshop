# The Reactive Web: Building Event-Driven Systems with AWS EventBridge

Welcome to the **Reactive Web Workshop**. In this 3-4 hour hands-on session, you will learn how to decouple microservices and build highly resilient, parallel workflows using AWS EventBridge, AWS Lambda, and Amazon SNS.

Instead of writing tightly coupled code where a failure in one service brings down the whole system, you will build an architecture where services communicate through an event bus. 

## 📋 Prerequisites & Resources

*   Please review [PREREQUISITES.md](PREREQUISITES.md) before starting to ensure your AWS account and local environment are properly configured.
*   **Reference:** [AWS CLI Command Reference / Cheat Sheet](https://docs.aws.amazon.com/cli/latest/index.html)

---

## 🚀 Workshop Steps

### Step 1: The "Bus" Stop (Setup)
*   Navigate to the **Amazon EventBridge Console**.
*   Go to **Event buses** and create a new custom bus named `Portfolio-Event-Bus`.
*   Verify the bus is active and ready to receive events.

### Step 2: Firing the First Flare (The Producer)
*   Open the **EventBridge Sandbox**.
*   Select your custom `Portfolio-Event-Bus`.
*   Use **Snippet 1** from [JSONSNIPPETS.md](JSONSNIPPETS.md) to structure your event.
*   Fire a test event and check the "Metrics" tab to confirm the bus received the signal.

### Step 3: Setting the Rules (Filtering & Routing)
You will create two rules to route events to different targets based on their content.
*   **Target 1: The Logger (CloudWatch)**
    *   Create a new rule attached to `Portfolio-Event-Bus`.
    *   Use **Snippet 3** from [JSONSNIPPETS.md](JSONSNIPPETS.md) to catch *all* events from our store.
    *   Set the target to a new CloudWatch Log Group.
*   **Target 2: The VIP Alert (Amazon SNS)**
    *   Create an SNS Topic and subscribe your email or phone number.
    *   Create a second rule attached to the bus.
    *   Use **Snippet 4** from [JSONSNIPPETS.md](JSONSNIPPETS.md) to filter only for orders where the price is greater than $100.
    *   Set the target to your new SNS Topic.

### Step 4: Testing & Chaos Validation
*   Fire an event with a price of `$50.00`. Check CloudWatch (it should be logged) and verify you did *not* receive an SNS alert.
*   Fire an event with a price of `$150.00`. Verify it is logged *and* you receive the VIP SNS alert.
*   **Chaos Test:** Deliberately break the SNS rule. Fire another event and observe that the Logger still works perfectly. This proves the services are fully decoupled.

### Step 5: Cleanup
To ensure your AWS bill remains at $0, delete the following resources:
*   EventBridge Rules (Logger and VIP Alert)
*   `Portfolio-Event-Bus`
*   SNS Topic and Subscriptions
*   CloudWatch Log Groups created for this workshop
