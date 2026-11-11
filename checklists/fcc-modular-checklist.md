# FCC modular approval checklist for host products

Duobay template · free to use · version 2026-10 · status of rules as of October 2026

Use this when your device contains a radio module that already has its own FCC ID (cellular, Wi-Fi, BLE, LoRa and so on). It helps you decide whether you can rely on the module's grant, what you still have to test, and how to label the product.

This is a planning checklist, not legal advice. The FCC laboratory or TCB you hire makes the final call. Primary sources:

- 47 CFR 15.212, Modular transmitters: https://www.ecfr.gov/current/title-47/chapter-I/subchapter-A/part-15/subpart-C/section-15.212
- 47 CFR Part 2, Subpart J, Equipment authorization procedures (including 2.1043 permissive changes and 2.925 / 2.935 identification and electronic labeling): https://www.ecfr.gov/current/title-47/chapter-I/subchapter-A/part-2/subpart-J
- FCC Knowledge Database (KDB), search for publication 996369: https://apps.fcc.gov/kdb/ (check the attachment titles below against the current KDB listing)
  - KDB 996369 D01 Module Equipment Authorization Guide
  - KDB 996369 D02 Module Q&A
  - KDB 996369 D03 OEM Manual (what the module maker must tell integrators)
  - KDB 996369 D04 Module Integration Guide (what the host maker must do)
- KDB 784748 (labeling guidance for Part 15 and Part 18 devices)
- KDB 447498 (RF exposure procedures, including simultaneous transmission)
- FCC Equipment Authorization search: https://www.fcc.gov/oet/ea/fccid

---

## Step 1 · Read the module's grant, not its datasheet

Look up the module's FCC ID and download the grant and the test reports.

- [ ] Grant type: full modular approval, or **limited** modular approval (LMA). An LMA can only be used in the hosts or conditions it names.
- [ ] Rule parts and frequency ranges listed on the grant match the bands you will use (for LTE: Parts 22, 24, 27 and 90 as applicable; for Wi-Fi and BLE: Part 15C or 15E).
- [ ] Output power on the grant is at or above what your firmware will configure.
- [ ] Grant conditions ("grant notes"): read every one. Common ones restrict antenna type and gain, require a minimum separation distance from the body, or say the module may only be used by the grantee or specific OEMs.
- [ ] RF exposure condition: **mobile** (typically 20 cm or more from the body) or **portable** (closer). A body-worn badge, wristband or pocket tracker is portable.
- [ ] The module maker's integration manual (per KDB 996369 D03): antenna list, trace design, required label wording, software restrictions.
- [ ] The module and its manufacturer are not on the FCC Covered List. Since December 26, 2025 the FCC will not authorize equipment that contains covered modules (FCC 25-71: https://docs.fcc.gov/public/attachments/FCC-25-71A1.pdf). As of October 2026 a later order (FCC 26-50, effective October 13, 2026) extends the ban to certain components made by covered entities. Check this for every module and every new build. Covered List: https://www.fcc.gov/supplychain/coveredlist

## Step 2 · Can you rely on the modular grant?

You can usually rely on the module's grant for the intentional-radiator part **only if all of these are true**:

- [ ] You use one of the antennas listed in the grant or manual, of the **same type** and with **equal or lower gain**.
- [ ] The antenna trace, connector and matching follow the module maker's reference design, or the grant explicitly covers your trace design.
- [ ] Your product meets the RF exposure condition on the grant. If the grant says mobile (20 cm) and your device is worn on the body, you **cannot** rely on it for RF exposure without further work.
- [ ] Only one transmitter operates at a time, **or** simultaneous transmission (for example LTE plus Wi-Fi or BLE) has been evaluated. Co-located transmitters often need a new RF exposure evaluation per KDB 447498.
- [ ] Your firmware cannot set power, channels or bands outside what the grant covers, and end users cannot change them.
- [ ] The module is used as delivered: no changes to its RF circuitry, shielding or firmware RF parameters.

If any line is unchecked, plan for one of these paths, in rough order of effort:

1. **Class II permissive change** filed by the module's grantee to add your antenna or use case (47 CFR 2.1043). Needs the module maker's cooperation.
2. **Change in FCC ID** (47 CFR 2.933): you take the module's test data under your own FCC ID with the grantee's permission, then add new tests.
3. **New certification** of the host product as the radio device, under your company's FCC ID.

## Step 3 · What the host product still needs, even with a valid modular grant

- [ ] **Part 15 Subpart B** for the host's unintentional emissions (digital circuits, clocks, switching regulators), usually under Supplier's Declaration of Conformity (SDoC). See KDB 996369 D04.
- [ ] **Host-level verification** that the module, installed in your enclosure next to your circuits, still meets its rules. KDB 996369 D04 describes the checks the host maker should run.
- [ ] **RF exposure** evaluation for your actual use position (SAR for portable devices) where Step 2 shows the grant does not cover it.
- [ ] **PTCRB** certification for cellular devices that will run on AT&T or T-Mobile, even if the module is PTCRB certified: https://www.ptcrb.com/get-certified/
- [ ] **Carrier** certification (for example Verizon's own process; AT&T acceptance after PTCRB).
- [ ] Other approvals your channel needs: UN38.3 for lithium batteries, safety listing (for example UL / IEC 62368-1) if retailers or customers require it.

## Step 4 · Labeling

- [ ] Host label shows the module's identifier in this form: **"Contains FCC ID: XXXYYYYYY"** or **"Contains Transmitter Module FCC ID: XXXYYYYYY"**. Use the exact wording the module manual requires.
- [ ] One line for each certified module inside the product.
- [ ] The Part 15 compliance statement required by 47 CFR 15.19, on the device or, if the device is too small, in the user manual.
- [ ] If the module's label is not visible once installed, the host label above is mandatory.
- [ ] Electronic labeling (e-label) on a display is allowed for devices with an integrated screen under 47 CFR 2.935. Check that the label is reachable within a few steps and cannot be removed by the user.
- [ ] If the device is too small for a physical label, check the small-device provisions in 47 CFR 15.19 and KDB 784748 before deciding to move the label to the manual or packaging.
- [ ] User manual includes the required FCC statements (15.19 and, for Class B digital devices, 15.105) and any RF exposure separation instructions from the module grant.

## Step 5 · Plan the test lab

- [ ] Choose an FCC-recognized accredited lab and a TCB. Confirm the lab's recognition status in the FCC's lab list at the time of testing.
- [ ] Confirm which FCC-recognized lab and TCB will test the device. We use labs outside mainland China, for example Taiwan, Hong Kong or the US.
- [ ] Ask the lab for a pre-scan before formal testing. Fixes after a failed formal test cost more time than a pre-scan.

## Step 6 · Records to keep

- [ ] Module grant, test reports and integration manual, saved with the date downloaded.
- [ ] Your antenna specification and measured gain.
- [ ] Your host test reports and SDoC.
- [ ] RF exposure evaluation.
- [ ] Label artwork as approved.
- [ ] Covered List check, dated, for each build.

---

Questions this checklist cannot answer for your product are what Gate 0 Feasibility is for. Duobay plans the certification path at Gate 0, runs it in your company's name and manages the labs. Lab and certification fees are paid by the client. duobay.ai/why-duobay#fcc-certification · hello@duobay.ai

Duobay is a service of Aximora Labs Inc., a US company.
