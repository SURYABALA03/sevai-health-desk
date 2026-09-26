# Sevai Health Desk

A mini healthcare support web app for an NGO. Patients and families can request free support, people can register as volunteers, and anyone can ask a question. Every submission is sorted by urgency automatically and gets an instant, personalised reply. A built-in FAQ chatbot answers common questions.

**Live demo:** https://your-site-name.netlify.app  *(replace with your link)*
**Source code:** https://github.com/your-username/sevai-health-desk  *(replace with your link)*

---

## NGO use-case

Small health NGOs usually receive help requests through phone calls, WhatsApp messages and paper forms. Coordinators then have to read every message by hand to decide who needs help first, and the same questions ("Is it free?", "How do I volunteer?") get answered again and again.

Sevai Health Desk gives the NGO one simple place where:

- **Patients and families** request help (doctor consultation, medicines, blood donors, transport, financial aid, elder care, mental health support).
- **Volunteers** register their skills and availability.
- **The public** asks questions or offers donations.
- **Coordinators** see every submission on a dashboard, with urgent cases at the top and a written summary of the day.

## AI / automation idea

The app uses a lightweight, rule-based NLP approach that runs entirely in the browser. It has four parts:

1. **Automatic triage.** When a patient support request is submitted, the description is scanned for warning signs (for example "chest pain", "not breathing", "ICU", "accident") and moderate signs (for example "fever", "dialysis", "running out", "cannot afford"). The patient's age is also considered. Each request gets a **High, Medium or Low** priority, along with the reason, so coordinators know who to call first.
2. **Category detection and routing.** The same text is matched against categories (medicines, transport, blood donation, financial aid and so on), and the request is routed to the right team, even when the person picked a different category in the dropdown.
3. **Auto-response.** Every submission gets an instant personalised reply with a reference number, expected call-back time, the team handling it, and a list of documents to keep ready. High-priority requests include emergency numbers (108/112). Requests that mention self-harm include the Tele-MANAS helpline (14416). Questions sent through the contact form are matched to the FAQ, so the person gets a useful answer right away.
4. **Data summary.** The coordinator dashboard writes a plain-English summary of all submissions: totals, priority breakdown, most requested kinds of help, which high-priority cases to call first, and what volunteers are offering.

Plus a **FAQ chatbot** that matches the user's question against a knowledge base of 12 common questions using keyword scoring. It detects emergencies and crisis messages and responds with helpline numbers instead of a normal answer. Answers can include a button that opens the right form.

## Features

- Three-in-one form: patient support, volunteer registration and contact
- Inline validation with clear error messages (Indian 10-digit mobile numbers, email, age, required fields)
- Instant triage result and auto-generated reply after submitting, with a "Copy reply" button
- Coordinator dashboard: stats, automatic summary, filterable table, CSV export, and a "Load sample data" button for demos
- Floating FAQ chatbot with suggested questions
- Responsive design for mobile, keyboard accessible, respects reduced-motion settings

## Tech stack

| Layer | Technology |
|---|---|
| Structure | HTML5 |
| Styling | CSS3 (custom properties, grid, flexbox), Google Fonts (Bricolage Grotesque, Figtree) |
| Logic | Vanilla JavaScript (ES6+), no frameworks |
| AI / automation | Rule-based NLP: keyword scoring for triage, categorisation and FAQ matching; template-based reply generation |
| Storage | Browser `localStorage` (prototype only) |
| Hosting | Netlify / Vercel (static site) |

No build step, no backend and no API keys are needed.

## Project structure

```
sevai-health-desk/
├── index.html   # Everything: layout, styles (in <style>) and logic (in <script>)
└── README.md
```

## Run locally

Download or clone the repository and open `index.html` in any browser. That's it.

## Deploy

**Netlify:** go to app.netlify.com, choose "Add new site", then "Deploy manually", and drag the project folder in. Or connect your GitHub repo.

**Vercel:** go to vercel.com, choose "Add New Project", import the GitHub repo, keep the default settings ("Other" framework, no build command) and deploy.

## Limitations

- Submissions are stored in each visitor's own browser, so the dashboard only shows data from that browser. This keeps the prototype free of any backend.
- Triage is keyword-based. It can miss urgent cases described in unusual words, or flag non-urgent ones. It is meant to help coordinators prioritise, not to replace their judgement.
- This is a concept prototype and not a medical service.

## Future scope

- Store submissions in Firebase Firestore or Supabase so all coordinators share one dashboard
- Replace keyword triage with an LLM (called through a serverless function so the API key stays private) for better understanding of free text
- Send the auto-reply by SMS, WhatsApp or email
- Tamil and Hindi support for the form and chatbot
- Coordinator login and case status tracking (new, assigned, resolved)

## Author

Swetha G, Amrita University
