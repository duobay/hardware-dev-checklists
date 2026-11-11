# Gate exit checklist

Duobay template · free to use, copy and adapt · version 2026-10

Use this at the end of every hardware development gate, with any vendor. Each gate should end with three things: evidence that the gate's work is done, every file you paid for in your hands, and a clear decision to continue, adjust or stop.

How to use it:

- Tick each line only when you hold the item yourself, in your own storage, not a link to the vendor's drive.
- "Can rebuild" means a person outside the vendor could produce the same output from the files alone.
- Lines marked **(stop if missing)** should block the gate payment or sign-off.

Gate names and typical durations follow Duobay's five-gate model (duobay.ai/how-it-works). Other vendors use EVT / DVT / PVT names; map them to the closest gate.

---

## Every gate (repeat at each one)

- [ ] Written gate report: what was planned, what was done, what changed, open issues. **(stop if missing)**
- [ ] Updated risk register, with owner and next action for each open risk.
- [ ] Change log since the previous gate (requirements, parts, schedule, cost).
- [ ] All source files for work paid so far, in native formats, in your repository or storage. **(stop if missing)**
- [ ] Signed IP assignment or confirmation that the contract's assignment clause has triggered for this gate's work. **(stop if missing)**
- [ ] List of third-party IP, licenses and any vendor-owned "platform" code still inside the design, with license terms.
- [ ] Invoice matches the fixed quote for this gate, or every difference is explained in writing.
- [ ] Fixed quote and scope for the next gate.
- [ ] Decision recorded: continue / adjust / stop, with date and who decided.

---

## Gate 0 · Feasibility (typical 1–2 weeks)

Requirements and architecture

- [ ] Product requirements document: use cases, environment, users, volumes, target retail or contract price.
- [ ] System architecture document: block diagram, chosen SoC / modules, power tree, interfaces, cloud and app boundaries.
- [ ] Power budget with stated assumptions (duty cycle, report interval, recording hours).
- [ ] Data-flow diagram: where every byte goes, which cloud region, who holds the keys.

Cost

- [ ] Costed BOM at the volumes you care about (for example 100, 1,000, 10,000), with sources and dates for prices.
- [ ] Landed DDP cost estimate: unit cost, freight, duties and tariffs by HTS code, brokerage, delivery. (Use the DDP landed-cost worksheet.)
- [ ] NRE estimate for later gates, tooling estimate, certification and lab fee estimate.

Certification and compliance

- [ ] Certification path: FCC rule parts, whether modular approval applies, RF exposure (SAR or MPE), PTCRB and carrier steps if cellular, UN38.3 if lithium battery. (Use the FCC modular checklist.)
- [ ] Module and chip supply-chain check against the FCC Covered List, with a fallback part where risk exists.
- [ ] Privacy and recording-consent requirements if the device has a microphone or camera.

Decision

- [ ] Risk register with the top risks ranked.
- [ ] Clear go / adjust / stop recommendation and the reasons.

Exit check: could you hand these documents to a different engineering firm and get a comparable quote for Gate 1? If not, ask what is missing.

---

## Gate 1 · Works-like prototype (typical 3–6 weeks, 3–5 units)

Hardware

- [ ] 3–5 working units physically delivered to you. **(stop if missing)**
- [ ] Carrier-board schematics and layout source in native CAD format, plus PDF.
- [ ] BOM for the prototype, including evaluation boards and modules used.

Firmware

- [ ] Firmware in your repository, with history, not a zip. **(stop if missing)**
- [ ] Build instructions that a new engineer can follow; toolchain versions pinned.
- [ ] You built the firmware yourself from source and flashed a unit. **(stop if it fails)**

Measurements

- [ ] Measured current in each power state, with the test setup described.
- [ ] Measured latency, audio quality, RF signal or positioning numbers relevant to your use case.
- [ ] Comparison of measured numbers against the Gate 0 targets.

Decision

- [ ] Go / adjust / stop recommendation, and an updated cost and certification view if anything changed.

---

## Gate 2 · EVT, first custom PCB (typical 6–10 weeks, 10–30 units)

Electrical

- [ ] Schematics in native format and PDF.
- [ ] PCB layout source in native format (not only Gerbers). **(stop if missing)**
- [ ] Gerbers, drill files, pick-and-place, assembly drawings, fabrication notes (stack-up, impedance, finish).
- [ ] BOM with manufacturer part numbers, approved alternates and lifecycle status.
- [ ] Antenna design files and matching-network values, with the measurement report.

Mechanical

- [ ] 3D CAD in native format plus STEP. **(stop if missing)**
- [ ] 2D drawings with critical dimensions and tolerances.
- [ ] Enclosure material and finish specification.

Firmware and software

- [ ] Firmware repository with tagged EVT release, build instructions and release notes.
- [ ] OTA update path working and tested, including a failed-update rollback.
- [ ] Device provisioning flow: identities, certificates or keys, and who holds the root keys (you should).
- [ ] Device-side protocol or SDK documentation for your app and cloud teams.
- [ ] Software bill of materials (SBOM) for the firmware, in SPDX or CycloneDX, with licenses.

Test

- [ ] EVT test report: bring-up results, power, RF, functional tests, known defects.
- [ ] 10–30 units delivered, with serial numbers matching the report.

Exit check: give the package to a second factory. Could they quote fabrication and assembly without calling the original vendor?

---

## Gate 3 · DVT / PVT, small batch (typical 8–16 weeks, 10–1,000 units)

Design verification

- [ ] Reliability test reports: drop, temperature, humidity, ingress (IP rating if claimed), button and connector cycles, battery cycle tests.
- [ ] RF pre-scan report and the fixes made.
- [ ] Final certification test reports and grants **in your company's name** (FCC ID grantee code yours, or a documented arrangement). **(stop if missing)**
- [ ] PTCRB and carrier certification letters if cellular.
- [ ] UN38.3 test summary for any lithium battery.

Tooling and production

- [ ] Molds and tooling list with location, owner (you), cavity count, expected life. Tools physically marked with your name. **(stop if missing)**
- [ ] Test fixtures, fixture drawings and fixture software.
- [ ] Production test procedure and pass/fail limits.
- [ ] Assembly work instructions and packaging specification.
- [ ] Locked BOM with second sources for single-source parts, or a written risk acceptance.
- [ ] Yield data from the pilot run, with top defect causes.

Units

- [ ] Near-final or sellable units delivered, with a QC report.
- [ ] Firmware release used in production, tagged, with SBOM.

Exit check: could another contract manufacturer run production from the molds, fixtures, procedures and files you now hold?

---

## Gate 4 · Mass production (ongoing)

Per lot

- [ ] QC report with every lot: incoming, in-process and outgoing inspection results.
- [ ] Serial number and firmware version list for the lot.
- [ ] Shipping documents and DDP invoice that matches the quoted landed price.

Ongoing

- [ ] Rolling forecast agreed, with lead times for critical parts.
- [ ] Buffer stock list for critical parts, and who owns it.
- [ ] End-of-life and lead-time alerts for parts in the BOM.
- [ ] Quarterly cost-down review with proposed changes and their requalification impact.
- [ ] Updated SBOM with every firmware release.

Transfer out (if you leave)

- [ ] Documented handover: every file above, current revisions, open issues.
- [ ] Molds, fixtures and buffer stock released to your new manufacturer.
- [ ] Certification grants and test reports remain valid and in your name.

---

Duobay is a service of Aximora Labs Inc., a US company. This checklist is general guidance, not legal advice. Questions or a review of your current vendor's deliverables: hello@duobay.ai or duobay.ai/start.
