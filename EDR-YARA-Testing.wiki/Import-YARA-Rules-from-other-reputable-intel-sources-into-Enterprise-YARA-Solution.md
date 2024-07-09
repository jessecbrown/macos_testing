**Purpose**: Provides expanded coverage. Although, we should be careful to use high fidelity sources so that FPs don’t balloon.

**Results**: 

Import is relatively easy via their command line tool. The Enterprise YARA Solution has also announced bulk YARA imports will be added into UI, no timeframe was provided on this. An initial complaint was that we could not separate rules into different compartments which could be used for different levels of detection feasibility or different use cases (threat hunting rules, high fidelity detection rules, detection rules belonging to a particular open source repo, etc). This functionality was later added per our request.


Some suggested rules:
* Paid: Crowdstrike
* Free: Florian Roth, Reversing Labs, Elastic Security, ESET Research, Chronicle, Strangereal Intel, Blackorbird

Another good resource for YARA rule recommendations: https://github.com/InQuest/awesome-yara