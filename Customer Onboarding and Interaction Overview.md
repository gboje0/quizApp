# EWE API – Customer Onboarding and Interaction Overview

**Document Scope:** Multi-Release Roadmap (Phases 2 through 4)  
**Target Audience:** Internal Stakeholders, Platform Team, and SDF Partners

---

## 1. Purpose of this Document
This document outlines how customers are expected to onboard and begin interacting with the API in each release. It serves as a central reference for stakeholders to know, and to use as a central document.

---

## 2. Release Roadmap & Interaction Models

### 2.1 API Portal Phase 2 (Current Release)
* **Summary:** This is the first release where users can begin interacting with the EWE API.
* **Interaction Model:** The onboarding process is fully manual,
    * API discovery, access requests, contract handling, and credential distribution are managed through SDF contacts.
    * API documentation and API keys are generated and shared manually.
* **Value:** This approach enables a controlled rollout and close support of early users.

### 2.2 API Portal Phase 3 (Next Release)
* **Summary:** This release makes APIs available to users with API key generation via MyFoundry. API documentations are still shared manually with customers.
* **Interaction Model:**
  * This release offers faster onboarding and greater control through self-service key generation.
  * Marketing communication has been shared with a call to action to request for API.
* **Value:** Operational overhead is reduced by key generation.

### 2.3 API Portal Phase 4 (Future Target)
* **Summary:** This release moves both API documentation and API key generation onto MyFoundry.
* **Interaction Model:**
  * API documentation and credential management are available on myfoundry.
  * Manual onboarding is still available as a fallback option.
* **Value:** Minimizes human intervention in the customer onboarding process.
---

## 3. Target Customers / Personas
The API serves two primary customer types across all releases:

* **Persona 1: Public Sector Partner (Organisational Account)**
  * *User Goal:* As a public sector partner, I want access to Economic Wellbeing Explorer,EWE, aggregated data through the API so that I can monitor economic stress in my local authority through customised dashboards.
* **Persona 2: Researcher (Individual Account)**
  * *User Goal:* As a researcher, I want access to EWE data through the API so that I can carry out my research project efficiently, without the restrictions or limitations of the Trusted Research Environment (TRE).

---

## 4. Customer Onboarding Journeys by Release

### 4.1 Phase 2: Detailed End-to-End Flow (Current)

#### Public Sector Partner
1. Customer discovers EWE API through interactions with SDF public sector contact.
2. Customer requests API access through email.
3. Customer receives contracts via emails from SDF contact.
   * New customer: is provided with contracts for Myfoundry dashboard.
5. Customer completes, signs, and returns the contracts to their SDF public contact.
6. Customer receives API documents and API keys via separate emails from their SDF contact.
7. Customer performs API test using the API documents.
8. Customer Integrate APIs into their application or dashboard.

#### Researcher
1. Researchers discover the EWE APIs through TRE access process.
2. Researcher completes Data Accessibility Check.
3. Researcher receives API documents and API keys via separate email from the SDF research team.
4. Researcher conduct end to end test of API using test examples in API document.
5. Researchers integrate API into their research tools or applications.
6. Researcher uses data generated from API for research.

---

### 4.2 Phase 3: Transition Flow (Key Self-Service)

#### Public Sector Partner
1. Customer discovers EWE API through marketing communication or interactions with their SDF public sector contact.
2. Customer requests API access through the call to action link on the marketing communication or by sending a request email to their SDF contact.
3. Customer receives contracts via emails from SDF contact.
   * New customer: is provided with contracts for Myfoundry dashboard.
5. Customer completes, signs, and returns the contracts to their SDF public contact.
6. Customer receives a confirmation emails that API request has been approved, the API documents and step by step guide on how to generating API keys on myfoundry.
7. Customer sign into their myfoundry account
    * Clicks on settings
    * Clicks on API keys
    * Clicks on generate API keys
10. Customer performs test on API using the API keys and examples in the API documents.
11. Customer Integrate API into their application or dashboard.

#### Researcher
1. Researchers discover the EWE APIs through marketing communication or TRE access process.
2. Researcher completes Data Accessibility Check process.
3. Researcher receives a confirmation emails that DAC was successful, the API documents and step by step guide on how to generating API keys on myfoundry.
4. Researcher signs into their myfoundry account
    * Clicks on settings
    * Clicks on API keys
    * Clicks on generate API keys
10. Researcher conduct end to end test of API using the API keys generated and examples in the API documents.
11. Researchers integrate API into their research tools or applications.  
9. Researcher uses data generated from API for research.

---

### 4.3 Phase 4: Target Flow (Full Portal Integration)

#### Public Sector Partner
1. Customer discovers EWE API through
    * MyFoundry API portal on myfoundry
    * Marketing communication.
    * their SDF contact
3. Customer requests API access through
    * SDF contact
    * call to action link on marketing communication.
3. Customer receives contracts via emails from SDF contact.
5. Customer completes, signs, and returns the contracts to their SDF public contact.
6. Customer receives a confirmation emails that API request has been approved, and a step by step guide on how to generating API keys on myfoundry.
7. Customer sign into their myfoundry account
    * Clicks on settings
    * Clicks on API keys
    * Clicks on generate API keys
10. Customer accesses and views live API documentations directly on MyFoundry.
11. Customer performs test on API using the API keys.
11. Customer Integrate API into their application or dashboard.

#### Researcher
1. Researchers discover the EWE APIs through TRE access process or MyFoundry portal.
2. Researcher completes Data Accessibility Check process.
3. Researcher receives a confirmation emails that DAC was successful,and step by step guide on how to generating API keys on myfoundry.
4. Researcher signs into their myfoundry account
    * Clicks on settings
    * Clicks on API keys
    * Clicks on generate API keys
10. Researcher accesses and views live API documentations directly on MyFoundry.
11. Researcher conduct end to end test of API using the API keys generated and examples in the API documents.
12. Researchers integrate API into their research tools or applications.  
9. Researcher uses data generated from API for research.

---

## 4.4 What’s New in This Journey
There are no prior onboarding processes before Phase 2; therefore, all steps described under Phase 2 represent the baseline experience for customer onboarding and interaction with the API. Phase 3 introduces automated key generation via MyFoundry, while Phase 4 migrates all documentation onto MyFoundry to eliminate manual email handoffs entirely.

## 4.5 Key Touchpoints

* **SDF contacts:** Discovery of the APIs in Phase 2 is solely by communication by the SDF contact (public sector team and research team) as no formal communication on the API has been done. In Phase 3, API key generation via MyFoundry is augmented by marketing communication. In Phase 4, the portal handles the baseline journey, but manual onboarding remains available via SDF contacts.
* **Authentication Setup:** In Phase 2, API keys are generated by the platform team and shared securely to user's SDF contact. In Phase 3 and Phase 4, API key generation is performed by the customer on MyFoundry.
* **Testing:** API testing by users is done using their API keys on API testing tools like Postman, Insomnia etc. using the examples in the API documents.
* **Documentation and Support:** In Phase 2 and Phase 3, a comprehensive API doc/guide containing API use cases is shared to users manually via email. In Phase 4, API documentation is hosted directly on MyFoundry. The Platform team is available for support across all phases.

## 4.6 Ongoing Customer Interaction
After onboarding:
* Customers authenticate using API keys (static in Phase 2, self-generated/managed via MyFoundry in Phase 3 and Phase 4).
* API usage is driven by customer applications (e.g., dashboards, research tools).
* There is no self-service key rotation or management in Phase 2; this capability becomes fully active in Phase 3 and Phase 4 via MyFoundry.
* Errors and issues are resolved via SDF contacts and Platform team support.
* Documentation is static and shared manually in Phase 2 and Phase 3, and becomes dynamic on MyFoundry in Phase 4.

---

## 5. Expected Customer Behaviour
* Users are expected to discover the API through SDF contacts, marketing campaigns, or the MyFoundry portal depending on the release phase.
* Users should initiate access requests via their designated channel (SDF contact or directly on the portal).
* Users must complete all contractual and data access requirements before receiving or generating API credentials.
* Users are expected to use the provided API documentation (emailed or portal-hosted) to guide setup and testing.
* Users should validate their integration using API testing tools (e.g., Postman, Insomnia).
* Users are expected to engage the Platform team via SDF contacts for support and issue resolution.
* Public sector partners are expected to integrate the API into dashboards or operational tools.
* Researchers are expected to use API data strictly within the scope of their approved research.

---

## 6. Impact of Changes
As Phase 2 is the first release, its onboarding model establishes the baseline experience for all users. Phase 3 and Phase 4 step-by-step progressions shift operations toward automation.

Expected outcomes:
* Enables first-time access to EWE data via API for both public sector partners and researchers.
* Supports a controlled and high-touch onboarding approach for early adopters, transitioning smoothly into faster onboarding and greater control.
* Allows the Platform team to closely monitor usage and gather feedback.
* Provides a foundation for future iterations, including the complete automation of onboarding and documentation delivery on MyFoundry.

---

## 7. Backward Compatibility / Existing Customers
Phase 2 is the first release of the API, and there are no existing customers or prior onboarding processes. Phase 3 and Phase 4 maintain backward compatibility by keeping manual onboarding workflows available as an alternative pathway.

---

## 8. Risks and Considerations
* Manual distribution of API keys (Phase 2) and documentation (Phase 2 and Phase 3) introduces operational overhead and potential security risks.
* Users may require additional support due to the absence of guided onboarding tools in early phases.
* Variability in onboarding experience depending on SDF contact handling prior to full portal automation.

---

## 9. Success Metrics
* Time to onboard a customer (request → access granted / key generation).
* Number of onboarded customers per persona.
* API usage (calls per customer).
* Support tickets during onboarding.
* % of successful initial integrations.
* % of users utilizing self-service key generation (Phase 3 and Phase 4).

---

## 10. Open Questions / Decisions
No open questions for these releases.

---

## 11. Appendix
* SDF API user guide 2.1
* MyFoundry Portal Access Guide
