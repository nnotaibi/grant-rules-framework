# Step 2 — Feature Builder Agent (Derived Feature Construction)

This step constructs a derived researcher profile containing semantically meaningful features used for eligibility screening and recommendation.

## Rule Set

**R1 (Career-stage proxy — Senior)**  
IF researcher Y’s `oldest_publication_year ≤ 2015`  
THEN set `career_stage_proxy = Senior`.

**R2 (Career-stage proxy — MCR)**  
IF researcher Y’s `oldest_publication_year ∈ [2016, 2020]`  
THEN set `career_stage_proxy = MCR`.

**R3 (Career-stage proxy — ECR)**  
IF researcher Y’s `oldest_publication_year ≥ 2021`  
THEN set `career_stage_proxy = ECR`.

**R4 (Collaboration readiness)**  
IF researcher Y has `past_arc_linkage > 0`  
THEN set `collaboration_ready = True`.

**R5 (Collaboration readiness)**  
IF researcher Y has `crc_p > 0`  
THEN set `collaboration_ready = True`.

**R6 (Collaboration readiness)**  
IF researcher Y has `num_industry_projects > 0`  
THEN set `collaboration_ready = True`.

**R7 (Industry impact)**  
IF researcher Y has `industry_experience = Yes`  
THEN set `industry_impact = True`.

**R8 (Industry impact)**  
IF researcher Y has `num_industry_projects > 0`  
THEN set `industry_impact = True`.

**R9 (Industry impact)**  
IF researcher Y has `crc_p > 0`  
THEN set `industry_impact = True`.

**R10 (Industry impact)**  
IF researcher Y has `past_arc_linkage > 0`  
THEN set `industry_impact = True`.

**R11 (Grant track record — ARC Discovery)**  
IF researcher Y has `past_arc_discovery > 0`  
THEN set `has_arc_discovery = True`.

**R12 (Grant track record — ARC Linkage)**  
IF researcher Y has `past_arc_linkage > 0`  
THEN set `has_arc_linkage = True`.

**R13 (Active researcher)**  
IF researcher Y has `output_current_lp_present > 0`  
THEN set `active_researcher = True`.

**R14 (Research role proxy)**  
IF researcher Y’s position contains any keyword in  
`{Research, Scientist, Fellow, Lecturer, Professor}`  
THEN set `research_role = True`.

**R15 (Merit tier — High)**  
IF `h_index ≥ 24` OR `citations ≥ 828`  
THEN set `merit_tier = High`.

**R16 (Merit tier — Medium)**  
IF `h_index ≥ 11` OR `citations ≥ 34`  
THEN set `merit_tier = Medium`.

**R17 (Merit tier — Low)**  
IF none of R15–R16 apply  
THEN set `merit_tier = Low`.

**R18 (Field tags from Interest)**  
IF researcher Y’s `interest_text` matches eligible field keywords  
(e.g., engineering, math, statistics, health, natural science)  
THEN set `field_tags = {matched_fields}`;  
ELSE set `field_tags = Unknown`.
