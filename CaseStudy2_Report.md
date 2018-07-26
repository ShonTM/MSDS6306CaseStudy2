---
title: "MSDS 6306 - Case Study 2 Project"
author: "Shon Mohsin and Laura Niederlander"
date: "25 July, 2018"
output:
  html_document:
    keep_md: yes
---



data import and tidy data

Introduction:

Comm



```r
crimedata  <- "http://archive.ics.uci.edu/ml/machine-learning-databases/communities/communities.data"
df <- read.csv(crimedata, header = FALSE)

crimedata <- df 
str(crimedata)
```

```
## 'data.frame':	1994 obs. of  128 variables:
##  $ V1  : int  8 53 24 34 42 6 44 6 21 29 ...
##  $ V2  : Factor w/ 109 levels "?","1","101",..: 1 1 1 58 107 1 79 1 1 1 ...
##  $ V3  : Factor w/ 800 levels "?","100","1000",..: 1 1 1 727 519 1 283 1 1 1 ...
##  $ V4  : Factor w/ 1828 levels "Aberdeencity",..: 796 1626 2 1788 142 1520 840 1462 669 288 ...
##  $ V5  : int  1 1 1 1 1 1 1 1 1 1 ...
##  $ V6  : num  0.19 0 0 0.04 0.01 0.02 0.01 0.01 0.03 0.01 ...
##  $ V7  : num  0.33 0.16 0.42 0.77 0.55 0.28 0.39 0.74 0.34 0.4 ...
##  $ V8  : num  0.02 0.12 0.49 1 0.02 0.06 0 0.03 0.2 0.06 ...
##  $ V9  : num  0.9 0.74 0.56 0.08 0.95 0.54 0.98 0.46 0.84 0.87 ...
##  $ V10 : num  0.12 0.45 0.17 0.12 0.09 1 0.06 0.2 0.02 0.3 ...
##  $ V11 : num  0.17 0.07 0.04 0.1 0.05 0.25 0.02 1 0 0.03 ...
##  $ V12 : num  0.34 0.26 0.39 0.51 0.38 0.31 0.3 0.52 0.38 0.9 ...
##  $ V13 : num  0.47 0.59 0.47 0.5 0.38 0.48 0.37 0.55 0.45 0.82 ...
##  $ V14 : num  0.29 0.35 0.28 0.34 0.23 0.27 0.23 0.36 0.28 0.8 ...
##  $ V15 : num  0.32 0.27 0.32 0.21 0.36 0.37 0.6 0.35 0.48 0.39 ...
##  $ V16 : num  0.2 0.02 0 0.06 0.02 0.04 0.02 0 0.04 0.02 ...
##  $ V17 : num  1 1 0 1 0.9 1 0.81 0 1 1 ...
##  $ V18 : num  0.37 0.31 0.3 0.58 0.5 0.52 0.42 0.16 0.17 0.54 ...
##  $ V19 : num  0.72 0.72 0.58 0.89 0.72 0.68 0.5 0.44 0.47 0.59 ...
##  $ V20 : num  0.34 0.11 0.19 0.21 0.16 0.2 0.23 1 0.36 0.22 ...
##  $ V21 : num  0.6 0.45 0.39 0.43 0.68 0.61 0.68 0.23 0.34 0.86 ...
##  $ V22 : num  0.29 0.25 0.38 0.36 0.44 0.28 0.61 0.53 0.55 0.42 ...
##  $ V23 : num  0.15 0.29 0.4 0.2 0.11 0.15 0.21 0.97 0.48 0.02 ...
##  $ V24 : num  0.43 0.39 0.84 0.82 0.71 0.25 0.54 0.41 0.43 0.31 ...
##  $ V25 : num  0.39 0.29 0.28 0.51 0.46 0.62 0.43 0.15 0.21 0.85 ...
##  $ V26 : num  0.4 0.37 0.27 0.36 0.43 0.72 0.47 0.1 0.23 0.89 ...
##  $ V27 : num  0.39 0.38 0.29 0.4 0.41 0.76 0.44 0.12 0.23 0.94 ...
##  $ V28 : num  0.32 0.33 0.27 0.39 0.28 0.77 0.4 0.08 0.19 0.11 ...
##  $ V29 : num  0.27 0.16 0.07 0.16 0 0.28 0.24 0.17 0.1 0.09 ...
##  $ V30 : num  0.27 0.3 0.29 0.25 0.74 0.52 0.86 0.27 0.26 0.33 ...
##  $ V31 : Factor w/ 98 levels "?","0","0.01",..: 38 24 30 38 53 50 26 20 31 19 ...
##  $ V32 : num  0.41 0.35 0.39 0.44 0.48 0.6 0.36 0.21 0.22 0.8 ...
##  $ V33 : num  0.08 0.01 0.01 0.01 0 0.01 0.01 0.03 0.04 0 ...
##  $ V34 : num  0.19 0.24 0.27 0.1 0.06 0.12 0.11 0.64 0.45 0.11 ...
##  $ V35 : num  0.1 0.14 0.27 0.09 0.25 0.13 0.29 0.96 0.52 0.04 ...
##  $ V36 : num  0.18 0.24 0.43 0.25 0.3 0.12 0.41 0.82 0.59 0.03 ...
##  $ V37 : num  0.48 0.3 0.19 0.31 0.33 0.8 0.36 0.12 0.17 1 ...
##  $ V38 : num  0.27 0.27 0.36 0.33 0.12 0.1 0.28 1 0.55 0.11 ...
##  $ V39 : num  0.68 0.73 0.58 0.71 0.65 0.65 0.54 0.26 0.43 0.44 ...
##  $ V40 : num  0.23 0.57 0.32 0.36 0.67 0.19 0.44 0.43 0.59 0.2 ...
##  $ V41 : num  0.41 0.15 0.29 0.45 0.38 0.77 0.53 0.34 0.36 1 ...
##  $ V42 : num  0.25 0.42 0.49 0.37 0.42 0.06 0.33 0.71 0.64 0.02 ...
##  $ V43 : num  0.52 0.36 0.32 0.39 0.46 0.91 0.49 0.18 0.29 0.96 ...
##  $ V44 : num  0.68 1 0.63 0.34 0.22 0.49 0.25 0.38 0.62 0.3 ...
##  $ V45 : num  0.4 0.63 0.41 0.45 0.27 0.57 0.34 0.47 0.26 0.85 ...
##  $ V46 : num  0.75 0.91 0.71 0.49 0.2 0.61 0.28 0.59 0.66 0.39 ...
##  $ V47 : num  0.75 1 0.7 0.44 0.21 0.58 0.28 0.52 0.67 0.36 ...
##  $ V48 : num  0.35 0.29 0.45 0.75 0.51 0.44 0.42 0.78 0.37 0.31 ...
##  $ V49 : num  0.55 0.43 0.42 0.65 0.91 0.62 0.77 0.45 0.51 0.65 ...
##  $ V50 : num  0.59 0.47 0.44 0.54 0.91 0.69 0.81 0.43 0.55 0.73 ...
##  $ V51 : num  0.61 0.6 0.43 0.83 0.89 0.87 0.79 0.34 0.58 0.78 ...
##  $ V52 : num  0.56 0.39 0.43 0.65 0.85 0.53 0.74 0.34 0.47 0.67 ...
##  $ V53 : num  0.74 0.46 0.71 0.85 0.4 0.3 0.57 0.29 0.65 0.72 ...
##  $ V54 : num  0.76 0.53 0.67 0.86 0.6 0.43 0.62 0.27 0.64 0.71 ...
##  $ V55 : num  0.04 0 0.01 0.03 0 0 0 0.02 0.02 0 ...
##  $ V56 : num  0.14 0.24 0.46 0.33 0.06 0.11 0.13 0.5 0.29 0.07 ...
##  $ V57 : num  0.03 0.01 0 0.02 0 0.04 0.01 0.02 0 0.01 ...
##  $ V58 : num  0.24 0.52 0.07 0.11 0.03 0.3 0 0.5 0.12 0.41 ...
##  $ V59 : num  0.27 0.62 0.06 0.2 0.07 0.35 0.02 0.59 0.09 0.44 ...
##  $ V60 : num  0.37 0.64 0.15 0.3 0.2 0.43 0.02 0.65 0.07 0.52 ...
##  $ V61 : num  0.39 0.63 0.19 0.31 0.27 0.47 0.1 0.59 0.13 0.48 ...
##  $ V62 : num  0.07 0.25 0.02 0.05 0.01 0.5 0 0.69 0 0.22 ...
##  $ V63 : num  0.07 0.27 0.02 0.08 0.02 0.5 0.01 0.72 0 0.21 ...
##  $ V64 : num  0.08 0.25 0.04 0.11 0.04 0.56 0.01 0.71 0 0.22 ...
##  $ V65 : num  0.08 0.23 0.05 0.11 0.05 0.57 0.03 0.6 0 0.19 ...
##  $ V66 : num  0.89 0.84 0.88 0.81 0.88 0.45 0.73 0.12 0.99 0.85 ...
##  $ V67 : num  0.06 0.1 0.04 0.08 0.05 0.28 0.05 0.93 0.01 0.03 ...
##  $ V68 : num  0.14 0.16 0.2 0.56 0.16 0.25 0.12 0.74 0.12 0.09 ...
##  $ V69 : num  0.13 0.1 0.2 0.62 0.19 0.19 0.13 0.75 0.12 0.06 ...
##  $ V70 : num  0.33 0.17 0.46 0.85 0.59 0.29 0.42 0.8 0.35 0.15 ...
##  $ V71 : num  0.39 0.29 0.52 0.77 0.6 0.53 0.54 0.68 0.38 0.34 ...
##  $ V72 : num  0.28 0.17 0.43 1 0.37 0.18 0.24 0.92 0.33 0.05 ...
##  $ V73 : num  0.55 0.26 0.42 0.94 0.89 0.39 0.65 0.39 0.5 0.48 ...
##  $ V74 : num  0.09 0.2 0.15 0.12 0.02 0.26 0.03 0.89 0.1 0.03 ...
##  $ V75 : num  0.51 0.82 0.51 0.01 0.19 0.73 0.46 0.66 0.64 0.58 ...
##  $ V76 : num  0.5 0 0.5 0.5 0.5 0 0.5 0 0 0 ...
##  $ V77 : num  0.21 0.02 0.01 0.01 0.01 0.02 0.01 0.01 0.04 0.02 ...
##  $ V78 : num  0.71 0.79 0.86 0.97 0.89 0.84 0.89 0.91 0.72 0.72 ...
##  $ V79 : num  0.52 0.24 0.41 0.96 0.87 0.3 0.57 0.46 0.49 0.38 ...
##  $ V80 : num  0.05 0.02 0.29 0.6 0.04 0.16 0.09 0.22 0.05 0.07 ...
##  $ V81 : num  0.26 0.25 0.3 0.47 0.55 0.28 0.49 0.37 0.49 0.47 ...
##  $ V82 : num  0.65 0.65 0.52 0.52 0.73 0.25 0.38 0.6 0.5 0.04 ...
##  $ V83 : num  0.14 0.16 0.47 0.11 0.05 0.02 0.05 0.28 0.57 0.01 ...
##  $ V84 : num  0.06 0 0.45 0.11 0.14 0.05 0.05 0.23 0.22 0 ...
##  $ V85 : num  0.22 0.21 0.18 0.24 0.31 0.94 0.37 0.15 0.07 0.63 ...
##  $ V86 : num  0.19 0.2 0.17 0.21 0.31 1 0.38 0.13 0.07 0.71 ...
##  $ V87 : num  0.18 0.21 0.16 0.19 0.3 1 0.39 0.13 0.08 0.79 ...
##  $ V88 : num  0.36 0.42 0.27 0.75 0.4 0.67 0.26 0.21 0.14 0.44 ...
##  $ V89 : num  0.35 0.38 0.29 0.7 0.36 0.63 0.35 0.24 0.17 0.42 ...
##  $ V90 : num  0.38 0.4 0.27 0.77 0.38 0.68 0.42 0.25 0.16 0.47 ...
##  $ V91 : num  0.34 0.37 0.31 0.89 0.38 0.62 0.35 0.24 0.15 0.41 ...
##  $ V92 : num  0.38 0.29 0.48 0.63 0.22 0.47 0.46 0.64 0.38 0.23 ...
##  $ V93 : num  0.46 0.32 0.39 0.51 0.51 0.59 0.44 0.59 0.13 0.27 ...
##  $ V94 : num  0.25 0.18 0.28 0.47 0.21 0.11 0.31 0.28 0.36 0.28 ...
##  $ V95 : num  0.04 0 0 0 0 0 0 0 0.01 0 ...
##  $ V96 : num  0 0 0 0 0 0 0 0 0 0 ...
##  $ V97 : num  0.12 0.21 0.14 0.19 0.11 0.7 0.15 0.59 0.01 0.22 ...
##  $ V98 : num  0.42 0.5 0.49 0.3 0.72 0.42 0.81 0.58 0.78 0.42 ...
##  $ V99 : num  0.5 0.34 0.54 0.73 0.64 0.49 0.77 0.52 0.48 0.34 ...
##   [list output truncated]
```

```r
colnames(crimedata) <- c("state",
"county",
"community",
"communityname ",
"fold",
"population",
"householdsize",
"racepctblack",
"racePctWhite",
"racePctAsian",
"racePctHisp",
"agePct12t21",
"agePct12t29",
"agePct16t24",
"agePct65up",
"numbUrban",
"pctUrban",
"medIncome",
"pctWWage",
"pctWFarmSelf",
"pctWInvInc",
"pctWSocSec",
"pctWPubAsst",
"pctWRetire",
"medFamInc",
"perCapInc",
"whitePerCap",
"blackPerCap",
"indianPerCap",
"AsianPerCap",
"OtherPerCap",
"HispPerCap",
"NumUnderPov",
"PctPopUnderPov",
"PctLess9thGrade",
"PctNotHSGrad",
"PctBSorMore",
"PctUnemployed",
"PctEmploy",
"PctEmplManu",
"PctEmplProfServ",
"PctOccupManu",
"PctOccupMgmtProf",
"MalePctDivorce",
"MalePctNevMarr",
"FemalePctDiv",
"TotalPctDiv",
"PersPerFam",
"PctFam2Par",
"PctKids2Par",
"PctYoungKids2Par",
"PctTeen2Par",
"PctWorkMomYoungKids",
"PctWorkMom",
"NumIlleg",
"PctIlleg",
"NumImmig",
"PctImmigRecent",
"PctImmigRec5",
"PctImmigRec8",
"PctImmigRec10",
"PctRecentImmig",
"PctRecImmig5",
"PctRecImmig8",
"PctRecImmig10",
"PctSpeakEnglOnly",
"PctNotSpeakEnglWell",
"PctLargHouseFam",
"PctLargHouseOccup",
"PersPerOccupHous",
"PersPerOwnOccHous",
"PersPerRentOccHous",
"PctPersOwnOccup",
"PctPersDenseHous",
"PctHousLess3BR",
"MedNumBR",
"HousVacant",
"PctHousOccup",
"PctHousOwnOcc",
"PctVacantBoarded",
"PctVacMore6Mos",
"MedYrHousBuilt",
"PctHousNoPhone",
"PctWOFullPlumb",
"OwnOccLowQuart",
"OwnOccMedVal",
"OwnOccHiQuart",
"RentLowQ",
"RentMedian",
"RentHighQ",
"MedRent",
"MedRentPctHousInc",
"MedOwnCostPctInc",
"MedOwnCostPctIncNoMtg",
"NumInShelters",
"NumStreet",
"PctForeignBorn",
"PctBornSameState",
"PctSameHouse85",
"PctSameCity85",
"PctSameState85",
"LemasSwornFT",
"LemasSwFTPerPop",
"LemasSwFTFieldOps",
"LemasSwFTFieldPerPop",
"LemasTotalReq",
"LemasTotReqPerPop",
"PolicReqPerOffic",
"PolicPerPop",
"RacialMatchCommPol",
"PctPolicWhite",
"PctPolicBlack",
"PctPolicHisp",
"PctPolicAsian",
"PctPolicMinor",
"OfficAssgnDrugUnits",
"NumKindsDrugsSeiz",
"PolicAveOTWorked",
"LandArea",
"PopDens",
"PctUsePubTrans",
"PolicCars",
"PolicOperBudg",
"LemasPctPolicOnPatr",
"LemasGangUnitDeploy",
"LemasPctOfficDrugUn",
"PolicBudgPerPop",
"ViolentCrimesPerPop"
)

head(crimedata)
```

```
##   state county community      communityname  fold population householdsize
## 1     8      ?         ?        Lakewoodcity    1       0.19          0.33
## 2    53      ?         ?         Tukwilacity    1       0.00          0.16
## 3    24      ?         ?        Aberdeentown    1       0.00          0.42
## 4    34      5     81440 Willingborotownship    1       0.04          0.77
## 5    42     95      6096   Bethlehemtownship    1       0.01          0.55
## 6     6      ?         ?   SouthPasadenacity    1       0.02          0.28
##   racepctblack racePctWhite racePctAsian racePctHisp agePct12t21
## 1         0.02         0.90         0.12        0.17        0.34
## 2         0.12         0.74         0.45        0.07        0.26
## 3         0.49         0.56         0.17        0.04        0.39
## 4         1.00         0.08         0.12        0.10        0.51
## 5         0.02         0.95         0.09        0.05        0.38
## 6         0.06         0.54         1.00        0.25        0.31
##   agePct12t29 agePct16t24 agePct65up numbUrban pctUrban medIncome pctWWage
## 1        0.47        0.29       0.32      0.20      1.0      0.37     0.72
## 2        0.59        0.35       0.27      0.02      1.0      0.31     0.72
## 3        0.47        0.28       0.32      0.00      0.0      0.30     0.58
## 4        0.50        0.34       0.21      0.06      1.0      0.58     0.89
## 5        0.38        0.23       0.36      0.02      0.9      0.50     0.72
## 6        0.48        0.27       0.37      0.04      1.0      0.52     0.68
##   pctWFarmSelf pctWInvInc pctWSocSec pctWPubAsst pctWRetire medFamInc
## 1         0.34       0.60       0.29        0.15       0.43      0.39
## 2         0.11       0.45       0.25        0.29       0.39      0.29
## 3         0.19       0.39       0.38        0.40       0.84      0.28
## 4         0.21       0.43       0.36        0.20       0.82      0.51
## 5         0.16       0.68       0.44        0.11       0.71      0.46
## 6         0.20       0.61       0.28        0.15       0.25      0.62
##   perCapInc whitePerCap blackPerCap indianPerCap AsianPerCap OtherPerCap
## 1      0.40        0.39        0.32         0.27        0.27        0.36
## 2      0.37        0.38        0.33         0.16        0.30        0.22
## 3      0.27        0.29        0.27         0.07        0.29        0.28
## 4      0.36        0.40        0.39         0.16        0.25        0.36
## 5      0.43        0.41        0.28         0.00        0.74        0.51
## 6      0.72        0.76        0.77         0.28        0.52        0.48
##   HispPerCap NumUnderPov PctPopUnderPov PctLess9thGrade PctNotHSGrad
## 1       0.41        0.08           0.19            0.10         0.18
## 2       0.35        0.01           0.24            0.14         0.24
## 3       0.39        0.01           0.27            0.27         0.43
## 4       0.44        0.01           0.10            0.09         0.25
## 5       0.48        0.00           0.06            0.25         0.30
## 6       0.60        0.01           0.12            0.13         0.12
##   PctBSorMore PctUnemployed PctEmploy PctEmplManu PctEmplProfServ
## 1        0.48          0.27      0.68        0.23            0.41
## 2        0.30          0.27      0.73        0.57            0.15
## 3        0.19          0.36      0.58        0.32            0.29
## 4        0.31          0.33      0.71        0.36            0.45
## 5        0.33          0.12      0.65        0.67            0.38
## 6        0.80          0.10      0.65        0.19            0.77
##   PctOccupManu PctOccupMgmtProf MalePctDivorce MalePctNevMarr FemalePctDiv
## 1         0.25             0.52           0.68           0.40         0.75
## 2         0.42             0.36           1.00           0.63         0.91
## 3         0.49             0.32           0.63           0.41         0.71
## 4         0.37             0.39           0.34           0.45         0.49
## 5         0.42             0.46           0.22           0.27         0.20
## 6         0.06             0.91           0.49           0.57         0.61
##   TotalPctDiv PersPerFam PctFam2Par PctKids2Par PctYoungKids2Par
## 1        0.75       0.35       0.55        0.59             0.61
## 2        1.00       0.29       0.43        0.47             0.60
## 3        0.70       0.45       0.42        0.44             0.43
## 4        0.44       0.75       0.65        0.54             0.83
## 5        0.21       0.51       0.91        0.91             0.89
## 6        0.58       0.44       0.62        0.69             0.87
##   PctTeen2Par PctWorkMomYoungKids PctWorkMom NumIlleg PctIlleg NumImmig
## 1        0.56                0.74       0.76     0.04     0.14     0.03
## 2        0.39                0.46       0.53     0.00     0.24     0.01
## 3        0.43                0.71       0.67     0.01     0.46     0.00
## 4        0.65                0.85       0.86     0.03     0.33     0.02
## 5        0.85                0.40       0.60     0.00     0.06     0.00
## 6        0.53                0.30       0.43     0.00     0.11     0.04
##   PctImmigRecent PctImmigRec5 PctImmigRec8 PctImmigRec10 PctRecentImmig
## 1           0.24         0.27         0.37          0.39           0.07
## 2           0.52         0.62         0.64          0.63           0.25
## 3           0.07         0.06         0.15          0.19           0.02
## 4           0.11         0.20         0.30          0.31           0.05
## 5           0.03         0.07         0.20          0.27           0.01
## 6           0.30         0.35         0.43          0.47           0.50
##   PctRecImmig5 PctRecImmig8 PctRecImmig10 PctSpeakEnglOnly
## 1         0.07         0.08          0.08             0.89
## 2         0.27         0.25          0.23             0.84
## 3         0.02         0.04          0.05             0.88
## 4         0.08         0.11          0.11             0.81
## 5         0.02         0.04          0.05             0.88
## 6         0.50         0.56          0.57             0.45
##   PctNotSpeakEnglWell PctLargHouseFam PctLargHouseOccup PersPerOccupHous
## 1                0.06            0.14              0.13             0.33
## 2                0.10            0.16              0.10             0.17
## 3                0.04            0.20              0.20             0.46
## 4                0.08            0.56              0.62             0.85
## 5                0.05            0.16              0.19             0.59
## 6                0.28            0.25              0.19             0.29
##   PersPerOwnOccHous PersPerRentOccHous PctPersOwnOccup PctPersDenseHous
## 1              0.39               0.28            0.55             0.09
## 2              0.29               0.17            0.26             0.20
## 3              0.52               0.43            0.42             0.15
## 4              0.77               1.00            0.94             0.12
## 5              0.60               0.37            0.89             0.02
## 6              0.53               0.18            0.39             0.26
##   PctHousLess3BR MedNumBR HousVacant PctHousOccup PctHousOwnOcc
## 1           0.51      0.5       0.21         0.71          0.52
## 2           0.82      0.0       0.02         0.79          0.24
## 3           0.51      0.5       0.01         0.86          0.41
## 4           0.01      0.5       0.01         0.97          0.96
## 5           0.19      0.5       0.01         0.89          0.87
## 6           0.73      0.0       0.02         0.84          0.30
##   PctVacantBoarded PctVacMore6Mos MedYrHousBuilt PctHousNoPhone
## 1             0.05           0.26           0.65           0.14
## 2             0.02           0.25           0.65           0.16
## 3             0.29           0.30           0.52           0.47
## 4             0.60           0.47           0.52           0.11
## 5             0.04           0.55           0.73           0.05
## 6             0.16           0.28           0.25           0.02
##   PctWOFullPlumb OwnOccLowQuart OwnOccMedVal OwnOccHiQuart RentLowQ
## 1           0.06           0.22         0.19          0.18     0.36
## 2           0.00           0.21         0.20          0.21     0.42
## 3           0.45           0.18         0.17          0.16     0.27
## 4           0.11           0.24         0.21          0.19     0.75
## 5           0.14           0.31         0.31          0.30     0.40
## 6           0.05           0.94         1.00          1.00     0.67
##   RentMedian RentHighQ MedRent MedRentPctHousInc MedOwnCostPctInc
## 1       0.35      0.38    0.34              0.38             0.46
## 2       0.38      0.40    0.37              0.29             0.32
## 3       0.29      0.27    0.31              0.48             0.39
## 4       0.70      0.77    0.89              0.63             0.51
## 5       0.36      0.38    0.38              0.22             0.51
## 6       0.63      0.68    0.62              0.47             0.59
##   MedOwnCostPctIncNoMtg NumInShelters NumStreet PctForeignBorn
## 1                  0.25          0.04         0           0.12
## 2                  0.18          0.00         0           0.21
## 3                  0.28          0.00         0           0.14
## 4                  0.47          0.00         0           0.19
## 5                  0.21          0.00         0           0.11
## 6                  0.11          0.00         0           0.70
##   PctBornSameState PctSameHouse85 PctSameCity85 PctSameState85
## 1             0.42           0.50          0.51           0.64
## 2             0.50           0.34          0.60           0.52
## 3             0.49           0.54          0.67           0.56
## 4             0.30           0.73          0.64           0.65
## 5             0.72           0.64          0.61           0.53
## 6             0.42           0.49          0.73           0.64
##   LemasSwornFT LemasSwFTPerPop LemasSwFTFieldOps LemasSwFTFieldPerPop
## 1         0.03            0.13              0.96                 0.17
## 2            ?               ?                 ?                    ?
## 3            ?               ?                 ?                    ?
## 4            ?               ?                 ?                    ?
## 5            ?               ?                 ?                    ?
## 6            ?               ?                 ?                    ?
##   LemasTotalReq LemasTotReqPerPop PolicReqPerOffic PolicPerPop
## 1          0.06              0.18             0.44        0.13
## 2             ?                 ?                ?           ?
## 3             ?                 ?                ?           ?
## 4             ?                 ?                ?           ?
## 5             ?                 ?                ?           ?
## 6             ?                 ?                ?           ?
##   RacialMatchCommPol PctPolicWhite PctPolicBlack PctPolicHisp
## 1               0.94          0.93          0.03         0.07
## 2                  ?             ?             ?            ?
## 3                  ?             ?             ?            ?
## 4                  ?             ?             ?            ?
## 5                  ?             ?             ?            ?
## 6                  ?             ?             ?            ?
##   PctPolicAsian PctPolicMinor OfficAssgnDrugUnits NumKindsDrugsSeiz
## 1           0.1          0.07                0.02              0.57
## 2             ?             ?                   ?                 ?
## 3             ?             ?                   ?                 ?
## 4             ?             ?                   ?                 ?
## 5             ?             ?                   ?                 ?
## 6             ?             ?                   ?                 ?
##   PolicAveOTWorked LandArea PopDens PctUsePubTrans PolicCars PolicOperBudg
## 1             0.29     0.12    0.26           0.20      0.06          0.04
## 2                ?     0.02    0.12           0.45         ?             ?
## 3                ?     0.01    0.21           0.02         ?             ?
## 4                ?     0.02    0.39           0.28         ?             ?
## 5                ?     0.04    0.09           0.02         ?             ?
## 6                ?     0.01    0.58           0.10         ?             ?
##   LemasPctPolicOnPatr LemasGangUnitDeploy LemasPctOfficDrugUn
## 1                 0.9                 0.5                0.32
## 2                   ?                   ?                0.00
## 3                   ?                   ?                0.00
## 4                   ?                   ?                0.00
## 5                   ?                   ?                0.00
## 6                   ?                   ?                0.00
##   PolicBudgPerPop ViolentCrimesPerPop
## 1            0.14                0.20
## 2               ?                0.67
## 3               ?                0.43
## 4               ?                0.12
## 5               ?                0.03
## 6               ?                0.14
```

## Data Set Citations
U. S. Department of Commerce, Bureau of the Census, Census Of Population And Housing 
1990 United States: Summary Tape File 1a & 3a (Computer Files),

U.S. Department Of Commerce, Bureau Of The Census Producer, Washington, DC and 
Inter-university Consortium for Political and Social Research Ann Arbor, Michigan. 
(1992)

U.S. Department of Justice, Bureau of Justice Statistics, Law Enforcement Management 
And Administrative Statistics (Computer File) U.S. Department Of Commerce, Bureau Of 
The Census Producer, Washington, DC and Inter-university Consortium for Political and 
Social Research Ann Arbor, Michigan. (1992)

U.S. Department of Justice, Federal Bureau of Investigation, Crime in the United 
States (Computer File) (1995)

Redmond, M. A. and A. Baveja: A Data-Driven Software Tool for Enabling Cooperative 
Information Sharing Among Police Departments. European Journal of Operational Research 
141 (2002) 660-678. 

## Introduction




```r
library(ggplot2)
##Crime Data HH Size, Violent Crimes per Population, by population, State, MedIncome, Age
 
crimedata.lm <- lm(ViolentCrimesPerPop ~ medIncome, data = crimedata)
newx <- crimedata$medIncome
newx <- sort(newx)

prd_c <- predict(crimedata.lm, newdata = data.frame(medIncome = newx), 
                 interval = c("confidence"), type = c("response"), level = .99) 
prd_p <- predict(crimedata.lm, newdata = data.frame(medIncome = newx), 
                 interval = c("predict"), type = c("response"), level = .99)
```



```r
plot(crimedata$medIncome, crimedata$violentCrimesPerPop, ylab = "Crimes per Population", xlab = "Median Income")
abline(crimedata.lm, col = "red")



lines(newx,prd_c[,2],col = "blue",lty = 2, lwd = 2)
lines(newx,prd_c[,3],col = "blue", lty = 2, lwd = 2)
lines(newx,prd_p[,2],col = "green", lty = 2, lwd = 2)
lines(newx,prd_p[,3],col = "green", lty = 2, lwd = 2)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-3-1.png)<!-- -->



```r
data = crimedata
cdss <- data.frame(crimedata$ViolentCrimesPerPop, crimedata$medIncome, crimedata$agePct12t29, crimedata$blackPerCap,crimedata$HispPerCap, crimedata$RentLowQ, crimedata$PctLess9thGrade)

head(cdss)
```

```
##   crimedata.ViolentCrimesPerPop crimedata.medIncome crimedata.agePct12t29
## 1                          0.20                0.37                  0.47
## 2                          0.67                0.31                  0.59
## 3                          0.43                0.30                  0.47
## 4                          0.12                0.58                  0.50
## 5                          0.03                0.50                  0.38
## 6                          0.14                0.52                  0.48
##   crimedata.blackPerCap crimedata.HispPerCap crimedata.RentLowQ
## 1                  0.32                 0.41               0.36
## 2                  0.33                 0.35               0.42
## 3                  0.27                 0.39               0.27
## 4                  0.39                 0.44               0.75
## 5                  0.28                 0.48               0.40
## 6                  0.77                 0.60               0.67
##   crimedata.PctLess9thGrade
## 1                      0.10
## 2                      0.14
## 3                      0.27
## 4                      0.09
## 5                      0.25
## 6                      0.13
```

```r
str(cdss)
```

```
## 'data.frame':	1994 obs. of  7 variables:
##  $ crimedata.ViolentCrimesPerPop: num  0.2 0.67 0.43 0.12 0.03 0.14 0.03 0.55 0.53 0.15 ...
##  $ crimedata.medIncome          : num  0.37 0.31 0.3 0.58 0.5 0.52 0.42 0.16 0.17 0.54 ...
##  $ crimedata.agePct12t29        : num  0.47 0.59 0.47 0.5 0.38 0.48 0.37 0.55 0.45 0.82 ...
##  $ crimedata.blackPerCap        : num  0.32 0.33 0.27 0.39 0.28 0.77 0.4 0.08 0.19 0.11 ...
##  $ crimedata.HispPerCap         : num  0.41 0.35 0.39 0.44 0.48 0.6 0.36 0.21 0.22 0.8 ...
##  $ crimedata.RentLowQ           : num  0.36 0.42 0.27 0.75 0.4 0.67 0.26 0.21 0.14 0.44 ...
##  $ crimedata.PctLess9thGrade    : num  0.1 0.14 0.27 0.09 0.25 0.13 0.29 0.96 0.52 0.04 ...
```

```r
summary(cdss$crimedata.ViolentCrimesPerPop)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   0.000   0.070   0.150   0.238   0.330   1.000
```




```r
x <- c(1, 1, 2, 2, 3, 3, 4, 4, 5, 5, 1, 1, 2, 2, 3, 3, 4, 4, 5, 5)
y <- c(4, 6, 5, 8, 6, 7, 9, 10, 11, 13, 15, 17, 20, 22, 27, 29, 34, 33, 38, 40)

gender <- factor(c(rep('Male', 10), rep('Female', 10)))
fake.data <- data.frame(x, y, gender)

plot(fake.data$x, fake.data$y, pch = c(2, 3)[as.numeric(fake.data$gender)],
     col=c('red', 'blue')[as.numeric(fake.data$gender)], lwd=2,
     xlab='x', ylab='y')
legend('topleft', c('Male', 'Female'), col=c('red', 'blue'), pch=c(2, 3), 
       lty=NULL, pt.lwd=2)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-5-1.png)<!-- -->

```r
model1 <- lm(y ~ x + gender + x:gender, data=fake.data)
summary(model1)
```

```
## 
## Call:
## lm(formula = y ~ x + gender + x:gender, data = fake.data)
## 
## Residuals:
##    Min     1Q Median     3Q    Max 
## -1.900 -0.825 -0.325  0.900  1.800 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)    
## (Intercept)    9.9500     0.9298  10.701 1.06e-08 ***
## x              5.8500     0.2803  20.867 4.97e-13 ***
## genderMale    -7.1500     1.3149  -5.438 5.48e-05 ***
## x:genderMale  -4.1500     0.3965 -10.467 1.45e-08 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 1.254 on 16 degrees of freedom
## Multiple R-squared:  0.9906,	Adjusted R-squared:  0.9889 
## F-statistic: 564.7 on 3 and 16 DF,  p-value: < 2.2e-16
```

```r
##Set male as the reference level:
fake.data2 <- within(fake.data, gender <- relevel(gender, ref = 'Male'))

model2 <- lm(y ~ x + gender + x:gender, data=fake.data2)
summary(model2)
```

```
## 
## Call:
## lm(formula = y ~ x + gender + x:gender, data = fake.data2)
## 
## Residuals:
##    Min     1Q Median     3Q    Max 
## -1.900 -0.825 -0.325  0.900  1.800 
## 
## Coefficients:
##                Estimate Std. Error t value Pr(>|t|)    
## (Intercept)      2.8000     0.9298   3.011  0.00828 ** 
## x                1.7000     0.2803   6.064 1.64e-05 ***
## genderFemale     7.1500     1.3149   5.438 5.48e-05 ***
## x:genderFemale   4.1500     0.3965  10.467 1.45e-08 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 1.254 on 16 degrees of freedom
## Multiple R-squared:  0.9906,	Adjusted R-squared:  0.9889 
## F-statistic: 564.7 on 3 and 16 DF,  p-value: < 2.2e-16
```

```r
confint(model2)
```

```
##                    2.5 %   97.5 %
## (Intercept)    0.8289084 4.771092
## x              1.1056935 2.294306
## genderFemale   4.3624555 9.937544
## x:genderFemale 3.3095237 4.990476
```

```r
##plot 4 grids
par(mfrow=c(2,2))
plot(model2)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-5-2.png)<!-- -->

```r
class(cdss$crimedata.ViolentCrimesPerPop)
```

```
## [1] "numeric"
```

```r
cdsv <- cdss$crimedata.ViolentCrimesPerPop

hist(cdsv, prob = TRUE, col = "blue", main= "Histogram of Violent Crime Per Population", xlab ="count", ylab="% of Crime per Pop")


curve(dnorm(x, mean=mean(cdsv), sd=sd(cdsv)), add=TRUE,
  col = "blue", main= "Histogram of Violent Crime Per Populatin", xlab ="count", ylab="% of Crime per Pop")
box()



##Scatterplot of the original data
##plot(temp, chirps, ylab = "Chirps Per Minute", xlab = "Temperature")

Income<- cor(crimedata$ViolentCrimesPerPop, crimedata$medIncome)
pop <- cor(crimedata$ViolentCrimesPerPop, crimedata$population)
HH <- cor(crimedata$ViolentCrimesPerPop, crimedata$householdsize)
age1221 <- cor(crimedata$agePct12t21, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-5-3.png)<!-- -->




```r
##high correlation btw crime and age 12-29 at 0.153.

cor(crimedata$agePct12t29, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.1533567
```

```r
cor(crimedata$agePct16t24, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.09934668
```

```r
cor(crimedata$agePct65up, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.06717145
```

```r
cor(crimedata$state, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.2113975
```

```r
corr <- c(Income, pop, age1221)
```


```r
plot(corr)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-7-1.png)<!-- -->

```r
qplot(crimedata$ViolentCrimesPerPop, crimedata$householdsize)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-7-2.png)<!-- -->

```r
## householdsize: mean people per household (numeric - decimal)


qplot(crimedata$ViolentCrimesPerPop, crimedata$population)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-7-3.png)<!-- -->

```r
##population: population for community: (numeric - decimal)


qplot(crimedata$state, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-7-4.png)<!-- -->

```r
##state: US state (by number) - not counted as predictive above, but if considered, should be consided nominal (nominal)


qplot(crimedata$medIncome, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-7-5.png)<!-- -->

```r
##medIncome: median household income (numeric - decimal)


qplot(crimedata$agePct12t21, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-7-6.png)<!-- -->

```r
qplot(crimedata$agePct12t29, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-7-7.png)<!-- -->

```r
qplot(crimedata$agePct16t24, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-7-8.png)<!-- -->

```r
qplot(crimedata$agePct65up, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-7-9.png)<!-- -->

```r
##40% of Age 12-29 concentration around .2 per 100K make up 
##percentage of population that is 12-29 in age (numeric - decimal)
## ViolentCrimesPerPop: total number of violent crimes per 100K popuation (numeric - decimal) GOAL attribute (to be predicted)
```
-- agePct12t21: percentage of population that is 12-21 in age (numeric - decimal)
-- agePct12t29: percentage of population that is 12-29 in age (numeric - decimal)
-- agePct16t24: percentage of population that is 16-24 in age (numeric - decimal)
-- agePct65up: percentage of population that is 65 and over in age (numeric - decimal)



## Data


```r
##Crime Data by Demographic ethnicity

cor(crimedata$whitePerCap, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.2092722
```

```r
cor(crimedata$blackPerCap, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.2753911
```

```r
cor(crimedata$indianPerCap, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.09085382
```

```r
cor(crimedata$AsianPerCap, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.1555917
```

```r
cor(crimedata$HispPerCap, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.2445529
```

```r
qplot(crimedata$whitePerCap, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-8-1.png)<!-- -->

```r
qplot(crimedata$blackPerCap, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-8-2.png)<!-- -->

```r
qplot(crimedata$indianPerCap, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-8-3.png)<!-- -->

```r
qplot(crimedata$AsianPerCap, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-8-4.png)<!-- -->

```r
qplot(crimedata$OtherPerCap, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-8-5.png)<!-- -->

```r
qplot(crimedata$HispPerCap, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-8-6.png)<!-- -->

```r
##blackPerCap, indianPerCap, AsianPerCap, OtherPerCap, HispPerCap, whitePerCap
##householdsize, population, ViolentCrimesPerPop, 
```
-- racepctblack: percentage of population that is african american (numeric - decimal)
-- racePctWhite: percentage of population that is caucasian (numeric - decimal)
-- racePctAsian: percentage of population that is of asian heritage (numeric - decimal)
-- racePctHisp: percentage of population that is of hispanic heritage (numeric - decimal)


```r
##Community Crime Data by Rental levels and population density 

cor(crimedata$RentLowQ, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.2518469
```

```r
cor(crimedata$RentMedian, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.2404937
```

```r
cor(crimedata$RentHighQ, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.2322902
```

```r
cor(crimedata$PopDens, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.2813895
```

```r
cor(crimedata$MedRent, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.2398638
```

```r
cor(crimedata$MedRentPctHousInc, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.3250453
```

```r
cor(crimedata$MedOwnCostPctInc, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.06384668
```

```r
qplot(crimedata$RentLowQ, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-9-1.png)<!-- -->

```r
qplot(crimedata$RentMedian, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-9-2.png)<!-- -->

```r
qplot(crimedata$RentHighQ, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-9-3.png)<!-- -->

```r
qplot(crimedata$PopDens, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-9-4.png)<!-- -->

```r
qplot(crimedata$MedRent, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-9-5.png)<!-- -->

```r
qplot(crimedata$MedRentPctHousInc, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-9-6.png)<!-- -->

```r
qplot(crimedata$MedOwnCostPctInc, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-9-7.png)<!-- -->

```r
##ViolentCrimesPerPop
##PopDens, RentLowQ, RentMedian, RentHighQ, MedRent, MedRentPctHousInc, MedOwnCostPctInc, 
```


```r
##Community crime data based on housing occupancy

cor(crimedata$HousVacant, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.4213958
```

```r
cor(crimedata$PctHousOccup, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.3190097
```

```r
cor(crimedata$PctHousOwnOcc, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.4706826
```

```r
cor(crimedata$PctVacantBoarded, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.4828158
```

```r
cor(crimedata$PctVacMore6Mos, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.02128283
```

```r
qplot(crimedata$HousVacant, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-10-1.png)<!-- -->

```r
qplot(crimedata$PctHousOccup, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-10-2.png)<!-- -->

```r
qplot(crimedata$PctHousOwnOcc, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-10-3.png)<!-- -->

```r
qplot(crimedata$PctVacantBoarded, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-10-4.png)<!-- -->

```r
qplot(crimedata$PctVacMore6Mos, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-10-5.png)<!-- -->

```r
##HousVacant, PctHousOccup, PctHousOwnOcc, PctVacantBoarded, PctVacMore6Mos
## House Occup Higher - Vacant and Boarded lower
```


```r
##Community Crime Data - Education and Employement

cor(crimedata$PctLess9thGrade, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.4110955
```

```r
cor(crimedata$PctNotHSGrad, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.4833659
```

```r
cor(crimedata$PctBSorMore, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.3146752
```

```r
cor(crimedata$PctUnemployed, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.5042346
```

```r
cor(crimedata$PctEmploy, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.3316428
```

```r
cor(crimedata$PctEmplManu, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.044906
```

```r
cor(crimedata$PctEmplProfServ, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.07148261
```

```r
cor(crimedata$PctOccupManu, crimedata$ViolentCrimesPerPop)
```

```
## [1] 0.2955812
```

```r
cor(crimedata$PctOccupMgmtProf, crimedata$ViolentCrimesPerPop)
```

```
## [1] -0.3391092
```

```r
qplot(crimedata$PctLess9thGrade, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-11-1.png)<!-- -->

```r
qplot(crimedata$PctNotHSGrad, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-11-2.png)<!-- -->

```r
qplot(crimedata$PctBSorMore, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-11-3.png)<!-- -->

```r
qplot(crimedata$PctUnemployed, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-11-4.png)<!-- -->

```r
qplot(crimedata$PctEmploy, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-11-5.png)<!-- -->

```r
qplot(crimedata$PctEmplManu, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-11-6.png)<!-- -->

```r
qplot(crimedata$PctEmplProfServ, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-11-7.png)<!-- -->

```r
qplot(crimedata$PctOccupManu, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-11-8.png)<!-- -->

```r
qplot(crimedata$PctOccupMgmtProf, crimedata$ViolentCrimesPerPop)
```

![](CaseStudy2_Report_files/figure-html/unnamed-chunk-11-9.png)<!-- -->

```r
##PctLess9thGrade, PctNotHSGrad, PctBSorMore, PctUnemployed, PctEmploy, PctEmplManu, PctEmplProfServ, PctOccupManu, PctOccupMgmtProf
```
-- PctLess9thGrade: percentage of people 25 and over with less than a 9th grade education (numeric - decimal)
-- PctNotHSGrad: percentage of people 25 and over that are not high school graduates (numeric - decimal)
-- PctBSorMore: percentage of people 25 and over with a bachelors degree or higher education (numeric - decimal)
-- PctUnemployed: percentage of people 16 and over, in the labor force, and unemployed (numeric - decimal)
-- PctEmploy: percentage of people 16 and over who are employed (numeric - decimal)
-- PctEmplManu: percentage of people 16 and over who are employed in manufacturing (numeric - decimal)
-- PctEmplProfServ: percentage of people 16 and over who are employed in professional services (numeric - decimal)
-- PctOccupManu: percentage of people 16 and over who are employed in manufacturing (numeric - decimal) ########
-- PctOccupMgmtProf: percentage of people 16 and over who are employed in management or professional occupations (numeric - decimal)


## Conclusion


