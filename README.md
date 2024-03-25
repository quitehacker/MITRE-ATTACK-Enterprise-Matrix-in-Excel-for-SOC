
# Enhanced MITRE ATT&CK® Coverage Tracker

Welcome to the Enhanced MITRE ATT&CK® Coverage Tracker, a streamlined and excel-centric approach designed for Security Operations Centers (SOCs) to manage and measure the coverage of MITRE ATT&CK® tactics and techniques. This project aims to provide SOC analysts and security consultants with a simple, portable, and effective tool for gaining insights into their defensive capabilities against cyber threats.

## Project Goal

The core of this project is the Excel file, `MITRE ATT&CK Enterprise Matrix for SOC.xlsx`, tailored to assess the coverage of MITRE ATT&CK® tactics and techniques based on your detection rules. This tool is crafted for DFIR consultants and SOC analysts working across various environments, offering a unique way to visualize the readiness against attacker tactics and pinpointing areas needing improvement.

## Features of the Coverage Tracker

- **Comprehensive Worksheets**: The Excel workbook is divided into intuitive worksheets, each designed to facilitate different aspects of your analysis. From inputting detection rules to visualizing technique coverage, the worksheets serve as a guide through your ATT&CK® coverage journey.
- **User-Friendly Design**: With a mix of colored headers for ease of navigation - gray for static fields, blue for calculated values, and white for user inputs - the workbook is designed for straightforward use. Focus on white columns for inputs to mark detection rules as active or to map them to specific ATT&CK® techniques.
- **Detailed Guidance**: From adding your first detection rule to understanding the coverage of techniques and sub-techniques, the documentation guides you every step of the way. Visual indicators, such as red for inconsistencies and green for detected techniques, make it easy to assess your SOC's readiness at a glance.

## Getting Started

1. **Detection Rules**: Begin by inputting your detection rules in the 'Detections' worksheet. This crucial step allows you to map your defensive capabilities to specific ATT&CK® techniques and sub-techniques.
2. **Technique Analysis**: Use the 'Techniques' worksheet to see the impact of your detection rules. Address any inconsistencies by ensuring the required data sources are available and correctly mapped.
3. **Coverage Overview**: The 'Status' and 'Coverage' worksheets provide a holistic view of your coverage. They help identify fully covered tactics, partially covered techniques, and areas with no detection rules in place.

## Customization and Updates

- **Adapting to New Techniques**: The workbook is flexible, allowing for the addition of custom detection rules or techniques not included in the standard ATT&CK framework.
- **Disabling Techniques**: Easily disable techniques or sub-techniques not relevant to your environment, ensuring your coverage analysis remains focused and accurate.
- **Data Source Management**: Incorporate custom data sources by updating the 'Sources' worksheet, further tailoring the tracker to your specific needs.

## Future Updates

Stay tuned for updates to the Excel file, including enhancements and expansions to accommodate new versions of the MITRE ATT&CK framework. Your feedback and contributions are welcome to help evolve this tool.

## Credits

Special thanks to Roberto Rodriguez (@Cyb3rWard0g) for the attackcti library, which inspired this project. This tool builds on the foundational work laid by the cybersecurity community to enhance defensive capabilities across the industry.

