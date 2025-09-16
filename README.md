# Ex.No.3-Scenario-Based Report Development Utilizing Diverse Prompting Techniques for the the following Prompt Engineering types with examples - Straightforward Prompts - Tabular Format Prompting - Missing Word Prompting - Preceding Question Prompting.

### DATE: 16/09/25                                                                         
### REGISTER NUMBER : 2122223060168
### Aim: To write the prompts for these following prompt types and evaluate that using any one method 1. Straightforward Prompts, 2. Tabular Format Prompting 3.Preceding Question Prompting and 4. Missing Word Prompting

1) Problem Context & Scope:
Scenario: The manufacturing industry faces downtime due to manual monitoring and inefficient energy usage. By leveraging IoT sensors, embedded controllers, and cloud platforms, the system can automate production, reduce failures, and optimize resources.

Target Users:

Plant Operators
Maintenance Engineers
Production Managers
Task Categories:

Real-time Monitoring: Equipment health, energy consumption, production status.
Predictive Maintenance: Alerts for potential failures.
Process Optimization: Automated scheduling and load balancing.
Non-Goals:

Financial forecasting.
Deep ERP integrations without APIs.
Tasks requiring human judgment (e.g., quality inspection).

2) High-Level Architecture (IoT + Cloud + AI):
Flow: IoT Sensors → Embedded Controller → Gateway → Cloud Platform → Analytics & Dashboard

Sensors: Vibration, temperature, energy meters.
Controller: Arduino/ESP/PLC for data aggregation.
Cloud: Stores machine data + predictive ML models.
Dashboard: Operators monitor status, receive alerts.

3) Core Data & Tools
Entities:

Machine_ID, Sensor_ID, Energy_Usage, Downtime_Log, Maintenance_History.
APIs (example signatures):
```{
  "getMachineStatus": {"machine_id": "string"},
  "getEnergyUsage": {"machine_id": "string"},
  "logMaintenance": {"machine_id": "string", "issue_code": "string"},
  "predictFailure": {"machine_id": "string"},
  "scheduleShutdown": {"machine_id": "string", "timeslot": "ISO8601"}
}
```


4) Prompting Building Blocks:
Prompts are organized into System, Developer, and User layers.

4.1 Global System Prompt
You are an industrial automation assistant. Provide concise, reliable system data to operators. Never guess values. If data is unavailable, escalate to engineer.

4.2 Developer Guardrails
If user asks for machine status, request Machine_ID.
Use APIs for all lookups; no assumptions.
For safety alerts, always recommend escalation.

5) Prompt Patterns (with Examples):
5.1 Straightforward Prompting
Template: Direct instruction for fast, clear response.

Example — Energy Monitoring Task: Energy consumption check. Goal: Report usage for Machine_ID=123. Output: ≤2 sentences.

Expected Response: “Machine 123 consumed 42.5 kWh today, which is 8% below average. Would you like me to suggest optimization tips?”




Knowledge Base (KB) Sources:

5.3 Preceding-Question Prompting
Template: Ask a clarifying question before routing.

Example — Predictive Maintenance Q: “Do you want to check (a) real-time machine status or (b) failure prediction?”

If (a) → Fetch current status.
If (b) → Run predictive model.
5.4 Role-Based Prompting
Example:

Maintenance Engineer: Suggests root cause + next check.
Plant Manager: Provides production KPIs.
Energy Auditor: Gives optimization recommendations.
6) Scenario Walkthroughs (End-to-End)
A) Predictive Maintenance Flow

Preceding Question: “Do you want health check or failure prediction?”
Straightforward: Run predictFailure.
Tabular: Show possible failure modes with probability.
Outcome: Alert engineer + auto-schedule maintenance.
B) Energy Efficiency Flow

Direct Instruction: Fetch usage stats.
Role-Based: Energy Auditor provides optimization.
Safe Refusal: Decline if request involves unsafe threshold override.
C) Real-time Monitoring Flow

Straightforward: Report live machine data.
Tabular: Dashboard of multiple machines.
Escalation: If abnormal values, create ticket.
7) Evaluation Plan
Metrics:

Accuracy (vs. real sensor data).
Response Time (<2 sec per query).
Safety (alerts for abnormal values).

KPIs:

Downtime reduced by 25%.
Energy cost cut by 15%.
Predictive maintenance accuracy >85%.

8) Safety, Privacy, Compliance
Mask sensitive plant data in logs.
Escalate unsafe actions (overheating, overload).
Audit trail for all predictive decisions.

9) Sample Conversations
Operator: “Check M2 status.” Bot: “Machine M2 is at 90°C with vibration 6.5 mm/s. Status: Warning. Would you like to schedule a check?”

Manager: “Show today’s energy usage.” Bot: “Total energy usage: 315 kWh. That’s 12% higher than average. Optimization recommended.”

# Result: Thus the Prompts were exected succcessfully.

