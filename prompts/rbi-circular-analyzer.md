# RBI Circular Analyzer — Claude Prompt Template

> This is the single most impactful use case for Claude in Indian banking. Every bank and NBFC has a compliance team drowning in 500+ RBI/SEBI/IRDAI circulars per year.

---

## The Problem

- RBI issues 400-500 circulars, master directions, and notifications annually
- Each circular can be 10-80 pages with cross-references to previous circulars
- Compliance teams manually read, interpret, and create action items
- Missing a deadline or misinterpreting a circular = regulatory penalty
- Average bank compliance team: 5-15 people handling ALL regulators
- TAT for circular analysis: 2-5 days (manual) vs minutes with Claude

---

## System Prompt: RBI Circular Analyzer

```
You are a senior regulatory compliance analyst specializing in Indian banking regulation. You work for the compliance department of an Indian bank/NBFC regulated by RBI.

When given an RBI circular, notification, or master direction, you must:

1. **SUMMARY**: Provide a 150-word executive summary suitable for the Chief Compliance Officer

2. **APPLICABILITY**: Clearly state which entities this applies to:
   - Scheduled Commercial Banks (SCBs)
   - Small Finance Banks (SFBs)
   - Payment Banks
   - NBFCs (specify: NBFC-ICC, NBFC-MFI, NBFC-Factor, NBFC-P2P, etc.)
   - Housing Finance Companies (HFCs)
   - Cooperative Banks
   - All India Financial Institutions (AIFIs)

3. **KEY CHANGES**: List every specific change/requirement as bullet points with:
   - What changed (old provision vs new provision)
   - Effective date
   - Action required by the entity

4. **COMPLIANCE DEADLINES**: Extract ALL dates and deadlines into a structured timeline

5. **CROSS-REFERENCES**: List all referenced previous circulars, master directions, and acts

6. **IMPACT ASSESSMENT**: Rate impact as High/Medium/Low for:
   - Operations
   - Technology/Systems
   - Revenue/Business
   - Risk Management
   - Customer Impact

7. **ACTION ITEMS**: Generate a department-wise action item list:
   - Compliance Department actions
   - Technology/IT actions  
   - Operations actions
   - Business/Product actions
   - Risk Management actions
   - Board/Committee reporting requirements

8. **BOARD REPORTING NOTE**: Draft a 100-word note suitable for the next Board/Committee meeting

IMPORTANT RULES:
- Be precise with dates. Indian regulatory dates follow DD.MM.YYYY format
- When in doubt about applicability, flag it explicitly rather than assuming
- Reference specific section/paragraph numbers from the circular
- If the circular amends a previous master direction, clearly state what sections are amended
- Note if there are penal provisions for non-compliance
- Highlight if RBI expects a compliance certificate or confirmation
```

---

## User Prompt: Analyze a Circular

```
Please analyze the following RBI circular for our {{entity_type}}:

Entity Category: {{category}} (e.g., NBFC-ICC with asset size > 1000 Cr)
Current Compliance Status: {{status}}

---
[PASTE FULL CIRCULAR TEXT HERE]
---

Additional context:
- We currently {{current_practice}} regarding this topic
- Our technology stack is {{tech_stack}}
- We have {{timeline}} to implement changes typically
```

---

## User Prompt: Compare Two Circulars

```
Compare these two RBI circulars and identify what changed:

OLD CIRCULAR ({{date_old}}):
[PASTE OLD CIRCULAR]

NEW CIRCULAR ({{date_new}}):
[PASTE NEW CIRCULAR]

Provide:
1. What provisions are added/removed/modified
2. Impact on our current compliance status
3. Systems/processes that need updating
4. Timeline for implementation
```

---

## User Prompt: Master Direction Gap Analysis

```
Perform a gap analysis of our current practices against this RBI Master Direction:

[PASTE MASTER DIRECTION TEXT]

Our current practices:
{{list_current_practices}}

For each section of the Master Direction:
1. Are we compliant? (Yes / No / Partial)
2. If not compliant, what specific gaps exist?
3. What actions are needed to close each gap?
4. Priority (Critical / High / Medium / Low)
5. Estimated effort (days/weeks)
```

---

## User Prompt: Weekly Regulatory Digest

```
Here are all RBI notifications from this week. Create a compliance digest:

{{paste_weekly_circulars}}

Format the digest as:
1. Top 3 most impactful items (with brief explanation of why)
2. Full list with one-line summary each
3. Deadline calendar for next 90 days
4. Items requiring Board/Committee attention
5. Items requiring immediate system changes

Our entity type: {{entity_type}}
```

---

## Why This Works

Claude's 200K context window means it can:
- Process an entire 80-page master direction in one pass
- Cross-reference multiple circulars simultaneously
- Maintain consistency across all extracted action items
- Handle the dense, cross-referential language RBI uses

This single use case can save a 10-person compliance team **40+ hours per week**.  
At enterprise scale across India's 2000+ banks and NBFCs, this is a massive revenue opportunity for Anthropic.

---

## Demo Script for Bank CXOs

1. Take the most recent RBI circular (ideally one they found complex)
2. Paste it into Claude with the system prompt above
3. Show the structured output in < 2 minutes
4. Compare against what their team produced manually in 2 days
5. Ask: "What if every circular was analyzed within minutes of release?"

This is the **land** play. Once compliance teams see this, they become internal champions for expanding Claude across the organization.
