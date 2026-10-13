# Sanjeevani AI — Intelligent Snakebite Care Platform

> Project documentation based on the uploaded **Snakebite doc..pdf** (Wellcome Snakebite Innovation Prize application material). This file summarizes the proposed solution as described in that document; it does not claim that planned features are already implemented or clinically validated.

## 1. Project Overview

**Sanjeevani AI** is a proposed AI-assisted snakebite response and care-coordination platform designed to help people in rural and underserved communities access timely, appropriate snakebite care.

The solution aims to connect the person bitten, community responders, ASHA workers, ambulance providers, and receiving hospitals through a coordinated workflow. It combines first-aid guidance, emergency communication, transport coordination, hospital readiness information, and follow-up.

## 2. Problem Statement

Snakebite is a time-critical medical emergency. Delays in recognizing danger, reaching suitable care, arranging transport, and communicating with a hospital can worsen outcomes.

Challenges described in the source document include:

- Limited access to reliable first-aid guidance in local languages.
- Difficulty identifying appropriate treatment facilities quickly.
- Delays in ambulance coordination and transport.
- Poor communication between the patient, responders, ambulance teams, and hospitals.
- Limited connectivity and digital access in some rural communities.
- Gaps in information about symptoms, bite location, travel time, and hospital preparedness.

## 3. Proposed Solution

Sanjeevani AI proposes a mobile-first workflow that can:

1. Provide first-aid instructions in supported local languages.
2. Ask for information about the incident, including symptoms and location.
3. Use AI-assisted snake identification as supplementary information when suitable images are available.
4. Help identify appropriate nearby treatment centres using distance, estimated travel time, and availability information where accessible.
5. Support ambulance coordination and share relevant incident details.
6. Notify the receiving hospital so staff can prepare for the patient's arrival.
7. Support communication among ASHA workers, community responders, ambulance providers, and hospitals.
8. Provide follow-up and anonymised information for service improvement and public-health analysis.

**Safety boundary:** The platform is intended to support rapid access to professional care. It must not delay transport while a user attempts to identify a snake, and it is not a substitute for clinicians or emergency services.

## 4. Intended Users

- People who have experienced a snakebite and their family members or caregivers.
- ASHA workers and community health workers.
- Community responders.
- Ambulance providers and dispatch teams.
- Hospitals and emergency-care staff.
- Public-health organisations and relevant local partners.

## 5. Core Features (Proposed)

### 5.1 Emergency First-Aid Guidance
- Clear, step-by-step guidance in supported local languages.
- Accessible instructions for users with limited technical experience.
- Prominent direction to seek urgent professional medical care.
- Guidance reviewed by qualified medical experts before real-world use.

### 5.2 Incident Reporting
- Capture essential incident details, such as symptoms, approximate time, and location.
- Use voice or simple guided inputs where feasible.
- Share only information needed for emergency response and care coordination.

### 5.3 AI-Assisted Snake Identification
- Optional image-based assistance to suggest a possible snake category.
- Display uncertainty and limitations clearly.
- Never make treatment decisions depend solely on the model's prediction.
- Keep emergency care and transport as the priority.

### 5.4 Treatment-Centre Discovery
- Help locate suitable nearby facilities.
- Consider distance and estimated travel time.
- Display facility information only when it can be verified and kept current.
- Avoid implying that antivenom or other treatment is available unless confirmed by a reliable source.

### 5.5 Ambulance and Hospital Coordination
- Share incident information with relevant responders, subject to consent and applicable emergency rules.
- Help communicate estimated arrival time and relevant patient details.
- Support hospital preparedness and smoother handover.

### 5.6 Follow-Up and Learning
- Support follow-up workflows where appropriate.
- Use anonymised or de-identified data for aggregate analysis only when lawful and properly governed.
- Use feedback from users, ASHA workers, healthcare staff, and community partners to improve usability.

## 6. High-Level User Journey

1. **Open the app or contact a trained responder.**
2. **See urgent first-aid guidance** in a language the user understands.
3. **Request emergency help** and share the incident location if possible.
4. **Record key incident details** without delaying care.
5. **Coordinate transport and identify a suitable receiving facility.**
6. **Send relevant information to the receiving hospital** when possible.
7. **Hand over care to qualified medical professionals.**
8. **Complete appropriate follow-up** and collect feedback for improvement.

## 7. High-Level System Design

The following is a conceptual architecture. The uploaded document does not specify a final implementation stack.

- **User interface:** Mobile-first app with accessible, multilingual screens.
- **Incident service:** Securely records incident details and status.
- **Guidance service:** Presents medically reviewed first-aid content.
- **AI assistance service:** Optional snake-image classification with confidence and limitations displayed.
- **Location and facility service:** Finds facilities and estimates routes using verified data sources.
- **Coordination service:** Supports communication with responders, ambulances, and hospitals.
- **Data and reporting layer:** Provides access-controlled operational records and de-identified aggregate reporting.
- **Security and governance:** Authentication and role-based access, encryption, consent handling, audit logs, retention controls, and incident response procedures.

These are design recommendations, not confirmation that these components have already been built.

## 8. Suggested Technology Stack

The source PDF does not establish a mandatory stack. A possible implementation could use:

| Layer | Possible choice | Purpose |
|---|---|---|
| Mobile frontend | Flutter or React Native | Android-first, cross-platform user experience |
| Web dashboard | React / Next.js | Responder and hospital dashboards |
| Backend API | Node.js with Express or FastAPI | Incident workflows and integrations |
| Database | PostgreSQL or MongoDB | Incident and operational data, selected after requirements analysis |
| AI model service | Python with PyTorch | Image-classification inference and model evaluation |
| Maps and routing | A reliable mapping/routing provider | Facility discovery and estimated travel times |
| Notifications | SMS/voice/push integrations | Emergency workflow updates, subject to local availability |
| Deployment | A compliant cloud or approved hosting environment | Secure hosting, monitoring, backups, and recovery |

Choose technologies only after reviewing connectivity, privacy, cost, local-language support, reliability, and partner integration requirements.

## 9. AI and Model Considerations

If a snake-identification model is developed:

- Evaluate it on representative images from the intended deployment regions.
- Test image quality, lighting, angle, background, and visually similar species.
- Measure per-class precision/recall, confusion matrices, calibration, and failure cases.
- Include an “unable to identify reliably” outcome.
- Do not use model confidence as proof of species identity or venom status.
- Do not use the prediction alone to recommend treatment.
- Maintain versioning, monitoring, expert review, and a process to disable unsafe model versions.

The uploaded document proposes AI-assisted identification but does not establish a particular model, accuracy, or clinically validated performance.

## 10. Safety, Ethics, and Privacy

The application material identifies technical, clinical, operational, and data-protection risks. Mitigations should include:

- **Clinical safety:** Medical-expert review of guidance; clear escalation to professional care; no diagnosis or treatment prescription based only on AI.
- **Model limitations:** Communicate uncertainty; test for misclassification; do not delay emergency response for a photo.
- **Data protection:** Collect the minimum necessary information; restrict access; encrypt data in transit and at rest; set retention and deletion rules.
- **Consent and transparency:** Explain data use in accessible language and obtain appropriate consent where required.
- **Operational reliability:** Plan for poor connectivity, inaccurate location, unavailable ambulances, and outdated facility information.
- **Human oversight:** Keep qualified healthcare professionals responsible for clinical decisions.
- **Governance:** Follow applicable laws, health-data requirements, local approvals, and research ethics processes before pilots or deployment.

## 11. Implementation Roadmap (Indicative)

The source document describes a proposed development and testing period and mentions a working mobile prototype followed by testing and validation. The following phases organise that intent into a practical roadmap; exact dates and deliverables should be confirmed with the team.

### Phase 1 — Discovery and Safety Requirements
- Interview snakebite survivors, caregivers, ASHA workers, ambulance teams, and clinicians.
- Map the current emergency pathway and local referral process.
- Define clinical safety requirements, consent, privacy, and escalation rules.

### Phase 2 — Prototype
- Build core mobile screens and incident reporting.
- Add reviewed first-aid content and basic facility discovery.
- Create a simple responder workflow and status tracking.

### Phase 3 — Coordination Integrations
- Test notifications and workflows with approved partners.
- Add ambulance and hospital handover processes where integrations are feasible.
- Design offline/low-connectivity behaviour.

### Phase 4 — AI Evaluation
- Assemble a properly licensed, representative dataset.
- Evaluate models with domain experts.
- Document limitations and establish a safe fallback.

### Phase 5 — Controlled Pilot
- Conduct usability and workflow testing with trained users.
- Test failure scenarios and emergency escalation.
- Measure response and coordination metrics without claiming clinical impact prematurely.

### Phase 6 — Iteration and Sustainability
- Improve the system based on feedback and evaluation.
- Plan maintenance, partner ownership, funding, training, and long-term operations.

## 12. Evaluation Metrics

Potential metrics to define before a pilot:

- Time from incident report to emergency-help request.
- Time to successful responder contact.
- Time from report to ambulance dispatch, where measurable.
- Time to arrival at an appropriate facility.
- Completeness of hospital handover information.
- Successful completion rate for key app workflows.
- First-aid guidance comprehension and usability.
- Performance and failure rates of any AI component on representative data.
- Availability and freshness of facility information.
- User satisfaction and accessibility across language groups.

These are proposed evaluation measures, not results already achieved.

## 13. Sustainability and Partnerships

The source application discusses collaboration with ASHA workers, healthcare providers, hospitals, ambulance services, NGOs, technology partners, and relevant public-health stakeholders.

A sustainable model should define:

- Who owns and maintains the service.
- How facility and ambulance information is kept current.
- Who trains and supports frontline users.
- How the service is funded after any prize or grant period.
- What data can be shared, with whom, and under what safeguards.
- How the solution will be adapted for different languages and local workflows.

## 14. Current Status and Limitations

According to the uploaded application material, Sanjeevani AI is described as an early-stage idea/prototype concept, with development, testing, and validation planned. The document mentions a target of a working mobile application prototype and a subsequent period of testing and validation.

Do not describe the following as completed unless the team has separate evidence:
- A deployed production application.
- Confirmed ambulance or hospital integrations.
- Verified live antivenom availability.
- Clinically validated snake-identification accuracy.
- Demonstrated reduction in mortality or morbidity.
- Proven impact at scale.

## 15. Team and Responsibilities

The application lists a multidisciplinary team covering AI/ML, backend development, mobile app development, UI/UX, research, testing, and project coordination. Confirm current names, roles, availability, and partner commitments with the team before publishing this section externally.

## 16. Open Questions to Resolve

- Which districts, languages, and user groups will the first pilot serve?
- Which clinicians will review and approve first-aid content?
- What emergency numbers and referral pathways apply in each pilot location?
- How will facility readiness and treatment availability be verified?
- Which ambulance and hospital partners have agreed to participate?
- What happens when mobile data, GPS, or the backend is unavailable?
- What data is essential, who can access it, and when is it deleted?
- What evidence is required before enabling AI-assisted identification in a live workflow?
- Who is responsible for operations, support, and ongoing funding?

## 17. Source

Primary source: **Snakebite doc..pdf**, a 25-page export of the Wellcome Snakebite Innovation Prize application for the proposed solution **Sanjeevani AI**. This Markdown file organises the proposal into project documentation and adds clearly labelled implementation suggestions where the source does not specify technical details.

---

**Document status:** Draft project README / overview. Update it as the design, implementation, partner commitments, safety review, and pilot evidence evolve.
