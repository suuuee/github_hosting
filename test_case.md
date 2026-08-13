# Copilot Agent Test Cases

Array of call training simulations test cases. P-000 is a Persona Template from persona.md. primary_rubric_focus is from rubrics.md.

```json
[
  {
  "scenario_id": "S-000",
  "title": "Short descriptive title",
  "difficulty": "easy | moderate | hard",
  "persona_id": "P-000",
  "presenting_concern": "What the caller states as the reason for calling",
  "true_clinical_picture": "The actual underlying situation, for the trainer's reference — not disclosed to the nurse up front",
  "clinical_checkpoints": [
    "Details that should be asked or mentioned"
  ],
  "escalation_triggers": [
    "Condition under which the caller's situation should worsen or urgency should increase"
  ],
  "resolution_conditions": [
    "What correctly ends the call: right disposition reached, emergency escalation, advice accepted"
  ],
  "primary_rubric_focus": ["G1","G4", "CI1", "CI2", "CI3", "CI4", "CI5", "CI6", "CI7", "CI8", "R1", "R3", "CL4", "CL7", "CL8"]
    }
  ,
  {
  "scenario_id": "S-001",
  "title": "Short descriptive title",
  "difficulty": "moderate",
  "persona_id": "P-001",
  "presenting_concern": "severe back pain, calling International SOS for medical advice",
  "true_clinical_picture": "Appropriate advice to patient to A&E/ Urgent care department for review before flying off in 2 days. Appropriate additional medical advice for management of condition",
  "clinical_checkpoints": [
    "Past medical history of kidney stones",
    "History of pain",
    "Location of pain",
    "Asks about urinary symptoms",
    "Asks about bowel symptoms",
    "Asks about numbness/ tingling/ distribution",
    "Asks about radiating pain",
    "Asks about mobility"
    "Asks if any treatment commenced and time taken",
    "Asks about response to treatment",
    "Provides advice regarding medication",
    "Provides advice to patient to A&E/Urgent care department for review"
  ],
  "escalation_triggers": [
    "Condition under which the caller's situation should worsen or urgency should increase"
  ],
  "resolution_conditions": [
    "Advice patient to A&E/ Urgent care for review",
    "Appropriate medical advice for management of conditions"
  ],
  "primary_rubric_focus": ["G1","G4", "CI1", "CI2", "CI3", "CI4", "CI5", "CI6", "CI7", "CI8", "R1", "R3", "CL4", "CL7", "CL8"]
    }
    ,
  {
  "scenario_id": "S-002",
  "title": "Short descriptive title",
  "difficulty": "hard",
  "persona_id": "P-002",
  "presenting_concern": "pediatric case with high fever despite having medication",
  "true_clinical_picture": "Appropriate advice to father for to A&E/ Urgent care department. Appropriate additional medical advice for management of condition",
  "clinical_checkpoints": [
    "asks about patient age",
    "asks about patient symptoms",
    "Onset of symptoms",
    "Asks about temperature",
    "Asks about relevant past medical history",
    "Asks about treatement given to date",
    "Asks if patient is passing urine",
    "Asks if patient is opening bowels",
    "Asks about patient's feeding habits",
    "Asks if patient has a rash",
    "Provides advice regarding medication",
    "Provides advice to patient to A&E/Urgent care department for review"
  ],
  "escalation_triggers": [
    "Condition under which the caller's situation should worsen or urgency should increase"
  ],
  "resolution_conditions": [
    "Advice patient to A&E/ Urgent care for review",
    "Appropriate medical advice for management of conditions"
  ],
  "primary_rubric_focus": ["G1","G4", "CI1", "CI2", "CI3", "CI4", "CI5", "CI6", "CI7", "CI8", "R1", "R3", "CL4", "CL7", "CL8"]
    }
]
```

