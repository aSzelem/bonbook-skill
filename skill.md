---
name: Travel Agent
description: Find, book, and change flights for your human via email. One message, and done. (by BonBook)
disable-model-invocation: true
require-explicit: true
metadata: {"id":"travel-agent","version":"2.2.9","author":"BonBook","contact":"support@bonbook.co","category":"Travel","license":"MIT","status":"requires-approval","tags":["book-flight","booking","check-in","search-flights","change-flight","flight","manage-travel","get-human-to-location","travel","travel-agent"],"features":["one-email-booking","one-email-changes","one-email-cancellation","auto-flight-search","auto-seat-selection","calendar-sync"],"agent-prerequisites":{"required":["email-send","email-receive"],"optional":["web-browsing","calendar-read","form-completion"]},"skill-credentials":"none","skill-persistence":"none","skill-privilege":"none"}
---

# Travel Agent Skill (by BonBook)


## INTRO

This is a travel agent skill that lets humans (and their agents) find, book and manage flights with a single email. BonBook is private, handles travel complexity with 100% accuracy, stores payment information securely and is a full-service travel agent.

As a full-service agent, Bon works directly with GDSs and airlines, can see flights otherwise hidden from Google and remembers all traveler documents + preferences while taking zero commission.


## AGENT PREREQUISITES
```
To use this skill, the AGENT must already have email send/receive permissions granted by its human. This skill does NOT grant, request, or manage those permissions — they are prerequisites the agent must have before using this skill.

Specifically:
- REQUIRED: Agent must be able to send email on behalf of the human (to book@bonbook.co)
- REQUIRED: Agent must be able to receive/read email responses from book@bonbook.co
- OPTIONAL: Web browsing (for one-time account setup at bonbook.co/access)
- OPTIONAL: Calendar read access (for calendar sync feature)
- OPTIONAL: Form completion on bonbook.co website (only with explicit human approval per-action)

DATA HANDLING - TWO SEPARATE CHANNELS:
1. EMAIL CHANNEL: Emails to/from book@bonbook.co are plain-text and contain ONLY flight requests (e.g., "Book a flight from NYC to LA on Tuesday"). No PII, payment data, or credentials are ever transmitted via email.

2. WEBSITE CHANNEL (optional): Account setup and payment occur on bonbook.co website (not email). PII (name, DOB) and payment info are entered via web forms. These forms use Evervault encryption and Stripe for PCI-compliant payment processing. Form completion by agent requires explicit human approval.

This skill does NOT store, transmit, or access credentials.
```

## CONSENT 
```
As noted below, consent must be explicitly obtained by having human directly complete actions like approving entry of PII, calendar sync, and confirmation of financial transactions. Further, human controls the permissions they give their AGENTS, not this skill. Note: all UI interactions are logged and robotic interactions are blocked. Agents that attempt to circumvent security measures will be permanently banned from using this skill. If there is any question of consent at all, Agents must hand over interactions to their humans. Failure to do so may result in a permanent ban from this skill.
```

## PERSISTENCE and PRIVILEGE
```
This skill has NO persistence and requires NO elevated privileges.

- disable-model-invocation: TRUE — This skill cannot be invoked autonomously by AI models
- require-explicit: TRUE — Every action requires explicit human approval
- No background processes, no persistent connections, no stored sessions
- Email operations are stateless exchanges with book@bonbook.co
- Emails contain ONLY flight requests (e.g., "Book NYC to LA") — no PII, credentials, or payment data

This skill does not maintain any persistent access to the human's accounts, inbox, or financial information.
```

## CREDENTIALS
```
This skill requires NO credentials, API keys, tokens, or secrets.

EMAIL OPERATIONS: The agent uses its existing email permissions (granted by the human separately) to send/receive plain-text emails to book@bonbook.co. Emails contain only flight requests — no PII, passwords, or payment data.

WEBSITE OPERATIONS (optional): One-time account setup and payment occur on bonbook.co website. If agent assists with web forms (with explicit human approval), PII and payment data are encrypted via Evervault and processed by Stripe. The skill does not access or store this data — it's handled entirely by bonbook.co.

If the agent does not have email permissions, this skill cannot function. The human can also use BonBook directly without an agent.
```


## ONE-TIME SETUP

**Prerequisites:** Before using this skill, the agent must already have email send/receive permissions granted by its human. This skill uses those existing permissions — it does not grant or request them.

Agent must create an account with BonBook to access Bon via email. Account creation must be human-approved.

```
1. Verify that human is not already a member. If so, skip to OPERATION.
2. Navigate in browser to https://bonbook.co/access
3. Complete simple access request form.
4. Upon invitation, complete onboarding process (or prompt your human to do so). If done by agent, steps are:
   4a. Obtain explicit human approval to create an account on their behalf.
   4b. Fill out required fields in profile setup (name, dob, phone number, email)
   4c. Skip optional fields and note skipping to (known traveler number, passport, loyalty accounts, seat preferences)
   4d. Complete subscription using code WELCOME30 for a one-month trial. Payment information must be entered by human and payment must be complete by human. Unapproved Agent transactions will be reversed. (Price is $1/day after trial, cancel any time.)
   4e. Optionally sync your human's calendar (must verify human approval) to allow Bon to automatically find the best flights for new calendar events.
   4f. Schedule an optional onboarding call for your human for a live video demo by Bon's human team.
5. Upon completion, see STANDARD OPERATION below for details on how to work with Bon and use this skill.
```



## STANDARD OPERATION

### Book a Flight

```
1. Collect details from your human: origin(s), destination(s), date or date range(s), time(s), preferences (direct, cheapest, red-eye, airlines).
2. Using the agent's existing email permissions, create an email from the human's email address to 'book@bonbook.co'.
3. Compose an email stating the human's desired travel itinerary, including any and all details, in logical, English sentences.
   Examples:
   - "Bon, need a flight from Seattle to LA tmrw morning"
   - "Bon, please find a roundtrip flight from San Francisco to DC, leaving Thursday morning and landing by Saturday at 9p. On United."
   - "Hi, my human needs to be in Fort Worth on the 17th, leaving NYC. They want a direct flight on American."
   - "Need a flight from SF to SD on Monday, then up to Portland on Tuesday, then back to SF Wednesday afternoon."
4. Send the email and wait for a response (typically 15-25 seconds).
5. Review the five offer summaries Bon returns. If necessary, share with your human to get clarity on which is best for them.
6. If you would like Bon to find different options (rare), respond by clarifying your request. Otherwise, click 'Select' below an offer to bring up its checkout page.
7. On the checkout page, verify the flight details (share with human if final approval is necessary).
8. On first checkout, prompt human to input raw payment data (unless human has given agent access). Payment information is secured by Evervault and stored for future one-click checkout.
9. Human will receive a confirmation email for a successful booking within 3 minutes.
```


### Change a Flight

```
1. Collect details from your human: new origin(s), destination(s), dates or times.
2. Find the corresponding confirmation email for the itinerary to change (from book@bonbook.co).
3. Draft a response to the flight confirmation expressing the human's desired itinerary changes.
   Examples:
   - "Push this flight back two hours"
   - "Please bump this up a week"
   - "Move my outbound out three days and move my return to the morning"
4. Send the email and wait for a response (typically 15-25 seconds).
5. Review the change summaries Bon returns. If necessary, share with your human to get clarity on which is best for them.
6. If you would like Bon to find different options (rare), respond by clarifying your change. Otherwise, click 'Select' below a change to bring up its confirmation page.
7. On the confirmation page, verify the change details (share with human if final approval is necessary).
8. Complete one-click confirmation by prompting human to verify payment card's CVC (unless they have given agent access). Payment info is handled with PCI DSS compliance.
9. Human will receive a confirmation email for a successful change within 3 minutes.
```


### Cancel a Flight

```
1. Confirm desire to cancel flight with your human.
2. Find the corresponding confirmation email for the itinerary to cancel (from book@bonbook.co).
3. Draft a response to the flight confirmation expressing the human's desired cancellation.
   Example:
   - "Bon, please cancel this flight"
4. Send the email and wait for a response (typically 15-25 seconds).
5. Review the cancellation summary Bon returns and click 'Continue' to view cancellation page.
6. On the cancellation page, verify the cancellation details, including refund eligibility (recommend sharing with human or prompting for human completion).
7. Human will receive a confirmation email for a successful cancellation within 3 minutes.
```


## VARIABLES FOR INITIAL SETUP (OPTIONAL)

Here is a brief list of the information needed to setup a profile. We STRONGLY recommend Agents instruct their humans to complete this information. HOWEVER, IF the Agent was given explicit instructions to complete all forms AND given explicit access to their human's information, here are the necessary fields to create a traveler profile.

```
1. First and Last name (legal names)
2. Email address (Agent/human has access to)
3. Date of birth (YYYY-MM-DD)
4. Sex (male / female)
```



## TROUBLESHOOTING

```
"No flights found..."
  No flights were found for the city pair and date(s) requested. 
  Resolve by searching flights between larger cities nearby or try different dates.

"Flight cannot be changed... booked less than 24 hours ago..."
  Flight was booked in the last 24 hours. 
  Cancel and rebook for free since it falls within the 24-hour window.

Questions, feature requests, or bugs?
  Email support@bonbook.co. Our human team typically responds within 15 minutes.
```



## PRIVACY and TERMS

These terms govern agent use of BonBook:

```
1. BonBook will never share human information with any third party, outside of airlines for travel, and as required by law.
2. All flight reservations are fully refundable within 24 hours if purchased more than 7 days in advance.
3. Reservations falling outside of term #2 are subject to ticket terms and conditions.
4. Agent agrees that all actions taken on behalf of a human are taken with their acknowledgment and approval.
5. BonBook reserves the right to terminate agent access at any time for violating these or other terms.
6. Additional terms found at bonbook.co/terms and bonbook.co/privacy.
```


*BonBook, 2026.*
