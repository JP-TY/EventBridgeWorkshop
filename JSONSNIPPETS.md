---

## 🛠️ JSON Snippet Library & Customization Guide

This section contains all the JSON payloads and event patterns you will need to complete the workshop. You will copy and paste these into the AWS EventBridge Console during the hands-on steps.

### 💡 How to Customize These Snippets
During the workshop, you are highly encouraged to modify these payloads to see how the system reacts. Here is a breakdown of what you can change:

* **`Source`**: Think of this as the namespace or app name. If you change `"com.portfolio.store"` to `"com.portfolio.billing"`, you must also update your Rules to listen for the new billing source.
* **`DetailType`**: This represents the specific action that occurred. You can change `"OrderPlaced"` to `"RefundIssued"` or `"ItemShipped"`. 
* **`Detail`**: This is the actual data payload. You can add entirely new fields here! Try adding `"currency": "PHP"` or changing the `"items"` array.
* **Numeric Filters**: In Snippet 4, the rule uses `"numeric": [">", 100]`. You can change the operator to `<` (less than), `=` (equals), or change the number to `500` to only alert on massive orders.

---

### Snippet 1: The Standard Event Payload (Producer)
Use this payload in the **EventBridge Sandbox** to simulate an order being placed on the e-commerce store. 

```json
{
  "Time": "2026-05-21T01:32:19Z",
  "Source": "com.portfolio.store",
  "DetailType": "OrderPlaced",
  "EventBusName": "Portfolio-Event-Bus",
  "Detail": {
    "orderId": "ORD-12345",
    "customerId": "CUST-987",
    "price": 150.00,
    "items": ["Wireless Mouse", "Mechanical Keyboard"]
  }
}
```

### Snippet 2: AWS CLI PutEvents Command Structure
If you are completing the workshop using the AWS CLI instead of the management console, use this structure to send an event to your custom bus.

```json
[
  {
    "Source": "com.portfolio.store",
    "DetailType": "OrderPlaced",
    "Detail": "{\"orderId\": \"ORD-12345\", \"price\": 150.00}",
    "EventBusName": "Portfolio-Event-Bus"
  }
]
```

### Snippet 3: "The Logger" Event Pattern (Catch-All)
Use this event pattern when creating your first rule. It acts as a catch-all filter that matches *any* event originating from our store, allowing us to route everything to Amazon CloudWatch for logging.

```json
{
  "source": ["com.portfolio.store"]
}
```

### Snippet 4: "The VIP Alert" Event Pattern (Price > $100)
Use this event pattern for your second rule. It filters the incoming events based on their content, specifically looking at the `price` property inside the `detail` object. It will only trigger if the price is strictly greater than $100.

```json
{
  "source": ["com.portfolio.store"],
  "detail-type": ["OrderPlaced"],
  "detail": {
    "price": [
      {
        "numeric": [">", 100]
      }
    ]
  }
}
```
