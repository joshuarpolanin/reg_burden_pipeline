# Search Log – A–G Non-HEA Regulatory Scoping

This log documents the searches used to build scoping tables for the A–G regulatory
families. Each entry corresponds to one “search episode” (a small batch of related
queries), so the client can see exactly what we looked for and what artifacts it produced.

## Entry format

- **ID**: Short handle (e.g., A-DOJ-001)
- **Date**: YYYY-MM-DD
- **Bucket**: A, B, C, D, E, F, or G
- **Scope**: Titles/parts/agency focus for this episode
- **Tools**: e.g., eCFR search, web.run (LLM web search), agency-level search
- **Queries / keywords**: Exact strings or close paraphrases of what we searched
- **Filters / exclusions**: Any explicit in/out criteria
- **Outputs**: Files created or updated in `data/` (paths + brief note)

---

## Family A – Civil Rights & Nondiscrimination

### Entry: A-HHS-001
- **Date**: 2025-12-04
- **Bucket**: A
- **Scope**: 45 CFR civil-rights regulations (Subtitle A, Subchapter A) implementing Title VI, Section 504, Title IX, and the Age Discrimination Act for HHS-funded programs.
- **Tools**: eCFR keyword search + general web search
- **Queries / keywords**:
  - `"45 CFR Part 80" "Nondiscrimination Under Programs Receiving Federal Assistance Through the Department of Health and Human Services"`
  - `"45 CFR Part 84" "Nondiscrimination on the Basis of Disability in Programs or Activities Receiving Federal Financial Assistance"`
  - `"45 CFR Part 86" "Nondiscrimination on the Basis of Sex in Education Programs or Activities Receiving Federal Financial Assistance"`
  - `"45 CFR Part 90" "Nondiscrimination on the Basis of Age in Programs or Activities Receiving Federal Financial Assistance"`
- **Filters / exclusions**:
  - Included only general civil-rights parts where the regulated entity is a "program or activity receiving Federal financial assistance" from HHS (i.e., recipients such as universities, academic medical centers).
  - Excluded ED's 34 CFR civil-rights parts (already mapped under Title 34 work).
  - Flagged but did not yet code health-specific nondiscrimination rules (e.g., 45 CFR Part 92) for a potential second HHS episode, since not all IHEs operate health programs.
- **Outputs**:
  - Identified 45 CFR Parts 80, 84, 86, and 90 as core Family A parts with clear IHE incremental burden.
  - These will populate a parent-level Family A table under `data/non_title34/` (e.g., `familyA_HHS_parent_scoping_YYYYMMDD.*`) using the agreed schema.

### Entry: A-DOJ-001
- **Date**: 2025-12-04
- **Bucket**: A
- **Scope**: 28 CFR DOJ civil-rights regulations relevant to IHEs, including ADA Title II/III, Title VI/IX/504/age implementations, and coordination regs.
- **Tools**: eCFR keyword search + general web search
- **Queries / keywords**:
  - `"28 CFR Part 35" "Nondiscrimination on the Basis of Disability in State and Local Government Services"`
  - `"28 CFR Part 36" "Nondiscrimination on the Basis of Disability by Public Accommodations and in Commercial Facilities"`
  - `"28 CFR Part 54" "Nondiscrimination on the Basis of Sex in Education Programs or Activities Receiving Federal Financial Assistance"`
  - `"28 CFR Part 42" "Nondiscrimination in Federally Assisted Programs" "Title VI" "Section 504" "Age Discrimination Act"`
  - `"28 CFR Part 41" "Nondiscrimination on the Basis of Handicap in Federally Assisted Programs"`
- **Filters / exclusions**:
  - Included ADA Title II and Title III parts (28 CFR 35, 36) because they directly regulate public and private universities as public entities/public accommodations.
  - Included DOJ’s Title IX regulation (28 CFR 54) and Title VI/504/Age Act subparts of 28 CFR Part 42 where recipients include IHEs receiving DOJ grants.
  - Included 28 CFR Parts 41 and 42 Subpart F as coordination/agency rules but plan to mark them as `ihe_only_incremental_burden_part = No` since obligations primarily fall on federal agencies.
- **Outputs**:
  - Identified 28 CFR Parts 35, 36, 54, and 42 (Subparts C, G, and I) as core Family A parts with IHE incremental burden when IHEs are DOJ funding recipients.
  - Identified 28 CFR Parts 41 and 42 Subpart F as coordination rules to be tracked but likely excluded from burden quantification.
  - These will populate a parent-level Family A table under `data/non_title34/` (e.g., `familyA_DOJ_parent_scoping_YYYYMMDD.*`) using the agreed schema.

---

## Family B – Student Safety, Crime, and Harassment

### Entry: B-DOJ-001 – Campus Safety / Violence Against Women (OVW Campus Program)

- Date run: 2025-12-04
- Family: B – Student-facing safety, crime, and harassment (non-Title 34)
- Titles searched:
  - Title 28 – Judicial Administration (DOJ)
- Core queries:
  - "28 CFR part 90 Grants to combat violent crimes against women on campuses"
  - "\"Grants to Combat Violent Crimes Against Women on Campuses\" \"28 CFR part 90\""
  - "\"Grants to reduce violent crimes against women on campus\" CFR"
- Key findings:
  - Identified historical DOJ regulations at 28 CFR part 90, subpart E, implementing the Campus Program (grants to combat violent crimes against women on campuses), with extensive campus-focused requirements (policies, training, victim services, data systems, coordination with law enforcement).
  - Confirmed that later DOJ rulemaking removed subpart E as unnecessary, but the underlying program remains authorized at 34 U.S.C. § 20125 and is implemented via OVW grant conditions/NOFOs.
- Disposition for scoping:
  - Add a parent-level row for 28 CFR part 90 (historical Subpart E – Campus Program) to the Family B – DOJ parent table, coded as:
    - `ihe_only_incremental_burden_part = Yes`
    - `in_scope_scoping_part = Yes`
    - `reg_domain = campus_violence_OVW_campus_program`
    - RA notes flag that the detailed regulations are historical and that current requirements are statute/NOFO-based.


---

## Family C – Disability, Access, and Accommodation

### Entry: C-001 – Non-Title-34 Disability/Access Regimes (Beyond Family A)

- **Date**: 2025-12-04
- **Bucket**: C – Disability, access, and accommodation (beyond standard employment law)
- **Scope**: Non-Title-34 Federal disability/accessibility regimes potentially affecting IHEs beyond the ADA/504 civil-rights regulations already captured in Family A.
- **Tools**: eCFR and general web search
- **Queries / keywords** (examples):
  - "36 CFR part 1191 ADA ABA accessibility guidelines"
  - "Architectural Barriers Act accessibility standards facilities designed built altered or leased with federal funds"
  - "36 CFR part 1194 Section 508 standards applicability private sector universities"
  - "24 CFR 100.205 design and construction requirements Fair Housing Act accessibility multifamily housing"
- **Filters / exclusions**:
  - Excluded regimes that apply only to Federal agencies (e.g., Section 508 ICT accessibility standards).
  - Excluded regimes that apply generically to all multifamily housing or all federally funded facilities (e.g., FHA design/construction, ABA standards) because they do not impose IHE-only burden beyond what other landlords or facility owners face.
  - Recognized that ADA Title II/III and Section 504 program-access obligations on IHEs are already represented under Family A.
- **Findings**:
  - No additional non-Title-34 disability/access regulations were identified that (a) are IHE-specific and (b) impose incremental burden beyond the general civil-rights regimes already captured under Family A.
- **Outputs**:
  - `data/non_title34/familyC_parent_scoping_20251204.xlsx` – parent-level table with standard schema and zero rows, documenting that the Family C universe is empty under the current “IHE-only incremental burden” rule.

---

## Family D – Research, Grants, and Sponsored Programs

### Entry: D-HHS-PHS-001 – Core PHS Research Compliance Regimes

- **Date**: 2025-12-04
- **Bucket**: D – Research, grants, and sponsored programs
- **Scope**: HHS/PHS-wide research compliance regulations that impose institutional requirements on universities and academic medical centers conducting PHS-supported research.
- **Titles / parts**:
  - 45 CFR Part 46 – Protection of Human Subjects (Common Rule + Subparts B–E).
  - 42 CFR Part 50, Subpart F – Promoting Objectivity in Research (PHS FCOI for grants/cooperative agreements).
  - 45 CFR Part 94 – Responsible Prospective Contractors (PHS FCOI for contracts).
  - 42 CFR Part 93 – Public Health Service Policies on Research Misconduct.
- **Representative queries / sources**:
  - "45 CFR part 46 Protection of Human Subjects HHS Common Rule"
  - "42 CFR part 50 subpart F Promoting Objectivity in Research PHS financial conflicts of interest"
  - "45 CFR part 94 Responsible Prospective Contractors PHS FCOI"
  - "42 CFR part 93 Public Health Service Policies on Research Misconduct"
- **Filters / exclusions**:
  - Focused on regulations that impose institutional systems-level obligations (IRBs, FWAs, FCOI policies, misconduct procedures) on PHS-supported research organizations.
  - Excluded NIH Grants Policy Statement and other policy documents that implement but do not themselves constitute CFR regulations.
- **Outputs**:
  - `data/non_title34/familyD_HHS_PHS_parent_scoping_20251204.xlsx` – parent-level scoping table with four rows (45 CFR 46; 42 CFR 50 Subpart F; 45 CFR 94; 42 CFR 93), all coded as `ihe_only_incremental_burden_part = Yes` and `in_scope_scoping_part = Yes`.

### Entry: D-FDA-002 – FDA Human-Subjects, IRB, GLP, and Part 11 Regimes

- **Date**: 2025-12-04
- **Bucket**: D – Research, grants, and sponsored programs
- **Scope**: FDA regulations that impose institutional requirements on research organizations (including universities and academic medical centers) conducting FDA-regulated clinical and nonclinical studies.
- **Titles / parts**:
  - 21 CFR Part 50 – Protection of Human Subjects (informed consent for FDA-regulated clinical investigations).
  - 21 CFR Part 56 – Institutional Review Boards (IRB composition, functions, records, and enforcement).
  - 21 CFR Part 58 – Good Laboratory Practice for Nonclinical Laboratory Studies.
  - 21 CFR Part 11 – Electronic Records; Electronic Signatures (Part 11).
- **Representative queries / sources**:
  - "21 CFR Part 50 Protection of Human Subjects FDA informed consent"
  - "21 CFR Part 56 Institutional Review Boards FDA clinical investigations"
  - "21 CFR Part 58 Good Laboratory Practice for Nonclinical Laboratory Studies"
  - "FDA regulations good clinical practice and clinical trials 21 CFR parts 11, 50, 54, 56, 58, 312" 
- **Filters / exclusions**:
  - Focused on research-facing FDA regulations that create institutional compliance systems (IRBs, GLP, validated electronic systems) for FDA-regulated products.
  - Did not enumerate every downstream clinical-trial part (e.g., 21 CFR 312, 314) individually at this stage; treated the core cross-cutting compliance regimes (50, 56, 58, 11) as the primary Family D anchors.
- **Outputs**:
  - `data/non_title34/familyD_FDA_parent_scoping_20251204.xlsx` – parent-level scoping table with four rows (21 CFR 11, 50, 56, 58), all coded `ihe_only_incremental_burden_part = Yes` and `in_scope_scoping_part = Yes`.

### Entry: D-USDA-003 – Animal Welfare Act Research-Facility Regime

- **Date**: 2025-12-04
- **Bucket**: D – Research, grants, and sponsored programs
- **Scope**: USDA Animal and Plant Health Inspection Service (APHIS) regulations implementing the Animal Welfare Act (AWA) for research facilities that use live animals in research, testing, or teaching.
- **Titles / parts**:
  - 9 CFR Part 1 – Definition of Terms (includes definition of “research facility” that explicitly covers higher education institutions using live animals in research and receiving federal funds or using commerce).
  - 9 CFR Part 2 – Regulations (Subpart C – Research Facilities; IACUC, training, veterinary care, recordkeeping, annual reports).
  - 9 CFR Part 3 – Standards (species-specific standards for housing, care, and transportation of covered animals used in research, testing, and teaching).
  - 9 CFR Part 4 – Rules of Practice Governing Proceedings Under the Animal Welfare Act (enforcement procedures).
- **Representative queries / sources**:
  - "9 CFR part 1 definition of terms research facility animal welfare act"
  - "9 CFR part 2 subpart C research facilities IACUC registration annual report"
  - "9 CFR part 3 standards housing facilities dogs and cats nonhuman primates research"
  - "9 CFR part 4 rules of practice governing proceedings under the Animal Welfare Act"
- **Filters / exclusions**:
  - Focused on AWA subchapter A (Parts 1–4), which together define, regulate, and set standards for research facilities using covered species.
  - Excluded transportation-only provisions outside the research context and non-AWA USDA animal-health rules.
- **Outputs**:
  - `data/non_title34/familyD_USDA_parent_scoping_20251204.xlsx` – parent-level scoping table with four rows (9 CFR Parts 1–4). Parts 1–3 coded `ihe_only_incremental_burden_part = Yes`, Part 4 coded `ihe_only_incremental_burden_part = Maybe` and `in_scope_scoping_part = Maybe`.

### Entry: D-EXPORT-004 – ITAR and EAR Export-Control Regimes

- **Date**: 2025-12-04
- **Bucket**: D – Research, grants, and sponsored programs
- **Scope**: Department of State and Department of Commerce regulations that govern exports of defense articles/defense services and dual-use items, including controlled technical data and software arising in university research.
- **Titles / parts (aggregated)**:
  - 22 CFR 120–130 – International Traffic in Arms Regulations (ITAR core: purpose, definitions, U.S. Munitions List, registration, licensing, and related provisions).
  - 15 CFR 730–774 – Export Administration Regulations (EAR core: general provisions, scope, general prohibitions, license exceptions, end-use/end-user controls, special controls, Commerce Control List).
- **Representative queries / sources**:
  - "22 CFR 120 International Traffic in Arms Regulations purpose and definitions"
  - "22 CFR 121 U.S. Munitions List"
  - "22 CFR 122 registration of manufacturers and exporters defense articles"
  - "15 CFR 730 export administration regulations general information"
  - "15 CFR 736 general prohibitions EAR"
  - "15 CFR 774 Commerce Control List"
- **Filters / exclusions**:
  - Treated ITAR and EAR as two aggregated regulatory regimes (core parts only) rather than enumerating every individual part and supplement.
  - Focused on provisions that structure institutional export-control obligations (registration, licensing, control lists, general prohibitions), as they drive the need for campus export-control programs.
- **Outputs**:
  - `data/non_title34/familyD_EXPORT_parent_scoping_20251204.xlsx` – parent-level scoping table with two aggregated rows (ITAR core, EAR core), both coded `ihe_only_incremental_burden_part = Yes` and `in_scope_scoping_part = Yes`.

---

## Family E – Privacy, Data Security, and Records

### Entry: E-GLBA-001 – GLBA Privacy and Safeguards Regimes (FTC)

- **Date**: 2025-12-04
- **Bucket**: E – Privacy, data security, and records
- **Scope**: FTC regulations implementing the Gramm-Leach-Bliley Act (GLBA) privacy and safeguards requirements for financial institutions, including certain colleges and universities that meet the GLBA “financial institution” definition.
- **Titles / parts**:
  - 16 CFR Part 313 – Privacy of Consumer Financial Information (Regulation P).
  - 16 CFR Part 314 – Standards for Safeguarding Customer Information (Safeguards Rule).
- **Representative queries / sources**:
  - "16 CFR part 313 Privacy of Consumer Financial Information Regulation P GLBA"
  - "16 CFR part 314 Standards for Safeguarding Customer Information GLBA Safeguards Rule"
  - "FTC GLBA privacy rule safeguards colleges and universities financial institutions"
- **Filters / exclusions**:
  - Focused on GLBA rules under FTC jurisdiction; did not add bank regulator GLBA rules (OCC, FRB, FDIC) at this stage.
  - Treated colleges and universities as in-scope when they act as GLBA "financial institutions" (e.g., student loan lenders/servicers or providers of other financial products/services), not simply as employers handling HR data.
- **Outputs**:
  - `data/non_title34/familyE_GLBA_parent_scoping_20251204.xlsx` – parent-level scoping table with two rows (16 CFR 313 and 16 CFR 314), both coded `ihe_only_incremental_burden_part = Yes` and `in_scope_scoping_part = Yes`.

### Entry: E-HIPAA-002 – HIPAA Privacy, Security, and Breach Regimes

- **Date**: 2025-12-04
- **Bucket**: E – Privacy, data security, and records
- **Scope**: HIPAA Administrative Simplification regulations that impose privacy, security, and breach-notification obligations on covered entities and business associates, including universities that operate HIPAA-covered health care or health plan components.
- **Titles / parts (aggregated)**:
  - 45 CFR Part 160 – General Administrative Requirements (definitions, applicability, preemption, compliance, enforcement).
  - 45 CFR Part 164 – Security and Privacy:
    - Subpart E – Privacy of Individually Identifiable Health Information (Privacy Rule).
    - Subpart D – Notification in the Case of Breach of Unsecured Protected Health Information (Breach Notification Rule).
    - Subpart C – Security Standards for the Protection of Electronic Protected Health Information (Security Rule).
- **Representative queries / sources**:
  - "45 CFR part 160 HIPAA general administrative requirements"
  - "45 CFR part 164 Security and Privacy Privacy Rule Subpart E"
  - "45 CFR 164.400-414 HIPAA Breach Notification Rule"
  - "HIPAA Security Rule 45 CFR part 160 and subparts A and C of part 164"
- **Filters / exclusions**:
  - Treated Part 164 as two aggregated entries: one for Privacy + Breach (Subparts E and D) and one for Security (Subpart C), rather than creating separate rows for each subpart.
  - Focused on institutional obligations that drive privacy/security programs (policies, NPPs, rights processes, risk analyses, technical safeguards, breach response), not transaction standards in Part 162.
- **Outputs**:
  - `data/non_title34/familyE_HIPAA_parent_scoping_20251204.xlsx` – parent-level scoping table with three rows (45 CFR 160; 45 CFR 164 Privacy/Breach; 45 CFR 164 Security), all coded `ihe_only_incremental_burden_part = Yes` and `in_scope_scoping_part = Yes`.

### Entry: E-OTHER-003 – COPPA and Other Privacy/Data Regimes

- **Date**: 2025-12-04
- **Bucket**: E – Privacy, data security, and records
- **Scope**: Non-GLBA, non-HIPAA privacy/data regulations that might plausibly affect higher education institutions in specialized contexts.
- **Titles / parts considered**:
  - 16 CFR Part 312 – Children's Online Privacy Protection Rule (COPPA Rule).
- **Representative queries / sources**:
  - "16 CFR part 312 Children's Online Privacy Protection Rule COPPA"
  - "Children's Online Privacy Protection Act 15 U.S.C. 6501-6506 online collection of personal information from children"
- **Findings**:
  - COPPA (16 CFR Part 312) regulates the collection, use, and disclosure of personal information from children under 13 by operators of websites or online services directed to children, or with actual knowledge of collecting from under-13 users.
  - Applicability depends on the nature of the online service, not on being an IHE per se. Most higher education institutions will not operate child-directed services as a core function, but some may run camps, outreach programs, or platforms that bring them under COPPA.
- **Filters / exclusions**:
  - Did not identify additional CFR-based, non-GLBA, non-HIPAA privacy/data regimes that clearly impose institution-level obligations on IHEs as IHEs (as opposed to generic online operators or employers).
- **Outputs**:
  - `data/non_title34/familyE_OTHER_parent_scoping_20251204.xlsx` – parent-level scoping table with one row for 16 CFR Part 312 (COPPA Rule), coded `ihe_only_incremental_burden_part = Maybe` and `in_scope_scoping_part = Maybe` to flag that inclusion is a policy decision for the client.

---

## Family F – Employment & Workforce (IHE-specific overlays)

### Entry: F-DHS-001 – SEVP School-Certification and F/M Student Regime (DHS)

- **Date**: 2025-12-04
- **Bucket**: F – Immigration and international education sponsorship
- **Scope**: DHS regulations in 8 CFR Part 214 that govern certification/oversight of schools enrolling F-1 and M-1 students and the F/M student-status rules that institutions must operationalize.
- **Titles / parts (aggregated)**:
  - 8 CFR 214.3 and 214.4 – SEVP certification, recertification, withdrawal, SEVIS petitions, DSOs, recordkeeping, reporting, site visits.
  - 8 CFR 214.2(f) and 214.2(m) – F-1 and M-1 student status conditions (full course of study, reduced course loads, employment/practical training, extensions, etc.).
- **Representative queries / sources**:
  - "8 CFR 214.3 certification of schools for enrollment of F and M nonimmigrants SEVP"
  - "8 CFR 214.4 denial of certification or recertification or withdrawal on notice"
  - "8 CFR 214.2(f) F-1 academic students requirements"
  - "8 CFR 214.2(m) M-1 vocational students requirements"
- **Filters / exclusions**:
  - Focused on F/M school-certification and F/M student-status provisions that create institutional obligations (SEVP, SEVIS, DSOs, compliance monitoring).
  - Did not include unrelated nonimmigrant categories (e.g., H-1B, O-1) at this stage, as those obligations are more generic employer sponsorship rather than IHE-specific regimes.
- **Outputs**:
  - `data/non_title34/familyF_DHS_parent_scoping_20251204.xlsx` – parent-level scoping table with two aggregated rows (SEVP school certification/oversight; F/M student requirements), both coded `ihe_only_incremental_burden_part = Yes` and `in_scope_scoping_part = Yes`.

### Entry: F-DOS-002 – J-1 Exchange Visitor Program Sponsors (Department of State)

- **Date**: 2025-12-05
- **Bucket**: F – Immigration and international education sponsorship
- **Scope**: Department of State regulations in 22 CFR Part 62 that govern the Exchange Visitor Program (J-1), focusing on universities designated as program sponsors for students and scholars.
- **Titles / parts**:
  - 22 CFR Part 62 – Exchange Visitor Program (general provisions plus university-relevant categories such as college and university students, professors, and research scholars).
- **Representative queries / sources**:
  - "22 CFR part 62 Exchange Visitor Program J-1 sponsor requirements"
  - "22 CFR 62.10 sponsor obligations responsible officer SEVIS"
  - "22 CFR 62.23 college and university students"
  - "22 CFR 62.20 professors and research scholars"
- **Filters / exclusions**:
  - Treated Part 62 as a single aggregated regime for university J-1 sponsors (Subpart A plus student/scholar categories).
  - Focused on institutional sponsor obligations (SEVIS records, designation of ROs/AROs, participant monitoring, reporting, insurance, and category-specific rules), not on individual visitor conduct alone.
- **Outputs**:
  - `data/non_title34/familyF_DOS_parent_scoping_20251205.xlsx` – parent-level scoping table with one row for 22 CFR Part 62, coded `ihe_only_incremental_burden_part = Yes` and `in_scope_scoping_part = Yes`.

### Entry: F-OTHER-003 – Other Immigration Sponsorship Regimes

- **Date**: 2025-12-05
- **Bucket**: F – Immigration and international education sponsorship
- **Scope**: Screening for additional immigration regimes that might impose IHE-only incremental burdens beyond SEVP (F/M school certification) and J-1 Exchange Visitor sponsorship.
- **Considerations**:
  - Nonimmigrant worker categories commonly used by universities (e.g., H-1B, O-1, TN, E-3).
  - Any special student or scholar categories not already captured under SEVP (8 CFR 214) or J-1 (22 CFR 62).
- **Findings / disposition**:
  - Employer-based nonimmigrant worker sponsorship regimes (H-1B, O-1, TN, etc.) apply broadly to many types of employers (e.g., hospitals, tech companies, law firms) and do not create IHE-only regulatory frameworks analogous to SEVP or J-1 sponsorship.
  - No additional CFR-based immigration regimes were identified that clearly impose institution-level obligations on higher education institutions as such, beyond the SEVP school-certification/F-M regime and the J-1 Exchange Visitor sponsor regime already captured in F-DHS-001 and F-DOS-002.
- **Outputs**:
  - `data/non_title34/familyF_OTHER_parent_scoping_20251205.xlsx` – parent-level scoping table with the standard schema and zero rows, documenting that the Family F “OTHER” universe is empty under the current 'IHE-only incremental burden' rule.

---

## Family G – Veterans, Military, and Other Federal Education-Benefit Provider Regimes

### Entry: G-VA-001 – VA Education Benefits Institutional Regimes

- **Date**: 2025-12-05
- **Bucket**: G – Veterans/military education benefits and other provider-based education-benefit regimes
- **Scope**: CFR-based VA education-benefit regulations that impose institutional approval, reporting, and compliance obligations on colleges and universities approved to enroll students using VA education benefits.
- **Titles / parts (aggregated)**:
  - 38 CFR Part 21 – Education benefits and institutional administration of educational assistance.
- **What we were looking for**:
  - A coherent CFR “provider/approved school” regime where IHEs face obligations because they are approved VA education-benefit providers (analogous in spirit to Title IV participation systems, but outside Title 34).
- **Representative queries / sources**:
  - "38 CFR Part 21 VA education benefits institutional approval reporting"
  - "State Approving Agencies 38 CFR Part 21"
  - "85/15 rule VA education benefits 38 CFR"
  - "VA compliance surveys educational institutions 38 CFR Part 21"
- **Inclusion logic**:
  - Part 21 creates institution-facing duties tied to VA education-benefit participation:
    - course/program approval (often through State Approving Agencies),
    - certification of enrollments and changes,
    - compliance surveys and oversight,
    - eligibility constraints such as 85/15 and bar-to-approval conditions.
  - These obligations attach to institutions as approved education-benefit providers, not to generic employers.
- **Disposition**:
  - Included as the core Family G VA parent regime.
- **Outputs**:
  - `data/non_title34/familyG_VA_parent_scoping_20251205.xlsx` – parent-level scoping table with one aggregated row for 38 CFR Part 21, coded:
    - `ihe_only_incremental_burden_part = Yes`
    - `in_scope_scoping_part = Yes`


### Entry: G-DOD-002 – DoD Voluntary Education / Tuition Assistance (TA)

- **Date**: 2025-12-05
- **Bucket**: G – Veterans/military education benefits and other provider-based education-benefit regimes
- **Scope**: CFR-based DoD Voluntary Education & Tuition Assistance regulations that create institutional requirements for schools choosing to enroll Service members using TA.
- **Titles / parts (aggregated)**:
  - 32 CFR Part 68 – Voluntary Education Programs.
  - Key institutional obligations are operationalized via:
    - DoD Voluntary Education Partnership MOU (Appendix A to Part 68),
    - Service-specific addenda (Appendices B–E).
- **What we were looking for**:
  - A CFR anchor that captures the institution-as-provider obligations for DoD TA participation.
- **Representative queries / sources**:
  - "32 CFR Part 68 Voluntary Education Programs Tuition Assistance"
  - "DoD Voluntary Education Partnership MOU Appendix A 32 CFR Part 68"
  - "Service-specific addenda Appendix B C D E 32 CFR Part 68"
  - "DoDI 1322.25 voluntary education TA institutions"
- **Inclusion logic**:
  - Institutional obligations appear when an educational institution elects to participate in TA:
    - signing and complying with the standardized MOU,
    - providing meaningful cost/attendance information,
    - adhering to required recruiting and marketing standards,
    - providing defined academic/student support expectations,
    - participating in complaint/quality-assurance processes.
  - This is a provider-based regime that does not apply to typical employers.
- **Disposition**:
  - Included as the core Family G DoD TA/VolEd parent regime.
- **Outputs**:
  - `data/non_title34/familyG_DOD_parent_scoping_20251205.xlsx` – parent-level scoping table with one aggregated row for 32 CFR Part 68, coded:
    - `ihe_only_incremental_burden_part = Yes`
    - `in_scope_scoping_part = Yes`


### Entry: G-OTHER-003 – Other Federal Education-Benefit Provider Regimes

- **Date**: 2025-12-05
- **Bucket**: G – Veterans/military education benefits and other provider-based education-benefit regimes
- **Scope**: Screening for additional CFR-based education-benefit/provider regimes (outside Titles 34 and 38, and outside 32 CFR Part 68) that impose institution-level compliance obligations on IHEs as approved education-benefit providers.
- **What we were looking for**:
  - Other Federal benefit systems requiring institutional approval, reporting, or compliance frameworks for higher education providers.
- **Representative queries / sources**:
  - "CFR education benefits institutional approval non Title 34"
  - "federal tuition assistance regulations CFR"
  - "education benefit provider requirements CFR"
- **Findings / disposition**:
  - No additional clearly CFR-based, IHE-provider regimes were identified that meet the 'IHE-only incremental burden' threshold beyond:
    - 38 CFR Part 21 (VA education benefits),
    - 32 CFR Part 68 (DoD Voluntary Education / TA).
- **Outputs**:
  - `data/non_title34/familyG_OTHER_parent_scoping_20251205.xlsx` – parent-level scoping table with the standard schema and zero rows, documenting that no additional Family G parent regimes were included under the current rule.

---

