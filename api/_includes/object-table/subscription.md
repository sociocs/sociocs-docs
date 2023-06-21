Name | Value {class="compact"}
--- | ---
id | Subscription ID
channel_key | Channel key linked to this webhook
created_at | Milliseconds timestamp of when the subscription was created
platform | Platform hosting the endpoint (value provided by the caller when creating the subscription)
provider | {{include "providers"}}
status | Status of the webhook subscription. `active` or `paused`
subscriber_reference_id | Unique identifier for the subscription (value provided by the caller when creating the subscription)
trigger_direction | Value is always `incoming`
webhook_url | Webhook endpoint URL