**Purpose**: To ensure full YARA coverage on all file types we deem necessary.

**Results**: 

Created a new extension section within Enterprise YARA Solution and added a few file types not included by default to test collection. Specifically, we are looking to see whether three files are collected from our endpoint: 7IsD.gif, Slingshot-2021.10.29.ova, testing.rtf.

We edit the policy in Enterprise YARA Solution indicating it should collect these three new filetypes: .gif, .rtf, .ova

Upon initial investigation, the files were not found within the Enterprise YARA Solution platform. Reached out to Enterprise YARA Solution for more information on this, the explanation was that Enterprise YARA Solution currently does not backscan new file types but plans to in the future. To overcome this and truly test whether these files are collected in the right circumstances, we can force a backscan by following some steps provided by the vendor.

After the backscan completed, results are as follows:
- 7IsD.gif:  This is uploaded and visible in Enterprise YARA Solution.
- Slingshot-2021.10.29.ova: This is neither uploaded nor visible in Enterprise YARA Solution. The reason being, it is a large file and Enterprise YARA Solution does not upload files >512MB. Note that this means the file would also be excluded from any YARA rules and ML model analysis.
- Testing.rtf: This is uploaded and visible in Enterprise YARA Solution.

Hashes:

bdb42d202f9857ca64a8dc03d33702f68c16a7856a0dd27806e333c630b450b6  7IsD.gif

20e6e79919af03de9a49ba62bf0cb5642b545a65cb567e8aa65e3f6612c53c98  Slingshot-2021.10.29.ova

16f40ad452cd381ff78a0e3d7d8ee4d47c03874d27a90354405d8137f91531e0  testing.rtf
