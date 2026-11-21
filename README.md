# AbdoSense AI

Local React / Vite / Tailwind frontend prototype. All encounters are synthetic and all model scores, SHAP and LIME charts are scripted illustrations. No real clinical use, trained model, backend, authentication or external clinical services.

## Run

Requires Node.js 20.19+ or 22.12+.

```powershell
npm install
npm run dev
```

Open the Local URL printed by Vite (normally http://127.0.0.1:5173).

```powershell
npm test
npm run build
npm run preview
```

Hash routing supports direct links without server rewrite configuration.

## Showcase

1. Open Alex Morgan from the queue or load the evolving appendicitis preset.
2. Continue through four steps. The body map supports click, Enter and Space; patient right appears on the viewer's left.
3. Generate the simulated assessment: illustrative appendicitis score 62%. Explore SHAP, LIME and Evidence tabs and select alternative differentials.
4. Add investigation results, load new clinical evidence, then reassess: WBC 15,200 and confirmed tenderness produce an illustrative 84%. V1 remains unchanged; comparison shows the new evidence and explanations.
5. Record a clinician decision and required reasoning. Preview and print the report, then return to dashboard / history.
6. Load emergency warning signs to show the independent safety gate. Load insufficient evidence to show disease-ranking abstention.
7. Refresh to verify persistence. Reset demo data from the sidebar to restore the three initial cases.

## Boundaries

- Safety rules are deliberately illustrative, incomplete and independent from the simulated prediction service. No configured alerts never means a patient is safe.
- Only exact predefined appendicitis inputs (initial or specified update) receive disease scores. Changed or custom inputs withhold rankings; there is no inference model.
- Clinical priority is separate from pain intensity and disease scores. Data completeness counts recorded fields; it is not confidence.
- Each assessment stores a separate copy of inputs, output, version and timestamp. Reassessment invalidates a previous finalized review, requiring review of the latest version. The timeline retains that prior review event.
- Browser localStorage is for fictional data only. Storage failure displays a warning. Reset clears demo encounters after confirmation.
- Printing uses the browser print dialog and print-specific CSS. Choose Save as PDF there if needed.
- Inter is used when installed, with Segoe UI / sans-serif fallback; no external fonts are required.

## Structure

`src/services/mockPredictionService.js`: isolated synthetic scenarios, independent gate and deterministic outputs.

`src/context/EncounterContext.jsx`: shared state and browser persistence.

`src/components/PainMap.jsx`: accessible nine-region SVG.

`src/main.jsx`: shell, dashboard, assessment, analysis/reassessment/review and report routes.

`src/style.css`: responsive desktop-first design and print layout.

## Verification

See `TEST-RESULTS.md` for automated and browser check results and their limits. Run the showcase in Chrome or Edge; native printing could not be fully verified in the embedded browser. The production build and five service tests passed.
