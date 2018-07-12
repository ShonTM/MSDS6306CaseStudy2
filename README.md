# MSDS6306CaseStudy2
MSDS6306 Case Study 2
Contributors: Shon Mohsin, Mallory Hightower, Laura N, Swee Chew

Dataset: Crimedata
http://archive.ics.uci.edu/ml/datasets/Communities+and+Crime

Roles
Shon - Project Manager, git 
Mallory - statistician - recommend tests
Swee - Analyst - minutes, coordination
Laura - Writeup, proof
All - R Code

Project Plan:
1. download data into git repository - Shon
2. create 1 RMD file - Swee 
3. Tidy data - Shon
4. regroup to do exploratory analysis - Group
5. Propose hypotheses
6. vote on hypothesis
7. propose tests
8. agree on ouptout format
9. Writeup - Laura (include structure and formatting)

Change log ## place date and update with changes made
SM 7/1 Created section for Tidy Data work in RMD. Created tidy data ready for analysis

LN 7/9 - upload the metadata files to github.
LN 7/9  Notes team meeting.
Start review the attributes within the rmd file on github.
Plot the Attributes and define what you see.

Laura - Attributes to Review include: (POLICE Attributes)
-- LemasSwornFT: number of sworn full time police officers (numeric - decimal)
-- LemasSwFTPerPop: sworn full time police officers per 100K population (numeric - decimal)
-- LemasSwFTFieldOps: number of sworn full time police officers in field operations (on the street as opposed to administrative etc) (numeric - decimal)
-- LemasSwFTFieldPerPop: sworn full time police officers in field operations (on the street as opposed to administrative etc) per 100K population (numeric - decimal)
-- LemasTotalReq: total requests for police (numeric - decimal)
-- LemasTotReqPerPop: total requests for police per 100K popuation (numeric - decimal)
-- PolicReqPerOffic: total requests for police per police officer (numeric - decimal)
-- PolicPerPop: police officers per 100K population (numeric - decimal)
-- RacialMatchCommPol: a measure of the racial match between the community and the police force. High values indicate proportions in community and police force are similar (numeric - decimal)
-- PctPolicWhite: percent of police that are caucasian (numeric - decimal)
-- PctPolicBlack: percent of police that are african american (numeric - decimal)
-- PctPolicHisp: percent of police that are hispanic (numeric - decimal)
-- PctPolicAsian: percent of police that are asian (numeric - decimal)
-- PctPolicMinor: percent of police that are minority of any kind (numeric - decimal)
-- OfficAssgnDrugUnits: number of officers assigned to special drug units (numeric - decimal)
-- NumKindsDrugsSeiz: number of different kinds of drugs seized (numeric - decimal)
-- PolicAveOTWorked: police average overtime worked (numeric - decimal)
-- LandArea: land area in square miles (numeric - decimal)
-- PopDens: population density in persons per square mile (numeric - decimal)
-- PctUsePubTrans: percent of people using public transit for commuting (numeric - decimal)
-- PolicCars: number of police cars (numeric - decimal)
-- PolicOperBudg: police operating budget (numeric - decimal)
-- LemasPctPolicOnPatr: percent of sworn full time police officers on patrol (numeric - decimal)
-- LemasGangUnitDeploy: gang unit deployed (numeric - decimal - but really ordinal - 0 means NO, 1 means YES, 0.5 means Part Time)
-- LemasPctOfficDrugUn: percent of officers assigned to drug units (numeric - decimal)
-- PolicBudgPerPop: police operating budget per population (numeric - decimal)
-- ViolentCrimesPerPop: total number of violent crimes per 100K popuation (numeric - decimal) GOAL attribute (to be predicted)


