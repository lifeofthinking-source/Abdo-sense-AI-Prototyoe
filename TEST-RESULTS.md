# Verification record

Verified on 21 November 2026.

## Automated checks

- `npm run build`: PASS. Vite produced the static production bundle in `dist/`.
- `npm test`: PASS, 5 tests, 0 failures.
- Covered: appendicitis 62 → 84 score transition, original V1 input/output preservation, explanation changes, independent safety rules, urgent escalation with disease abstention, insufficient/custom-input abstention, unavailable evidence rejection, seed isolation and JSON round-trip.
- Build notes: React Router emitted two non-fatal `use client` directive warnings. No build errors.

## Browser checks

Visited overview, patient queue, new assessment, existing assessment, analysis, report and case history routes.

- PASS: four-step assessment navigation and preserved inputs.
- PASS: nine-region map mouse selection and Enter keyboard selection, including patient-right orientation.
- PASS: appendicitis V1 scores 62/18/12/8; SHAP and LIME tabs; evidence tab; alternative disease selection.
- PASS: load WBC 15,200 and confirmed RLQ tenderness; create V2; updated scores 84/7/5/4; V1 retained at 62 with WBC unknown; comparison and explanation change displayed.
- PASS: finalization disabled until reasoning entered; review and report generated; reviewed status in history after refresh.
- PASS: urgent synthetic case displays all three independent warning flags before prediction; urgency remains urgent with disease ranking withheld; escalation decision saved to report.
- PASS: incomplete synthetic case withholds disease ranking and explanations; missing inputs shown as unknown; further-assessment decision saved to report.
- PASS: new encounter with blank age cannot continue; entered age survives refresh at its saved encounter route.
- PASS: new preset shortcut creates and saves a populated encounter.
- PASS in Chrome: in-page reset confirmation, cancel, confirm and return to initial three encounters / zero reviews.
- No application error logs captured during inspected browser sessions.

## Verification limits

- Print button invokes native `window.print()` and dedicated print CSS is included. The embedded browser's native print interaction blocked browser automation; actual print preview pagination, PDF saving and physical printing were NOT verified. Use Chrome or Edge for the showcase and manually check Print Report there.
- Browser flow checks used the Vite development server. The production bundle built successfully but did not receive a separate browser pass.
- Desktop visuals were inspected. Mobile/device layouts and assistive technologies were not comprehensively tested.
- Storage-denied and quota-exceeded fallback is implemented but was not forced in the browser.
- This is a scripted UI demonstration, with no clinical validation, calibration, real ML inference, real SHAP/LIME execution, or medical performance testing.
